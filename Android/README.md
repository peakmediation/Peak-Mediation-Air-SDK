#Air Native Extension for Peak Mediation Platform (Android)

##This is an Air native extension for Peak Mediation Platform SDK on Android.

###Installation
You should add airPeak.ane to your application project's Build Path and make sure to package it with your app (more information here).
Integration instructions
To get started, you need to allow these permissions:

    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/>
    <uses-permission android:name="android.permission.VIBRATE"/>

You need to add the following in your AIR manifest:

      <application android:hardwareAccelerated="true">
          <!-- Peak Mediation Platform -->
      <activity
      android:name="com.jirbo.adcolony.AdColonyOverlay"
      android:configChanges="keyboardHidden|orientation|screenSize"
      android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen"/>

      <activity
      android:name="com.jirbo.adcolony.AdColonyFullscreen"
      android:configChanges="keyboardHidden|orientation|screenSize"
      android:theme="@android:style/Theme.Black.NoTitleBar.Fullscreen"/>

      <activity
      android:name="com.jirbo.adcolony.AdColonyBrowser"
      android:configChanges="keyboardHidden|orientation|screenSize"
      android:theme="@android:style/Theme.Black.NoTitleBar.Fullscreen"/>

      <activity
      android:name="com.my.target.ads.MyTargetActivity"
      android:hardwareAccelerated="true"
      android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"/>

      <activity
      android:name="com.unity3d.ads.adunit.AdUnitActivity"
      android:configChanges="fontScale|keyboard|keyboardHidden|locale|mnc|mcc|navigation|orientation|screenLayout|screenSize|smallestScreenSize|uiMode|touchscreen"
      android:hardwareAccelerated="true"
      android:theme="@android:style/Theme.NoTitleBar.Fullscreen"/>

      <activity android:name="com.applovin.adview.AppLovinInterstitialActivity"/>

      <activity
      android:name="com.vungle.publisher.FullScreenAdActivity"
      android:configChanges="keyboardHidden|orientation|screenSize"
      android:theme="@android:style/Theme.NoTitleBar.Fullscreen"/>

      <activity
      android:name="com.vungle.publisher.VideoFullScreenAdActivity"
      android:configChanges="keyboardHidden|orientation|screenSize"
      android:theme="@android:style/Theme.NoTitleBar.Fullscreen" />

      <activity android:name="com.apptracker.android.module.AppModuleActivity"
      android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
      android:hardwareAccelerated="false">
      </activity>

      <activity
      android:name="com.inmobi.rendering.InMobiAdActivity"
      android:configChanges="keyboardHidden|orientation|keyboard|smallestScreenSize|screenSize|screenLayout"
      android:hardwareAccelerated="true"
      android:theme="@android:style/Theme.NoTitleBar"/>

      <receiver android:name="com.inmobi.commons.core.utilities.uid.ImIdShareBroadCastReceiver"
      android:enabled="true"
      android:exported="true">
      <intent-filter>
      <action android:name="com.inmobi.share.id"/>
      </intent-filter>
      </receiver>

      <service android:name="com.inmobi.signals.activityrecognition.ActivityRecognitionManager"
      android:enabled="true"/>

      <activity
      android:name="com.nativex.monetization.activities.InterstitialActivity"
      android:configChanges="orientation|screenSize"
      android:hardwareAccelerated="true"
      android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen"/>

      <activity
      android:name="com.nativex.videoplayer.VideoActivity"
      android:configChanges="orientation|screenSize"/>

      <activity
      android:name="com.flurry.android.FlurryFullscreenTakeoverActivity"
      android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize"
      android:hardwareAccelerated="true" />

      <activity android:name="com.mopub.mobileads.MoPubActivity"
      android:configChanges="keyboardHidden|orientation|screenSize"/>
      <activity android:name="com.mopub.mobileads.MraidActivity"
      android:configChanges="keyboardHidden|orientation|screenSize"/>
      <activity android:name="com.mopub.common.MoPubBrowser"
      android:configChanges="keyboardHidden|orientation|screenSize"/>
      <activity android:name="com.mopub.mobileads.MraidVideoPlayerActivity"
      android:configChanges="keyboardHidden|orientation|screenSize"/>

      <activity android:name="com.avocarrot.androidsdk.VideoActivity"/>
      <activity android:name="com.avocarrot.androidsdk.RedirectActivity" />

      </application> 
      
      
###Also add the extensionID in the extension tag(if it is not automatically added):

      <extensions>
          <extensionID>com.peak.air</extensionID>
      </extensions>

##Using Peak SDK AIR Native Extension
 
###1. Define constants for listening events: 
    public static var EVENT_LEVEL_SDK_INITIALIZATION_SUCCESS:String = "initializationSuccess";
    public static var EVENT_LEVEL_SDK_INITIALIZATION_FAILED:String = "initializationFailed";
    public static var EVENT_BANNER_SHOW_SUCCESS:String = "bannerShowSuccess";
    public static var EVENT_BANNER_SHOW_FAILED:String = "bannerShowFailed";
    public static var EVENT_INTERSTITIAL_SHOW_SUCCESS:String = "interstitialShowSuccess";
    public static var EVENT_INTERSTITIAL_SHOW_FAILED:String = "interstitialShowFailed";
    public static var EVENT_INTERSTITIAL_CLOSED:String = "interstitialClosed";
    public static var EVENT_COMPLETED_REWARD_EXPERIENCE:String = "completedRewardExperience";
    public static var EVENT_NATIVE_AD_SHOW_SUCCESS:String = "nativeAdShowSuccess";
    public static var EVENT_NATIVE_AD_SHOW_FAILED:String = "nativeAdShowFailed";

###2. Call the init method:

     PeakAirExtension.init();
 
###3. Add a listener for events and write method:

    PeakAirExtension.dispatcher.addEventListener(StatusEvent.STATUS, _handlerPeakAirExtensionStatus);
    private function _handlerPeakAirExtensionStatus(event:StatusEvent):void{ 
              switch(event.level){
                   case Constants.EVENT_LEVEL_SDK_INITIALIZATION_SUCCESS:{
                       // To do
                       break;
                   }
                   case Constants.EVENT_LEVEL_SDK_INITIALIZATION_FAILED:{
                       // To do
                       break;
                   }
                   case Constants.EVENT_BANNER_SHOW_SUCCESS:{
                       // To do
                       break;
                   }
                   case Constants.EVENT_BANNER_SHOW_FAILED:{
                       // To do
                       break;
                   }
                   case Constants.EVENT_INTERSTITIAL_SHOW_SUCCESS:{
                         // To do
                         break;
                     }
                     case Constants.EVENT_INTERSTITIAL_SHOW_FAILED:{
                         // To do
                         break;
                     }
                    case Constants.EVENT_INTERSTITIAL_CLOSED:{
                         // To do
                         break;
                     }
                     case Constants.EVENT_COMPLETED_REWARD_EXPERIENCE:{
                         // To do
                         break;
                     }
                    case Constants.EVENT_NATIVE_AD_SHOW_SUCCESS:{
                         // To do
                         break;
                     }
                     case Constants.EVENT_NATIVE_AD_SHOW_FAILED:{
                         // To do
                         break;
                     }
              } 
     }
###4. Initialize peak sdk in your activity with your application id:

    PeakAirExtension.initialize(appId:String):void

###5. Check ad availability for specified zone:

    var isAdAvailable:Boolean = PeakAirExtension.checkAdAvailable(AD_ZONE_ID);

###6. Show interstitial ad:

    private function showInterstitial():void{
        PeakAirExtension.showInterstitial(AD_ZONE_ID);
    }
 
###7. Show native ad:

    private var _objectNativeAd:Object;
    private function showNativeAd():void{
        if(PeakAirExtension.checkAdAvailable(AD_ZONE_ID){
            objectNativeAd = PeakAirExtension.showNativeAd(AD_ZONE_ID);
        }
        if(objectNativeAd != null){
            PeakAirExtension.trackNativeAdShown(AD_ZONE_ID);
        }
    }
    private function bindNativeAdToViews():void{
        //fill views with received native ad data

      // load the _objectNativeAd.mainImage into your ImageView for the main image
      // load the _objectNativeAd.icon into your ImageView for icon image
      // get the _objectNativeAd.privacyIcon url and get from this url Bitmap:
        var spritePrivacyIcon:Sprite = new Sprite();
        addChild(spritePrivacyIcon);
        var privacyIcon:Bitmap = PeakAirExtension.getPrivacyIcon(_objectNativeAd.privacyIcon) as Bitmap;
        spritePrivacyIcon.addChild(privacyIcon);
      // set the _objectNativeAd.title into you TextView for title
      // set the _objectNativeAd.text into you TextView for description text
      // set the _objectNativeAd.actionText into your Button

        // set listener on your button
        buttonNativeAdClick.addEventListener(MouseEvent.CLICK, handleNativeAdClicked, false, 0, true);

      // set listener on your sprite with privacy icon
      spritePrivacyIcon.addEventListener(MouseEvent.CLICK, handleNativeAdPrivacyIconClicked, false, 0, true);
    }
    private function handleNativeAdClicked(event:MouseEvent):void{
        PeakAirExtension.handleNativeAdClicked(AD_ZONE_ID);
    }
    private function handleNativeAdPrivacyIconClicked(event:MouseEvent):void{
        PeakAirExtension.handleNativeAdPrivacyIconClicked(AD_ZONE_ID);
    }
 
###8. Show banner:

    private function showBanner():void{
        PeakAirExtension.showBanner(AD_ZONE_ID, x, y, width, height);
    }
 
###9. Component activity:

    this.stage.addEventListener(Event.DEACTIVATE, stage_deactivateHandler, false, 0, true);
    private function stage_deactivateHandler(event:Event):void {
        PeakAirExtension.onPause();
        this.stage.addEventListener(Event.ACTIVATE, stage_activateHandler, false, 0, true);
    }
    private function stage_activateHandler(event:Event):void {
        this.stage.removeEventListener(Event.ACTIVATE, stage_activateHandler);
        PeakAirExtension.onResume();
    }
    private function killApp():void{
        PeakAirExtension.onDestroy();
    }
    
###10. Set Target Gender:
    PeakAirExtension.setTargetGender(PeakTargetGender.UNKNOWN);
    //or
    //PeakAirExtension.setTargetGender(PeakTargetGender.MALE);
    //or
    //PeakAirExtension.setTargetGender(PeakTargetGender.FEMALE);
    
###11. Set Target Age:
    PeakAirExtension.setTargetingAge(value); // value:int
