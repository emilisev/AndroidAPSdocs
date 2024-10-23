# Freestyle Libre 2

The Freestyle Libre 2 sensor is now a real CGM even with the official app. Still, LibreLink cannot send data to AAPS. There are several solutions to use it with AAPS.

## 1. Use a Bluetooth bridge and OOP

Bluetooth transmitters can be used with the Libre 2 (EU) and an [out of process algorithm](https://drive.google.com/file/d/1f1VHW2I8w7Xe3kSQqdaY3kihPLs47ILS/view) app. You can receive blood sugar readings every 5 minutes like with the [Libre 1](./Libre1.md).

Check the bridge and app you want to use are compatible with your sensor and xDrip+ (older Blucon and recent ones won't work, Miaomiao 1 needs firmware 39 and Miaomiao 2 firmware 7).

The Libre2 OOP is creating the same BG readings as with the original reader or the LibreLink app via NFC scan. AAPS with Libre 2 do a 10 to 25 minutes smoothing to avoid certain jumps. See below [Value smoothing & raw values](#value-smoothing--raw-values). OOP generates readings every 5 minutes with the average of the last 5 minutes. Therefore the BG readings are not that smooth but match the original reader device and faster follow the "real" BG readings. If you try to loop with OOP please enable all smoothing settings in xDrip+.

There are some good reasons to use a Bluetooth transmitter:

-   You can choose various OOP2 calibration strategies (1): have the reader values using "no calibration", or calibrate the sensor like a Libre 1 using "calibrate based on raw" or ultimately calibrate the the readers like values with "calibrate based on glucose".  
  Make sure to leave OOP1 disabled (2).

    → Hamburger Menu → Settings → Less common settings → Other misc. options

![OOP2 Calibration](../images/Libre2_OOP2Calibration.png)

-   The Libre 2 sensor can be used 14.5 days as the Libre 1
-   8 hours backfilling is fully supported

Remark: The transmitter can be used in parallel to the LibreLink app without interfering with it.

## 2. Use xDrip+ direct connection

```{admonition} Libre 2 EU only
:class: warning
xDrip+ doesn't support direct connection to Libre 2 US and AUS.  
```

- Follow [these instructions](https://www.minimallooper.com/post/how-to-setup-freestyle-libre-2-and-oop2-to-use-a-native-bluetooth-connection-in-xdrip) to setup xDrip+ but make sure to download [this latest OOP2](https://drive.google.com/file/d/1f1VHW2I8w7Xe3kSQqdaY3kihPLs47ILS/view) as the one in the document is obsolete.
- Follow setup instructions on [xDrip+ settings page](../CompatibleCgms/xDrip.md).

-   Select xDrip+ in in [ConfigBuilder, BG Source](../SettingUpAaps/ConfigBuilder.md#bg-source).

## 3. Use Diabox

- Install [Diabox](https://www.bubblesmartreader.com/_files/ugd/6afd37_f183eabd4fbd44fcac4b1926a79b094f.pdf). In Settings, Integration, enable Share data with other apps.

![Diabox](../images/Diabox.png)

- Select xDrip+ in in [ConfigBuilder, BG Source](../SettingUpAaps/ConfigBuilder.md#bg-source).

## 4. Use Juggluco

- Download and install the Juggluco app from [here](https://www.juggluco.nl/Juggluco/download.html).
- Follow the instructions [here](https://www.juggluco.nl/Juggluco/index.html)
- In Settings, enable xDrip+ broadcast (which doesn't send data to xDrip+ but to AAPS).

![Juggluco broadcast to AAPS](../images/Juggluco_AAPS.png)

- Select xDrip+ in in [ConfigBuilder, BG Source](../SettingUpAaps/ConfigBuilder.md#bg-source).

```{admonition} Use with xDrip+
:class: note
You can set Juggluco to broadcast to xDrip+ with Patched Libre Broadcast (you should disable xDrip+ broadcast), in order to calibrate (see here) and avoid 1 minute readings to be sent to AAPS.  
![Juggluco broadcast to xDrip+](../images/Juggluco_xDrip.png)  
You will then need to set xDrip+ data source to Libre 2 Patched App to receive data from Juggluco.  
```

## 5. Use the patched LibreLink app with xDrip+

```{admonition} Libre 2 EU only
:class: warning
The patched app is an old version (22/4/2019) and might not be compatible with recent Android releases.  
```

### Step 1: Build the patched app

For legal reasons, "patching" has to be done by yourself. Utilisez les moteurs de recherche pour trouver les liens correspondants. There are two variants: The recommended original patched app blocks any internet traffic to avoid tracking. The other variant supports LibreView.

L'application patchée doit être installée au lieu de l'application originale. Le prochain capteur démarré avec celle-ci transmettra les valeurs actuelles de glycémie à l'application xDrip+ exécutée sur votre smartphone via Bluetooth.

Important : Pour éviter d'éventuels problèmes, il peut être utile dans un premier temps d'installer et de désinstaller l'application originale sur un smartphone compatible NFC. Le NFC doit être activé. Cela ne consomme pas plus d'énergie. Installez ensuite l'application patchée.

L'application patchée peut être identifiée par la notification d'autorisation au premier plan. The foreground authorization service improves the connection stability compared to the original app which does not use this service.

![LibreLink Foreground Service](../images/Libre2_ForegroundServiceNotification.png)

Other indications could be the Linux penguin logo in the three dot menu -> Info or the font of the patched app (2) different from the original app (1). Ces critères sont facultatifs en fonction de la source de l'application que vous choisissez.

![LibreLink Font Check](../images/LibreLinkPatchedCheck.png)

Assurez-vous que NFC est activé, activez l'autorisation de mémoire et d'emplacement pour l'application corrigée, activez l'heure et le fuseau horaire automatiques et définissez au moins une alarme dans l'application patchée.

### Step 2: Start the sensor with the patched app

Maintenant, démarrez le détecteur Libre2 avec l'application patchée en scannant simplement le capteur. Assurez-vous d'avoir défini tous les paramètres.

Paramètres obligatoires pour réussir le démarrage du capteur :

-   NFC activé / BT activé
-   autorisation de mémoire et d'emplacement activée
-   service d'emplacement activé
-   réglage automatique de l'heure et du fuseau horaire
-   définir au moins une alarme dans l'application patchée

Veuillez noter que l'activation du service de localisation est primordial. Il ne s'agit pas de l'autorisation d'application qui doit être également définie !

![LibreLink permissions memory & location](../images/Libre2_AppPermissionsAndLocation.png)

![automatic time and time zone + alarm settings](../images/Libre2_DateTimeAlarms.png)

Once the sensor started with the patched app, you won't be able to connect it to another app/phone. If you uninstall the patched app, you will lose alarms and continuous BG readings.

La première configuration de connexion au capteur est critique. L'application LibreLink tente d'établir une connexion sans fil au capteur toutes les 30 secondes. Si un ou plusieurs paramètres obligatoires sont manquants, ils doivent être renseignés. Vous n'avez pas de limite de temps pour le faire. Le capteur essaye constamment de configurer la connexion. Même si cela dure plusieurs heures. Be patient and try different settings before even thinking of changing the sensor.

Tant que vous voyez un point d'exclamation rouge ("!") on the upper left corner of the LibreLink start screen there is no connection or some other setting blocks LibreLink to signal alarms. Vérifiez si le son est activé et que toutes les applications de blocage de notifications sont désactivées. Ce n'est que lorsque le point d'exclamation est parti, que la connexion est établie et que les valeurs de glycémies sont envoyées au smartphone. Cela devrait se produire après un maximum de 5 minutes.

![LibreLink no connection](../images/Libre2_ExclamationMark.png)

Si le point d'exclamation reste ou si vous obtenez un message d'erreur, cela peut avoir plusieurs raisons :

-   Android location service is not granted - please enable it in system settings
-   automatic time and time zone not set - please change settings accordingly
-   activate alarms - at least one of the three alarms must be activated in LibreLink
-   le Bluetooth est éteint - veuillez l'activer
-   le son est bloqué
-   les notifications de l'application sont bloquées
-   les notifications de l'écran de veille sont bloqués

Le redémarrage du téléphone peut vous aider, vous devrez peut-être le faire plusieurs fois. Dès que la connexion est établie, le point d'exclamation rouge disparaît et l'étape la plus importante est franchie. Il peut arriver, selon les paramètres du système, que le point d'exclamation reste mais que vous obtenez des lectures. Dans les deux cas, c'est bon. Le capteur et le téléphone sont maintenant connectés, chaque minute une valeur de glycémie est transmise.

![LibreLink connection established](../images/Libre2_Connected.png)

Dans de rares cas, cela peut aider de vider le cache bluetooth et/ou réinitialiser toutes les connexions réseau via le menu système. Cela supprime tous les périphériques bluetooth connectés ce qui peut aider à configurer une nouvelle connexion bluetooth spécifique. That procedure is safe as the started sensor is remembered by the patched LibreLink app. Il ne faut rien faire de plus ici. Il suffit d'attendre que l'application patchée se connecte au capteur.

Après une connexion réussie, les paramètres du smartphone peuvent être modifiés si nécessaire. Cela n'est pas recommandé, mais vous pouvez vouloir économiser de l'énergie. Le service de localisation peut être éteint, le volume peut être réglé à zéro ou les alarmes peuvent être à nouveau désactivées. Les glycémies sont de toute façon transmises.

Toutefois, lors du démarrage du capteur suivant, tous les paramètres devront à nouveau être définis !

Remarque: L'application patchée en a besoin dans l'heure qui suit le préchauffage pour activer une connexion. Pour les 14 jours de fonctionnement, ils ne sont pas nécessaires. Dans la plupart des cas, lorsque vous rencontrez des problèmes avec le démarrage d'un capteur, le service de localisation a été désactivé. For Android it is needed for proper bluetooth operation(!) to connect. Reportez-vous à la documentation Android de Google.

During the 14 days you can use in parallel one or more NFC capable smartphones (not the reader device!) running the original LibreLink app for scanning via NFC. Il n'y a pas de limite de temps pour les démarrer. Vous pouvez par exemple utiliser un téléphone en parallèle à partir du 5ème jour. Le second téléphone peut télécharger les glycémies dans le Cloud d'Abbott (LibreView). LibreView peut générer des rapports pour votre équipe soignante.

Please note that the original patched app **does not have any connection to the internet** to avoid tracking.

Cependant, il existe une variante de l'application patchée supportant LibreView avec un accès Internet activé. Veuillez noter que vos données sont ensuite transférées dans le cloud. But your endo team reporting is fully supported then. Avec cette variante il est également possible de déplacer les alarmes vers un autre appareil qui n'a pas démarré le capteur. Cherchez avec google dans les forums allemands sur le diabète pour voir comment cela peut être fait.

### Step 3: Install and configure xDrip+ app

Les glycémies sont reçues sur le smartphone par l'application xDrip+.

-   You can safely download the [latest APK (stable)](https://xdrip-plus-updates.appspot.com/stable/xdrip-plus-latest.apk) unless you need recent features, in which case you should use the latest [Nightly Snapshot](https://github.com/NightscoutFoundation/xDrip/releases).
-   Set xDrip+ with the [patched app data source](../CompatibleCgms/xDrip.md#libre-2-patched-app).
-   Follow setup instructions on [xDrip+ settings page](../CompatibleCgms/xDrip.md).

### Step 4: Start sensor

- → Hamburger Menu (1) → Start sensor (2) → Start sensor (3) → Answer "Not Today" (4).

![xDrip+ Start Libre Transmitter & Sensor 3](../images/xDrip_Libre_Transmitter03.png)

This will not physically start any Libre2 sensor or interact with them in any case. Il s'agit simplement d'indiquer à xDrip+ qu'un nouveau capteur envoie des glycémies. Si possible, entrez deux valeurs de glycémie capillaire pour l'étalonnage initial. Maintenant, les glycémies doivent être affichées dans xDrip+ toutes les 5 minutes. Les valeur manquées, par ex. si vous étiez trop loin de votre téléphone, ne seront pas actualisées à postériori.

Après un changement de capteur, xDrip+ détectera automatiquement le nouveau capteur et supprimera toutes les données d'étalonnage. You may check you blood glucose after activation and make a new initial calibration.

### Step 5: Configure AAPS (for looping only)

-   In AAPS go to Config Builder > BG Source and check 'xDrip+'

![xDrip+ BG Source](../images/ConfBuild_BG_xDrip.png)

-   If AAPS does not receive BG values when phone is in airplane mode, use 'Identify receiver' as describe on [xDrip+ settings page](./xDrip.md#identify-receiver).

Jusqu'à présent, en utilisant le Freestyle Libre 2 comme source Gly, vous ne pouvez pas activer les fonctions 'Activer SMB toujours' et 'Activer SMB après les glucides' dans l'algorithme SMB. Les valeurs de GLY du Freestyle Libre 2 ne sont pas assez lisses pour l'utiliser en toute sécurité. See [Smoothing blood glucose data](../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md) for more details.

(Libre2-experiences-and-troubleshooting)=
### Experiences and Troubleshooting

#### Connectivité

The connectivity is good with most phones, with the exception of Huawei mobile phones. La connexion peut s'interrompre si le téléphone portable se trouve dans la poche opposée au capteur ou si vous êtes à l'extérieur. Wear your phone on the sensor side of your body. Dans les pièces, où le Bluetooth se propage avec des réflexions, aucun problème ne devrait survenir. Si vous avez des problèmes de connectivité, testez avec un autre téléphone. Cela peut aussi aider positionner le capteur avec l'antenne BT interne pointant vers le bas. La fente sur l'applicateur doit pointer vers le bas lors de la pose du capteur.

#### Value smoothing & raw values

Technically, the current blood sugar value is transmitted to xDrip+ every minute. A weighted average filter calculates a smoothed value over the last 25 minutes by default. You can change the period in the NFC Scan features menu.

→ Hamburger menu → Settings → NFC Scan features → Smooth libre 3 data when using xxx method

![xDrip+ advanced settings Libre 2 & raw values](../images/xDrip_Libre3_Smooth.png)

Ceci est obligatoire pour la boucle. The curves look smooth and the loop results are great. Les valeurs brutes sur lesquelles les alarmes sont basées sont un peu plus instables, mais correspondent également aux valeurs que le lecteur affiche. De plus, les valeurs brutes peuvent être affichées dans le graphique xDrip+ afin de pouvoir réagir à temps en cas de changements rapides. Please switch on Less Common Settings \> Advanced Settings for Libre2 \> "show Raw values" and "show Sensors Infos". Ainsi les valeurs brutes sont affichées sous forme de petits points blancs et des informations supplémentaires sur les capteurs sont disponibles dans le menu Système.

Les valeurs brutes sont très utiles lorsque les glycémies changent rapidement. Même si les points sont moins stables, vous détecterez beaucoup mieux la tendance qu'avec l'utilisation de la ligne lissée pour prendre les bonnes décisions de traitement.

→ Hamburger menu → Settings → Less common settings → Advanced settings for Libre 2

![xDrip+ advanced settings Libre 2 & raw values](../images/Libre2_RawValues.png)

#### Durée du capteur

La durée d'exécution du capteur est fixée à 14 jours. Les 12 heures supplémentaires du capteur Libre1 n'existent plus. xDrip+ shows additional sensor information after enabling Advanced Settings for Libre2 → "show Sensors Infos" in the system menu like the starting time. The remaining sensor time can also be seen in the patched LibreLink app. Le temps de capteur restant peut également être vu dans l'application LibreLink patchée, Either in the main screen as remaining days display or as the sensor start time in the three-point menu → Help → Event log under "New sensor found".

![Libre 2 start time](../images/Libre2_Starttime.png)

#### Nouveau capteur

Un échange de capteurs a lieu à la volée : configurez le nouveau capteur peu avant l'activation. Dès que xDrip+ ne reçoit plus de données de l'ancien capteur, démarrez le nouveau capteur avec l'application patchée. Après une heure, les nouvelles valeurs doivent apparaître automatiquement dans xDrip+.

Si ce n'est pas le cas, vérifiez les paramètres du téléphone et procédez comme avec le premier démarrage. Vous n'avez pas de limite de temps. Essayez de trouver les bons paramètres. Vous n'avez pas besoin de remplacer immédiatement le capteur avant d'avoir vous essayé différentes combinaisons. Les capteurs sont robustes et essaient en permanence d'établir une connexion. Veuillez prendre votre temps. Dans la plupart des cas, vous avez accidentellement changé un paramètre qui cause maintenant des problèmes.

Une fois réussi, sélectionnez "Sensor Stop" et "Supprimer l'étalonnage seulement" dans xDrip+. Cela indique à xDrip+ qu'un nouveau capteur est mis en place et que les anciennes calibrations ne sont plus valables et doivent donc être supprimées. Aucune interaction n'est faite avec le capteur Libre2 ici ! Vous n'avez pas besoin de démarrer le capteur dans xDrip+.

![xDrip+ missing data when changing Libre 2 sensor](../images/Libre2_GapNewSensor.png)

#### Étalonnage

You can calibrate the Libre2 **with an offset of -40 mg/dl to +20 mg/dL \[-2,2 mmol/l to +1,1 mmol/l\]** (intercept). The slope isn't changeable. Please check by fingerpricking after setting a new sensor, keeping in mind it might not be accurate in the first 12 hours after insertion. Since there can be large differences to the blood measurements, verify every 24 hours and calibrate if necessary. If the sensor is completely off after a few days, it should then be replaced.

### Contrôles de cohérence

Les capteurs Libre2 vérifient que les glycémies lues sont plausibles pour détecter les mauvaises valeurs. Dès que le capteur bouge sur le bras ou est légèrement relevé, les valeurs peuvent commencer à fluctuer. Dans ce cas le capteur Libre2 s'éteindra pour des raisons de sécurité. Malheureusement, lors du scan avec l'application, des vérifications complémentaires sont faites. L'application peut désactiver le capteur même si celui-ci est OK. Actuellement le test interne est trop strict. Avoid scanning the sensor with another phone to reduce the risk of unexpected sensor shutdown.

# Best practices for calibrating a Libre 2 sensor

Pour obtenir les meilleurs résultats en étalonnant un capteur libre 2, il y a des « règles » à suivre. They apply independently of the software combination (e.g. patched libre-app, oop2, …) that is used to handle the libre 2 values.

1.  The most important rule is to only calibrate the sensor when you have a flat bg level for at least 15 minutes. The delta between the last three readings should not exceed 10 mg/dl (over 15min not between each reading). As the libre 2 does not measure your blood glucose level but your flesh glucose level there is some time lag especially when bg level is rising or falling. This time lag can lead to way too large calibration offsets in unfavourable situations even if the bg level rise / fall is not that much. So whenever possible avoid to calibrate on rising or falling edges. -> If you have to add a calibration when you do not have a flat bg level (e.g. when starting a new sensor) it is recommended to remove that calibration(s) as soon as possible and add a new one when in flat bg levels.
2.  Actually this one is automatically taken into account when following rule 1 but to be sure: When doing comparison measurements your bg level should also be flat for about 15min. Do not compare when rising or falling. Important: You still shall do blood glucose measurements whenever you desire, just don’t use the results for calibration when rising or falling!
3.  As calibrating the sensor in flat levels is a very good starting point it is also strongly recommended to calibrate the sensor only within your desired target range like 70 mg/dl to 160 mg/dl. The libre 2 is not optimized to work over a huge range like 50 mg/dl to 350 mg/dl (at least not in a linear manner), so try to only calibrate when within your desired range. -> Simply accept that values outside your calibration range will not perfectly match blood glucose levels.
4.  Ne calibrez pas trop souvent. Calibrating the sensor very often mostly leads to worse results. When the sensor delivers good results in flat conditions just don’t add any new calibration as it does not have any -useful- effect. It should be sufficient to recheck the status every 3-5 days (of course also in flat conditions).
5.  Évitez l'étalonnage lorsque ce n'est pas nécessaire. This might sound silly but it is not recommended to add a new calibration if the blood glucose to flesh glucose level difference is only ±10 mg/dl (e.g. blood glucose level: 95, Libre sensor 100 -> do NOT add the 95, blood glucose level: 95, Libre sensor 115 -> add the 95 to be taken into account for the calibration)

Quelques remarques générales : Après avoir activé un nouveau capteur et à la fin de vie du capteur, il est logique de faire des mesures de comparaison plus souvent que 3-5 jours, comme indiqué dans la règle n° 4. Pour les capteurs neufs et anciens, il est plus probable que les valeurs brutes changent et qu'une nouvelle calibration soit requise. De temps en temps, il arrive qu'un capteur ne fournisse pas de valeurs valides. Il est fort probable que la valeur du capteur soit faible par rapport à la glycémie réelle (par ex. capteur : 50 mg/dl, gly : 130 mg/dl) même après calibration. Si c'est le cas, le capteur ne peut pas être calibré pour donner des résultats exploitables. E.g. Par ex. en utilisant l'application libre patchée, on peut ajouter un décalage de +20 mg/dl maximum. S'il vous arrive que le capteur donne des valeurs beaucoup trop faibles, n’hésitez pas à le remplacer car il ne s’améliorera pas. Même s'il peut s'agir de capteurs défectueux, lorsque l'on voit des capteurs qui fournissent des valeurs beaucoup trop basses très souvent, essayez d’utiliser différentes zones pour placer votre capteur. Même dans la zone officielle (bras supérieur), il peut y avoir des endroits où les capteurs ne fournissent pas de valeurs valides. Il s'agit d'une sorte d'essai pour trouver les zones qui fonctionnent pour vous.
