---
layout: page
title: "Home"
permalink: /
---

# Open Source Software at Wanderu

At Wanderu, we rely heavily on Open Source software. We consider it
important to contribute to a healthy Open Source ecosystem.

Over time, team members at Wanderu have created Open Source
projects that we use in-house to solve problems. You can find most
of those projects in this github repository.

## wanderu.commander: Python CLI Generation

wanderu.commander is a Python module that wraps ArgParse and
creates an easy to use and read CLI experience. It uses
directory structure to specify commands and decorators
for simple argument specification.

Project here: [wanderu.commander](https://github.com/Wanderu/wanderu.commander)

## Bamboo Queuing System

We had a need at Wanderu to evolve an existing queuing system and
migrating to a completely new model was too much work. After some
time we had built a completely independent job queuing system
based on redis. We had a few needs that other queuing systems
were not able to satisfy. Some of the features that this system
has includes:

- Distributed workers (enforced by the protocol)
- Global rate limits (max number of simultaneous workers) specified
on a per-named queue basis.
- Ack/Fail/Recover capability
- Multiple named queues
- Priority queues (some jobs should be completed before others)
  - Ability to requeue at a higher priority
- Scheduling (release job for work at a specified time)
- Rescheduling on failure
- Dead letter queue after failure
- At least once processing
- Multiple language support (Python, Twisted Async Python,
Node/Javascript, golang)
- Visibility into what work is being done and what work is scheduled

All of these features are built into the queuing system itself.
The system is based on a set of Lua scripts that run atomically on
redis.

- Base redis lua scripts: [bamboo-scripts](https://github.com/Wanderu/bamboo-scripts)
- Python Library: [wanderu.bamboo](https://github.com/Wanderu/wanderu.bamboo)
- Javascript Library: [jsbamboo](https://github.com/Wanderu/jsbamboo)
- Go Library: [go-bamboo](https://github.com/Wanderu/go-bamboo)

## Bandit PyTest Plugin

We use pytest at Wanderu (or are migrating from nose to it).
We also use [bandit](https://github.com/PyCQA/bandit) as a way
to find security issues in projects. We developed a plugin for
pytest to run bandit along with the test suite.

Project here: [pytest-bandit](https://github.com/Wanderu/pytest-bandit)
