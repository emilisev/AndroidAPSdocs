# Préférences

- **Open preferences** by clicking the three-dot menu on the top right side of the home screen.

  ![Open preferences](../images/Pref2020_Open2.png)

- Vous pouvez accéder directement aux préférences d'un certain onglet (par ex. onglet pompe) en sélectionnant cet onglet et en cliquant sur Préférences du plugin.

  ![Open plugin preferences](../images/Pref2020_OpenPlugin2.png)

- **Sub-menus** can be opened by clicking the triangle below the sub-menu title.

  ![Open submenu](../images/Pref2020_Submenu2.png)

- With the **filter** on top of the preferences screen you can quickly access certain preferences. Il suffit de taper une partie du texte que vous cherchez.

  ![Preferences filter](../images/Pref2021_Filter.png)

```{contents}
:backlinks: entry
:depth: 2
```

(Preferences-general)=
## General

![Preferences > General](../images/Pref2020_General.png)

**Units**

- Définissez les unités mmol/l ou mg/dl selon vos préférences.

**Language**

- Nouvelle option pour utiliser la langue par défaut du téléphone (recommandé).

- Si vous voulez AAPS dans une autre langue que la langue du téléphone, vous pouvez choisir parmi une large variété.

- Si vous utilisez des langues différentes, vous pouvez parfois voir un mélange de langues. Cela est dû à un problème Android, le remplacement de la langue par défaut d'Android parfois ne fonctionne pas.


**Patient name**

- Peut être utilisé si vous devez différencier plusieurs configurations (par ex. deux enfants DT1 de votre famille).

(Preferences-protection)=
### Protection

(Preferences-master-password)=

![Preferences > General - Protection](../images/Pref2020_General2.png)

#### Mot de passe principal

- Necessary to be able to [export settings](../Maintenance/ExportImportSettings.md) as they are encrypted from version 2.7. **Biometric protection may not work on OnePlus phones. This is a known issue of OnePlus on some phones.**

- Ouvrez les préférences (menu trois points en haut à droite de l'écran d'accueil)

- Cliquez sur le triangle sous " Général "

- Cliquez sur " Mot de passe principal "

- Entrez le mot de passe, confirmez le et cliquez sur OK.

  ![Set master password](../images/MasterPW.png)

#### Protection des paramètres

- Protect your settings with a password or phone's biometric authentication (i.e. [child is using AAPS](../RemoteFeatures/RemoteMonitoring.md)).

- Custom password should be used if you want to use master password just for securing [exported settings](../Maintenance/ExportImportSettings.md).

- If you are using a custom password click on line "Settings password" to set password as described [above](#master-password).

  ![Protection](../images/Pref2020_Protection.png)

#### Protection de l'Application

- Si l'application est protégée, vous devez entrer un mot de passe ou utiliser l'authentification biométrique du téléphone pour ouvrir AAPS.
- L'application s'arrêtera immédiatement si un mot de passe erroné est entré, mais s'exécute toujours en arrière-plan si elle a déjà été ouverte avec succès.

#### Protection des bolus

- Bolus protection might be useful if AAPS is used by a small child and you [bolus via SMS](../RemoteFeatures/SMSCommands.md).

- Dans l'exemple ci-dessous, vous voyez l'invite de protection biométrique. Si l'authentification biométrique ne fonctionne pas, cliquez dans la zone au-dessus de l'invite blanche et entrez le mot de passe principal.

  ![Prompt biometric protection](../images/Pref2020_PW.png)

(Preferences-skin)=
#### Skin

- Vous pouvez choisir parmi quatre thèmes :

  ![Select skin](../images/Pref2021_SkinWExample.png)

- Le thème 'Basse résolution' a des étiquettes plus courte et "âge/niveau" ont été enlevé dans la zone Careportal de l'onglet Action pour avoir plus d'espace disponible sur un écran de très basse résolution.

- La différence entre les autres thèmes dépend de l'orientation du téléphone.

##### Orientation portrait

- **Original Skin** and **Buttons are always displayed on bottom of screen** are identical
- **Large Display** has an increased size of all graphs compared to other skins

##### Orientation paysage

- Using **Original Skin** and **Large Display**, you have to scroll down to see buttons at the bottom of the screen

- **Large Display** has an increased size of all graphs compared to other skins

  ![Skins depending on phone's display orientation](../images/Screenshots_Skins.png)

(Preferences-overview)=
## Aperçu

- Dans la section Aperçu, vous pouvez définir les préférences de l'écran d'accueil.

  ![Preferences > Overview](../images/Pref2020_OverviewII.png)

### Garder l'écran allumé

- Utile lors d'une présentation.
- Cela consomme beaucoup d'énergie, il est donc prudent de brancher votre téléphone sur un chargeur.

(Preferences-buttons)=
### Boutons

- Définissez quels boutons sont visibles en bas de votre écran d'accueil.

  ![Preferences > Buttons](../images/Pref2020_OV_Buttons.png)

- Avec les paramètres incrément, vous pouvez définir les quantités pour les trois boutons des boîtes de dialogue glucides et insuline pour une entrée facile.

  ![Preferences > Buttons > Insulin](../images/Pref2020_OV_Buttons2.png)

  ![Preferences > Buttons > Carbs](../images/Pref2020_OV_Buttons3.png)

(Preferences-quick-wizard)=
### Assistant Rapide

- Si vous avez une collation ou un repas fréquent, vous pouvez utiliser le bouton Assistant Rapide pour entrer facilement la quantité de glucides et définir les règles de calcul.

- Dans le paramétrage, vous définissez au cours de quelle période le bouton sera visible sur votre écran d'accueil - ne définissez qu'un bouton par période.

  ![Preferences > Quick Wizard Button Setup](../images/Pref2020_OV_QuickWizard.png)

- Si vous cliquez sur le bouton Assistant Rapide, AAPS calculera et proposera un bolus pour ces glucides en fonction de vos valeurs actuelles (glycémie ou insuline active si configurées).

- La proposition doit être confirmée avant l'injection de l'insuline.

  ![Preferences > Quick Wizard Button](../images/Pref2020_OV_QuickWizard2.png)

(Preferences-default-temp-targets)=
### Cibles Temporaires par défaut

- [Temp targets (TT)](../DailyLifeWithAaps/TempTargets.md) allow you to define change your blood glucose target for a certain time period.

- Avec la configuration de CT par défaut, vous pouvez facilement changer vos cibles d'activité, de repas imminent, etc.

  ![Preferences > Default temp targets](../images/Pref2020_OV_DefaultTT.png)

- Faites un appui long sur votre cible dans le coin supérieur droit de l'écran d'accueil ou utilisez les raccourcis dans le bouton orange « Glucides » en bas.

  ![Preferences > Use default temp targets](../images/Pref2020_OV_DefaultTT2.png)

###

### Insuline par défaut pour Amorcer/Remplir

- If you want to fill tube or prime cannula through AAPS you can do this through [actions tab](../DailyLifeWithAaps/AapsScreens.md#action-tab).
- Les valeurs prédéfinies peuvent être configurées dans cette boite de dialogue.

(Preferences-range-for-visualization)=
### Fourchette de visualisation

- Définissez quelle partie du graphique sur l'écran d'accueil doit être votre plage cible et sera remplie avec fond vert.

  ![Preferences > Range for visualization](../images/Pref2020_OV_Range2.png)

### Shorten tab titles

- Permet de voir plus de onglets à l'écran.

- Par exemple, l'onglet "OpenAPS AMA" devient "OAPS", "Objectifs" devient "OBJ" etc.

  ![Preferences > Tabs](../images/Pref2020_OV_Tabs.png)

### Afficher les notes dans les boîtes de dialogue

- Vous permet d'ajouter des textes courts de notes à vos traitements (assistant bolus, glucides, insuline...)

  ![Preferences > Notes in treatment dialogs](../images/Pref2020_OV_Notes.png)

(Preferences-status-lights)=
### Status lights

- Les voyants d'état donnent une alerte visuelle pour

  - Age du capteur
  - Sensor battery level for certain smart readers (see [screenshots page](../DailyLifeWithAaps/AapsScreens.md#sensor-level-battery) for details).
  - Âge de l'insuline (jours d'utilisation du réservoir)
  - Niveau du réservoir (unités)
  - Âge de la canule
  - Âge Pile Pompe
  - Âge Pile Pompe (%)

- Si le seuil d'alerte est dépassé, les valeurs seront affichées en jaune.

- Si le seuil critique est dépassé, les valeurs seront affichées en rouge.

- Dans les versions antérieures à AAPS 2.7 le paramètrage des seuils pour les voyants d'état être effectué dans Nightscout.

  ![Preferences > Status Lights](../images/Pref2020_OV_StatusLights2.png)

(Preferences-advanced-settings-overview)=
### Paramètres avancés (Aperçu)

![Preferences > Advanced Settings](../images/Pref2021_OV_Adv.png)

(Preferences-superbolus)=
#### Superbolus

- Option to enable superbolus in bolus wizard.
- [Superbolus](https://www.diabetesnet.com/diabetes-technology/blue-skying/super-bolus/) is a concept to "borrow" some insulin from basal rate in the next two hours to prevent spikes.

## Traitements de sécurité

### Type de patient

- Les limites de sécurité sont établies en fonction de l'âge sélectionné dans ce paramètre.
- Si vous commencez à atteindre ces limites restrictives (comme le Maximum Bolus), il est temps de changer d’un cran.
- C’est une mauvaise idée de selectionner un âge supérieur a l'âge réel car cela peut conduire à un surdosage lorsque l'on entre une valeur incorrecte dans la boîte de dialogue de l’insuline (en oubliant le point décimal ou la virgule par exemple).
- If you want to know the actual numbers for these hard-coded safety limits, scroll to the algorithm feature you are using on [this page](../DailyLifeWithAaps/KeyAapsFeatures.md).

### Maximum Bolus autorisé \[U\]

- Défini la quantité maximale d’insuline que AAPS est autorisé à administrer en une fois lors d'un bolus.
- Ce paramètre existe comme une limite de sécurité pour empêcher l'injection d’un bolus trop important dû à une saisie accidentelle ou une erreur de l’utilisateur.
- Il est recommandé de définir cette valeur à un montant raisonnable qui correspond approximativement à la quantité maximale d’insuline de bolus que vous êtes susceptible d’avoir besoin pour un repas ou pour une dose de correction.
- Cette restriction s’applique également aux résultats de l'assistant bolus.

### Maximum de Glucides autorisé \[g\]

- Défini la quantité maximale de glucides que l'assistant bolus de AAPS est autorisée à utiliser.
- Ce paramètre existe comme une limite de sécurité pour empêcher l'injection d’un bolus trop important dû à une saisie accidentelle ou une erreur de l’utilisateur.
- Il est recommandé de définir cette valeur à un montant raisonnable qui correspond approximativement à la quantité maximale de glucides que vous êtes susceptible d’avoir dans d'un repas.

## Loop

(Preferences-aps-mode)=
### Mode APS

- Basculer entre les boucles ouvertes et fermées ainsi que le mode arrêt glycémie basses (AGB)
- **Open looping** means TBR suggestions are made based on your data and appear as a notification. Après confirmation manuelle, la commande d'injection de l'insuline sera transférée à la pompe. Ce n'est que si vous utilisez la pompe virtuelle que vous devez la saisir manuellement.
- **Closed looping** means TBR suggestions are automatically sent to your pump without confirmation or input from you.
- **Low glucose suspend** is similar to closed looping, but overrides the maxIOB setting to zero. Cela signifie que si la glycémie diminue, le système peut réduire le débit basal pour vous, mais si la glycémie augmente, il n'augmentera le débit basal que si l'IA est négative (liée à un Arrêt Glycémie Basse précédent).

(Preferences-minimal-request-change)=
### Changement minimum \[%\]

- Lorsque vous utilisez le mode boucle ouverte, vous recevrez des notifications chaque fois que le programme AAPS vous recommande d'ajuster le débit de basal.
- Pour réduire le nombre de notifications, vous pouvez utiliser une plage cible de glycémie plus étendue ou augmenter le pourcentage de changement minimal.
- Ce paramètre défini le changement relatif minimum qui déclenchera une notification.

(Preferences-advanced-meal-assist-ama-or-super-micro-bolus-smb)=
## Assistance Améliorée Repas (AAR ou AMA) ou Super Micro Bolus (SMB)

Depending on your settings in [config builder](../SettingUpAaps/ConfigBuilder.md) you can choose between two algorithms:

- [Advanced meal assist (OpenAPS AMA)](../DailyLifeWithAaps/KeyAapsFeatures.md#advanced-meal-assist-ama) - state of the algorithm in 2017
- [Super Micro Bolus (OpenAPS SMB)](../DailyLifeWithAaps/KeyAapsFeatures.md#super-micro-bolus-smb) - most recent algorithm recommended for beginners

### Paramètres OpenAPS AMA

- Permet au système de reagir plus rapidement après un bolus de repas SI vous entrez les Glucides de manière fiable.
- More details about the settings and Autosens can be found in the [OpenAPS docs](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autosens.html).

(Preferences-max-u-h-a-temp-basal-can-be-set-to)=
#### Débit max en U/h pour une Temp Basal

- Existe comme une limite de sécurité pour empêcher AAPS d'etre capable d'administrer un dosage de Basal dangereusement élevé.
- La valeur est definie en Unités d'insuline par heure (U/h).
- Il est conseillé de definir cette valuer de facon raisonnable et sensée. A good recommendation is to take the **highest basal rate** in your profile and **multiply it by 4**.
- Par exemple, si le dosage basal le plus élevé de votre profil est de 0,5 U/h, vous pourriez le multiplier par 4 pour obtenir la valeur de 2 U/h.
- See also [detailed feature description](../DailyLifeWithAaps/KeyAapsFeatures.md#max-uh-a-temp-basal-can-be-set-to-openaps-max-basal).

#### L'IA basal maximum que OpenAPS peut délivrer \[U\]

- Une quantité d'insuline basale supplémentaire (en unités) a pu s'accumuler dans votre corps, en plus de votre profil basal normal.
- Une fois cette valeur atteinte, AAPS cessera de délivrer de l'insuline basale supplémentaire jusqu'à ce que votre Insuline basale Active (IA) aie diminuée et soit de nouveau dans cette plage.
- This value **does not consider bolus IOB**, only basal.
- Cette valeur est calculée et surveillée indépendamment de votre débit de basal normal. Ce n'est que l'insuline basale additionnelle en plus du débit normal qui est pris en compte.

When you begin looping, **it is advised to set Max Basal IOB to 0** for a period of time, while you are getting used to the system. Cela empêche AAPS de donner de l'insuline basale supplémentaire. Pendant ce temps, AAPS sera toujours en mesure de limiter ou de désactiver votre insuline basale pour prévenir l'hypoglycémie. C'est une étape importante pour :

- Avoir un certain temps pour s'habituer en toute sécurité au système AAPS et surveiller son fonctionnement.
- Profiter de l'occasion pour parfaire votre profil basal et votre Sensibilité à l'Insulin (SI).
- Voir comment AAPS limite votre insuline basale pour prévenir l'hypoglycémie.

Lorsque vous vous sentez à l'aise, vous pouvez autoriser le système à commencer à vous donner de l'insuline basale supplémentaire, en augmentant la valeur de l'IA basal Max. The recommended guideline for this is to take the **highest basal rate** in your profile and **multiply it by 3**. Par exemple, si le dosage basal le plus élevé de votre profil est de 0,5 U/h, vous pourriez le multiplier par 3 pour obtenir la valeur de 1,5 U/h.

- Vous pouvez commencer prudemment avec cette valeur et l'augmenter lentement avec le temps.
- Ce ne sont que des lignes directrices; chacun a un corps différent. Vous trouverez peut-être que vous avez besoin plus ou moins que ce qui est recommandé ici, mais commencez toujours prudemment et ajustez lentement.

**Note: As a safety feature, Max Basal IOB is hard-limited to 7u.**

#### Autosens

- [Autosens](../DailyLifeWithAaps/KeyAapsFeatures.md#autosens) looks at blood glucose deviations (positive/negative/neutral).
- Il essaiera de comprendre à quel point vous êtes sensible/résistant en fonction de ces écarts et ajustera le débit basal et la SI en fonction de ces écarts.
- Si vous sélectionnez "Autosens ajuste aussi les cibles" l'algorithme modifiera également votre cible de glycémie.

#### Paramètres avancés (OpenAPS AMA)

- Normalement, vous n'avez pas à modifier les paramètres dans cette boîte de dialogue !
- If you want to change them anyway make sure to read about details in [OpenAPS docs](https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/preferences-and-safety-settings.html#) and to understand what you are doing.

(Preferences-openaps-smb-settings)=
### Paramètres OpenAPS SMB

- In contrast to AMA, [SMB](../DailyLifeWithAaps/KeyAapsFeatures.md#super-micro-bolus-smb) does not use temporary basal rates to control glucose levels, but mainly small super micro boluses.

- You must have started [objective 9](../SettingUpAaps/CompletingTheObjectives.md#objective-9-enabling-additional-oref1-features-for-daytime-use-such-as-super-micro-bolus-smb) to use SMB.

- The first three settings are explained [above](#max-uh-a-temp-basal-can-be-set-to).

- Details on the different enable options are described in [OpenAPS feature section](../DailyLifeWithAaps/KeyAapsFeatures.md#enable-smb).

- *How frequently SMBs will be given in min* is a restriction for SMB to be delivered only every 4 min by default. Cette valeur empêche le système d'émettre trop souvent des SMB (par exemple dans le cas où une cible temporaire a été définie). Vous ne devriez pas modifier ce paramètre sauf si vous en connaissez exactement les conséquences.

- If 'Sensitivity raises target' or 'Resistance lowers target' is enabled [Autosens](../DailyLifeWithAaps/KeyAapsFeatures.md#autosens) will modify your glucose target according to your blood glucose deviations.

- Si la cible est modifiée, elle sera affichée avec un fond vert sur votre écran d'accueil.

  ![Target modified by autosens](../images/Home2020_DynamicTargetAdjustment.png)

(Preferences-carb-required-notification)=
#### Notification glucides requis

- Cette fonctionnalité n'est disponible que si l'algorithme SMB est sélectionné.

- Il sera suggéré de manger des glucides supplémentaires quand l'algorithme détecte que des glucides sont requis.

- Dans ce cas, vous recevrez une notification qui peut être reportée pendant 5, 15 ou 30 minutes.

- De plus, les glucides requis seront affichés dans la section GA sur votre écran d'accueil.

- Un seuil peut être défini - Glucides minimum requis pour suggestion.

- Les notifications Glucides requis peuvent être envoyées sur Nightscout si vous le souhaitez, dans ce cas une annonce sera affichée et diffusée.

  ![Display carbs required on home screen](../images/Pref2020_CarbsRequired.png)

#### Paramètres avancés (OpenAPS SMB)

- Normalement, vous n'avez pas à modifier les paramètres dans cette boîte de dialogue !
- If you want to change them anyway make sure to read about details in [OpenAPS docs](https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/preferences-and-safety-settings.html#) and to understand what you are doing.

## Paramètres d’absorption

![Paramètres d’absorption](../images/Pref2020_Absorption.png)

### min_5m_carbimpact

- L'algorithme utilise l'IGly (impact glycémique) pour déterminer quand les glucides sont absorbés.

- La valeur n'est utilisée que pendant les lacunes dans les lectures MGC ou lorsque l'activité physique "consomme" l'augmentation de la glycémie qui autrement aurai permis la décomposition des GA par AAPS.

- Parfois, lorsque l'absorption de glucides ne peut pas être déterminée de façon dynamique en fonction des glycémies, AAPS intègre une décomposition par défaut à vos glucides. De base, c'est une sécurité intégrée.

- To put it simply: The algorithm "knows" how your BGs *should* behave when affected by the current dose of insulin etc.

- Chaque fois qu'il y a un écart positif par rapport au comportement attendu, certains glucides sont absorbés/décomposés. Gros changement = beaucoup de glucides, etc.

- Le min_5m_carbimpact définit l'impact par défaut de l'absorption des glucides par 5 minutes. For more details see [OpenAPS docs](https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/preferences-and-safety-settings.html?highlight=carbimpact#min-5m-carbimpact).

- La valeur standard pour AMA est de 5, pour SMB c'est 8.

- Le graphique GA sur l'écran d'accueil indique quand min_5m_impact est utilisé en plaçant un cercle orange en haut.

  ![COB graph](../images/Pref2020_min_5m_carbimpact.png)

### Durée max d’absorption d'un repas

- Si vous mangez souvent des repas riches en matières grasses ou en protéines, vous devrez augmenter votre temps d'absorption des repas.

### Paramètres avancés - Ratio autosens

- Define min. and max. [autosens](../DailyLifeWithAaps/KeyAapsFeatures.md#autosens) ratio.
- Normalement les valeurs standards (max. 1,2 et min. 0,7) ne devrait pas être modifiées.

## Paramètres de la pompe

The options here will vary depending on which pump driver you have selected in [Config Builder](../SettingUpAaps/ConfigBuilder.md#pump).  Appairez et réglez votre pompe selon les instructions relatives à la pompe :

- [DanaR Insulin Pump](../CompatiblePumps/DanaR-Insulin-Pump.md)
- [DanaRS Insulin Pump](../CompatiblePumps/DanaRS-Insulin-Pump.md)
- [Accu Chek Combo Pump](../CompatiblePumps/Accu-Chek-Combo-Pump.md)
- [Accu Chek Insight Pump](../CompatiblePumps/Accu-Chek-Insight-Pump.md)
- [Medtronic Pump](../CompatiblePumps/MedtronicPump.md)

If using AAPS to open loop then make sure you have selected Virtual Pump in config builder.

(Preferences-nsclient)=
## NSClient

![NSClient](../images/Pref2020_NSClient.png)

Original communication protocol, can be used with older Nightscout versions.

- Set your *Nightscout URL* (i.e. <https://yoursitename.yourplaform.dom>).
  - **Make sure that the URL is WITHOUT /api/v1/ at the end.**
- The *[API secret](https://nightscout.github.io/nightscout/setup_variables/#api-secret-nightscout-password)* (a 12 character password recorded in your Nightscout variables).
- This enables data to be read and written between both the Nightscout website and AAPS.
- Vérifiez deux fois les fautes de frappe ici si vous êtes coincé dans l'objectif 1.

## NSClientV3

![NSClientV3](../images/Pref2024_NSClientV3.png)

[New protocol introduced with AAPS 3.2.](../Maintenance/ReleaseNotes.md#important-comments-on-using-v3-versus-v1-api-for-nightscout-with-aaps) Safer and more efficient.

```{admonition} V3 data uploaders
:class: warning

When using NSClientV3, all uploaders must be using the API V3. Since most are not compatible yet, this means **you must let AAPS upload all data** (BG, treatments, ...) to Nightscout and disable all other uploaders if they're not V3 compliant.
```

- Set your *Nightscout URL* (i.e. <https://yoursitename.yourplaform.dom>).
  - **Make sure that the URL is WITHOUT /api/v1/ at the end.**
- In Nightscout, create an *[Admin token](https://nightscout.github.io/nightscout/security/#create-a-token)* (requires [Nightscout 15](https://nightscout.github.io/update/update/) to use the V3 API) and enter it in **NS access token** (not your API Secret!).
- This enables data to be read and written between both the Nightscout website and AAPS.
- Vérifiez deux fois les fautes de frappe ici si vous êtes coincé dans l'objectif 1.
- Leave Connect to websockets enabled (recommended).

### Synchronization

Synchronization choices will depend on the way you will want to use AAPS.

You can select which data you want to [upload and download to or from Nightscout](../SettingUpAaps/Nightscout.md#aaps-settings).

### Options d'alarme

![Options d'alarme](../images/Pref2024_NSClient_Alarms.png)

- Alarm options allows you to select which Nightscout alarms to use through the app. AAPS will alarm when a Nightscout alarms trigger.
  - For the alarms to sound you need to set the Urgent High, High, Low and Urgent Low alarm values in your [Nightscout variables](https://nightscout.github.io/nightscout/setup_variables/#alarms).
  - They will only work whilst you have a connection to Nightscout and are intended for parent/caregivers.
  - If you have the CGM source on your phone (i.e. xDrip+ or BYODA) then use those alarms instead of Nightscout Alarms.
- Create notifications from Nightscout [announcements](https://nightscout.github.io/nightscout/discover/#announcement) will echo Nightscout announcements in the AAPS notifications bar.
- You can change stale data and urgent stale data alarms threshold when no data is received from Nightscout after a certain time.

### Paramètres de connexion

![NSClient connection settings](../images/ConfBuild_ConnectionSettings.png)

- Connection settings define when Nightscout connection will be enabled.
- Restreignez le téléchargement de Nightscout au Wi-Fi seulement ou même à certains SSID Wi-Fi.
- Si vous souhaitez utiliser uniquement un réseau WiFi spécifique, vous pouvez entrer son SSID.
- Plusieurs SSID peuvent être séparés par un point-virgule.
- Pour supprimer tous les SSID, entrez un espace dans la zone.

(Preferences-advanced-settings-nsclient)=
### Paramètres avancés (NSClient)

![NS Client advanced settings](../images/Pref2024_NSClientAdv.png)

Options in advanced settings are self-explanatory.

## Communicateur SMS

- Options will only be displayed if SMS communicator is selected in [Config Builder](../SettingUpAaps/ConfigBuilder.md#sms-communicator).
- Ce paramètre permet de contrôler à distance de l'application en envoyant des instructions au téléphone du patient que l'application appliquera comme Suspendre la boucle ou un bolus.
- Further information is described in [SMS Commands](../RemoteFeatures/SMSCommands.md).
- Une sécurité supplémentaire est obtenue grâce à l'utilisation d'une application authentificateur et d'un code PIN supplémentaire à la fin du jeton.

## Automatisation

Select which location service shall be used:

- Utiliser la localisation passive : AAPS ne prend la localisation que si d'autres applications la demandent
- Utiliser la localisation par le réseau : Localisation de votre Wifi
- Utiliser la localisition GPS (Attention ! Peut entrainer une consommation excessive de la batterie !)

## Alertes locales

![Alertes locales](../images/Pref2020_LocalAlerts.png)

- Les paramètres doivent être explicites.

## Choix de données

![Choix de données](../images/Pref2020_DataChoice.png)

- Vous pouvez aider davantage au développement d'AAPS en envoyant des rapports de plantage aux développeurs.

## Paramètres de maintenance

![Paramètres de maintenance](../images/Pref2020_Maintenance.png)

- Standard recipient of logs is <logs@aaps.app>.

## Open Humans

- Vous pouvez aider la communauté en faisant don de vos données à des projets de recherche ! Details are described on the [Open Humans page](../SupportingAaps/OpenHumans.md).

- Dans les préférences, vous pouvez définir quand les données doivent être téléchargées

  - uniquement si connecté au WiFi
  - uniquement si en charge
