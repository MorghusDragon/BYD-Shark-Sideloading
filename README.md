BYD Shark 6 Sideloading Guide
=============================

Install ADB
-----------

You can install ADB from [Google](https://developer.android.com/tools/adb), but I've found the easiest way is to use a package manager like [Chocolatey](https://community.chocolatey.org/packages/adb) to install it.


Enable ADB within the car
-------------------------

Go to Car -> System -> Version and then press on the text "Factory Reset" (not the "Reset" button on the right) 10 times within a few seconds. After pressing it 10 times, a new menu should pop up. On this new menu, not all options are visible in landscape mode, so rotate the screen vertically and two buttons should show up on the top.

"CONNECT USB TO ENABLE DEBUGGING MODE/REVOKE USB DEBUGGING ENABLE AUTHORIZATION(STEBU/UKE)"

Press this button and a notification should pop up.

"Turn on ADB debugging !"

This is written a bit awkwardly, but when it says "on" in the message, it is enabled. Press it again to disable it (recommended once you're done with installing apps).


Connect your car to your home WiFi and find its IP address
----------------------------------------------------------

Press the WiFi symbol on the top right and connect to your home's WiFi network. Once connected, it'll show your car's IP address. Note it down.


Connect to the car with ADB from your PC
----------------------------------------

On your PC, press Windows + X and choose "Powershell" or "Terminal".

Enter the following:

```
adb connect <IP Address>
```

Replace `<IP Address>` with your car's IP address that you noted down in the step above, so for example:

```
adb connect 192.168.1.123
```

Once connected, it should say `connected to 192.168.1.123:5555`. Now you can start uploading apps.


Install Aurora Store
--------------------

Download the latest Aurora Store APK here: https://auroraoss.com/downloads/AuroraStore/Latest/latest.apk

Once downloaded, in your terminal, type `cd Downloads` to switch to the Downloads directory.

Next, to install Aurora store, type:

```
adb install latest.apk
```

Once installed, we need to grant Aurora Store extra permissions so it functions correctly. Type:

```
adb shell appops set com.aurora.store REQUEST_INSTALL_PACKAGES allow
adb shell appops set com.aurora.store WRITE_EXTERNAL_STORAGE allow
adb shell appops set com.aurora.store MANAGE_EXTERNAL_STORAGE allow
```

Now you can open the Aurora Store in your apps menu on the car.


Install YouTube and some other Google apps
------------------------------------------

I'm using [vanced.to](https://vanced.to) for this. Download the [ReVanced Manager](https://vanced.to/revanced-manager) and install it the same way as the Aurora Store:

```
adb install revanced.net_revanced_manager_v2.0.11.apk
```

(The file you downloaded might have a different version number)

You can then download YouTube and other apps through the ReVanced Manager app. Make sure to also install MicroG and login to your Google account through the MicroG app. If you can't login, disable the "Authenticate with device registration" setting and enable the "Strip device name for authentication" setting.