# Fork from org.apache.cordova.splashscreen

This plugin displays and hides a splash screen during application launch. It is forked for custom logic of for iOS devices. The only change is that spinner indicator for iOS can be controlled for showing. 

If you want the spinner to be shown add in global config.xml this preference line

<preference name="shouldShowTopActivityIndicatorSpinnerSplash" value="true"/> 

The default option is false


## Installation

    cordova plugin add org.apache.cordova.splashscreen


## Supported Platforms

- Amazon Fire OS
- Android
- BlackBerry 10
- iOS
- Windows Phone 7 and 8
- Windows 8


## Methods

- splashscreen.show
- splashscreen.hide

### Android Quirks

In your config.xml, you need to add the following preferences:

    <preference name="SplashScreen" value="foo" />
    <preference name="SplashScreenDelay" value="10000" />

Where foo is the name of the splashscreen file, preferably a 9 patch file. Make sure to add your splashcreen files to your res/xml directory under the appropriate folders. The second parameter represents how long the splashscreen will appear in milliseconds. It defaults to 3000 ms. See [Icons and Splash Screens](http://cordova.apache.org/docs/en/edge/config_ref_images.md.html)
for more information.

## splashscreen.hide

Dismiss the splash screen.

    navigator.splashscreen.hide();


### BlackBerry 10, WP8, iOS Quirk

The `config.xml` file's `AutoHideSplashScreen` setting must be
`false`. To delay hiding the splash screen for two seconds, add a
timer such as the following in the `deviceready` event handler:

        setTimeout(function() {
            navigator.splashscreen.hide();
        }, 2000);

## splashscreen.show

Displays the splash screen.

    navigator.splashscreen.show();


Your application cannot call `navigator.splashscreen.show()` until the app has
started and the `deviceready` event has fired. But since typically the splash
screen is meant to be visible before your app has started, that would seem to
defeat the purpose of the splash screen.  Providing some configuration in
`config.xml` will automatically `show` the splash screen immediately after your
app launch and before it has fully started and received the `deviceready`
event. See [Icons and Splash Screens](http://cordova.apache.org/docs/en/edge/config_ref_images.md.html)
for more information on doing this configuration. For this reason, it is
unlikely you need to call `navigator.splashscreen.show()` to make the splash
screen visible for app startup.
