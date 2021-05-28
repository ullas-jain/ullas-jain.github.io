---
title: "Know what dependencies are present in your release-apk."
excerpt: "So you want to know what dependencies are present in your release-apk."
last_modified_at: 2021-05-03T09:45:06-05:00
tags: 
  - release-apk
  - dependencies
  - android-gradle-plugin
  - android/sunflower
toc: true
---

No, we are not going to reverse engineer the release-apk. _Not today._

This is more of a sanity verification to make sure everything is 
baked according to standards in the final release-apk.

## Why ?

With multiple engineers pushing code everyday to a massive project, it is easy to miss those un-necessary libraries that are being baked into release-apk. 

Example: 
Test libraries like `junit` or `mockito`.
Debug target libraries like `chuck` 

## Prerequisites

- An Android project having [gradle](https://gradle.org/) as it's build system.
- Project should have [Android-gradle-plugin](https://developer.android.com/studio/releases/gradle-plugin) version `4.0.0` or higher (defined in the project's build.gradle, inside `buildScript { }` block).

## Show me code

Let's inspect the same with android's famous open-sourced project [android/sunflower](https://github.com/android/sunflower).
We can see that `sunflower` project is having [android-gradle-plugin version >= 4.0.0](https://github.com/android/sunflower/blob/main/build.gradle#L62)

Step 1: Clone the repository using HTTPS or SSH.

```shell
git clone git@github.com:android/sunflower.git
```

Step 2: Navigate to `android/sunflower` and assemble the release variant.

```shell
./gradlew :app:assembleRelease
```

Step 3: After assembling the app, navigate to project's build/outputs folder to find the *magical* `sdkDependency.txt`

```shell
cd /sunflower/app/build/outputs/sdk-dependencies/release
```

Generated `sdkDependency.txt` file would look something like this

```json
library {
  maven_library {
    groupId: "androidx.databinding"
    artifactId: "viewbinding"
    version: "4.1.2"
  }
  digests {
    sha256: "\355\276\304B\\nr/|\331\025IM&\236r6g\r\032f\r%M\336\264`\027\270-\246g"
  }
}
library {
  maven_library {
    groupId: "androidx.lifecycle"
    artifactId: "lifecycle-runtime"
    version: "2.3.0"
  }
  digests {
    sha256: "\224\365(\375_\261#\367[ne\320zn\365\315l\016i\254`M\020j\252\022pR\202Eb4"
  }
}
library {
  maven_library {
    groupId: "androidx.collection"
    artifactId: "collection"
    version: "1.1.0"
  }
  digests {
    sha256: "c*\016T\aF\035\347t@\223R\224\016)*)\0207rB\a\247\207\202\fw\332\367\323;r"
  }
}
```

## What's happening underneath

When building your app using Android Gradle plugin 4.0.0 and higher, the plugin includes metadata that describes the dependencies that are compiled into your app. When uploading your app, the Play Console inspects this metadata to provide you with the following benefits:


> Get alerts for known issues with SDKs and dependencies your app uses. Receive actionable feedback to resolve those issues.


The data is compressed, encrypted by a Google Play signing key, and stored in the signing block of your release app. 
However, you can inspect the metadata yourself in the local intermediate build files in the following directory: 
`<project>/<module>/build/outputs/sdk-dependencies/release/sdkDependency.txt.`


## Closing


- At the time of this writing, there are about `69` androidX libraries present in the release variant of `android/sunflower`.
- `sdkDependency.txt` is not generated for `debug` variants.





