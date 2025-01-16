---
title: "Microservices Challenges: Balancing Costs and Benefits – Part 2"
published: false
seo_enabled: false
description: "Discover key challenges in microservices adoption, from API evolution to team autonomy, and learn strategies to balance costs and benefits effectively."
#excerpt_text: "We’ll explore some common challenges organizations face when implementing microservices"
excerpt_image: "/assets/images/posts/2025-01-05-Microservices-Challenges-1/growtika-ZfVyuV8l7WU-unsplash-1.webp"
excerpt_image_copyright: 'Picture by unsplash.com/@growtika'
categories: [Engineering Management, Software Architecture]
tags: [Microservices, API Strategy, Team Autonomy]
hidden: true
---

We’ll continue


### 3. Missing distributed tracing

The cost of missing distributed tracing is 

- Longer troubleshooting times.
- Missed inefficient API calls  
- Longer onboarding period
- 

// TODO

Original team worked on implementing the system in microservices knows it intimately. They know by heart, how a particular kind of request flows thorough the services, they know where to look, if a problem occurs.

At this stage, distributed tracing (filtering logs across services for a particular request) may be considered as something optional, since it doesn't seem to add direct value to the business.

Later, when multiple teams add more services and functionalities, map of the system may become harder to     
When a problem occurs, which (logs of) services to look, they know how a particular kind of request flows thorough the web of services, where to add a new functionality. Implementing distributed tracing may seem as a low priority task, since it isn't something that adds a direct value to the business. 

### 4. Missing API Evolution strategy / system
As mentioned earlier, stable API is the backbone of microservices architecture, yet

// TODO

### 5. Heavy usage of synchronous architecture (or under utilizing event driven )
// TODO

### 6. Not separating databases (Or using shared, normalized data source)
// TODO

## Conclusion
// TODO




#### The following can assist in managing libraries within microservices:

- If domain-wide libraries are used, they should:
    - Owned by a designated team, responsible for maintaining the library, reviewing, and merging pull requests, including those created by other teams.
    - Maintain a clearly defined scope of functionality.
    - Avoid introducing unnecessary transient dependencies.
- Libraries limited to a team scope typically pose fewer problems, allowing teams to make changes to their own library freely.


## Establish an API evolution strategy early on

A well-designed microservices architecture has two main pillars:

- Good separation of concerns between the services: Each service performs a distinct task within the business domain.
- Robust API: This contract between services (and clients), which enables efficient task execution without restricting independent service development.

Even with a good initial API design, changes will inevitably be necessary over time.

Modifying the API freely isn't viable as it risks disrupting communication between services and their consumers.

This problem is more apparent on point-to-point architecture (usually synchronous protocols like REST or gRPC), since the API itself builds more rigid dependency between services, but asynchronous, publish / subscribe architecture needs to be evolved as well.

One approach is to avoid changing or removing anything from the API, only adding to it. While this will work, it can lead to a less understandable domain over time, particularly for new team members.

Alternatively, API versioning can be implemented. Changes are made to a new version of the API, with both old and new versions running simultaneously. Consumers are notified of the change, and once it's certain that the older API is no longer in use, it can be removed.

While technologies like Hypermedia can aid in (synchronous) API evolution, but AFAIK, there isn't a comprehensive protocol, library, or tool specifically designed for the purpose of API evolution and expiration.

Therefore, good traceability of the request flow and a policy (a management process) is needed for API evolution and expiration.

<br>



_Will continue with traceability on Part 2_