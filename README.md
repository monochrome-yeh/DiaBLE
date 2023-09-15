To build the project you have to duplicate the file _DiaBLE.xcconfig_, rename the copy to _DiaBLEOverride.xcconfig_ (the missing reference displayed by Xcode in red should then point to it) and edit it by deleting the last line `#include?... ` and replacing `##TEAM_ID##` with your Apple Team ID so that the first line should read for example `DEVELOPMENT_TEAM = Z25SC9UDC8`.

Currently I am targeting only the latest betas of Xcode and iOS and focusing on the new Libre 3 and Dexcom G7.

Please refer to the [**TODOs**](https://github.com/gui-dos/DiaBLE/blob/main/TODO.md) list for the up-to-date status of all the current limitations and known bugs of this **prototype**.

**Warnings:**
  * the temperature-based calibration algorithm has been derived from the old LibreLink 2.3: it is known that the Vendor improves its algorithms at every new release, smoothing the historical values and projecting the trend ones into the future to compensate the interstitial delay but these further stages aren't understood yet; I never was convinced by the simple linear regression models that others apply on finger pricks;
  * activating the BLE streaming of data on a Libre 2 will break other apps' pairings and you will have to reinstall them to get their alarms back again; in Test mode it is possiBLE however to sniff the incoming data of multiple apps running side-by-side by just activating the notifications on the same BLE characteristics: the same technique is used to analyze the Libre 3 incoming traffic since the Core Bluetooth connections are reference-counted;
  * connecting directly to a Libre 2/3 from an Apple Watch is currently just a proof of concept that it is technically possiBLE: keeping the connection in the background will require additional work and AFAIK nobody else is capaBLE of doing the job... :-P

---
***Credits***: [@dabear](https://github.com/dabear), [@ivalkou](https://github.com/ivalkou), [@j-kaltes](https://github.com/j-kaltes), [LibreMonitor](https://github.com/UPetersen/LibreMonitor/tree/Swift4), [Loop](https://github.com/LoopKit/Loop), [Nightscout LibreLinkUp Uploader](https://github.com/timoschlueter/nightscout-librelink-up), [xDrip](https://github.com/Faifly/xDrip), [xDrip+](https://github.com/NightscoutFoundation/xDrip), [xDrip4iO5](https://github.com/JohanDegraeve/xdripswift).

###### ***Disclaimer: the decrypting keys I am publishing are not related to user accounts and can be dumped from the sensor memory by using DiaBLE itself. The online servers I am using probably are tracking your personal data but all the traffic sent/received by DiaBLE is clearly shown in its logs. The reversed code I am pasting has been retrieved from other GitHub repos or reproduced simply by using open-source tools like `jadx-gui`.***