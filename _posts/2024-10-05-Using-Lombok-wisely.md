---
title: "Using Lombok wisely: Questions to consider"
seo_enabled: true
description: "Risks of using Lombok"
excerpt_text: "Like any tool, Lombok can be useful or misused. Misuse of it is probably what makes Lombok polarizing..."
excerpt_image: /assets/images/posts/2024-10-Using-Lombok-Wisely/banner-lombok.webp
categories: [Programming]
tags: [Java, Lombok, Software Team Management]
redirect_from: "/24/9/Risks-Of-Using-Lombok"
---

Like any tool, Lombok can be useful or misused. Misuse of it is probably what makes Lombok polarizing.

Usefulness of it depends on factors like project requirements, which Lombok annotations are being used etc.

Questions in this article may help to reflect on these factors.


## Is Lombok a language extension?

Lombok generates and hides potentially repetitive code. Since code generating tools cannot introduce new semantics or paradigms to the language, the design of the project cannot (and shouldn't) change by using them.

Whether Lombok can be considered a language extension depends on the perspective; it brings visible syntax changes, but the actual capabilities of the language remains the same.


## Is the improvement only visual?
 
Are we introducing a Lombok annotation because it makes the code look tidy, or is the design exactly the way we want as well? After all, we're still responsible from the hidden code it generates.

Is it better than generating the code using IDE for our particular case? 

Sometimes, this compromise works well; `@EqualsAndHashCode`, can help avoid mistakes when new fields are added to a class, while reducing review time, or, `@Builder` can improve readability, especially on inner classes, without compromising design.

Other times, visual simplicity might come at the expense of better design. As shown in the pseudocode example below, visually appealing alternative with `@AllArgsConstructor` is not better, when it is missing a validation:

{%- include image.html url="/assets/images/posts/2024-10-Using-Lombok-Wisely/AllArgsConstructor_pseudo_sample.webp"  -%}

In some cases, visible code can help with reflecting on design decisions, similar to how explaining code to a rubber duck can be helpful - out of sight can lead to out of mind. Though not every annotation needs this.


## Are we delaying delivery with unproductive discussions?

Developers may have different experiences and opinions about Lombok.

While some annotations can streamline development, others, like `@SneakyThrows` need careful consideration, [as noted by Lombok documentation](https://projectlombok.org/features/SneakyThrows). Lombok also includes experimental annotations, which come with [their own risk](https://projectlombok.org/features/experimental/). Some consider extralinguistic behavior of Lombok risky.

Lombok leaves it to the developers to assess the value of each annotation. This can lead to unproductive debates or longer review times. Since the purpose of Lombok is to boost productivity, it is worth reflecting on these discussions.

One solution can be to align the team on a common approach by having guidelines, such as "We are not using experimental features of Lombok", or encouraging deeper understanding of the tool.
Alternatives like [AutoValue](https://github.com/google/auto) or [Immutables](https://immutables.github.io/) can also be considered.


## Are multiple code manipulation tools in use?

Sometimes multiple tools and libraries can manipulate the code by changing AST or bytecode. 

These can be dependency injection frameworks like Micronout, Quarkus or Dagger, AOP libraries like AspectJ, circuit breakers etc.

Frameworks provide a well-tested bill of materials (BoM), ensuring compatibility between dependencies. Code manipulating libraries outside this set can occasionally lead to subtle issues, especially when multiple tools modify the same class. One time, circuit breakers were silently disabled in our project because of this. 

In such cases, it is a good idea to test these tools against potential interference, and use them cautiously, whether it's Lombok or another code modifying tool.


## Did we consider native Java features instead of `@Builder`, `@With`, etc.?

By the time of writing this article, native withers for records are in development: [JEP-468](https://openjdk.org/jeps/468).

For builders: Named arguments like in Kotlin probably won't come to Java, but Project Valhalla's [value classes](https://openjdk.org/jeps/401) will promote domain driven design solutions (less primitive obsession), allowing for safer to constructors, which reduces the need for builders - perhaps a topic for another article.

If these features are present by the time you're reading, consider using them.

Also, consider using records, instead of `@Value` and similar annotations, not only to reduce boilerplate, but to take advantage of the new semantics they introduce, which allow for efficient memory usage, pattern matching, decomposition and more.


## Final thoughts

Not using Lombok won't improve the design, but misusing or overusing it won't boost productivity.

I hope this article can help with finding the right balance for your team and project.
