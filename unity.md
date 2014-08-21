#Unity Quickstart

Gimmie has 2 libraries for Unity, Wrapper and Components. Wrapper is C# library for making API call without pre-made Gimmie UI Components but easier
to integrate because it doesn't need platform library. Components is C# library for calling to platform library (Android and iOS) that you need to 
download and put together with C# files but it gives pre-made Gimmie UI that you can customise.

## Wrapper

- [Add wrapper files](https://github.com/gimmie/unity/blob/master/Wrapper) into **Assets/Plugins**
- Initial `GimmieWrapper` before call other Gimmie API

```cs
    GimmieWrapper.InitGimmie("key", "secret");
    GimmieWrapper.Login("awesomeUser");
```

- Call Gimmie API in your game when user do something inside. [Here is the list of our API.](http://support.gimmie.io/hc/en-us/articles/202788800-API)

### Sample Wrapper

```cs
    using Gimmie;
    ...
    string profileEndpoint = "https://api.gimmieworld.com/1/profile.json";
    // Key and Secret are from Gimmit portal.
    GimmieWrapper.InitGimmie("key", "secret");
    GimmieWrapper.Login("awesomeUser");
    JSONObject j = GimmieWrapper.CallGimmie(profileEndpoint);
    Debug.Log("JSON fields accessed: "+ j["response"]["user"]["awarded_points"].n);
```

## Android

## iOS
