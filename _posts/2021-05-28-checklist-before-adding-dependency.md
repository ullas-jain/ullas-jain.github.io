---
title: "Checklist before adding a new dependency to your android-app"
excerpt: "Some dependencies are essential for your app to scale. Some may have adverse effect."
last_modified_at: 2021-05-28T09:45:06-05:00
tags: 
  - release-apk
  - dependencies
toc: true
---
Some dependencies are essential to make your app scale faster. Example - Networking libraries such as Retrofit/OkHttp.

Some dependencies might be good in the initial stages, but they pose problems when,

**Change** -  to new and better libraries.

**Updrade** - to the newer version of same dependency which might come with breaking api changes.

**Maintainance** - Your teammates might not be aware that such a library is added to the code-base.

Hence, we will look at some checklist items that you need to reflect on (possibly fill it and share it with your android-team) before adding the new library.
This also serves as a document that your team could look back on, to understand why this dependency was added in the first place.

## Components Impacted

*What components and modules will be impacted upon adding this library.*

## Usage

*Details on how to use the library.*

## Why do we need XYZ library?

*What problem does it solve?*

*How does the problem affect consumers of the app?*

*Can we achieve this requirement using core-libraries of android or kotlin instead?*


## Adoption strategy.

*Is XYZ library is replacing any other existing library?*
…*if yes, share the details on migration strategy..*

*Rollout strategy : Are we doing a/b testing to make sure it behaves correctly?*
*…share the details on adoption strategy, when do we plan to rollout 100%..*


## What are the alternatives to XYZ library?

*Can we extract just the required functionality and add it instead? If no, why not?*

*Have we verified the open issues/active maintenance.. of the library?*

*What other libraries were considered?*
…*mention pros and cons, build time, apk size…*

*Data on memory profiling*
*..objects allocation..*
*..shallow size..*
*…share the screenshot and mention any other relevant data*

*Why the selected library is better than the other alternatives?*


## What is the impact on adding XYZ library in terms of ?

*APK size of release and debug flavors.*

*Build time on local and CI.*

*Method count that the library adds in release flavor.*

*Performance of the app.*
*…how app behaves while other apps are open in background…*
*.have we checked on the leaks using leak-canary?*


## To have a smooth update of this library with a better alternative in the future.

*Can we create a facade and access library via facade?*


## References

*Github link*
