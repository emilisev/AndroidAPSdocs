(Accessing-logfiles-accessing-logfiles)=
# Accès aux fichiers log

* Connecter le téléphone à un ordinateur en mode de transfert de fichiers
* Locate the log files in the AAPS data directory

   * (2.8.2) The folder will be at a location similar to ***Internal storage(1) / Android / data / info.nightscout.androidaps / files***
   * (3.0.0) The folder will be at a location similar to ***Internal storage(1) / AAPS / logs***
   * Le nom du dossier de stockage racine (1) peut varier légèrement selon le téléphone.

![logs](../images/aapslog.png)

* The current log is a .log file which can be viewed in a number of ways such as [LogCat](https://developer.android.com/studio/debug/am-logcat.html) within Android Studio, any Log Viewer android app, or simply as plain text.
* Les fichiers journaux précédents sont compressés et stockés dans des dossiers dans l'ordre de date / heure.
* If you are sharing your log file in [discord](https://discord.gg/4fQUWHZ4Mw) to talk about a potential bug, please unzip and upload the file dated before the error occurred.
