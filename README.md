![PLAKC](http://plakc.ninja/images/plakc.png)

## ABOUT PLAKC
* [PLAKC](http://www.plakc.com) is an In-Game Advertising network that works on the psychology of immersed gamers.  

## ABOUT THIS REPOSITORY 
+ This repository contains PLAKC Unity3D SDK.
+ Current version is 2019.1.0  
+ Links:
    - [Releases](https://github.com/Plakc/plakc-unity/releases)  
    - [FAQ](https://github.com/Plakc/plakc-unity/wiki/FAQ)  
    - [Integration Scenarios](https://github.com/Plakc/plakc-unity/wiki/Integration-Scenarios)
    
## REQUIREMENTS ##
1. Unity version 5.3.0 or above    
2. Build target set to Android, iOS, Standalone. (Supports VR)  
  
## QUICK INTEGRATION GUIDE ##

1. REGISTERING YOUR GAME
  + Go to [our developer page](http://www.plakc.ninja). Sign up if you haven't and then sign in. Follow the instructions to register you game and obtain a game ID.
    
2. GETTING THE SDK
  + Go to the [releases page](https://github.com/Plakc/plakc-unity/releases/latest). Download the latest Plakc Unity SDK unitypackage file from the downloads section.  
  + Import the unitypackage.  
	
3. SETTING UP AD SPOTS
  + Go to `Toolbar > Plakc > Configuration` to enter your Developer ID, Game ID integration. While your game is in development, check the "Test Mode" button. 
  + Go to a scene you want to show ads in and click on `Toolbar > Plakc > Create Ad Unit` followed by the type of ad unit you want to create. The types available are in-game billboard and UI screen ads. Place the ads in the game's environment and UI as desired.
  + Click on `Plakc>Add Initializer Script to Scene` on the first scene of your game to create a PLAKC initializer object. This onject is responsible for invoking the SDKs start method.      	
  
4. SDK FUNCTIONS
    + You can also call the following method to initialize the Sdk at any time, the Initializer object described above does that on its own.  
  ```
  Plakc.Sdk.Start(hasAds => {
        if(hasAds)
            Debug.Log("PLAKC has ads");
        else
            Debug.Log("No PLAKC ads available");  
  });
  ``` 
  + Apart from native and in game ads, the SDK also popup ads that the developer can invoke any time. The following code snippet demonstrates the usage:  
  ```
    Plakc.Sdk.ShowPopupAd();
  ```
  + To query if the SDK has ads, use :  
  ```
  Plakc.Sdk.HasAds(); // returns bool
  ```
  
5. BUILD CONFIGURATION
  - Stripping Level (under `Player Settings>Other Settings`) should be set to **Disabled**. This is critical.  
  - On Android, add the following Activity to the main AndroidManifest.xml file : `<activity android:name="com.plakc.browser.PlakcBrowserActivity" android:configChanges="orientation|screenSize|uiMode|screenLayout|smallestScreenSize" android:hardwareAccelerated="true" android:windowSoftInputMode="stateAlwaysHidden" />`
  - The SDK currently does not support IL2CPP, requires full .NET 2.0 support  
  
6. PUBLISHING  
  - Due to complaince requirements, Google Play needs developers to disclose Ad Network activity in their privacy policy. Add the following clause to your provacy policy :
    
  _Ad Networks_  
    
  _We may feature advertising within our Service. The advertisers may collect and use information about you, such as your Service session activity, device identifier, MAC address, IMEI, geo-location information, installed applications and IP address. They may use this information to provide advertisements of interest to you. In addition, you may see our games advertised in other services. After clicking on one of these advertisements and installing our game, you will become a user of our Service. In order to verify the installs, a device identifier may be shared with the advertiser._

___You can find a sample privacy policy [here](https://github.com/Plakc/plakc-unity/wiki/Sample-Privacy-Policy)___
## TIPS ##

+ Be sure to use a transparent / alpha shader for your ad display renderers if you want the ads to be so.

+ You can initialize the SDK anytime in the session. **However, we recommend that you do so as soon as possible** (at the splash screen) so that the ads are made ready early. Just click `Plakc>Add Initializer Script to Scene` at your splash screen or call `Plakc.Sdk.Start(adsCallback => {});`  

+ Select "Enable Test Ads" to see if your integration is working right.  

<!--
+ Check out some [integration scenarios](https://github.com/Plakc/plakc-unity/wiki/Integration-Scenarios) for best practices on integrating PLAKC effectively.
-->

## CONTACT ##
* Visit [plakc.com](www.plakc.com) for more information
* Email us at info@thezerogames.com for any queries
