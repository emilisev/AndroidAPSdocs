# Fonctionnement de AAPS via votre montre connectée Wear OS
(Watchfaces-aaps-watchfaces)=

## Cadrans AAPS

Il existe plusieurs cadrans de montres qui sont inclus dans la version de base de l'APK Wear de AAPS et que vous pouvez choisir. Ces cadrans incluent le delta moyen, l'IA, le débit temporaire de basal actuel et les profils de basal ainsi que le graphique des glycémies.

Vérifiez que les notifications d'AAPS ne sont pas bloquées sur la montre. La confirmation de l'action (par ex. bolus, cible temporaire) est envoyée par une notification que vous devrez glisser et cocher.

Les actions disponibles sur les cadrans de montre sont :
* Appuyez deux fois sur la glycémie pour accéder au menu AAPS
* Appuyez deux fois sur le graphique de la glycémie pour changer l'échelle de temps du graphique

## Sélectionnez un cadran AAPS sur votre montre WearOS
Il existe plusieurs cadrans de montre disponibles dans la version standard de l'APK AAPS pour Wear OS. Une fois que vous avez installé l'APK AAPS Wear sur votre montre, ils seront disponibles. Voici les étapes pour en sélectionner un :

1. Sur votre montre (WearOS uniquement), appuyez longuement sur votre cadran actuel pour faire apparaître l'écran de sélection du cadran et faites défiler complètement vers la droite jusqu'à ce que vous voyiez le bouton "Ajouter un cadran de montre" et sélectionnez-le

![Screenshot_20231123_124657_sysui](https://github.com/openaps/AndroidAPSdocs/assets/10778155/efd4268f-0536-4a31-9ba1-f98108f32483)

2. Faites défiler vers le bas de la liste jusqu'à ce que vous voyez la section "Téléchargées" et trouvez "AAPS (Perso)" et cliquez sur le milieu de l'image pour l'ajouter à votre shortlist de cadrans. Ne vous inquiétez pas de l'apparence actuelle de la montre "AAPS (Perso)", nous sélectionnerons votre skin préféré à l'étape suivante.

![Screenshot_20231123_124619_sysui](https://github.com/openaps/AndroidAPSdocs/assets/10778155/036dc7c4-6672-46c8-b604-8810a16a2eb3)

3. Maintenant, ouvrez AAPS sur votre téléphone et allez au plugin Wear (activez-le dans la Configuration (dans le bloc Synchronisation) si vous ne le voyez pas dans vos plugins actuels en haut).

![Screenshot_20231123_090941_AAPS](https://github.com/openaps/AndroidAPSdocs/assets/10778155/5df23fa3-791b-4c9a-999a-251391a82835)

4. Click on the "Load Watchface" button and select the watchface that you like

![Screenshot_20231123_130410_AAPS](https://github.com/openaps/AndroidAPSdocs/assets/10778155/adde2eca-1df7-4382-b9ab-346819c35d9d)

5. Vérifiez sur votre montre, le cadran de "AAPS (Perso)" devrait maintenant afficher l'apparence que vous avez sélectionnée. Attendre quelques secondes si nécessaire. Vous pouvez maintenant personnaliser les options, etc. en appuyant longuement sur le cadran puis en appuyant sur le bouton "Personnaliser" sous l'image de cadran.


## Cadrans disponibles

![Available watchfaces](../images/Watchface_Types.png)

(Watchfaces-new-watchface-as-of-AAPS-2-8)=
### Nouveaux cadrans depuis AAPS 2.8

![Watchface Digital Style](../images/Watchface_DigitalStyle.png)

* La couleur, les lignes et le cercle sont personnalisables via la roue crantée du menu de sélection du cadran.

## Cadran AAPS v2 - Légende

![Legend AAPSv2 watchface](../images/Watchface_Legend.png)

A - temps écoulé depuis le dernier calcul de la boucle

B - lecture du capteur MGC

C - nombre de minutes depuis la dernière lecture MGC

D - changement par rapport à la dernière lecture MGC (en mmol ou mg/dl)

E - variation moyenne des lectures MGC depuis 15 minutes

F - niveau de batterie du téléphone

G - débits de basal (en U/h ou en % pendant un DBT)

H - BGI (blood glucose interaction) -> the degree to which BG “should” be rising or falling based on insulin activity alone.

I - glucides (glucides actifs | e-glucides à venir)

J - Insuline Active (bolus | basal)

## Accès menu principal de AAPS

Pour accéder au menu principal d'AAPS, vous pouvez utiliser les options suivantes :
* double appui sur votre valeur de glycémie
* sélectionnez l'icône AAPS dans les applications de la montre
* appuyez sur la complication AAPS (si configuré pour le menu)

## Paramètres (dans la montre)

Pour accéder aux paramètres du cadran, entrez dans le menu principal AAPS, faites glisser vers le haut et sélectionnez "Paramètres".

Filled star is for enabled state (**On**), and hollow star icon indicates that setting is disabled (**Off**):

![Settings on/off](../images/Watchface_Settings_On_Off.png)

### Paramètres du compagnon AAPS

* **Vibrate on Bolus** (default `On`):
* **Units for Actions** (default `mg/dl`): if **On** units for actions is `mg/dl`, if **Off** unit is `mmol/l`. Utilisé lors de la définition d'une CT à partir de la montre.

(Watchfaces-watchface-settings)=

### Watchface settings

* **Show Date** (default `Off`): note, date is not available on all watchfaces
* **Show IOB** (default `On`): Display or not IOB value (setting for detailed value is in AAPS wear parameters)
* **Show COB** (default `On`): Display or not COB value
* **Show Delta** (default `On`): Display or not the BG variation of the last 5 minutes
* **Show AvgDelta** (default `On`): Display or not the average BG variation of the last 15 minutes
* **Show Phone Battery** (default `On`): Phone battery in %. Rouge si en dessous de 30%.
* **Show Rig Battery** (default `Off`): Rig battery is a synthesis of Phone battery, pump battery and sensor battery (generally the lowest of the 3 values)
* **Show Basal Rate** (default `On`): Display or not current basal rate (in U/h or in % if TBR)
* **Show Loop Status** (default `On`): show how many minutes since last loop run (arrows around value turn red if above 15').
* **Show BG** (default `On`): Display or not last BG value
* **Show Direction Arrow** (default `On`): Display or not BG trend arrow
* **Show Ago** (default `On`): show how many minutes since last reading.
* **Dark** (default `On`): You can switch from black background to white background (except for Cockpit and Steampunk watch face)
* **Highlight Basals** (default `Off`): Improve the visibility of basal rate and temp basals
* **Matching divider** (default `Off`): For AAPS, AAPSv2 and AAPS(Large) watchfaces, show contrast background for divider (**Off**) or match divider with the background color (**On**)
* **Chart Timeframe** (default `3 hours`): you can select in the sub menu the max time frame of your chart between 1 hour and 5 hours.

### Paramètre Interface Utilisateur

* **Input Design**: with this parameter, you can select the position of "+" and "-" buttons when you enter commands for AAPS (TT, Insulin, Carbs...)

![Input design options](../images/Watchface_InputDesign.png)

### Specific watchface parameters

#### Cadran Steampunk

* **Delta Granularity** (default `Medium`)

![Steampunk_gauge](../images/Watchface_Steampunk_Gauge.png)

#### Circle WF

* **Big Numbers** (default `Off`): Increase text size to improve visibility
* **Ring History** (default `Off`): View graphically BG history with gray rings inside the hour's green ring
* **Light Ring History** (default `On`): Ring history more discreet with a darker gray
* **Animations** (default `On`): When enabled, on supported by watch and not in power saving low-res mode, watchface circle will be animated

### Paramètres des commandes

* **Wizard in Menu** (default `On`): Allow wizard interface in main menu to input Carbs and set Bolus from watch
* **Prime in Menu** (default `Off`): Allow Prime / Fill action from watch
* **Single Target** (default `On`):
  * `On`: you set a single value for TT
  * `Off`: you set Low target and high target for TT

* **Wizard Percentage** (default `Off`): Allow bolus correction from wizard (value entered in percentage before confirmation notification)

(Watchfaces-complications)=

## Complications

_Complication_ is a term from traditional watchmaking, where it describes addition to the main watchface - as another small window or sub-dial (with date, day of the week, moon phase, etc.). Wear OS 2.0 apporte cette métaphore pour permettre aux fournisseurs de données personnalisés, comme la météo, les notifications, compteurs de fitness et plus encore, d'ajouter ces informations à tous les cadrans qui supportent les complications.

AAPS Wear OS app supports complications since build `2.6`, and allow any third party watchface that supports complications to be configured to display AAPS related data (BG with the trend, IOB, COB, etc.).

Complications also serve as **shortcut** to AAPS functions. En appuyant dessus, vous pouvez ouvrir les menus et dialogues de AAPS (selon la complication et la configuration).

![Complications_On_Watchfaces](../images/Watchface_Complications_On_Watchfaces.png)

### Types de Complication

AAPS Wear OS ne fournit que des données brutes, selon les formats prédéfinis. Il revient au cadran récepteur de décider où et comment mettre en forme les complications, y compris sa mise en page, sa bordure, sa couleur et sa police. Parmi les nombreux types de complications Wear OS disponibles, AAPS utilise :

* `SHORT TEXT` - Contains two lines of text, 7 characters each, sometimes referred to as value and label. Il est généralement affiché à l'intérieur d'un cercle ou d'une petite pilule - l'un au-dessous de l'autre, ou côte à côte. C'est une complication très compacte. AAPS essaye de supprimer les caractères inutiles pour l'ajuster : en arrondissant les valeurs, en supprimant les zéros de début et de fin des valeurs, etc.
* `LONG TEXT` - Contains two lines of text, about 20 characters each. Il est généralement affiché à l'intérieur d'un rectangle ou d'une longue pilule - l'une en dessous d'un autre. Il est utilisé pour plus de détails et des statuts textuels.
* `RANGED VALUE` - Used for values from predefined range, like a percentage. Il contient une icône, une étiquette et est généralement rendu en tant que cadran de progression circulaire.
* `LARGE IMAGE` - Custom background image that can be used (when supported by watchface) as background.

### Paramètres des complications

Pour ajouter une complication à un cadran, configurez-le par un appui long et cliquez sur la roue crantée en dessous. Selon la façon dont s'effectue le paramétrage du cadran - soit cliquez sur les espaces réservés, soit entrez dans le menu de paramétrage des complications du cadran. Les complications de AAPS sont regroupées dans le sous-menu AAPS.

Quand vous configurez les complications dans un cadran, Wear OS présente et filtre la liste des complications qui sont adaptées à la zone sélectionnée dans le cadran. Si certaines complications ne sont pas dans la liste, c'est probablement parce qu'elle ne peut pas être utilisée à cet endroit.

### Complications fournies par AAPS

AAPS fournit les complications suivantes :

![AAPS_Complications_List](../images/Watchface_Complications_List.png)

* **BR, CoB & IoB** (`SHORT TEXT`, opens _Menu_): Displays _Basal Rate_ on the first line and _Carbs on Board_ and _Insulin on Board_ on the second line.
* **Blood Glucose** (`SHORT TEXT`, opens _Menu_): Displays _Blood Glucose_ value and _trend_ arrow on the first line and _measurement age_ and _BG delta_ on the second line.
* **CoB & IoB** (`SHORT TEXT`, opens _Menu_): Displays _Carbs on Board_ on the first line and _Insulin on Board_ on the second line.
* **CoB Detailed** (`SHORT TEXT`, opens _Wizard_): Displays current active _Carbs on Board_ on the first line and planned (future, eCarbs) Carbs on the second line.
* **CoB Icon** (`SHORT TEXT`, opens _Wizard_): Displays _Carbs on Board_ value with a static icon.
* **Full Status** (`LONG TEXT`, opens _Menu_): Shows most of the data at once: _Blood Glucose_ value and _trend_ arrow, _BG delta_ and _measurement age_ on the first line. On the second line _Carbs on Board_, _Insulin on Board_ and _Basal Rate_.
* **Full Status (flipped)** (`LONG TEXT`, opens _Menu_): Same data as for standard _Full Status_, but lines are flipped. Can be used in watchfaces which ignores one of two lines in `LONG TEXT`
* **IoB Detailed** (`SHORT TEXT`, opens _Bolus_): Displays total _Insulin on Board_ on the first line and split of _IoB_ for _Bolus_ and _Basal_ part on the second line.
* **IoB Icon** (`SHORT TEXT`, opens _Bolus_): Displays _Insulin on Board_ value with a static icon.
* **Uploader/Phone Battery** (`RANGED VALUE`, opens _Status_): Displays battery percentage of AAPS phone (uploader), as reported by AAPS. Affichée avec une jauge de pourcentage avec de l'icône de la batterie qui reflète la valeur envoyée. It may be not updated in real-time, but when other important AAPS data changes (usually: every ~5 minutes with new _Blood Glucose_ measurement).

Additionally, there are three complications of `LARGE IMAGE` kind: **Dark Wallpaper**, **Gray Wallpaper** and **Light Wallpaper**, displaying static AAPS wallpaper.

### Paramètres des complications

* **Complication Tap Action** (default `Default`): Decides which dialog is opened when user taps complication:
  * _Default_: action specific to complication type _(see list above)_
  * _Menu_: AAPS main menu
  * _Wizard_: bolus wizard - bolus calculator
  * _Bolus_: direct bolus value entry
  * _eCarb_: eCarb configuration dialog
  * _Status_: status sub-menu
  * _None_: Disables tap action on AAPS complications
* **Unicode in Complications** (default `On`): When `On`, the complication will use Unicode characters for symbols like `Δ` Delta, `⁞` vertical dot separator or `⎍` Basal Rate symbol. Le rendu de ces symboles dépend de la police, et cela peut être très spécifique au cadran. This option allows switching Unicode symbols `Off` when needed - if the font used by custom watchface does not support those symbols - to avoid graphical glitches.


## Tuiles (ou Cartes) Wear OS

Les tuiles Wear OS fournissent un accès facile aux informations et aux actions utilisateur pour faire les choses. Les tuiles ne sont disponibles que sur montres Android fonctionnant sur Wear Os version 2.0 et supérieure.

Les tuiles vous permettent d'accéder rapidement aux actions de l'application AAPS sans passer par le menu de la montre. Les tuiles sont optionnelles et peuvent être ajoutées et configurées par l'utilisateur.

Les tuiles sont utilisées « à côté » de n'importe quel cadran de montre. Pour accéder à une tuile, une fois activé, glissez de droite à gauche sur votre cadran pour les afficher.

Veuillez noter que les tuiles n'affichent pas l'état courant de l'application AAPS et ne feront qu'une demande, qui devra-t être confirmée sur la montre avant d'être appliquée.


## Comment ajouter les tuiles :

Avant d'utiliser les tuiles, vous devez activer "Commandes depuis la montre" dans les paramètres "Wear OS" d'AAPS.

![Wear phone preferences enabled](../images/wear_phone_preferences.jpg)

Selon votre version de Wear OS, la marque et le smartphone il y a deux façons d'activer les tuiles :
1. On your watch, from your watch face;
    - Sur votre montre, depuis votre cadran ; - Glissez vers la droite jusqu'à ce que vous atteigniez le "+ Ajout de carte" - Sélectionnez une des tuiles.
    - Select one of the tiles.
2. Sur votre téléphone, ouvrez l'application compagnon pour votre montre.
    - - Pour Samsung ouvrez "Galaxy Wearable", ou pour d'autres marques "Wear OS"
   - Cliquez sur la section "Cartes", puis sur le bouton "+ Ajouter"
   - Trouvez la tuile AAPS que vous souhaitez ajouter en la sélectionnant. ![Wear phone add tile](../images/wear_companion_app_add_tile.png) The order of the tiles can be changed by dragging and dropping

Le contenu des tuiles peut être personnalisé en appuyant longuement sur une tuile et en cliquant sur le bouton "Éditer" ou l'icône "Engrenage".


### Tuile APS(Actions)

La tuile d'action peut contenir de 1 à 4 boutons d'action définis par l'utilisateur. Pour configurer, appuyez longuement sur la tuile, qui affichera les options de configuration. Des actions similaires sont également disponibles via le menu de montre standard.

Les actions prises en charge dans la tuile d'action peuvent envoyer des requêtes dans l'application AAPS pour

* **Calc**; do a bolus calculation, based on carb input and optional a percentage [1]
* **Insulin**; request insulin delivery by entering the unit of insulin
* **Treatment**; request both insulin delivery and add carbs
* **Carbs**; add (extended) carbs
* **TempT**; set a custom temporary target and duration

![Wear action tile, sample calculator](../images/wear_actions.png)

[1] Via, le menu Wear OS, réglez l'option "Pourcentage de Calculateur" à "ON" pour afficher le pourcentage d'entrée dans la calculatrice de bolus. The default percentage is based on the phone settings in the"Overview" section ["Deliver this part of the bolus wizard result %"](../SettingUpAaps/Preferences.md#not-documented-anymore-please-fix-me) When the user does not provide a percentage, the default value from the phone is used. Configurez les autres paramètres de l'assistant bolus dans l'application téléphone via "Préférences" "Paramètres de l'assistant".


### Tuile AAPS(Cible Temp)

La tuile cible temporaire peut demander une cible temporaire basée sur les préréglages du téléphone AAPS. Configure preset time and targets through the phone app setting by going to "Preferences", "Overview", ["Default Temp-Targets"](../SettingUpAaps/Preferences.md#default-temp-targets)  and set the duration and targets for each preset. Configurez les actions visibles sur la tuile à travers les paramètres de tuile. Faites un appui long sur la tuile pour afficher les options de configuration et sélectionnez 1 à 4 options :

* **Activity**; for sport
* **Hypo**; to raise the target during hypo treatment
* **Eating soon**; to lower the target to raise the insulin on board
* **Manual**; set a custom temporary target and duration
* **Cancel**; to stop the current temporary target

![Wear actions tile edit](../images/wear_tile_tempt_edit.png)


### Tuile AAPS(Assistant rapide)

La tuile Assistant rapide peut contenir 1 à 4 boutons d'action de l'assistant, définis avec l'application du téléphone[2]. See [QuickWizard](../SettingUpAaps/Preferences.md#quick-wizard). Vous pouvez définir des repas standards (glucides et méthode de calcul du bolus) à afficher sur la tuile en fonction de l'heure de la journée. Idéal pour les repas et collations les plus courants que vous mangez pendant la journée. Vous pouvez spécifier si les boutons de l'assistant rapide s'afficheront sur le téléphone, la montre ou les deux. Veuillez noter que le téléphone ne peut afficher qu'un seul bouton de l'assistant rapide à la fois. La configuration de l'assistant rapide peut également spécifier un pourcentage personnalisé de l'insuline pour le bolus. Le pourcentage personnalisé vous permet de varier, par exemple, la collation à 120%, l'absorption lente du petit déjeuner 80% et le traitement hypo de la collation à 0%

![Wear actions tile and phone configuration](../images/quickwizard_watch_phone.png)

[2] Wear OS limite la fréquence de mise à jour des tuiles à une seule fois toutes les 30 secondes. When you notice that the changes on your phone are not reflected on the tile, consider; waiting 30 seconds, using the "Resend all data" button from the Wear OS section of AAPS, or removing the tile and adding it again. Pour modifier l'ordre des boutons de l'Assistant rapide, faites glisser un élément vers le haut ou vers le bas.


## Toujours actif

Long battery life for Android Wear OS smartwatches is a challenge. Some smartwatches get as much as 30 hours before recharging. The display should be switched off for optimal power saving when not in use. Most watches support the “Always on” display.

Since AAPS version 3, we can use a “Simplify UI” during always-on-mode. This UI only contains the blood glucose, direction, and time. This UI is power-optimized with less frequent updates, showing less information and lightening fewer pixels to save power on OLED displays.

The simplified UI mode is available for the watch-faces: AAPS, AAPS V2, Home Big, Digital Style, Steampunk, and Cockpit. The simplified UI is optional and is configured through the watch face settings. (log press the watch face and click “edit” or the gear icon) Select the configuration “Simplify UI" and set it to “Always on” or “Always on and charging”.

### Mode nuit

While charging, it would be helpful if the display could stay “always-on” and show your blood glucose during the night. However, the standard watch-faces are too bright and have too much information, and the details are hard to read with sleepy eyes. Therefore, we added an option for the watch-face to simplify the UI only during charging when set in the configuration.

The simplified UI mode is available for the watch-faces: AAPS, AAPS V2, Home Big, Digital Style, Steampunk, and Cockpit. The simplified UI is optional and is configured through the watch face settings. (log press the watch face and click “edit” or the gear icon) Select the configuration “Simplify UI" and set it to “During charging” or “Always on and charging”

The Android developer options enable your watch to stay awake during charging. To make the developer options available, see the [official documentation](https://developer.android.com/training/wearables/get-started/debugging). Set the “Stay awake when charging” to “on” in the developer options”.

Note: not all displays can handle always-on very well. It can cause screen burn-in, especially on the older OLED displays. The watches will generally dim the display to prevent burn-in; please check your owner’s manual, the manufacturing, or the internet for advice.

![Watchface Nightstand](../images/Watchface_nightstand.jpg)

![Simplified UI](../images/Watchface_simplified_ui.png)

## Snooze Alert shortcut
It is possible to create a shortcut to snooze the alerts/alarm of AAPS. Muting the sound via your watch is convenient and faster without reaching for your phone. Note; you still have to check your alarm message on your phone and handle it accordingly, but you can check that later. When your watch has two buttons, you can assign a key to the `AAPS Snooze Alert` program.

To link the button on the Samsung Watch 4 go to `Settings > Advanced Features > Customize Buttons > Double press > AAPS Snooze Alert`

### Snooze xDrip
When you use xDrip and have xDrip installed on the watch, the 'AAPS Snooze Alert' shortcut will also Snooze any xDrip alarm.


## Conseils sur les performances et la durée de vie des batteries

Wear OS watches are very power-constrained devices. The size of the watch case limits the capacity of the included battery. Even with recent advancements both on hardware and software side, Wear OS watches still require daily charging.

If an experienced battery span is shorter than a day (from dusk to dawn), here are some tips to troubleshoot the issues.

Main battery-demanding areas are:

* Active display with a backlight on (for LED) or in full intensity mode (for OLED)
* Rendering on screen
* Radio communication over Bluetooth

Since we cannot compromise on communication (we need up-to-date data) and want to have the most recent data rendered, most of the optimizations can be done in _display time_ area:

* Stock watchfaces are usually better optimized than custom one, downloaded from the store.
* It is better to use watchfaces that limit the amount of rendered data in inactive / dimmed mode.
* Be aware when mixing other Complications, like third party weather widgets, or other - utilizing data from external sources.
* Start with simpler watchfaces. Add one complication at the time and observe how they affect battery life.
* Try to use **Dark** theme for AAPS watchfaces, and [**Matching divider**](#watchface-settings). On OLED devices it will limit the amount of pixels lit and limit burnout.
* Check what performs better on your watch: AAPS stock watchfaces or other watchfaces with AAPS Complications.
* Observe over a few days, with different activity profiles. Most watches activate the display on glancing, movement and other usage-related triggers.
* Check your global system settings that affect performance: notifications, backlight/active display timeout, when GPS is activated.
* Check [list of tested phones and watches](../CompatiblePhones/ListOfTestedPhones.md) and [ask community](../GettingHelp/WhereCanIGetHelp.md) for other users experiences and reported battery lifetime.
* **We cannot guarantee that data displayed on watchface or complication is up-to-date**. In the end, it is up to Wear OS to decide when to update a watchface or a complication. Even when the AAPS app requests update, the System may decide to postpone or ignore updates to conserve battery. When in doubt and low on battery on watch - always double-check with main AAPS app on phone.

(Watchfaces-troubleshooting-the-wear-app)=
## Dépannage de l'application wear :

*  Sometimes it helps to re-sync the apps to the watch as it can be a bit slow to do so itself: Android Wear > Cog icon > Watch name > Resync apps.
*  Enable ADB debugging in Developer Options (on watch), connect the watch via USB and start the Wear app once in Android Studio.
*  If Complications does not update data - check first if AAPS watchfaces work at all.

## Garmin
There are a couple of watch faces for Garmin that integrate with xDrip or Nightscout on the [Garmin ConnectIQ store](https://apps.garmin.com/en-US/search?keyword=glucose&device=&deviceLimit=&appType=&sort=&start=0&count=30).

[AAPS Glucose Watch](https://apps.garmin.com/apps/3d163641-8b13-456e-84c3-470ecd781fb1) integrates directly with AAPS. It shows loop status data (insulin on board, temporary basal) in addition to glucose readings and sends heart rate readings to AAPS. It is available in the ConnectIQ store, the necessary AAPS plugin is only available from AAPS 3.2.

![Screenshot](../images/Garmin_WF.png) ![Screenshot](../images/Garmin_WF-annotated.png)

## Troubleshooting Sony smartwatch setup

Although it was discontinued a few years ago, if you are using a Sony Smartwatch SW 3 please see here for a troubleshooting guide: [Troubleshooting Sony Smartwatch SW 3](../UsefulLinks/SonySW3.md)

## Des cadrans supplémentaires AAPS personnalisés sont également disponibles

[Here](../UsefulLinks/AdditionalWatchfaces.md) you can download Zip-Files with custom watchfaces made by other users.

## Build your own watchface

If you want to build your own watchface, follow the [guide here](../UsefulLinks/CustomWatchfaceReference.md).

Once you have built a custom watchface, you can share your own **AAPS** custom watchface with others, the zip-file can be uploaded in the folder  "ExchangeSiteCustomWatchfaces" via a Pull Request into Github. Lors de la fusion du "Pull Request", l'équipe de documentation extraira le fichier image et le nom du cadran du fichier Zip, et ajoutera le lien de téléchargement à la liste ci-dessous.