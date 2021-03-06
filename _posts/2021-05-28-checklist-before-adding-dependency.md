---
title: "Checklist before adding a new dependency to your android-app"
excerpt: "Some dependencies are essential for your app to scale. Some may have an adverse effect."
last_modified_at: 2021-05-28T09:45:06-05:00
tags: 
  - android
  - release-apk
  - dependencies
toc: true
---
Some dependencies are essential to make your app scale faster. Example - Networking libraries such as Retrofit/OkHttp.

Some dependencies might seem good in the initial stages, but they pose problems when,

**Change** -  to newer/better libraries.

**Upgrade** - to the newer version of the same dependency which might come with breaking api changes.

**Maintenance** - Your teammates might not be aware that such a library is added to the code-base.

Hence, we will look at some checklist items that you need to reflect on (possibly fill it and share it with your android-team) before adding a new library.
This also serves as a document that your team could look back on, to understand why this dependency was added in the first place.

## Components Impacted

*What components and modules will be impacted upon adding this library?*

## Usage

*Details on how to use the library.*
*Show me code!*

## Why do we need XYZ library?

*What problem does it solve?*

*How does the problem affect consumers of the app?*

*Can we achieve this requirement using core libraries of android or kotlin instead?*


## Adoption strategy.

*Is XYZ library is replacing any other existing library?* *If yes, share the details on migration strategy.*

*Rollout strategy - Are we doing a/b testing to make sure it behaves correctly?*
*Share the details on adoption strategy, when do we plan to roll out 100%?*


## What are the alternatives to XYZ library?

*Can we extract just the required functionality and add it instead? If no, why not?*

*Have we verified the open issues/active maintenance etc of the library?*

*What other libraries were considered?*
*mention pros and cons, build time, apk size.*

*Data on memory profiling*
*objects allocation*, *shallow size*, *share the screenshot and mention any other relevant data.*

*Why the selected library is better than the other alternatives?*


## What is the impact of adding XYZ library in terms of?

*APK size of release and debug flavors.*

*Build time on local and CI.*

*Method count that the library adds in release flavor.*

*Performance of the app* -
*How the app behaves while other apps are open in the background?*
*Have we checked the leaks using leak-canary after integrating library to the app?*


## To have a smooth update of this library with a better alternative in the future.

*Can we create a facade and access the library via facade?*


## References

*Github link*
