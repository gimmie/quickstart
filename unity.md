#Unity Quickstart

Gimmie has 2 libraries for Unity, Wrapper and Components. Wrapper is C# library for making API call without pre-made Gimmie UI Components but easier
to integrate because it doesn't need platform library. Components is C# library for calling to platform library (Android and iOS) that you need to 
download and put together with C# files but it gives pre-made Gimmie UI that you can customise.

## Wrapper

- [Add wrapper files](https://github.com/gimmie/unity/blob/master/Wrapper) into __Assets/Plugins__
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

- Download [Gimmie SDK for Unity](http://gimmieworld.s3.amazonaws.com/sdk/Gimmie-AndroidSDK-1.8.4-Unity.zip)
- Extract and copy 'res/' and all files in 'libs'
- Create a binding class, you can use a basic one here: [GimmieBinding.cs](https://github.com/gimmie/unity/blob/master/GimmieBinding.cs)
- Modify AndroidManifest.xml to include all the Gimmie declarations. See [example here](https://github.com/gimmie/unity/blob/master/android/AndroidManifest.xml)

### Sample project structure

```
Assets/
    Plugins/
        Android/
            res/
            AndroidManifest.xml
            GimmieBinding.cs
            gimmie-api-1.0.3.jar
            MixpanelAPI.jar
            Parse-1.5.0.jar
            scribe-1.3.5.jar
            tagsoup-1.2.1.jar
            unity-actionbarsherlock.jar
            unity-gimmie-components.jar
            unity-viewpager.jar
            unity-websocket.jar
        Your-other-plugins/
```

### Guest User

To handle guest user tapping on notification and show your login page, create a empty game object name __GimmieBinding__ and add GimmieBinding.cs script to that object

### Rewards country

Rewards in Gimmie catalog can target to specific country, to show rewards in target country, add below meta code to __AndroidManifest.xml__ file

```xml
<meta-data android:name="com.gimmie.data.default_country" android:value="<country code>" />
```

Default country is __global__ which means only rewards set to global will show in catalog.

## iOS

- Building and export project from Unity
- Download iOS integration files([GMUnityIntegration.h](https://github.com/gimmie/unity/blob/master/ios/GMUnityIntegration.h) and [GMUnityIntegration.mm](https://github.com/gimmie/unity/blob/master/ios/GMUnityIntegration.mm)) and put in exported project
- [Download Gimmie iOS SDK](http://gimmieworld.s3.amazonaws.com/sdk/gimmie-ios-latest.zip) and extract into exported project.
- Add this framework in build phase
 - CoreTelephony.framework
 - Security.framework
 - libicucore.dylib
- Add __Gimmie__ type __Dictionary__ to Info.plist. Under it, add key __key__ and __secret__ with values from Gimmie portal.
- Open your project Build Settings, select All and find Other Linker Flags. Add __-ObjC__ and __-all_load__ to that property.
- Build the project with Xcode

### Rewards Country

Add __country__ to __Gimmie__ Dictionary in Info.plist with country code as value for showing country rewards in catalog.

## Initialize

Call the following to bind Gimmie to each new context, for example in `Start()`:

```cs
    void Start() {
        GimmieBinding.InitGimmie();
    }
```

After init Gimmie it will automatically login user with __guest:randomid__ which is anonymous user. Anonymous user is the same as
normal user, it can earn points and redeem but it also can transfer points to other user. To transfer the points, call `Login`
with your internal user id and points will get merge.

To check is user anonymous, call `Gimmie.IsAnonymousUser()`.

## Showing rewards catalog and trigger events

To show rewards catalog on any button add below code to Unity logic file.

```cs
    GimmieBinding.ShowGimmieRewardsCatalogue();
```

To trigger event

```cs
    GimmieBinding.TriggerGimmieEvent("event_name");
```

## Handle need login for guest user

Guest user is generated user id prefix with __guest:__. This user can earn points and instant rewards but cannot claim or open the
catalog. When they tap on notification, nothing will happen.

To allow them claim rewards and open catalog, implements login function by adding __GimmieNeedLogin__ to any __MonoBehavior__ that get
new user login from your services or any 3rd party and use that login to Gimmie by call `GimmieBinding.Login("newuserid")` for
transfering points and rewards that user has earned while login as guest.

## Known Issues

- What's the parameter in this function `GimmieWrapper.Login("")`

Login function take username parameter generated from your system or game. It can be timestamp that saved or 
Facebook ID when user open your game and login with Facebook. This is for linking information in Gimmie with
your system.

__We don't generated__ any login for you because Gimmie is additional information to your user information.
We don't store your user firstname lastname or even email when your login.

- Duplicated scribe library

```
UNEXPECTED TOP-LEVEL EXCEPTION:
java.lang.IllegalArgumentException: already added: Lorg/scribe/builder/api/Api;
```

In plugin folder, remove __scribe-(version).jar__ file because other library already has that in dependencies.

- Duplicated Android Supported library

```
UNEXPECTED TOP-LEVEL EXCEPTION:
java.lang.IllegalArgumentException: already added: Landroid/support/v4/hardware/display/DisplayManagerCompat;
```

In plugin folder, remove __android-support-v4.jar__ file because other library already has that in dependencies.

- Missing Sherlock resources

```
/path/in/game/gimmie_Android_SDK_Unity/res/values/gm__styles.xml:4: error: Error retrieving parent for item: No resource found that matches the given name '@style/Theme.Sherlock.Light'.
/path/in/game/gimmie_Android_SDK_Unity/res/values/gm__styles.xml:5: error: Error: No resource found that matches the given name: attr 'actionBarStyle'.
```

Copy all res and jar files including ActionBar Sherlock and ViewPager in plugins folder to your games.
