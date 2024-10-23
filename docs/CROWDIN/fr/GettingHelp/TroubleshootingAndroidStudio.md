(troubleshooting_androidstudio-troubleshooting-android-studio)=
# Dépannage d'Android Studio

(troubleshooting_androidstudio-lost-keystore)=
## Fichier de clés perdu
If you use the same keystore when updating AAPS you do not have to uninstall the previous version on your smartphone. C'est pourquoi il est recommandé de stocker le fichier de clés dans un dossier de sauvegarde sûr.

Si vous essayez d'installer l'apk, signé avec un fichier de clés différent de celui d'avant, vous recevrez un message d'erreur indiquant que l'installation a échoué!

Si vous ne trouvez plus votre ancien fichier de clés ou son mot de passe, procédez comme suit :

1. [Export settings](../Maintenance/ExportImportSettings.md) on your phone.
2. Copiez le fichier de configuration de votre téléphone vers un emplacement externe (par ex. votre ordinateur, un service cloud...).
4. Generate signed apk of new version as described on the [Update guide](../Maintenance/UpdateToNewVersion) and transfer it to your phone.
5. Désinstaller la précédente version de AAPS sur votre téléphone.
6. Installez la nouvelle version de AAPS sur votre téléphone.
7. [Import settings](../Maintenance/ExportImportSettings.md#restoring-from-your-backups-on-a-new-phone-or-fresh-installation-of-aaps) to restore your objectives and configuration.

   Si vous ne pouvez pas les trouver sur votre téléphone, copiez les depuis le stockage externe vers votre téléphone.

8. Vérifiez vos options d'optimisation de la batterie et désactivez-les à nouveau.
9. Keep on looping.

## Gradle Sync en échec
Gradle Sync peut échouer pour diverses raisons. Quand vous recevez un message indiquant que la synchronisation gradle a échouée, ouvrez l'onglet "Build" (1) en bas d'Android Studio et vérifiez quel message d'erreur (2) est affiché.

  ![Gradle Failed](../images/studioTroubleshooting/07_GradleSyncFailed2.png)

Ci-dessous les échecs courants de synchronisation de gradle :
* [Uncommitted changes](#uncommitted-changes)
* [No cached version of ... available](#could-not-resolveno-cached-version)
* [Incompatible Gradle JVM](#incompatible-gradle-jvm)
* [Incompatible version of the Android Gradle plugin](#incompatible-version-of-android-gradle-plugin)

*Important*: After you have followed the instructions for your specific problem, you need to trigger the [gradle sync](#gradle-resync) again.

(troubleshooting_androidstudio-uncommitted-changes)=
### Uncommitted changes

Si vous recevez un message d'erreur comme ceci

![Gradle Uncommited Changes](../images/studioTroubleshooting/02_GradleUncommitedChanges.png)

#### Étape 1 - Vérifiez l'installation de git
  * Ouvrez l'onglet Terminal (1) en bas d'Android Studio, copiez le texte suivant et collez le dans le terminal.
    ```
    git --version
    ```

    ![Gradle Git Version](../images/studioTroubleshooting/03_GitVersion.png)

    Note : Il y a un espace et deux traits d'union entre git et version !

  * Vous devez recevoir un message indiquant quelle version de git est installée, comme vous pouvez le voir dans la capture d'écran ci-dessus. In this case, go to [Step 2](#step-2-check-for-uncommitted-changes).

  * Dans le cas où vous recevez un message disant
    ```
    Git: command not found
    ```
    votre installation Git n'est pas correcte.

  * [Check git installation](../SettingUpAaps/BuildingAaps.md#steps-for-installing-git)

  * Quand vous êtes sur Windows et que git vient juste d'être installé, vous devez redémarrer votre ordinateur pour rendre git disponible après l'installation

  * Si Git est installé, que vous avez redémarré (si sous Windows), et git n'est toujours pas trouvé :

  * Cherchez dans votre ordinateur un fichier "git.exe".

    Notez pour vous, dans quel répertoire il se trouve.

  * Allez dans les variables d'environnement de Windows, sélectionnez la variable "PATH" et cliquez sur Modifier. Add the directory where you have found your git installation.

  * Sauver et fermer.

  * Redémarrer Android Studio.

#### Étape 2 : Vérifier les modifications non commitées.

  * In Android Studio, oben the "Commit" Tab (1) on the left-hand side. ![Commit Tab: Uncommitted changes](../images/studioTroubleshooting/04_CommitTabWithChanges.png)
  * Vous pouvez voir "Default changeset" (2) ou "Unversioned files" (3):

    * Pour "Default Changeset", vous avez probablement mis à jour gradle ou modifié certains contenus du fichier par erreur.

    * Faites un clic droit sur "Default Changeset" et sélectionnez "Rollback"

      ![Commit Tab: Rollback changes](../images/studioTroubleshooting/05_CommitTabRollback.png)

    * Les fichiers sont récupérés à nouveau depuis le serveur Git. If there are no other changes in the commit tab, go to [Step 3](#gradle-resync).

  * Si vous pouvez voir "Unversioned Files", vous pouvez avoir stocké des fichiers dans votre répertoire soure qui devraient être ailleurs, par ex. votre fichier de de clés.

    * Utilisez votre explorateur de fichiers habituel sur votre ordinateur pour déplacer ou couper et coller ce(s) fichier(s) à un autre endroit.

    * Go back to Android Studio and click the Refresh button (4) within the Commit tab to make sure the file is not stored in the AAPS directory anymore.

      If there are no other changes in the commit tab, go to [Step 3](#gradle-resync).


(troubleshooting_androidstudio-step-3-gradle-resync)=

#### Étape 3 : Resynchroniser Gradle (encore)

Follow the instructions at [Gradle Resync](#gradle-resync).

(troubleshooting_androidstudio-android-gradle-plugin-requires-java-11-to-run)=

(incompatible-gradle-jvm)=
### Incompatible Gradle JVM

![Incompatible Gradle JVM](../images/studioTroubleshooting/160_InkompatibelAndroidGradleJVM.png) If you experience the following error message, you need to download a correct JVM version before you can try again:
* Open the gradle view by clicking on the elephant (1) on the right side of Android Studio and open the settings (2) and select **Gradle Settings** (3):

![Open Gradle Settings](../images/studioTroubleshooting/161_GradleSettings.png)

* Open the **Gradle JDK** options, then select **Download JDK...**

![Select Download JDK](../images/studioTroubleshooting/162_DownloadJDK.png)

* At **Version** (1), you need to select **17**. Then select the **JetBrains Runtime** from the **Vendor** (2) options. Do not change the **Location** (3).

![Select JDK 17](../images/studioTroubleshooting/163_JDKSelection.png)

* Close the **Settings** dialog with **OK**.
* You now need to restart the Gradle Sync. Follow the instructions at [Gradle Resync](#gradle-resync).

(incompatible-version-of-android-gradle-plugin)=
### Incompatible version of Android Gradle plugin

  If you experience the following error message

  ![Incompatible version of Android Gradle plugin](../images/studioTroubleshooting/15_InkompatibelAndroidGradlePlugin.png)

  You are using an outdated version of Android Studio. In the menu, go to Help > Check for updates and install any updates of Android Studio and its plugins that are found.

(troubleshooting_androidstudio-could-not-resolve-no-cached-version)=
### Could not resolve/No cached version

  Si vous rencontrez ce message d'erreur:

![Could not resolve... No cached version](../images/studioTroubleshooting/08_NoCachedVersion.png)

  * Sur la droite, ouvrez l'onglet Gradle (1).

    Make sure the button shown at (2) is *NOT* selected.

    ![Gradle Offline Mode](../images/studioTroubleshooting/10_GradleOfflineMode.png)

  * Now you need to trigger a [Gradle Resync](#gradle-resync)

(troubleshooting_androidstudio-unable-to-start-daemon-process)=
### Unable to start daemon process

  Si vous voyez un message d'erreur ci-dessous, vous utilisez probablement un système Windows 10 32 bits. This is not supported by Android Studio 3.5.1 and above and unfortunately nothing the AAPS developer can do about!

  There are a lot of manuals on the internet how to determine wether you have a 32-bit or 64-bit OS - i.e. [this one](https://support.microsoft.com/en-us/windows/32-bit-and-64-bit-windows-frequently-asked-questions-c6ca9541-8dce-4d48-0415-94a3faa2e13d).

  ![Screenshot Unable to start daemon process](../images/AndroidStudioWin10_32bitError.png)

(gradle-resync)=
### Resynchronisation Gradle

  If you can still see the message that the gradle sync failed, now select the Link "Try again". ![Gradle Sync Failed Mode](../images/studioTroubleshooting/01_GradleSyncFailed.png)


  Si vous ne voyez plus le message, vous pouvez toujours le déclencher manuellement:

  * Ouvrez l'onglet Gradle (1) sur le côté droit de Android Studio.

    ![Gradle Reload](../images/studioTroubleshooting/06_GradleResyncManually.png)

  * Right-click on AAPS (2)

  * Cliquez sur "Reload Gradle Project" (3)

## Générer l'APK signé avec succès mais avec 0 variantes de compilation

Lorsque vous générez l'apk signé, vous pouvez obtenir la notification que la génération a été effectuée avec succès mais on vous dit que 0 variantes de compilation ont été générées:

![APK generated with 0 build variants](../images/studioTroubleshooting/14_BuildWith0Variants.png)

C'est un faux avertissement. Check the directory your selected as "Destination folder" for generation (step [Generate Signed APK](../SettingUpAaps/BuildingAaps.md#build-the-aaps-signed-apk)) and you will find the generated apk there!


## L'application a été créée avec les avertissements du compilateur/kotlin

Si votre compilation est terminée avec succès mais que vous obtenez des avertissements du compilateur ou de kotlin (indiqués par un point d'exclamation jaune ou bleu), alors vous pouvez ignorer ces avertissements.

 ![Gradle finished with warnings](../images/studioTroubleshooting/13_BuildWithWarnings.png)

Votre application a été correctement compilée et peut être transférée au téléphone!


## La clé a été créée avec des erreurs

Lors de la création d'un fichier de clés pour pouvoir générer un APK signé, sous Windows, le message d'erreur suivant peut apparaître

![La clé a été créée avec des erreurs](../images/AndroidStudio35SigningKeys.png)

Cela semble être un bug avec Android Studio 3.5.1 et son environnement Java livré sous Windows. La clé est créée correctement mais une recommandation est affichée à tort comme une erreur. Cela peut actuellement être ignoré.


## No CGM data is received by AAPS

* Si vous utilisez l'application Dexcom G6 patchée, cette application est obsolète. Use the [BYODA](../CompatibleCgms/DexcomG6.md#if-using-g6-with-build-your-own-dexcom-app) app instead.

* In case you are using xDrip+: Identify receiver as described on [xDrip+ settings page](../CompatibleCgms/xDrip.md#identify-receiver).


## Application non installée.

![phone app note installed](../images/Update_AppNotInstalled.png)

* Assurez-vous d'avoir transféré le fichier “app-full-release.apk” sur votre téléphone.
* Si vous avez le message "App non installé" sur votre téléphone, suivez ces étapes :

1. [Export settings](../Maintenance/ExportImportSettings.md) (in AAPS version already installed on your phone)
2. Désinstaller AAPS sur votre téléphone.
3. Enable airplane mode & turn off bluetooth.
4. Installer la nouvelle version (« app-full-release.apk »)
5. [Import settings](../Maintenance/ExportImportSettings.md)
6. Activer le bluetooth et désactiver le mode avion

## Application installée mais ancienne version

If you built the app successfully, transferred it to your phone and installed it successfully but the version number stays the same then you might have missed to [update your local copy](../Maintenance/UpdateToNewVersion.md#2-update-your-local-copy)

## Rien ci-dessus n'a marché

Si aucun des conseils ci-dessus ne vous a aidé, vous pourriez envisager de repartir de zéro pour reconstruire l'application :

1. [Export settings](../Maintenance/ExportImportSettings.md) (in AAPS version already installed on your phone)

2. Ayez vos mots de passe pour la clé et le fichier de clés sous la main. In case you have forgotten passwords you can try to find them in project files as described [here](https://youtu.be/nS3wxnLgZOo).

    Ou vous pouvez recréer un nouveau fichier de clés.

3. Build app from scratch as described [here](../SettingUpAaps/BuildingAaps.md#download-the-aaps-code).

4. Quand vous avez construit l'APK avec succès, supprimez l'application existante sur votre téléphone, transférez le nouvel apk sur votre téléphone et installez le.
5. [Import settings](../Maintenance/ExportImportSettings.md) again to restore your objectives and settings.
6. Vous devez vérifier vos options d'optimisation de la batterie et désactivez-les à nouveau.

## Pire scénario

Dans le cas où même construire l'application à partir de rien ne résout pas votre problème, vous pouvez essayer de désinstaller complètement Android Studio. Certains utilisateurs ont signalé que cela a résolu leur problème.

**Make sure to uninstall all files associated with Android Studio.** If you do not completely remove Android Studio with all hidden files, uninstalling may cause new problems instead of solving your existing one(s). Les manuels pour une désinstallation complète peuvent être trouvés en ligne, par ex.

[https://stackoverflow.com/questions/39953495/how-to-completely-uninstall-android-studio-from-windowsv10](https://stackoverflow.com/questions/39953495/how-to-completely-uninstall-android-studio-from-windowsv10).

Install Android Studio from scratch as described [here](../SettingUpAaps/BuildingAaps.md#install-android-studio).
