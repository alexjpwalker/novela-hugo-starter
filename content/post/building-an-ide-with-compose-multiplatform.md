---
timeToRead: 7
authors: []
title: Building an IDE with Compose Multiplatform
excerpt: 'Since September 2021, we’ve been building on a vision: we wanted people
  developing with TypeDB to have a better integrated development environment.'
date: 2022-11-30T00:00:00+00:00
hero: "/images/1_a96kt0stoxkn7s8dcxfadw.webp"

---
TypeDB Studio

This time last year, our existing graphical interface for [TypeDB](https://github.com/vaticle/typedb) only allowed for the running of simple queries. We wanted to replace it with something expansive that gave our users a top-down view of their entire database. Building this product, an integrated development environment (IDE), is no mean feat. We had to find a flexible, multiplatform user interface (UI) framework that could handle what members of the [TypeDB community](https://vaticle.com/discord) were going to throw at it.

### Goodbye Electron…

There are a few UI frameworks that fit this description and are very popular choices right now, the most notable of which is [Electron](https://www.electronjs.org/). We built our previous UI, Workbase, on Electron with [Vue.js](https://vuejs.org/) but found it did not scale well with the complexity of the application.

When searching for a new framework there were, naturally, a lot of considerations to make and constraints to meet. We wanted to be able to use a language that had strong support for multithreading and a sensible build system, and JavaScript doesn’t quite fit the bill compared to a more mature language such as Java. Java has [concurrency](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/concurrent/package-summary.html) and type safety at the heart of the language and uses them as guiding principles, rather than having been added [iteratively](https://nodejs.org/api/worker_threads.html) [at a later stage](https://www.typescriptlang.org/). As such, using these features during development is easier and makes for a smoother experience.

There are, of course, things about Java that are not ideal. Principally, it is quite verbose. Also, the type system is far from perfect: for example we’d rather avoid the infamous ‘null’, a “[Billion Dollar Mistake](https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/)”. The various UI frameworks for Java are also fairly old (e.g. Swing released in 1998, JavaFX released in 2008) and haven’t been brought up to speed with the latest in modern UI development.

While we were looking for solutions to this dilemma, we came across a new kid on the block.

### Hello Compose Multiplatform!

First, there was [Jetpack Compose](https://developer.android.com/jetpack/compose), which was created by Google for building interfaces for Android applications. Jetpack Compose follows a declarative design model akin to Vue and [Angular](https://angular.io/) and has the ability to make intelligent choices about which parts of the UI to ‘recompose’ based on changes to the underlying state of the program. Then came [Compose Multiplatform](https://www.jetbrains.com/lp/compose-mpp/), the result of collaboration between Google and JetBrains, the creators of our favourite IDEs like [IntelliJ IDEA](https://www.jetbrains.com/idea/). We loved Compose Multiplatform for bringing the latest UI development patterns used in creating Android applications to the desktop.

![](https://miro.medium.com/max/1400/0*8-sH9Mgjv7MkNZvx.png)

Example applications built with Compose Multiplatform.

Lorem ipsum dolor sit amet