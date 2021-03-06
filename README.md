# watchservice-ktx

Kotlin API wrapper for Java's WatchService powered with Channels and Coroutines. a.k.a. KWatchChannel

## Getting started

This repository is hosted via [jitpack](https://jitpack.io/) since it's by far the easiest delivery method while also being pretty transparent to the developer.

Make sure you have added jitpack to the list of your repositories:

```kotlin
maven("https://jitpack.io")
```

Then simply add the `watchservice-ktx` dependency

```kotlin
dependencies {
  compile("com.github.vishna:watchservice-ktx:master-SNAPSHOT")
}
```

## Example usage

```kotlin
val currentDirectory  = File(System.getProperty("user.dir"))

val watchChannel = currentDirectory.asWatchChannel()

launch {
  watchChannel.consumeEach { event ->
    // do something with event
  }
}

// once you no longer need this channel, make sure you close it
watchChannel.close()
```

For more documentation on API see [watchservice.kt](https://github.com/vishna/watchservice-ktx/blob/master/src/main/kotlin/dev/vishna/watchservice/watchservice.kt) or check out the [medium article](https://medium.com/@vishna/kotlin-watchservice-a-better-file-watcher-using-channels-coroutines-and-sealed-classes-7ab5c9df3ada)
