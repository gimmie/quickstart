#Android API Integration

Gimmie Android API is a wrapper class for calling Gimmie in Android without need to do restful call by yourself. Gimmie API
wrapper can get from [Gimmie SDK](http://gimmieworld.s3.amazonaws.com/sdk/gimmie-android-latest.zip) file by extract the zip 
and look into __libs__ directory.

## Integrate with Gradle

For Gimmie API Library, you can integrate with gradle by following below steps

- Add Gimmie maven repository to __build.gradle__ file

```groovy
repositories {
  maven {
    url = 'https://developer.gimmieworld.com/releases/maven/'
  }
}
```

- In dependencies, add `gimmie-api` as compile

```groovy
dependencies {
  compile 'com.gimmie:gimmie-api:1.0+'
}
```

In Android project, you might want to add transitive and make it value as false to exclude duplicate library when compiles
(json, http common library, ...)

```groovy
dependencies {
  compile ('com.gimmie:gimmie-api:1.0+') {
    transitive = false
  }
}
```

That's all
