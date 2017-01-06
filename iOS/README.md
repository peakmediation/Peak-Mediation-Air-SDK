#Air Native Extension for Peak Mediation Platform (iOS)#

This is an Air native extension for Peak Mediation Platform SDK on iOS.

##Integration instruction##

####1. Use git clone command to clone this repository. Git documentation.
``` $ git clone https://github.com/peakmediation/Peak-Mediation-Air-SDK.git```
or load these anes as a [zip-archive]( https://github.com/peakmediation/Peak-Mediation-Air-SDK.git/archive/master.zip).

####2. Add *.ane to you project:
 Open properties of your project in Adobe Flash Builder-> select "select ActionScript Build Path" -> select "Native extensions tab"-> Press on "add ANE" button and select the *.ane, which you got on the 1 step.

Open properties of your project in Adobe Flash Builder-> select "ActionScript Build Packaging"->go to "Native extensions" tab and be sure that ANEs which was added on the step 2 is active ( there should be present a green tick).
####3. Add to *-app.xml in your projects the next fields:
      <iPhone>
            <InfoAdditions>
            <![CDATA[
            .........
                  <key>NSAppTransportSecurity</key>
                  <dict>
                        <key>NSAllowsArbitraryLoads</key>
                        <true/>
                        <key>NSExceptionDomains</key>
                        <dict>
                               <key>example.com</key>
                              <dict>
                                    <key>NSIncludesSubdomains</key>
                                    <true/>
                              </dict>
                        </dict>
                  </dict>
                  <key>LSApplicationQueriesSchemes</key>
            <array>
            <string>fb</string>
		 <string>instagram</string>
		 <string>tumblr</string>
		 <string>twitter</string>
            </array>
            .........
            ]]></InfoAdditions>
      </iPhone>

#### 4.Add the extensionID in the end of *-app.xm:
      <extensions>
          <extensionID>com.peak.air</extensionID>
      </extensions>

##Using Peak SDK AIR Native Extension
####1. In your project initialize library with your application id:  
      com.peak.air.PeakAirExtension.init();
      com.peak.air.PeakAirExtension.initialize(PEAK_APP_ID);

 and add event listener:
      private function listenToPeak(event:StatusEvent):void{.....}
      com.peak.air.PeakAirExtension.dispatcher.addEventListener( StatusEvent.STATUS, listenToPeak);

 In this way you can follow a status of advertising via ```event.level``` and envents in step 9
  
####2. Check ad availability for specified zone:  
      var isAvaliable:Boolean = com.peak.air.PeakAirExtension.checkAdAvailable(AD_ZONE_ID);

####3. Show interstitial ad:  
      com.peak.air.PeakAirExtension.showInterstitial(AD_ZONE_ID);

####4. Show banner:  
    //  **xPos, yPos** - banner positions on the screen.  
    //  **width, height** - banner size.  
    //  AD_ZONE_ID:String, xPos:int, yPos:int, width:int, height:int
       com.peak.air.PeakAirExtension.showBanner(AD_ZONE_ID, xPos, yPos, width, height ); 
      
####5. Remove banner from the screen:  
    com.peak.air.PeakAirExtension.removeBanner();
####6. Get native ad. Native Ads will allow developers to show ads in custom formats in their applications. The next function returns structure with information about advertising:  
    var native:com.peak.air.PeakNativeAd = com.peak.air.PeakNativeAd( showNativeAd(NATIVE_AD_ZONE_ID) );
####7. Unlike Banner and Interstitial ads, the impressions and clicks are not automatically handled, and need to be wrapped when events do occur. Call the next method to track that native ad for current zone was shown:  
     com.peak.air.PeakAirExtension.trackNativeAdShown(NATIVE_AD_ZONE_ID);

####8. Use the next method to handle click on the "Call to Action" button. Call of this method will redirect the user to the website for that ad:   
    com.peak.air.PeakAirExtension.handleNativeAdClicked(NATIVE_AD_ZONE_ID);
####9. You can detect the next app advertising states:    
    com.peak.air.PeakAirExtension.EVENT_LEVEL_SDK_INITIALIZATION_SUCCESS //= "initializationSuccess";
    com.peak.air.PeakAirExtension.EVENT_LEVEL_SDK_INITIALIZATION_FAILED //= "initializationFailed"; 
    com.peak.air.PeakAirExtension.EVENT_BANNER_SHOW_SUCCESS // = "bannerShowSuccess";
    com.peak.air.PeakAirExtension.EVENT_BANNER_SHOW_FAILED // = "bannerShowFailed";
    com.peak.air.PeakAirExtension.EVENT_INTERSTITIAL_SHOW_SUCCESS //= "interstitialShowSuccess";
    com.peak.air.PeakAirExtension.EVENT_INTERSTITIAL_SHOW_FAILED //= "interstitialShowFailed";
    com.peak.air.PeakAirExtension.EVENT_INTERSTITIAL_CLOSED //= "interstitialClosed";
    com.peak.air.PeakAirExtension.EVENT_COMPLETED_REWARD_EXPERIENCE// = "completedRewardExperience";
    com.peak.air.PeakAirExtension.EVENT_NATIVE_AD_SHOW_SUCCESS //= "nativeAdShowSuccess";
    com.peak.air.PeakAirExtension.EVENT_NATIVE_AD_SHOW_FAILED //= "nativeAdShowFailed";
	
###10. Targeting:
Peak SDK provides a way to set preffered targeting age and gender to inrease eCPM. This will not restrict ads to show only targeted ads.
There are 2 method for targeting in PeakSDK for air:
#####10.1. For gender targeting:
  ```setTargetingGender( PeakTargetGender gender ); ```

   where "gender" could be one of the values below:
   ```UNKNOWN = 0,
     MALE = 1,
     FEMALE = 2.```
by default the target gender is set to ```UNKNOWN```.
#####10.2. For agetargeting:
   ```setTargetingAge( int age );```
   
where  "age " could be any value from (-1) to n.  By default target gender is set to (-1).
These methods for targeting must be called calling after ```PeakAirExtension.init()``` and before ```PeakAirExtension.initialize(PEAK_APP_ID)```.

###Example:
    PeakAirExtension.dispatcher.addEventListener(StatusEvent.STATUS, listenToPeak)
    private function listenToPeak(event:StatusEvent):void
     {
        if(event.level == com.peak.air.PeakAirExtension.EVENT_LEVEL_SDK_INITIALIZATION_SUCCESS )
        {
            if( checkAdAvailable( AD_INTERSTITIAL_ZONE_ID ) )
            {
                com.peak.air.PeakAirExtension.showInterstitial( AD_INTERSTITIAL_ZONE_ID );
             }
        }
    }

