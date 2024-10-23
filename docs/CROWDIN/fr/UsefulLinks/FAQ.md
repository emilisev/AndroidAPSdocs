# FAQ for loopers

How to add questions to the FAQ: Follow the these [instructions](../SupportingAaps/HowToEditTheDocs.md)

## General

### Can I just download the AAPS installation file?

Non. There is no downloadable apk file for AAPS. You have to [build](../SettingUpAaps/BuildingAaps.md) it yourself. En voici la raison :

AAPS is used to control your pump and give insulin. Selon la réglementation actuelle, en Europe, tous les systèmes de classe IIa ou IIb, sont des dispositifs médicaux qui nécessitent une approbation réglementaire (un marquage CE) qui nécessitent diverses études et approbations. La distribution d'un dispositif non homologué est illégal. Des réglementations similaires existent dans d'autres parties du monde.

Ce règlement n'est pas limité qu'aux ventes (dans le sens d'obtenir de l'argent pour quelque chose), mais s'applique à n'importe quel moyen de distribution (même en accès gratuit). Construire vous même un appareil médical est la seule façon d'utiliser l'application en respectant ces règlements.

C'est pourquoi les apk ne sont pas disponibles.

(FAQ-how-to-begin)=
### How to begin?
First of all, you have to **get loopable hardware components**:

* A [supported insulin pump](../Getting-Started/CompatiblePumps.md),
* an [Android smartphone](../CompatiblePhones/ListOfTestedPhones.md) (Apple iOS is not supported by AAPS - you can check [iOS Loop](https://loopkit.github.io/loopdocs/)) and
* a [continuous glucose monitoring system](../Getting-Started/CompatiblesCgms.md).

Secondly, you have to **setup your hardware**. See [example setup with step-by-step tutorial](Sample-Setup.md).

Thirdly, you have to **setup your software components**: AAPS and CGM/FGM source.

Fourthly, you have to learn and **understand the OpenAPS reference design to check your treatment factors**. Le principe fondateur de boucle fermée est que votre débit de basal et vos ratios Glucides/Insuline (G/I) et Sensibilité à l'Insuline (SI) sont bien déterminés.  Toutes les recommandations supposent que vos besoins en basal sont satisfaits et que les pics ou les creux que vous voyez sont le résultat d'autres facteurs qui nécessitent par conséquent des ajustements (exercices, stress, etc.).  The adjustments the closed loop can make for safety have been limited (see maximum allowed temporary basal rate in [OpenAPS Reference Design](https://openaps.org/reference-design/)), which means that you don't want to waste the allowed dosing on correcting a wrong underlying basal. Si par exemple vous êtes souvent bas à l'approche d'un repas, il est probable que vos débits de basal nécessitent un ajustement.  You can use [autotune](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html#phase-c-running-autotune-for-suggested-adjustments-without-an-openaps-rig) to consider a large pool of data to suggest whether and how basals and/or ISF need to be adjusted, and also whether carb ratio needs to be changed.  Or you can test and set your basal the [old fashioned way](https://integrateddiabetes.com/basal-testing/).

### What practicalities of looping do I have?

#### Password protection
Si vous ne voulez pas que vos préférences soient facilement modifiées, vous pouvez protéger le menu Préférences par un mot de passe en sélectionnant dans les préférences "Mot de passe pour paramètres" et en tapant le mot de passe choisi. La prochaine fois que vous allez dans le menu Préférences, il demandera ce mot de passe avant d'aller plus loin. Si plus tard vous souhaitez supprimer l'option de mot de passe, allez dans "Mot de passe pour paramètres" et supprimez le texte.

#### Android Wear Smartwatches
If you plan to use the android wear app to bolus or change settings then you need to ensure notifications from AAPS are not blocked. La confirmation de l'action se fait par notification.

(FAQ-disconnect-pump)=
#### Disconnect pump
If you take your pump off for showering, bathing, swimming, sports or other activities you must let AAPS know that no insulin is delivered to keep IOB correct.

The pump can be disconnected using the Loop Status icon on the [AAPS Home Screen](../DailyLifeWithAaps/AapsScreens.md#loop-status).

#### Recommendations not only based on one single CGM reading
Pour plus de sécurité, les recommandations faites ne sont pas basées sur une unique lecture MGC, mais sur le delta moyen.  Therefore, if you miss some readings it may take a while after getting data back before AAPS kicks in looping again.

#### Further readings
Il y a plusieurs blogs avec de bons conseils pour vous aider à comprendre les aspects pratiques de la boucle :
  * [Fine-tuning Settings](https://seemycgm.com/2017/10/29/fine-tuning-settings/) See my CGM
  * [Why DIA matters](https://seemycgm.com/2017/08/09/why-dia-matters/) See my CGM
  * [Limiting meal spikes](https://diyps.org/2016/07/11/picture-this-how-to-do-eating-soon-mode/) #DIYPS
  * [Hormones and autosens](https://seemycgm.com/2017/06/06/hormones-2/) See my CGM

### What emergency equipment is recommended to take with me?
Vous devez avoir le même équipement d'urgence avec vous, comme tous les autres diabétique de T1 avec une pompe à insuline.  When looping with AAPS it is strongly recommended to have the following additional equipment with or near to you:

* Pack de batteries et câbles pour charger votre smartphone, votre montre et, le cas échéant, votre lecteur BT ou votre périphérique de connection
* Piles de la Pompe
* Current [apk](../SettingUpAaps/BuildingAaps.md) and [preferences files](../Maintenance/ExportImportSettings.md) for AAPS and any other apps you use (e.g. xDrip+, BYO Dexcom) both locally and in the cloud (Dropbox, Google Drive).

### How can I safely and securely attach the CGM/FGM?
Vous pouvez le coller.  Il existe plusieurs « overpatchs » pré-troués adaptés aux systèmes MGC disponibles (recherchez sur Google, eBay ou Amazon). Certains boucleur utilisent également des pansements hydrofilm standard ou des bandes adhésives moins chères.

Vous pouvez le fixer.  Vous pouvez également acheter un brassard pour maintenir le MGC/MGF en place (recherche Google, eBay ou Amazon).

## AAPS settings

La liste suivante a pour but de vous aider à optimiser les paramètres. Il peut être préférable de commencer par le haut et de travailler vers le bas. Essayez de valider un seul paramètre avant d'en changer un autre. Travaillez avec de petites étapes plutôt que de faire de grands changements à la fois. You can use [Autotune](https://autotuneweb.azurewebsites.net/) to guide your thinking, although it should not be followed blindly: it may not work well for you or in all circumstances. Notez que les paramètres interagissent les uns avec les autres - vous pouvez avoir des paramètres "erronés" qui fonctionnent bien ensemble dans certaines circonstances (par exemple si une basal trop élevé se produit en même temps qu'une Gly trop élevée) mais pas dans d'autres. Cela signifie que vous devez tenir compte de tous les paramètres et vérifier qu'ils fonctionnent ensemble dans une variété de circonstances.

### Duration of insulin activity (DIA)
#### Description & testing
La durée que met l'insuline pour descendre à zéro.

C'est très souvent paramétré trop court. La plupart des gens voudront au moins 5 heures, voire 6 ou 7 heures.

(FAQ-impact)=
#### Impact
Une DAI trop courte peut conduire à des hypoglycémies. Et vice-versa.

Si la DAI est trop courte, AAPS pensera que votre bolus précédent est entièrement consommé trop tôt, et si la glycémie est encore élevée, il vous injectera plus d'insuline. (En pratique, il n’attend pas aussi longtemps, mais il prédit ce qui va se passer et continue d’ajouter de l’insuline). Cela crée essentiellement un «empilement d'insuline» dont AAPS n'est pas au courant.

L'exemple d'une DAI trop courte est une hyperglycémie suivie d'une correction excessive de AAPS et d'une hypoglycémie derrière.

### Basal rate schedule (U/h)
#### Description & testing
La quantité d'insuline nécessaire, pendant une durée d'une heure, pour maintenir glycémie à un niveau stable.

Testez vos débits de basal en suspendant la boucle, en jeûnant, en attendant 5 heures après la nourriture, et en voyant comment la glycémie change. Répétez plusieurs fois.

Si la glycémie baisse, le débit de basal est trop élevé. Et vice-versa.
#### Impact
Un débit de basal trop élevé peut conduire à des hypoglycémies. Et vice-versa.

'Principes de base' de AAPS par rapport au débit de basal par défaut. Si le débit de basal est trop élevé, un « zéro-temp » comptabilisera une IA négative plus importante qu’il ne le devrait. Cela conduira AAPS à faire des corrections plus importante qu'il ne le devrait pour amener l'IA à zéro.

Ainsi, un débit de base trop élevé créera des hypoglycémies, à la fois avec le débit par défaut, mais également pendant quelques heures, lorsque AAPS fera les corrections pour atteindre la cible.

Inversement, un débit de basal trop faible peut conduire à des hyperglycémie, et une impossibilité à ramener les niveaux vers la cible.

### Insulin sensitivity factor (ISF) (mmol/l/U or mg/dl/U)
#### Description & testing
La diminution de glycémie prévue suite à l'administration d'1U d'insuline (en anglais ISF).

En supposant que le débit de base est correct, vous pouvez la tester en suspendant la boucle, en vérifiant que l'IA est nulle, et en prenant quelques carrés de sucre pour atteindre un niveau de glycémie "élevé" et stable.

Then take an estimated amount of insulin (as per current 1/ISF) to get to your target BG.

Soyez prudent, car elle est bien souvent trop faible. Trop basse signifie qu'1 U va faire baisser la glycémie plus vite que prévu.
#### Impact
**Lower ISF** (i.e. 40 instead of 50) meaning insulin drops your BG less per unit. This leads to a more aggressive / stronger correction from the loop with **more insulin**. Si elle est trop basse, cela peut conduire à des hypoglycémies.

**Higher ISF** (i.e. 45 instead of 35) meaning insulin drops your BG more per unit. This leads to a less aggressive / weaker correction from the loop with **less insulin**. Si elle est trop élevée, cela peut conduire à des hyperglycémies.

**Exemple :**
* Glycémie est à 190 mg/dl (10,5 mmol) et la cible est à 100 mg/dl (5,6 mmol).
* Donc, vous voulez une correction de 90 mg/dl (= 190 - 100).
* ISF = 30 -> 90 / 30 = 3 units of insulin
* ISF = 45 -> 90 / 45 = 2 units of insulin

Une SI trop faible (pas rare) peut entraîner des "sur-corrections", car AAPS pense qu'il a besoin de plus d'insuline que nécessaire pour corriger une glycémie élevée. Cela peut conduire à des glycémies en "montagnes russes" (surtout à jeun). Dans ce cas, vous devez augmenter votre SI. Cela conduira AAPS à donner de plus petites doses de correction, et évitera une sur-correction d'une hyperglycémie suivie d'une hypoglycémie.

Inversement, une SI trop élevée peut entraîner une sous-correction, ce qui signifie que votre glycémie reste au-dessus de la cible – c'est particulièrement perceptible après une nuit.

### Insulin to carb ratio (IC) (g/U)
#### Description & testing
La quantité de glucides en grammes pour chaque unité d'insuline.

En anglais les acronymes utilisés sont I:C, IC ou également Ratio Carbone (CR).

En supposant que le débit de basal est correct, vous pouvez tester en vérifiant que l'IA est nulle et que vous êtes à l'objectif glycémique, en mangeant une quantité exacte de glucides connue, et en prenant la valeur estimée d'insuline basée sur le rapport actuel de G/I. Le mieux est de manger de la nourriture de votre mangez habituellement à ce moment de la journée et de compter ses glucides précisément.

> **NOTE:** 
> 
> Dans certains pays européens, des unités de pain ont été utilisées pour déterminer la quantité d'insuline nécessaire à l'alimentation. A l'origine 1 unité de pain est équivalent à 12g de glucides, mais plus tard certains ont changés la référence à 10g de glucides.
> 
> Dans ce modèle, la quantité de glucides est la référence et la quantité d'insuline variable. ("Quelle quantité d'insuline est nécessaire pour couvrir une unité de pain?")
> 
> Lors de l'utilisation du ratio G/I, la quantité d'insuline est la référence et la quantité de glucides est variable. ("Combien de glucides peuvent être couverts par une unité d'insuline?")
> 
> Exemple :
> 
> Bread unit factor (BU = 12g carbs): 2,4 U/BU -> You need 2,4 units of insulin when you eat one bread unit.
> 
> Corresponding IC: 12g / 2,4 U = 5,0 g/U -> 5,0g carbs can be covered with one unit of insulin.
> 
> BU factor 2,4 U / 12g   ===>   IC = 12g / 2,4 U = 5,0 g/U
> 
> Conversion tables are available online i.e. [here](https://www.mylife-diabetescare.com/files/media/03_Documents/11_Software/FAS/SOF_FAS_App_KI-Verha%CC%88ltnis_MSTR-DE-AT-CH.pdf).

#### Impact
**Lower IC** = less food per unit, i.e. you are getting more insulin for a fixed amount of carbs. Peut aussi être appelé "plus agressif".

**Higher IC** = more food per unit, i.e. you are getting less insulin for a fixed amount of carbs. Peut aussi être appelé "moins agressif".

Si, après que le repas ait été digéré et que l'IA est revenu à zéro, votre glycémie reste plus élevée qu'avant avoir mangé, il y a de fortes chances que le ratio G/I soit trop élevé. Inversement, si votre glycémie est inférieure à celle précédent le repas, le ratio G/I est trop faible.

## APS algorithm
### Why does it show "dia:3" in the "OPENAPS AMA"-tab even though I have a different DIA in my profile?

![AMA 3h](../images/Screenshot_AMA3h.png)

Dans l'AMA, DAI ne signifie pas "Durée d'Action de l'Insuline". C'est un paramètre qui était connecté au DAI. Maintenant, cela signifie "à quel moment la correction devrait être terminée". Cela n'a rien à voir avec le calcul de l'IA. Dans OpenAPS SMB, ce paramètre n'est plus nécessaire.

### Profile

#### Why using min. 5h DIA (insulin end time) instead of 2-3h?
Well explained in [this article](https://www.diabettech.com/insulin/why-we-are-regularly-wrong-in-the-duration-of-insulin-action-dia-times-we-use-and-why-it-matters/). Don't forget to `ACTIVATE PROFILE` after changing your DIA.

#### What causes the loop to frequently lower my BG to hypoglycemic values without COB?
Tout d'abord, vérifiez votre débit de basal et faites un test de débits de basal sans glucides. S'il est correct, c'est généralement provoqué par une SI trop faible. Une SI trop basse ressemble généralement à ceci :

![ISF too low](../images/isf.jpg)

#### What causes high postprandial peaks in closed loop?
Tout d'abord, vérifiez votre débit de basal et faites un test de débits de basal sans glucides. If it is correct and your BG is falling to your target after carbs are fully absorbed, try to set an 'eating soon' temp target in AAPS some time before the meal or think about an appropriate prebolus time with your endocrinologist. Si votre glycémie est trop élevée après le repas et encore trop élevée une fois les glucides absorbés, pensez à diminuer votre G/I avec votre diabétologue.  Si votre glycémie est trop élevée avec des GA et trop faible après l'absorption complète des glucides, pensez à augmenter votre ratio G/I et faite un prébolus avec un décalage horaire vu avec votre diabétologue.

## Other settings

### Nightscout settings

#### AAPSClient says 'not allowed' and does not upload data. What can I do?
In AAPSClient check 'Connection settings'. Peut-être n'êtes-vous pas connecté à un Wi-Fi autorisé ou vous avez activé "Uniquement pendant la charge" et votre câble de charge n'est pas branché.

### CGM settings

#### Why does AAPS say 'BG source doesn't support advanced filtering'?
If you do use another CGM/FGM than Dexcom G5 or G6 in xDrip native mode, you'll get this alert in AAPS OpenAPS-tab. See [Smoothing blood glucose data](../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md) for more details.

### Pump

#### Where to place the pump?
Il y a de nombreuses possibilités de placer la pompe. Peu importe si vous êtes en boucle fermée ou pas.

#### Batteries
La boucle peut réduire la durée de vie de la pile de la pompe plus rapidement que la normale car le système interagit bien plus qu'un utilisateur manuel.  Il est préférable de changer la pile à 25% car la communication devient alors difficile.  Vous pouvez définir des alarmes d'avertissement pour la pile de la pompe à l'aide de la variable PUMP_WARN_BATT_P dans votre site Nightscout.  Les astuces pour augmenter la durée de vie de la pile sont les suivantes :
* réduire la durée d'affichage de l'écran LCD (dans le menu des paramètres de la pompe)
* réduire la durée du rétro-éclairage (dans le menu des paramètres de la pompe)
* sélectionnez les paramètres de notification à un bip plutôt que de vibrer (dans le menu des paramètres de la pompe)
* only press the buttons on the pump to reload, use AAPS to view all history, battery level and reservoir volume.
* AAPS app may often be closed to save energy or free RAM on some phones. When AAPS is reinitialized at each startup it establishes a Bluetooth connection to the pump, and re-reads the current basal rate and bolus history. Cela consomme de la batterie. To see if this is happening, go to Preferences > NSClient and enable 'Log app start to NS'. Nightscout will receive an event at every restart of AAPS, which makes it easy to track the issue.  To reduce this happening, whitelist AAPS app in the phone battery settings to stop the app power monitor closing it down.

   Par exemple, pour l'inscire sur la liste blanche avec un téléphone Samsung fonctionnant sous Android Pie :
   * Go to Settings -> Device Care -> Battery
   * Scroll until you find AAPS and select it
   * Désélectionnez "Mettre l'application en veille"
   * ALSO go to Settings -> Apps -> (Three circle symbol in the top-right of the screen) select "special access" -> Optimize battery usage
   * Scroll to AAPS and make sure it is de-selected.

* nettoyez les bornes de la pile avec un tampon d'alcool pour s'assurer qu'aucune cire ou draisse de fabrication ne reste.
* for [Dana R/RS pumps](../CompatiblePumps/DanaRS-Insulin-Pump.md) the startup procedure draws a high current across the battery to purposefully break the passivation film (prevents loss of energy whilst in storage) but it doesn't always work to break it 100%.  Supprimez et réinsérez la batterie 2 à 3 fois jusqu'à ce qu'elle affiche 100 % à l'écran, ou utilisez la clé de batterie pour faire un court circuit bref de la batterie avant de l'insérer en appliquant aux deux bornes une fraction de seconde.
* see also more tips for [particular types of battery](../CompatiblePumps/Accu-Chek-Combo-Tips-for-Basic-usage.md#battery-type-and-causes-of-short-battery-life)

#### Changing reservoirs and cannulas
The change of cartridge cannot be done via AAPS but must be carried out as before directly via the pump.
* Long press on "Open Loop"/"Closed Loop" on the Home tab of AAPS and select 'Suspend Loop for 1h'
* Now nnect the pump and change the reservoir as per pump instructions.
* Ainsi le remplissage de la tubulure et de la canule peuvent être faites directement sur la pompe. In this case use [PRIME/FILL button](../DailyLifeWithAaps/AapsScreens.md#action-tab) in the actions tab just to record the change.
* Une fois reconnecté à la pompe, continuez la boucle en appuyant sur "Suspendu (X m)".

Le changement d'une canule n'utilise cependant pas la fonction "Remplir tubulure" / "Remplir canule" de la pompe, mais remplit l'ensemble de perfusion et/ou la canule à l'aide d'un bolus qui n'apparaît pas dans l'historique des bolus. Cela signifie qu'il n'interrompt pas un débit de basal temporaire en cours d'exécution.  On the Actions (Act) tab, use the [PRIME/FILL button](../DailyLifeWithAaps/AapsScreens.md#action-tab) to set the amount of insulin needed to fill the infusion set and start the priming. Si la quantité n'est pas suffisante, répétez le remplissage.  You can set default amount buttons in the Preferences > Other > Fill/Prime standard insulin amounts.  Consultez les notices de vos canules et tubulures pour savoir combien d'unités doivent être injectées en fonction de la longueur de l'aiguille et de la longueur de la tubulure.

### Wallpaper

You can find the AAPS wallpaper for your phone on the [phones page](../CompatiblePhones/ListOfTestedPhones.md#phone-background).

### Daily usage

#### Hygiene

##### What to do when taking a shower or bath?
Vous pouvez retirer la pompe pour prendre une douche ou un bain. Pour ce court laps de temps, vous pouvez ne pas en avoir besoin, mais vous devez dire à AAPS que vous avez été déconnecté pour que les calculs IOB soient corrects. See [description above](#disconnect-pump).

#### Work
Selon votre de travail, vous pouvez peut-être utiliser différents paramètres de traitement pendant les jours travaillés. As a looper you should consider a [profile switch](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md) for your typical working day.  Par exemple, vous pouvez passer à un profil supérieur à 100 % si vous avez un emploi moins fatigant (par ex. assis derrière un bureau), ou moins de 100 % si vous êtes actif et debout toute la journée.  You could also consider a high or low temporary target or a [time shift of your profile](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md#time-shift-of-the-circadian-percentage-profile) when working much earlier or later than regular, of if you work different shifts. Vous pouvez aussi créer un second profil (par exemple "maison" et "jour de travail") et faire un changement de profil quotidien vers le profil dont vous avez besoin.

### Leisure activities

(FAQ-sports)=
#### Sports
Vous devez retravailler vos vieilles habitudes sportives à partir de l'époque "d'avant-boucle". Si vous consommez simplement des glucides de sportifs comme avant, la boucle fermée les reconnaîtra et les corrigera en conséquence.

Donc, vous auriez plus de glucides à bord, mais en même temps, la boucle les neutraliserait en libérerant de l'insuline.

Lors de la boucle, vous devriez essayer ces étapes :
* Make a [profile switch](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md) < 100%.
* Set an [activity temp target](../DailyLifeWithAaps/TempTargets.md#activity-temp-target) above your standard target.
* If you are using SMB make sure ["Enable SMB with high temp targets"](../DailyLifeWithAaps/KeyAapsFeatures.md#enable-smb-with-high-temp-targets) and ["Enable SMB always"](../DailyLifeWithAaps/KeyAapsFeatures.md#enable-smb-always) are disabled.

Le pré-traitement et le post-traitement de ces paramètres sont importants. Faite les changements suffisament tôt avant le sport et tenez compte de l'effet sur les muscles après.

If you do sports regularly at the same time (i.e. sports class in your gym) you can consider using [automation](../DailyLifeWithAaps/Automations.md) for profile switch and TT. L'automatisation basée sur l'emplacement peut également être une idée, mais rend l'anticipation du traitement plus difficile.

Le pourcentage du changement de profil, la valeur de votre cible temporaire d'activité et le meilleur moment pour effectuer ces changements sont propres à chacun. Commencez prudemment si vous recherchez la valeur qui vous convient (commencez par un pourcentage faible et une CT plus élevée).

#### Sex
You can remove the pump to be 'free', but you should tell AAPS so that the IOB calculations are correct.  See [description above](#disconnect-pump).

#### Drinking alcohol
La consommation d'alcool est dangereux en mode boucle fermée car l'algorithme ne peut pas prévoir correctement l'impact de l'alcool sur la glycémie. You have to check out your own method for treating this using the following functions in AAPS:

* désactivation de la boucle fermée et traitement du diabète manuellement ou
* réglage d'une cible de temp élevées et désactivation des RNS pour éviter l'augmentation de l'IA par la boucle en raison d'un repas non signalé
* faire un changement de profil pour nettement moins de 100%

Lorsque vous buvez de l'alcool, vous devez toujours avoir un œil sur votre MGC pour éviter manuellement une hypoglycémie en mangeant des glucides.

#### Sleeping

##### How can I loop during the night without mobile and WIFI radiation?
De nombreux utilisateurs mettent le téléphone en mode avion la nuit. If you want the loop to support you when you are sleeping, proceed as follows (this will only work with a local BG-source such as xDrip+ or ['Build your own Dexcom App'](../CompatibleCgms/DexcomG6.md#if-using-g6-with-build-your-own-dexcom-app), it will NOT work if you get the BG-readings via Nightscout):

1. Activez le mode avion de votre mobile.
2. Attendez que le mode avion soit actif.
3. Activez le Bluetooth.

Maintenant vous ne recevez pas d'appels téléphonique, et vous n'êtes pas connecté à Internet. Mais la boucle est toujours en cours.

Certaines personnes ont découvert des problèmes de diffusion locale (AAPS ne recevant pas les valeurs Gly de xDrip+) lorsque le téléphone est en mode avion. Go to Settings > Inter-app settings > Identify receiver and enter `info.nightscout.androidaps`.

![xDrip+ Basic Inter-app Settings Identify receiver](../images/xDrip_InterApp_NS.png)


#### Travelling

##### How to deal with time zone changes?
Avec les pompes Dana R et Dana R coréenne, vous n'avez rien à faire. For other pumps see [time zone travelling](../DailyLifeWithAaps/TimezoneTraveling-DaylightSavingTime.md) page for more details.

### Medical topics

#### Hospitalization
If you want to share some information about AAPS and DIY looping with your clinicians, you can print out the [guide to AAPS for clinicians](../Resources/clinician-guide-to-AndroidAPS.md).

#### Medical appointment with your endocrinologist

##### Reporting
You can either show your Nightscout reports (https://YOUR-NS-SITE.com/report) or check [Nightscout Reporter](https://nightscout-reporter.zreptil.de/).


## Frequent questions on Discord and their answers...

### My problem is not listed here.

[Information to get help.](../GettingHelp/WhereCanIGetHelp.md)

### My problem is not listed here but I found the solution

[Information to get help.](../GettingHelp/WhereCanIGetHelp.md)

**Remind us to add your solution to this list!**

### AAPS stops everyday around the same time.

Arrêter la protection Google Play. Vérifiez que les applications "nettoyant" (par ex. CCleaner, etc.) et désinstallez-les. AAPS / Menu 3 points / À propos / Suivre le lien "Garder l'application en cours d'exécution en arrière-plan" pour arrêter toutes les optimisations de batterie.

### How to organize my backups ?

Exporter les paramètres très régulièrement : après chaque changement de pod, après modification de votre profil, lorsque vous avez terminé et validé un objectif, si vous changez votre pompe… Même si rien ne change, exportez une fois par mois. Conserver plusieurs anciens fichiers d'exportation.

Copy on an internet drive (Dropbox, Google etc) : all the apks you used to install apps on your phone (AAPS, xDrip, BYODA, Patched LibreLink…) as well as the exported setting files from all your apps.

### I have problems, errors building the app.

Veuillez

* check [Troubleshooting Android Studio](../GettingHelp/TroubleshootingAndroidStudio) for typical errors and
* the tipps for with a [step by step walktrough](https://docs.google.com/document/d/1oc7aG0qrIMvK57unMqPEOoLt-J8UT1mxTKdTAxm8-po).

### I'm stuck on an objective and need help.

Effectuez une capure d'écran avec la question et les réponses. Postez les sur la chaine AAPS sur Discord. N'oubliez pas de préciser quelles options vous choisissez (ou pas) et pourquoi. Vous obtiendrez des conseils et de l'aide, mais vous devrez trouver les réponses vous-même.

### How to reset the password in AAPS v2.8.x ?

Open the hamburger menu, start the Configuration wizard and enter new password when asked. You can quit the wizard after the password phase.

### How to reset the password in AAPS v3.x

You find the documentation [here](../Maintenance/Update3_0.md#reset-master-password).

### My link/pump/pod is unresponsive (RL/OL/EmaLink…)

With some phones, there are Bluetooth disconnects from the Links (RL/OL/EmaL...).

Some also have non responsive Links (AAPS says that they are connected but the Links can't reach or command the pump.)

La façon la plus simple de faire travailler toutes ces pièces ensemble est de : 1/ Supprimer le lien depuis AAPS 2/ Éteindre le lien 3/ Sélectionner le menu 3 points AAPS pour quitter AAPS 4/ Faire un appui long sur l'icône AAPS, menu Android, infos sur l'application AAPS, Forcer l'arrêt AAPS, puis Supprimer la mémoire cache (Ne pas supprimer la mémoire principale !) 4bis/ Rarement certains téléphones peuvent avoir besoin d'un redémarrage ici. You can try without reboot. 5/ Allumer le smartphone 6/ Démarrer AAPS 7/ Sélectionner l'onglet Pod, menu à 3 points, recherche et connexion

### Build error: file name too long

While trying to build I get an error stating the file name is too long. Solutions possibles : Déplacez vos sources vers un répertoire plus proche du répertoire racine de votre disque (par exemple "c:\src\AAPS-EROS").

Depuis Android Studio : Assurez-vous que la synchronisation et l'indexage "Gradle" sont terminés après avoir ouvert le projet et effectué un Pull depuis GitHub. Execute a Build->Clean Project before doing a Rebuild Project. Execute File->Invalidate Caches and Restart Android Studio.

### Alert: Running dev version. Closed loop is disabled

AAPS is not running in "developer mode". AAPS shows the following message: "running dev version. La boucle fermée est désactivée".

Make sure AAPS is running in "developer mode": Place a file named "engineering_mode" at the location "AAPS/extra". Any file will do as long as it is properly named. Make sure to restart AAPS for it to find the file and go into "developer mode".

Hint: Make a copy of an existing logfile and rename it to "engineering_mode" (note: no file extension!).

### Where can I find settings files?

Settings files will be stored on your phone's internal storage in the directory "/AAPS/preferences". WARNING: Make sure not to lose your password as without it you will not be able to import an encrypted settings file!

### How to configure battery savings?

Properly configuring Power Management is important to prevent your Phone's OS to suspend AAPS and related app's and services when your phone is not being used. As a result AAPS can not do its work and/or Bluetooth connections for sensor and Rileylink (RL) may be shut down causing "pump disconnected" alerts and communication errors. On the phone, go to settings->Apps and disable battery savings for: AAPS xDrip or BYODA/Dexcom app The Bluetooth system app (you may need to select for viewing system apps first) Alternatively, fully disable all battery savings on the phone. As a result your battery may drain faster but it is a good way to find out if battery savings is causing your problem. The way battery savings is implemented greatly depends on the phone's brand, model and/or OS version. Because of this it is almost impossible to give instructions to properly set battery savings for your setup. Experiment on what settings work best for you. For additional information, see also Don't kill my app

### Pump unreachable alerts several times a day or at night.

Your phone may be suspending AAPS services or even Bluetooth causing it to loose connection to RL (see battery savings) Consider configuring unreachable alerts to 120 minutes by going to the top right-hand side three-dot menu, selecting Preferences->Local Alerts->Pump unreachable threshold [min].

### Where can I delete treatments in AAPS v3 ?

3 dots menu, select treatements, then 3 dots menu again and you have different options available.

### Configuring and Using the AAPSClient remote app

AAPS can be monitored and controlled remotely via the AAPSClient app and optionally via the associated Wear app running on Android Wear watches. Note that the AAPSClient (remote) app is distinct from the NSClient configuration in AAPS, and the AAPSClient (remote) Wear app is distinct from the AAPS Wear app--for clarity the remote apps will be referred to as 'AAPSClient remote' and 'AAPS remote Wear' apps.

To enable AAPSClient remote functionality you must: 1) Install the AAPSClient remote app (the version should match the version of AAPS being used) 2) Run the AAPSClient remote app and proceed through the configuration wizard to grant required permissions and configure access to your Nightscout site. 3) At this point you may want to disable some of the Alarm options, and/or advanced settings which log the start of the AAPSClient remote app to your Nightscout site. Once this is done, AAPSClient remote will download Profile data from your Nightscout site, the 'Overview' tab will display CGM data and some AAPS data, but but may not display graph data, and will indicate that a profile isn't yet set. 4) To activate the profile:
- Enable remote profile synchronization in AAPS > NSClient > Options
- Activate the profile in NSClient remote > Profile After doing so, the profile will be set, and AAPSClient remote should display all data from AAPS. Hint: If the graph is still missing, try changing the graph settings to trigger an update. 5) To enable remote control by the AAPSClient, selectively enable the aspects of AAPS (Profile changes, Temp Targets, Carbs, etc.) that you would like to be able to control remotely via AAPS > NSClient > Options . Once these changes are made, you'll be able to remotely control AAPS via either Nightscout or AAPSClient remote.

If you'd like to monitor/control AAPS via the AAPSClient remote Wear App, you'll need both AAPSClient remote and the associated Wear app to be installed. To compile the AAPSClient remote Wear app, follow the standard instructions for installing/configuring the AAPS wear app, except when compiling it, choose the AAPSClient variant.

### I have a red triangle / AAPS won't enable closed loop / Loops stays in LGS / I have a yellow triangle

The red and yellow triangles are a security feature in AAPS v3.

Red triangle means that you have duplicate BGs and AAPS can't calculate precisely the deltas. You can't close the loop. You need to delete one BG of each duplicated value in order to clear the red triangle. Go to BYODA or xDRIP tab, long press one line you want to delete, check one of each lines that are doubled (or via 3 dots menu and Delete, depending on your AAPS version). You may need to reset the AAPS databases if there are too many double BGs. In this case, you'll also loose stats, IOB, COB, selected profile.

Possible origin of the problem: xDrip and/or NS backfilling BGs.

The yellow triangle means unstable delay between each BG reading. You don't receive BGs every 5 min regularly or missing BGs. It is often a Libre problem. It also happens when you change G6 transmitter. Si le triangle jaune est lié au changement de transmetteur G6, il disparaîtra après plusieurs heures (environ 24h). Dans le cas du Freestyle Libre, le triangle jaune restera. La boucle peut être fermée et fonctionnera correctement.


### Can I move an active DASH Pod to other hardware?
This is possible. Note that as moving is "unsupported" and "untested" there is some risk involved. Best to try the procedure when your Pod is about to expire so when things go wrong not much is lost.

Critical is that pump "state" (which includes it's MAC address) in AAPS and DASH match on reconnecting

### Procedure I follow in this:

1) Suspend the DASH pump. This makes sure there are no running or queued commands active when DASH loses connection 2) Put the phone into airplane mode to disable BT (as well as WiFi and Mobile data). This way it is guaranteed AAPS and DASH can not communicate. 3) Export settings (which includes the DASH state) 4) Copy the settings file just exported from the phone (as it is in airplane mode and we do not want to change that, easiest way is using USB cable) 5) Copy the settings file to the alternate phone. 6) Import settings on the alternate phones AAPS. 7) Check the DASH tab to verify it is seeing the Pod. 8) Un-suspend the Pod. 9) Check the DASH tab and confirm it is communicating with the Pod (use the refresh button)

Congratulations: you did it!

_Wait!_ You still have the main phone thinking it can reconnect to the same DASH:

1) On the main phone choose "deactivate". This is safe because the phone has no way of communicating with DASH to actually deactivated the Pod (it is still in airplane mode) 2) Deactivation will result in a communications error - this is expected. 3) Just hit "retry" a couple of times until AAPS offers the option to "Discard" the Pod.

When Discarded, verify AAPS is reporting "No Active Pod". You can now safely disable airplane mode again.

### How do I import settings from earlier versions of AAPS into AAPS v3 ?

You can only import settings (in AAPS v3) that were exported using AAPS v2.8x or v3.x. If you were using a version of AAPS older than v2.8x or you need to use setting exports older than v2.8x, then you need to install AAPS v2.8 first. Import the older settings of v2.x in v2.8. After checking that all is OK, you can export settings from v2.8. Install AAPS v3 and import v2.8 settings in v3.

If you use the same key to build v2.8 and v3, you won't even have to import settings. You can install v3 over v2.8.

There were some new objectives added. You'll need to validate them. 

