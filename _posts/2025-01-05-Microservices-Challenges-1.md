---
title: "Microservices challenges: Balancing costs and benefits – 1"
published: true
seo_enabled: true
description: "Common challenges in microservices adoption - Part1: Microservices vs. monolith, shared libraries and microservices"
excerpt_text: "Some common challenges I've observed—and helped address, when establishing microservices."
excerpt_image: "/assets/images/posts/2025-01-05-Microservices-Challenges-1/growtika-ZfVyuV8l7WU-unsplash-1.webp"
excerpt_image_copyright: 'Picture by unsplash.com/@growtika'
categories: [Engineering Management, Software Architecture]
tags: [Microservices, API Strategy, Software Team Management]
hidden: false
---

I'll mention some common challenges I've observed—and helped address, when establishing microservices.


## The main reason to use microservices

**Microservices architecture is primarily a solution to a management challenge: improving organizational scalability, by enabling multiple teams to develop, test, and deploy independently.**

Other important benefits of microservices, such as easier integration and with external services, or using different technologies on different parts of the system are also worth remembering.


## Challenges:

### 1. Using Microservices where we shouldn't

Let's remember;
- Microservices don’t mandate full commitment. Depending on the state and requirements, a system with a mix of microservices and monolithic parts could be optimal for a given domain.
- Microservices are inherently expensive; they involve multiple processes, containers, virtual machines, pipelines, data source instances, service discovery mechanisms, network communication overhead and more.


### Sample scenarios

{%- include image.html url="/assets/images/posts/2025-01-05-Microservices-Challenges-1/monolith_space_odyssey_c.webp" description="Sometimes, embracing a monolith lets you rest easy" title="Sometimes, embracing a monolith lets you rest easy" height="320px" -%}

- #### Requirements and API are not yet stable
**Microservices provide flexibility in many areas, but not when it comes to API.**
Changing an API can be a painful and sometimes compromised exercise. When requirements and API are still evolving, starting with a modular monolith can be employed to easily evolve modules and their interactions with each other, whilst avoiding higher cost of microservices.

> A stable, robust API is key to successfully establishing microservices. 

- #### No parallel working teams
When there aren't multiple teams to leverage the [main benefit of using microservices](#the-main-reason-to-use-microservices "Enabling multiple teams to develop, test, and deploy independently"), it might be wiser to avoid associated costs and management overhead. A common practice among startups, where resources are often limited.

- #### Multiple services serving the same or similar domain
Strong  interdependency (tight coupling) between services can occur at inception or during evolution of a system. This manifests as services needing to be deployed and tested together, slowing delivery. When services are managed by separate teams, communication overhead can significantly reduce productivity. A change in design—such as merging them into a single modular service—may be a viable solution.


For a monolithic design to be beneficial and not to bring additional costs when splitting off microservices from it, it should be implemented with a clean design, in a cohesive and modular way. Otherwise, teams may have to rewrite the services from scratch.



### 2. Shared libraries becoming a coupling point

In the early, monolithic stages of system, sharing reusable code by introducing a library is a common practice, improving productivity and consistency.

When applied to a microservices architecture, these libraries may become a common coupling points between services, compromising team autonomy.

{%- include image.html url="/assets/images/posts/2025-01-05-Microservices-Challenges-1/kelly-ziesenis-carter-unsplash-cropped.webp" description="Your library without a clear owner may become a problem" title="Photo by Kelly Ziesenis Carter" -%}

> Clear ownership of services is crucial when establishing microservices.

Over time, with multiple teams making changes, ownership of these libraries may become ambiguous. Since changing or removing existing code from them can disrupt other teams' work, only new code gets added, leading to a bloated codebase.

On top of that, transient dependencies of libraries may lead to dependency conflicts, getting in the way of upgrades and adoption of different technologies. Old code causes accumulation of old dependencies, feeding the issue.

These libraries can also complicate working with external providers; should they depend on the library, or should the library adapt to their API changes over time?

All these issues undermine [the main benefit of using microservices](#the-main-reason-to-use-microservices "Enabling multiple teams to develop, test, and deploy independently").

Some strategies to manage this can be:

  - Developing smaller, atomic libraries with clearly assigned owners.
  - Letting teams maintain their own copy of libraries.
  - Avoiding in-house libraries and allowing some code duplication across services. (This may seem inefficient or controversial, but is much preferable over tight coupling. Service independence is top priority of microservices)
  - Assigning a dedicated team to manage the library. (Can be challenging)

How and where these strategies can be applied can be a topic of another article.


## To be continued

In Part 2, we will continue exploring challenges like API evolution, distributed tracing, and more.
