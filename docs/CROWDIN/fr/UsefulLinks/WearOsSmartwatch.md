# Fonctionnement de AAPS via votre montre connectée Wear OS

(Watchfaces-aaps-watchfaces)=

## Cadrans AAPS

Il existe plusieurs cadrans de montres qui sont inclus dans la version de base de l'APK Wear de AAPS et que vous pouvez choisir. Ces cadrans incluent le delta moyen, l'IA, le débit temporaire de basal actuel et les profils de basal ainsi que le graphique des glycémies.

Vérifiez que les notifications d'AAPS ne sont pas bloquées sur la montre. La confirmation de l'action (par ex. bolus, cible temporaire) est envoyée par une notification que vous devrez glisser et cocher.

Les actions disponibles sur les cadrans de montre sont :

- Appuyez deux fois sur la glycémie pour accéder au menu AAPS
- Appuyez deux fois sur le graphique de la glycémie pour changer l'échelle de temps du graphique

## Sélectionnez un cadran AAPS sur votre montre WearOS

Il existe plusieurs cadrans de montre disponibles dans la version standard de l'APK AAPS pour Wear OS. Une fois que vous avez installé l'APK AAPS Wear sur votre montre, ils seront disponibles. Voici les étapes pour en sélectionner un :

1. Sur votre montre (WearOS uniquement), appuyez longuement sur votre cadran actuel pour faire apparaître l'écran de sélection du cadran et faites défiler complètement vers la droite jusqu'à ce que vous voyiez le bouton "Ajouter un cadran de montre" et sélectionnez-le

![Screenshot\_20231123\_124657\_sysui](https://github.com/openaps/AndroidAPSdocs/assets/10778155/efd4268f-0536-4a31-9ba1-f98108f32483)

2. Faites défiler vers le bas de la liste jusqu'à ce que vous voyez la section "Téléchargées" et trouvez "AAPS (Perso)" et cliquez sur le milieu de l'image pour l'ajouter à votre shortlist de cadrans. Ne vous inquiétez pas de l'apparence actuelle de la montre "AAPS (Perso)", nous sélectionnerons votre skin préféré à l'étape suivante.

![Screenshot\_20231123\_124619\_sysui](https://github.com/openaps/AndroidAPSdocs/assets/10778155/036dc7c4-6672-46c8-b604-8810a16a2eb3)

3. Maintenant, ouvrez AAPS sur votre téléphone et allez au plugin Wear (activez-le dans la Configuration (dans le bloc Synchronisation) si vous ne le voyez pas dans vos plugins actuels en haut).

![Screenshot\_20231123\_090941\_AAPS](https://github.com/openaps/AndroidAPSdocs/assets/10778155/5df23fa3-791b-4c9a-999a-251391a82835)

4. Click on the "Load Watchface" button and select the watchface that you like

![Screenshot\_20231123\_130410\_AAPS](https://github.com/openaps/AndroidAPSdocs/assets/10778155/adde2eca-1df7-4382-b9ab-346819c35d9d)

5. Vérifiez sur votre montre, le cadran de "AAPS (Perso)" devrait maintenant afficher l'apparence que vous avez sélectionnée. Attendre quelques secondes si nécessaire. Vous pouvez maintenant personnaliser les options, etc. en appuyant longuement sur le cadran puis en appuyant sur le bouton "Personnaliser" sous l'image de cadran.

## Cadrans disponibles

![Cadrans disponibles](../images/Watchface_Types.png)

(Watchfaces-new-watchface-as-of-AAPS-2-8)=

### Nouveaux cadrans depuis AAPS 2.8

![Cadran Digital](../images/Watchface_DigitalStyle.png)

- La couleur, les lignes et le cercle sont personnalisables via la roue crantée du menu de sélection du cadran.

## Cadran AAPS v2 - Légende

![Légende du cadran AAPS v2](../images/Watchface_Legend.png)

A - temps écoulé depuis le dernier calcul de la boucle

B - lecture du capteur MGC

C - nombre de minutes depuis la dernière lecture MGC

D - changement par rapport à la dernière lecture MGC (en mmol ou mg/dl)

E - variation moyenne des lectures MGC depuis 15 minutes

F - niveau de batterie du téléphone

G - débits de basal (en U/h ou en % pendant un DBT)

H - IG (BGI) Impact Glycémique -> l'augmentation ou diminution que "devrait" avoir la glycémie en fonction de l'activité de l'insuline seule.

I - glucides (glucides actifs | e-glucides à venir)

J - Insuline Active (bolus | basal)

## Accès menu principal de AAPS

Pour accéder au menu principal d'AAPS, vous pouvez utiliser les options suivantes :

- double appui sur votre valeur de glycémie
- sélectionnez l'icône AAPS dans les applications de la montre
- appuyez sur la complication AAPS (si configuré pour le menu)

## Paramètres (dans la montre)

Pour accéder aux paramètres du cadran, entrez dans le menu principal AAPS, faites glisser vers le haut et sélectionnez "Paramètres".

L'étoile remplie est pour l'état activé (**On**), et l'étoile vide indique que le paramètre est désactivé (**Off**) :

![Paramètres On/Off](../images/Watchface_Settings_On_Off.png)

### Paramètres du compagnon AAPS

- **Vibrer sur Bolus** (par défaut `On`):
- **Unités des Actions** (par défaut `mg/dl`) : si **On** l'unité des actions est `mg/dl`, si **Off** l'unité est `mmol/l`. Utilisé lors de la définition d'une CT à partir de la montre.

(Watchfaces-watchface-settings)=

### Watchface settings

- **Afficher Date** (par défaut `Off`): remarque, la date n'est pas disponible sur tous les cadrans
- **Afficher IA** (par défaut `On`) : afficher ou non la valeur de l'IA (le paramétrage de l'affichage des valeurs détaillées est dans les paramètres Wear de l'Assistant de Configuration d'AAPS)
- **Afficher GA** (par défaut `On`) : afficher ou non la valeur GA
- **Afficher Delta** (par défaut `On`) : afficher ou non la variation de Gly des 5 dernières minutes
- \*\* Afficher Delta Moyen\*\* (par défaut `On`) : afficher ou non la variation moyenne des Gly des 15 dernières minutes
- **Afficher Batterie Téléphone** (par défaut `On`) : batterie du téléphone en %. Rouge si en dessous de 30%.
- **Afficher Batterie Système** (par défaut `Off`) : la batterie système est une synthèse de la batterie du Téléphone, de la pompe et de la pile du capteur (en général la plus faible des 3 valeurs)
- **Afficher Basale** (par défaut `On`) : afficher ou non le débit de basal (en U/h ou en % si DBT)
- **Afficher État Boucle** (par défaut `On`) : afficher ou non le nombre de minutes depuis le dernier calcul de boucle (les flèches autour de la valeur deviennent rouge si au-dessus de 15').
- **Afficher Glycémie** (par défaut `On`) : afficher ou non la dernière valeur de glycémie
- **Afficher flèche** (par défaut `On`) : afficher ou non la flèche de tendance Gly
- **Afficher Min Passées** (par défaut `On`) : afficher ou non le nombre de minutes depuis la dernière lecture.
- **Sombre** (par défaut `On`) : Vous pouvez changer l'arrière plan du cadran de noir à blanc (sauf pour les cadrans Cockpit et Steampunk)
- **Surbrillance Basale** (par défaut `Off`) : Améliorer la visibilité des débits de basal et basales temporaires
- **Séparateur** (par défaut `Off`) : pour les cadrans AAPS, AAPSv2 et AAPS(Large), affiche le fond du séparateur contrasté avec l'arrière plan (**Off**) ou de la même couleur que l'arrière plan (**On**)
- **Echelle Graphique** (par défaut `3 heures`) : vous pouvez sélectionner dans le sous-menu de la durée max de votre graphique entre 1 heure et 5 heures.

### Paramètre Interface Utilisateur

- **Design de saisie** : avec ce parametre, vous pouvez sélectionner la position des boutons "+" et "-" quand vous entrez des commandes pour AAPS (CT, Insuline, Glucides...)

![Input design options](../images/Watchface_InputDesign.png)

### Specific watchface parameters

#### Cadran Steampunk

- **Précision Delta** (par défaut `Moyenne`)

![Cadran Steampunk](../images/Watchface_Steampunk_Gauge.png)

#### Circle WF

- **Gros chiffres** (par défaut `Off`) : Augmenter la taille du texte pour améliorer la visibilité
- **Historique** (par défaut `Off`) : Afficher graphiquement l'historique des Gly avec des cercles gris à l'intérieur de l'anneau vert de l'heure
- **Historique Léger** (par défaut `On`) : cercles plus discrets avec un gris foncé
- **Animations** (par défaut `On`) : Si activé, sur les montres supportée et hors mode économie d'énergie basse résolution, le cercle du cadran est animé

### Paramètres des commandes

- **Assistant dans Menu** (par défaut `On`) : Autoriser l'action Assistant dans le menu principal pour renseigner les Glucides et faire des Bolus à partir de la montre

- **Amorcer dans Menu** (par défaut `Off`) : Autoriser l'action Amorcer/Remplir à partir de la montre

- **Cible unique** (par défaut `On`):
  - `On`: vous définissez une valeur unique pour une CT
  - `Off`: vous définissez une cible basse et haute pour une CT

- **Assistant Pourcentage** (par défaut `Off`) : Autoriser la correction du bolus à partir de l'assistant (valeur saisie en pourcentage avant la confirmation)

(Watchfaces-complications)=

## Complications

La _complication_ est un terme issu de l'horlogerie traditionnelle, il décrit l'ajout à la montre principale d'une autre petite fenêtre ou sous-cadran (avec date, jour de la semaine, phase lunaire, etc.). Wear OS 2.0 apporte cette métaphore pour permettre aux fournisseurs de données personnalisés, comme la météo, les notifications, compteurs de fitness et plus encore, d'ajouter ces informations à tous les cadrans qui supportent les complications.

AAPS Wear OS prend en charge les complications depuis la version `2.6`, et permet à tout les cadrans qui supporte les complications d'être configuré pour afficher les données liées à AAPS (Gly avec tendance, IA, GA, etc.).

Les complications servent également de **raccourci** aux fonctions AAPS. En appuyant dessus, vous pouvez ouvrir les menus et dialogues de AAPS (selon la complication et la configuration).

![Complications\_On\_Watchfaces](../images/Watchface_Complications_On_Watchfaces.png)

### Types de Complication

AAPS Wear OS ne fournit que des données brutes, selon les formats prédéfinis. Il revient au cadran récepteur de décider où et comment mettre en forme les complications, y compris sa mise en page, sa bordure, sa couleur et sa police. Parmi les nombreux types de complications Wear OS disponibles, AAPS utilise :

- `TEXTE COURT` - Contient deux lignes de texte, 7 caractères chacune, parfois appelés valeur et étiquette. Il est généralement affiché à l'intérieur d'un cercle ou d'une petite pilule - l'un au-dessous de l'autre, ou côte à côte. C'est une complication très compacte. AAPS essaye de supprimer les caractères inutiles pour l'ajuster : en arrondissant les valeurs, en supprimant les zéros de début et de fin des valeurs, etc.
- `TEXTE LONG` - Contient deux lignes de texte, d'environ 20 caractères chacune. Il est généralement affiché à l'intérieur d'un rectangle ou d'une longue pilule - l'une en dessous d'un autre. Il est utilisé pour plus de détails et des statuts textuels.
- `PLAGE DE VALEUR` - Utilisée pour les valeurs d'une plage prédéfinie, comme un pourcentage. Il contient une icône, une étiquette et est généralement rendu en tant que cadran de progression circulaire.
- `GRANDE IMAGE` - Image d'arrière-plan personnalisée qui peut être utilisée (si pris en charge par le cadran) en arrière-plan.

### Paramètres des complications

Pour ajouter une complication à un cadran, configurez-le par un appui long et cliquez sur la roue crantée en dessous. Selon la façon dont s'effectue le paramétrage du cadran - soit cliquez sur les espaces réservés, soit entrez dans le menu de paramétrage des complications du cadran. Les complications de AAPS sont regroupées dans le sous-menu AAPS.

Quand vous configurez les complications dans un cadran, Wear OS présente et filtre la liste des complications qui sont adaptées à la zone sélectionnée dans le cadran. Si certaines complications ne sont pas dans la liste, c'est probablement parce qu'elle ne peut pas être utilisée à cet endroit.

### Complications fournies par AAPS

AAPS fournit les complications suivantes :

![Liste des complications AAPS](../images/Watchface_Complications_List.png)

- **Gly, GA & IA** (`TEXTE COURT`, ouvre _Menu_) : Affiche _Débit de Basal_ sur la première ligne et _Glucides Actifs_ et _Insuline Active_ sur la deuxième ligne.
- **Glycémie** (`TEXTE COURT`, ouvre _Menu_) : Affiche la valeur de la _Glycémie_ et la flèche de _tendance_ sur la première ligne et _l'âge de la mesure_ et le _delta Gly_ sur la deuxième ligne.
- **GA & IA** (`TEXTE COURT`, ouvre _Menu_) : affiche _Glucides Actifs_ sur la première ligne et _Insuline Active_ sur la deuxième ligne.
- **GA Détaillé** (`TEXTE COURT`, ouvre _Assistant_) : affiche la valeur courante de _Glucides Actifs_ sur la première ligne et les glucides planifiés (Glucides étendus à venir) sur la deuxième ligne.
- **Icone GA** (`TEXTE COURT`, ouvre _Assistant_) : affiche la valeur de _Glucides Actifs_ avec une icône statique.
- **Statut Complet** (`TEXTE LONG`, ouvre _Menu_) : Indique que la plupart des données en même temps : _Glycémie_ et flèche de _tendance_, _Delta Gly_ et _âge de la mesure_ sur la première ligne. Sur la deuxième ligne _Glucides Actifs_, _Insuline Active_ et _Débit de basal_.
- **Statut Complet (inversé)** (`TEXTE LONG`, ouvre _Menu_) : Même données que pour le _Statut Complet_, mais les lignes sont inversées. Peut être utilisé dans certains cadrans qui ignorent l'une des deux lignes dans les `TEXTE LONG`
- **IA Détaillé** (`TEXTE COURT`, ouvre _Bolus_) : Affiche l'_Insuline Active_ totale sur la première ligne et la part d'_IA_ pour le _Bolus_ et la _Basale_ sur la deuxième ligne.
- **Icone IA** (`TEXTE COURT`, ouvre _Bolus_) : Affiche la valeur _Insuline Active_ avec une icône statique.
- **Batterie du téléphone** (`PLAGE DE VALEURS`, ouvre _Etats_) : Affiche le pourcentage de batterie du téléphone AAPS, tel que signalé par AAPS. Affichée avec une jauge de pourcentage avec de l'icône de la batterie qui reflète la valeur envoyée. Il peut ne pas être mis à jour en temps réel, mais lorsque d'autres données importantes de AAPS changent (en général: toutes les ~ 5 minutes avec une nouvelle mesure de _Glycémie_).

De plus, il y a trois complications de type `IMAGE LARGE` : **Fond d'écran noir**, **fond d'écran gris** et **fond d'écran clair**, affichant une image AAPS statique.

### Paramètres des complications

- **Action Appui Complication** (par défaut `Défaut`) : Décide de l'action qui s'ouvre lorsque l'utilisateur appui sur la Complication :
  - _Default_: action specific to complication type _(see list above)_
  - _Menu_ : menu principal AAPS
  - _Assistant_ : assistant bolus - calculateur bolus
  - _Bolus_: direct bolus value entry
  - _eGlucides_ : boîte de dialogue de configuration eGlucides
  - _Etats_ : sous-menu d'états
  - _Aucun_ : Désactive l'action sur les complications AAPS
- **Unicode dans Complications** (par défaut `On`) : Si `On`, la complication utilise des caractères Unicode pour les symboles tels que `Δ` Delta, `⁞` séparateur de point vertical ou `⎍` symbole du débit de basal. Le rendu de ces symboles dépend de la police, et cela peut être très spécifique au cadran. Cette option permet de désactiver les symboles `Unicode` quand c'est nécessaire - si la police utilisée par le cadran personnalisé ne prend pas en charge ces symboles - pour éviter les problèmes graphiques.

## Tuiles (ou Cartes) Wear OS

Les tuiles Wear OS fournissent un accès facile aux informations et aux actions utilisateur pour faire les choses. Les tuiles ne sont disponibles que sur montres Android fonctionnant sur Wear Os version 2.0 et supérieure.

Les tuiles vous permettent d'accéder rapidement aux actions de l'application AAPS sans passer par le menu de la montre. Les tuiles sont optionnelles et peuvent être ajoutées et configurées par l'utilisateur.

Les tuiles sont utilisées « à côté » de n'importe quel cadran de montre. Pour accéder à une tuile, une fois activé, glissez de droite à gauche sur votre cadran pour les afficher.

Veuillez noter que les tuiles n'affichent pas l'état courant de l'application AAPS et ne feront qu'une demande, qui devra-t être confirmée sur la montre avant d'être appliquée.

## Comment ajouter les tuiles :

Avant d'utiliser les tuiles, vous devez activer "Commandes depuis la montre" dans les paramètres "Wear OS" d'AAPS.

![Activer les préférences du téléphone Wear](../images/wear_phone_preferences.jpg)

Selon votre version de Wear OS, la marque et le smartphone il y a deux façons d'activer les tuiles :

1. On your watch, from your watch face;
   - Sur votre montre, depuis votre cadran ; - Glissez vers la droite jusqu'à ce que vous atteigniez le "+ Ajout de carte" - Sélectionnez une des tuiles.
   - Select one of the tiles.
2. Sur votre téléphone, ouvrez l'application compagnon pour votre montre.
   - - Pour Samsung ouvrez "Galaxy Wearable", ou pour d'autres marques "Wear OS"
   - Cliquez sur la section "Cartes", puis sur le bouton "+ Ajouter"
   - Trouvez la tuile AAPS que vous souhaitez ajouter en la sélectionnant.
     ![Wear phone add tile](../images/wear_companion_app_add_tile.png) L'ordre des tuiles peut être modifié en glisser-déposer

Le contenu des tuiles peut être personnalisé en appuyant longuement sur une tuile et en cliquant sur le bouton "Éditer" ou l'icône "Engrenage".

### Tuile APS(Actions)

La tuile d'action peut contenir de 1 à 4 boutons d'action définis par l'utilisateur. Pour configurer, appuyez longuement sur la tuile, qui affichera les options de configuration. Des actions similaires sont également disponibles via le menu de montre standard.

Les actions prises en charge dans la tuile d'action peuvent envoyer des requêtes dans l'application AAPS pour

- **Calc** : faire un calcul de bolus, basé sur l'entrée de glucides et avec un pourcentage optionnel [1]
- **Insuline** : demander l'injection d'insuline en entrant les unités d'insuline
- **Traitement** : demander à la fois l'injection d'insuline et ajouter des glucides
- **Glucides** : ajouter des glucides (étendus)
- **TempT** : définir une cible temporaire personnalisée ainsi que sa durée

![Wear action tile, sample calculator](../images/wear_actions.png)

[1] Via, le menu Wear OS, réglez l'option "Pourcentage de Calculateur" à "ON" pour afficher le pourcentage d'entrée dans la calculatrice de bolus. The default percentage is based on the phone settings in the"Overview" section ["Deliver this part of the bolus wizard result %"](../SettingUpAaps/Preferences.md#not-documented-anymore-please-fix-me) When the user does not provide a percentage, the default value from the phone is used. Configurez les autres paramètres de l'assistant bolus dans l'application téléphone via "Préférences" "Paramètres de l'assistant".

### Tuile AAPS(Cible Temp)

La tuile cible temporaire peut demander une cible temporaire basée sur les préréglages du téléphone AAPS. Configure preset time and targets through the phone app setting by going to "Preferences", "Overview", ["Default Temp-Targets"](../SettingUpAaps/Preferences.md#default-temp-targets) and set the duration and targets for each preset. Configurez les actions visibles sur la tuile à travers les paramètres de tuile. Faites un appui long sur la tuile pour afficher les options de configuration et sélectionnez 1 à 4 options :

- **Activité** : pour le sport
- **Hypo** : pour augmenter la cible pendant le traitement d'une hypo
- **Repas imminent** : pour baisser la cible et augmenter l'insuline à bord
- **Manuel** : pour définir une cible temporaire personnalisée ainsi que sa durée
- **Annuler** : pout arrêter la cible temporaire actuelle

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

![Cadran Mode Nuit](../images/Watchface_nightstand.jpg)

![Interface simplifiée](../images/Watchface_simplified_ui.png)

## Snooze Alert shortcut

It is possible to create a shortcut to snooze the alerts/alarm of AAPS. Muting the sound via your watch is convenient and faster without reaching for your phone. Note; you still have to check your alarm message on your phone and handle it accordingly, but you can check that later. When your watch has two buttons, you can assign a key to the `AAPS Snooze Alert` program.

To link the button on the Samsung Watch 4 go to `Settings > Advanced Features > Customize Buttons > Double press > AAPS Snooze Alert`

### Snooze xDrip

When you use xDrip and have xDrip installed on the watch, the 'AAPS Snooze Alert' shortcut will also Snooze any xDrip alarm.

## Conseils sur les performances et la durée de vie des batteries

Wear OS watches are very power-constrained devices. The size of the watch case limits the capacity of the included battery. Even with recent advancements both on hardware and software side, Wear OS watches still require daily charging.

If an experienced battery span is shorter than a day (from dusk to dawn), here are some tips to troubleshoot the issues.

Main battery-demanding areas are:

- Active display with a backlight on (for LED) or in full intensity mode (for OLED)
- Rendering on screen
- Radio communication over Bluetooth

Since we cannot compromise on communication (we need up-to-date data) and want to have the most recent data rendered, most of the optimizations can be done in _display time_ area:

- Stock watchfaces are usually better optimized than custom one, downloaded from the store.
- It is better to use watchfaces that limit the amount of rendered data in inactive / dimmed mode.
- Be aware when mixing other Complications, like third party weather widgets, or other - utilizing data from external sources.
- Start with simpler watchfaces. Add one complication at the time and observe how they affect battery life.
- Try to use **Dark** theme for AAPS watchfaces, and [**Matching divider**](#watchface-settings). On OLED devices it will limit the amount of pixels lit and limit burnout.
- Check what performs better on your watch: AAPS stock watchfaces or other watchfaces with AAPS Complications.
- Observe over a few days, with different activity profiles. Most watches activate the display on glancing, movement and other usage-related triggers.
- Check your global system settings that affect performance: notifications, backlight/active display timeout, when GPS is activated.
- Check [list of tested phones and watches](../CompatiblePhones/ListOfTestedPhones.md) and [ask community](../GettingHelp/WhereCanIGetHelp.md) for other users experiences and reported battery lifetime.
- **We cannot guarantee that data displayed on watchface or complication is up-to-date**. In the end, it is up to Wear OS to decide when to update a watchface or a complication. Even when the AAPS app requests update, the System may decide to postpone or ignore updates to conserve battery. When in doubt and low on battery on watch - always double-check with main AAPS app on phone.

(Watchfaces-troubleshooting-the-wear-app)=

## Dépannage de l'application wear :

- Sometimes it helps to re-sync the apps to the watch as it can be a bit slow to do so itself: Android Wear > Cog icon > Watch name > Resync apps.
- Enable ADB debugging in Developer Options (on watch), connect the watch via USB and start the Wear app once in Android Studio.
- If Complications does not update data - check first if AAPS watchfaces work at all.

## Garmin

There are a couple of watch faces for Garmin that integrate with xDrip or Nightscout on the [Garmin ConnectIQ store](https://apps.garmin.com/en-US/search?keyword=glucose\&device=\&deviceLimit=\&appType=\&sort=\&start=0\&count=30).

[AAPS Glucose Watch](https://apps.garmin.com/apps/3d163641-8b13-456e-84c3-470ecd781fb1) integrates directly with AAPS. It shows loop status data (insulin on board, temporary basal) in addition to glucose readings and sends heart rate readings to AAPS. It is available in the ConnectIQ store, the necessary AAPS plugin is only available from AAPS 3.2.

![Capture d'écran](../images/Garmin_WF.png) ![Capture d'écran](../images/Garmin_WF-annotated.png)

## Troubleshooting Sony smartwatch setup

Although it was discontinued a few years ago, if you are using a Sony Smartwatch SW 3 please see here for a troubleshooting guide: [Troubleshooting Sony Smartwatch SW 3](../UsefulLinks/SonySW3.md)

## Des cadrans supplémentaires AAPS personnalisés sont également disponibles

[Here](../UsefulLinks/AdditionalWatchfaces.md) you can download Zip-Files with custom watchfaces made by other users.

## Build your own watchface

If you want to build your own watchface, follow the [guide here](../UsefulLinks/CustomWatchfaceReference.md).

Quand vous avez personnalisé un cadran, vous pouvez partager votre propre cadran **AAPS** avec les autres utilisateurs, le fichier ZIP peut être déversé dans le dossier "ExchangeSiteCustomWatchfaces" via un Pull Request dans Github. Lors de la fusion du "Pull Request", l'équipe de documentation extraira le fichier image et le nom du cadran du fichier Zip, et ajoutera le lien de téléchargement à la liste ci-dessous.