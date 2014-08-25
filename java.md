#Java API

Gimmie Java API is a wrapper class for calling Gimmie in Java application or
Android  without need to do restful call by yourself. Gimmie API wrapper can get
from [Gimmie SDK](http://gimmieworld.s3.amazonaws.com/sdk/gimmie-android-latest.zip)
file by extract the zip and look into __libs__ directory.

## Gimmie API with Gradle

For Gimmie API Library, you can add to Gradle by follow below steps

- Add Gimmie maven repository to __build.gradle__ file

```groovy
repositories {
  maven {
    url = 'http://maven.gimmie.io/'
  }
}
```

- In dependencies, add `gimmie-api` as compile

```groovy
dependencies {
  compile 'com.gimmie:gimmie-api:1.0+'
}
```

In Android project, you might want to add transitive and make it value as false
to exclude duplicate library when compiles (json, http common library, ...)

```groovy
dependencies {
  compile ('com.gimmie:gimmie-api:1.0+') {
    transitive = false
  }
}
```

That's all

## Sample Java code

```Java
import com.gimmie.Gimmie;
import com.gimmie.Configuration;

public class Sample {

  public static void main(Object args...) {
    HashMap<String, Object> template = new HashMap<String, Object>();
    template.put(Configuration.API_KEY, "game_key_from_portal");
    template.put(Configuration.API_SECRET, "game_secret_from_portal");

    Configuration configuration = new Configuration(template);
    Gimmie gimmie = Gimmie.getInstance(configuration);

    gimmie.trigger("event_name",
      new AsyncResult<CombineResponse>() {

        public void getResult(CombineResponse response) {
          // Handle response here
        }

        public void getError(GimmieError error) {
          // Handle error here
        }

      });
  }

}

```
