# Necessary checks after update coming from AAPS 2.6

- The program code was changed significantly when switching to AAPS 2.7.
- Therefore it is important that you make some changes or check settings after the update.
- Please see [release notes](ReleaseNotes.md#version-270) for details on new and extended features.

## Check BG source

- Check if BG source is correct after update.
- Especially when using [xDrip+](../CompatibleCgms/xDrip.md) it might happen, that BG source is changed to Dexcom app (patched).
- Open [Config builder](../SettingUpAaps/ConfigBuilder.md#bg-source) (hamburger menu on top left side of home screen)
- Scroll down to "BG source".
- Select correct BG source if changes are necessary.

![BG bron](../images/ConfBuild_BG.png)

## Finish exam

- AAPS 2.7 contains new objective 11 (in later versions renumbered to objective 10!) for [automation](../DailyLifeWithAaps/Automations.md).
- You have to finish exam ([objective 3 and 4](../SettingUpAaps/CompletingTheObjectives.md#objective-3-prove-your-knowledge)) in order to complete [objective 11](../SettingUpAaps/CompletingTheObjectives.md#objective-11-enabling-additional-features-for-daytime-use-such-as-dynamic-sensitivity-plugin-dynisf).
- If for example you did not finish the exam in [objective 3](../SettingUpAaps/CompletingTheObjectives.md#objective-3-prove-your-knowledge) yet, you will have to complete the exam before you can start [objective 11](../SettingUpAaps/CompletingTheObjectives.md#objective-11-enabling-additional-features-for-daytime-use-such-as-dynamic-sensitivity-plugin-dynisf).
- This will not effect other objectives you have already finished. Je behoudt alle reeds afgeronde doelen!

## Set master password

- Necessary to be able to [export settings](ExportImportSettings.md) as they are encrypted as of version 2.7.
- Open Preferences (three-dot-menu on top right of home screen)
- Click triangle below "General"
- Click "Master-Password"
- Enter password, confirm password and click ok.

![Set master password](../images/MasterPW.png)

## Exporteer instellingen

- AAPS 2.7 uses a new encrypted backup format.
- You must [export your settings](ExportImportSettings.md) after updating to version 2.7.
- Settings files from previous versions can only be imported in AAPS 2.7. Export will be in new format.
- Make sure to store your exported settings not only on your phone but also in at least one safe place (your pc, cloud storage...).
- If you build AAPS 2.7 apk with the same keystore than in previous versions you can install new version without deleting the previous version.
- All settings as well as finished objectives will remain as they were in the previous version.
- In case you have lost your keystore build version 2.7 with new keystore and import settings from previous version as described in the [troubleshooting section](../GettingHelp/TroubleshootingAndroidStudio#lost-keystore).

## Autosens (Hint - no action necessary)

- Autosens is changed to a dynamic switching model which replicates the reference design.
- Autosens will now switch between a 24 and 8 hours window for calculating sensitivity. Hij kiest voor de meest gevoelige.
- Als je voorheen oref1 gebruikte, zul je waarschijnlijk merken dat het systeem minder dynamisch omgaat met veranderingen, als gevolg van het gebruiken van 24 ofwel 8 uur.

## Set Pump Password for Dana RS (if using Dana RS)

- Pump password for [Dana RS](../CompatiblePumps/DanaRS-Insulin-Pump.md) was not checked in previous versions.
- Open Preferences (three-dot-menu on top right of screen)
- Scroll down and click triangle next to "Dana RS".
- Click "Pump password (v1 only)"
- Enter pump password ([Default password](../CompatiblePumps/DanaRS-Insulin-Pump.md#default-password) is different depending on firmware version) and click OK.

![Set Dana RS password](../images/DanaRSPW.png)

To change password on Dana RS follow instructions on [DanaRS page](../CompatiblePumps/DanaRS-Insulin-Pump.md#change-password-on-pump).