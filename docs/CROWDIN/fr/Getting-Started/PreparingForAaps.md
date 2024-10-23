# Se préparer à démarrer avec AAPS

Bienvenue ! This documentation aims to guide users who are preparing to setup and start using the Android Artificial Pancreas System (**AAPS**).

## Trouver votre chemin dans la documentation

An **index** and explanation of the documentation structure can be found [here](../index.md), you can also reach it by clicking on the **AAPS** symbol at the top left of the documentation. Vous y trouverez une vue d'ensemble des fonctionnalités décrites dans chaque chapitre de la documentation. Vous pouvez également utiliser le menu à gauche de cette page pour naviguer dans la documentation. Finally, there is a handy search function, directly below the **AAPS** symbol.

We aim to make it easy to determine both the capabilities and limitations of **AAPS**. It can be disappointing to discover after investing time in reading the documentation that you might not have a compatible insulin pump or CGM, or that **AAPS** offers different functionality than hoped for.

Many experience-related details in the **AAPS** documentation make more sense when you are actually using **AAPS** in real-time. Just as it is difficult to learn a sport only by reading the rules, it takes a combination of learning the foundations of the rules for safely operating **AAPS** and then learning how best to apply those rules as you start to use **AAPS**.

(preparing-safety-first)=

## La sécurité avant tout
“Un grand pouvoir implique de grandes responsabilités... ”

### Sûreté technique
**AAPS** has an extensive set of safety features. These impose constraints which are gradually removed through staged completion of a series of [Objectives](../SettingUpAaps/CompletingTheObjectives.md) which involve testing specific parameters and answering multiple choice questions. **AAPS** features are unlocked as the Objectives are successfully completed. This process allows the user to migrate safely in stages from Open Loop to Closed Loop, while learning about the different features of **AAPS**.

The [Objectives](../SettingUpAaps/CompletingTheObjectives.md) have been designed to achieve the best possible introduction to **AAPS**, taking into consideration the typical errors and general trends **AAPS** developers have observed with new users. Mistakes can happen because the beginner is inexperienced and too eager to get started with **AAPS**, or has overlooked key points. The [Objectives](../SettingUpAaps/CompletingTheObjectives.md) aim to minimise these issues.

### Sûreté médicale
```{admonition} Avoid permanent and painful damage to your eyes and nerves
:class: danger
Caution is advised concerning rapid improvements in blood glucose control and lowering of HbA1c 
```

An important safety consideration is that a **rapid reduction in HbA1c and improved blood glucose control in those who have had elevated glucose levels for some time can cause permanent damage**. De nombreuses personnes atteintes de diabète n'ont pas connaissance de ça, et tous les professionnels de santé ne parlent pas de ce problème à leurs patients.

This damage can include **sight loss, and permanent neuropathy (pain)**. Il est possible d'éviter que ces atteintes ne se produisent en faisant baisser plus lentement les niveaux de glycémie moyens. If you currently have an elevated HbA1c and are moving to **AAPS** (or any other closed loop system), _please_ discuss this potential risk with your clinical team before starting, and agree a timescale with gradually decreasing safe glucose targets with them. You can easily set higher glucose targets in **AAPS** initially (currently, the highest target you can select is 10.6 mmol/L but you can also maintain a purposefully weak profile if needed), and then reduce the target as the months pass.

#### À quelle vitesse puis-je réduire mon HbA1c sans risquer des dommages permanents ?

One retrospective [study](https://pubmed.ncbi.nlm.nih.gov/1464975/) of 76 patients reported that the risk of progression of retinopathy increased by 1.6 times, 2.4 times and 3.8 times if the Hba1C dropped 1%, 2% or 3% respectively over a 6 month period. They suggested that the **"decrease in HbA1c value during any 6-month period should be limited to less than 2% in order to prevent the progression of retinopathy....Too rapid a decrease at the initiation of glycemic control could cause severe or transient exacerbation of the progression of retinopathy."**

N.B. If you use different HbA1c units (mmol/mol rather than %), click [here](https://www.diabetes.co.uk/hba1c-units-converter.html) for a HbA1c calculator tool.

In another retrospective [evaluation](https://academic.oup.com/brain/article/138/1/43/337923) of 954 patients, researchers noted that:

**"With a decrease in HbA1c of 2–3% points over 3 months there was a 20% absolute risk of developing treatment-induced neuropathy in diabetes, with a decrease in HbA1c of >4% points over 3 months the absolute risk of developing treatment-induced neuropathy in diabetes exceeded 80%."**

A [commentary](https://academic.oup.com/brain/article/138/1/2/340563) on this work agreed that to avoid complications **the goal should be to reduce A1c by <2% over 3 months.** You can read other reviews on the topic [here](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6587545/pdf/DOM-21-454.pdf) and [here](https://www.mdpi.com/1999-4923/15/7/1791).

It is generally recognised that _newly_ diagnosed type 1 diabetics (who often have very high HbA1c at diagnosis, before starting insulin therapy) appear to be able to rapidly reduce their HbA1c immediately after diagnosis without encountering these risks to the same extent, because they have not had elevated blood glucose levels for such a sustained period. Cependant, cela reste important d'en discuter avec votre équipe médicale.

### Aucun inhibiteur SGLT-2

```{admonition} NO SGLT-2 inhibitors
:class: danger
SGLT-2 inhibitors, also called gliflozins, inhibit reabsorption of glucose in the kidney. Gliflozins incalculably lower blood sugar levels, and so you MUST NOT take them while using a closed loop system like AAPS! There would be a significant risk of ketoacidosis and/or hypoglycemia! The combination of this medication with a system that lowers basal rates in order to increase BG is especially dangerous. 

In a nutshell:
- **Example 1: risk of Hypo**
>During lunch, you use **AAPS** to bolus based on consuming 45g of glucose. The problem is that unbeknownst to AAPS, the inhibitors cause the body to eliminate some of the carbs resulting in your body having too much insulin compared to the absorbed Carbs, resulting in hypoglycemia.

- **Example 2: risk of Ketoacidosis**
>The inhibitors eliminate some of the carbs in the background causing a reduction in your BG. **AAPS** will automatically instruct the pump to decrease insulin intake  including basal. Over time this can result  in your  BG remaining below target value to the point where the body does not have enough background insulin to absorb any carbs resulting in Ketoacidosis. Ordinarily, Ketoacidosis  develops in T1D patients because their pump fails which would trigger alerts on their phone and be noticeable due to a high BG value. However, the danger with Gliflozins  is that there would be no AAPS alerts as  the pump remains operational and the BG potentially remains within target.  

Common brand names of SGLT-2 inhibitors include: Invokana, Farxiga, Jardiance, Glyxambi, Synjardy, Steglatro, and Xigduo XR, others.
```


### Principes clés de la boucle avec AAPS

The key principles and concepts of looping must be understood before using **AAPS**. This is achieved by investing your personal time into reading the **AAPS** documentation, and completing the Objectives which aim to provide you with a solid platform for safe and effective use of **AAPS**. The volume of **AAPS** documentation may seem overwhelming at first but be patient and trust the process - with the proper approach, you'll get there!

La vitesse de progression dépendra de chacun, mais sachez qu'il faut généralement 6 à 9 semaines pour compléter tous les objectifs. Many people start to build, install and setup **AAPS** well in advance of starting to use it. To aid with this, the system has a "virtual pump" which can be used during completion of the early objectives, so that you can become familiar with **AAPS** without actually using it to deliver insulin. A detailed breakdown of the timeline is given below, be aware that by objective 8 of **AAPS** you are closed looping, the later objectives add in additional features like **SMS commands** and **automations** which are useful to some users, but not essential to the core function of **AAPS**.

Success with **AAPS** requires a proactive approach, a willingness to reflect on the BG data and flexibility to make the necessary adjustments to **AAPS** in order to improve your outcomes. Just as it is nearly impossible to learn to play a sport by reading about the rules alone, the same can be said of **AAPS**.

#### Plan for delays and minor issues in getting everything set up and running

In the preliminary stages of getting started with **AAPS**, you may experience difficulties getting all the components of the loop communicating effectively with each other (and potential followers), and when fine-tuning your settings. Some glitches cannot be resolved until **AAPS** is used in everyday life, but plenty of help is available on the Facebook group and Discord. Veillez à vous organiser et à choisir un moment approprié, comme une matinée calme en week-end (par ex. pas tard la nuit ou quand vous êtes fatigué, ou avant une réunion importante ou un voyage) pour travailler à la résolution des problèmes que vous pouvez rencontrer.

#### Compatibilité des technologies

**AAPS** is only compatible with certain types of insulin pumps, CGMs and phones, and some technology may not be available for use in various countries. In order to avoid any disappointment or frustrations, please read the [CGM](../Getting-Started/CompatiblesCgms.md), [pump](../Getting-Started/CompatiblePumps.md) and [phone](../Getting-Started/Phones.md) sections.

#### Temps pour compiler l'application et progression la boucle fermée

The time to build the **AAPS** app  depends on your level of expertise and technical ability. Typically for inexperienced users, it can take up to half a day or a full day (with help from the community) in order to build **AAPS**. The process will significantly speed up for newer **AAPS** versions, as you become more experienced.

Pour vous aider dans le processus de compilation, il y a des pages dédiées dans la documentation :

- List of questions and answers for frequent errors that are likely to occur in [FAQs (Section](../UsefulLinks/FAQ.md) K);

- “[How to install AAPS](../SettingUpAaps/BuildingAaps.md)? (Section D) which includes [Troubleshooting](../GettingHelp/GeneralTroubleshooting.md) Subsection.

How long it takes to get to closed looping depends on the individual, but an approximate timescale for getting to full looping with AAPS can be found ([here](#how-long-will-it-take-to-set-everything-up))


#### Keystore & configuration settings export file

A “keystore” (.jks file) is a password encrypted file unique to your own copy of **AAPS**. Votre téléphone Android l'utilise pour s'assurer que personne d'autre ne peut mettre à jour votre version personnelle sans le magasin de clés. In short, as part of the **AAPS** build, you should:

1.  Enregistrer le fichier de votre magasin de clés (fichier .jks utilisé pour signer votre application) dans un endroit sûr;

2.  Vous assurer de conserver le mot de passe de votre fichier de clés.


This will ensure that you can use that exact same keystore file each time an updated version of **AAPS** is created. On average, there will be 2 **AAPS** updates required each year.

In addition, **AAPS** provides the ability to [export all your configuration settings](../Maintenance/ExportImportSettings.md). Cela vous permet de récupérer votre système en toute sécurité tout en changeant de téléphone, de mettre à jour/réinstaller l'application avec un minimum d'interruption. 

#### Troubleshooting

N''hésitez pas à contacter la communauté AAPS s'il y a des points sur lesquels vous avez des hésitations - il n'y a pas de question bête ! Tous les utilisateurs, quel que soit leur niveau d'expérience, sont encouragés à poser leurs questions. Response times to questions are usually quick due to the number of **AAPS** users.

##### [ask on the AAPS Facebook group](https://www.facebook.com/groups/AndroidAPSUsers/)

##### [ask on the AAPS Discord channel](https://discord.gg/4fQUWHZ4Mw)





#### [Where to go for help](../Where-To-Go-For-Help/Background-reading.md)?

Cette section a pour but de fournir aux nouveaux utilisateurs des liens vers des ressources afin d'obtenir de l'aide, y compris l'accès au soutien de la communauté composé à la fois d'utilisateurs nouveaux et expérimentés qui peuvent clarifier les questions, et résoudre les pièges habituels qui peuvent subvenir avec AAPS.

#### [Section For Clinicians](../Resources/clinician-guide-to-AndroidAPS.md)

This is a [section specificially for clinicians](../Resources/clinician-guide-to-AndroidAPS.md) who want to know more about AAPS and open source artificial pancreas technology. There is also guidance on [how to talk to your clinical team](./Introduction.md#how-can-i-approach-discussing-aaps-with-my-clinical-team) in the Introduction.

## Que va-t-on compiler et installer?

This diagram provides an overview of the key components (both hardware and software) of the **AAPS** system:

![preparing_overview](../images/preparing_images/AAPS_preparing_overview_01.png)


In addition to the three basic hardware components (phone, pump, glucose sensor), we also need: 1) The **AAPS** app 2) A reporting server and 3) A continuous glucose monitor (CGM) app

### 1) An Android Phone Application: **AAPS**

**AAPS** is an app that runs on android smartphones & devices. You are going to build the **AAPS** app (an apk file) yourself, using a step-by-step guide, by downloading the **AAPS** source code from GitHub, installing the necessary programs (Android Studio, GitHub desktop) on your computer and building your own copy of **AAPS** app. You will then transfer the **AAPS** app across to your smartphone (by email, USB cable _etc._) and install it.

### 2) Un serveur de reporting : NightScout (Tidepool*)

In order to fully take advantage of **AAPS**, you need to setup a Nightscout server. Vous pouvez le faire vous-même (lien vers les instructions) ou, à défaut, payer un petit abonnement pour un service Nightscout tout prêt installé (lien vers T1 pal 10.be etc). Nightscout is used to collect data from **AAPS** over time and can generate detailed reports correlating CGM and insulin patterns. It is also possible for caregivers to use Nightscout to remotely communicate with the **AAPS** application, to oversee their child’s diabetic management. Dans les fonctionnalités de communication à distance, on trouve la surveillance en temps réel de la glycémie et de l'insuline active, l'administration à distance d'insuline (par SMS) et les annonces de repas. Tenter d'analyser vos performances dans le suivi du diabète en examinant les données de glycémie séparément des données de la pompe, c'est comme conduire une voiture où le conducteur est aveugle et le passager décrit la scène.  Tidepool est disponible comme alternative à Nightscout, pour les versions AAPS 3.2 et ultérieures.

### 3) Application pour le capteur MGC

Depending on your glucose sensor/CGM, you will need a compatible app for receiving glucose readings and sending them to **AAPS**. The different options are shown below and more information is given in the [compatible CGMs section](../Getting-Started/CompatiblesCgms.md):

![dexcom_options](../images/preparing_images/AAPS_connectivity_Dex_02.png) ![libre_options](../images/preparing_images/AAPSconnectivity_libre.png) ![eversense_options](../images/preparing_images/AAPS_connectivity_eversense.png)

### Maintenance of the **AAPS** system

Both **Nightscout** and **AAPS** must be updated approximately once a year, as improved versions are released. Dans certains cas, la mise à jour peut être repoussée, dans d'autres cas, elle est fortement recommandée ou considérée comme essentielle pour la sécurité. Ces mises à jour seront notifiées sur les groupes Facebook et les serveurs Discord. Les notes de version indiqueront clairement la marche à suivre. Il est probable que de nombreuses personnes se poseront des questions similaires aux vôtres au moment de la mise à jour, et vous trouverez le soutien nécessaire pour effectuer les mises à jour.

(preparing-how-long-will-it-take?)=
## Combien de temps pour tout mettre en place ?

As mentioned earlier, using **AAPS** is more of a “journey” that requires investment of your personal time. Il ne s'agit pas d'une installation à faire une seule fois. Current estimates for building **AAPS**, installing and configuring **AAPS** and **CGM** software and getting from open loop to hybrid closed looping with **AAPS** are about 4 to 6 months overall. It is therefore suggested that you prioritize building the **AAPS** app and working through the early objectives as soon as possible, even if you are still using a different insulin delivery system (you can use a virtual pump up to objective 5).

Certains des objectifs demandent d'attendre un certain nombre de jours avant de les valider, pour vous assurer que vous comprenez la nouvelle fonctionnalité. Il n'est pas possible de contourner ce temps d'attente, ces délais minimaux ont été mis en place pour votre propre sécurité.

Voici une estimation approximative du temps nécessaire :

| Tasks                                                                     |           Temps estimé            |
| ------------------------------------------------------------------------- |:---------------------------------:|
| Lecture initiale de la documentation                                      |             1-2 jours             |
| Installation/configuration du PC pour permettre la compilation            |            2-8 heures             |
| Mise en place du serveur de reporting                                     |              1 heure              |
| Installation d'une application MGC (xDrip+, BYODA, …)                     |              1 heure              |
| Configuration initiale MGC → xDrip+ → AAPS                                |              1 heure              |
| Configuration initiale AAPS → pompe                                       |              1 heure              |
| Configuration AAPS → Nightscout/Tidepool (reporting seulement)            |              1 heure              |
| Optional : Configuring NightScout ↔ **AAPS** & NSFollowers                |              1 heure              |
| Objectif 1 : Mise en place de la visualisation et du suivi                |              1 heure              |
| Objectif 2 : Apprendre à contrôler AAPS                                   |              2 heure              |
| Objectif 3 : Prouver ses connaissances                                    |         Jusqu'à 14 jours          |
| Objectif 4 : Démarrage de la boucle ouverte                               |          7 jours minimum          |
| Objectif 5 : Comprendre votre boucle ouverte                              |              7 jours              |
| Objectif 6 : Démarrage de la boucle fermée (Arrêt pour Glycémie Basse)    | 5 jours minimum, jusqu'à 14 jours |
| Objectif 7 : Réglage de la boucle fermée                                  | 1 jours minimum, jusqu'à 7 jours  |
| Objectif 8 : Ajustement de la basale et des ratios, activation d'Autosens | 7 jours minimum, jusqu'à 14 jours |
| Objectif 9 : Activation des Super Micro Bolus (SMB)                       |         28 jours minimum          |
| Objectif 10: Automatisation                                               |         28 jours minimum          |
| Objectif 11 : SI dynamique                                                |         28 jours minimum          |

Once you are fully operational on **AAPS**, you will still need to regularly fine tune your settings in order to improve your overall diabetic management.

## Requirements

### Considérations médicales

In addition to the medical warnings in the [safety section](#safety-first) there are also different parameters, depending on which insulin you are using in the pump.

#### Choix de l'insuline

**AAPS** calculations are based on insulin concentrations of 100U/ml (same as pump’s standard). Les types suivants de préréglages de profil d'insuline sont pris en charge :

- Insuline à Action Rapide Oref: Humalog/NovoRapid/NovoLog
- Ultra-Rapid ORef:  Fiasp
- Lyumjev

Pour les utilisateurs Expérimentés/Avancés uniquement :
- Profil d'insuline ajustable Oref: Vous permet de définir vous-même le pic d'activité de l'insuline


### Pré-requis techniques

Cette documentation a pour but de réduire autant que faire se peut l'expertise technique requise. You will need to use your computer to build the **AAPS** application in Android Studio (step-by-step instructions). Vous devrez également configurer un serveur sur Internet dans un environnement accessible, configurer plusieurs applications pour le téléphone Android et acquérir des connaissances sur la gestion du diabète. This can be  achieved by moving step-by-step, being patient, and help from the **AAPS** community. If you are already able to navigate the internet, manage your own Gmail emails, and keep your computer up-to-date, then it is a feasible task to build the **AAPS**. Il faut juste y aller tranquillement.

### Smartphones

#### AAPS et versions Android
The current version of **AAPS** (3.2) requires an Android smartphone with Google **Android 9.0 or above**. Si vous pensez à acheter un nouveau téléphone (à compter de juillet 2024), préférez la version Android 13. Users are strongly encouraged to keep their build of **AAPS** up to date for safety reasons, however for users unable to use a device with Android 9.0 or newer, earlier versions of  **AAPS** compatible for older Android versions like [Android 8](https://github.com/nightscout/AndroidAPS/releases/tag/2.8.2.1) and [Android 7](https://github.com/nightscout/AndroidAPS/releases/tag/2.6.2), remain available from previous releases (check the release notes for legacy versions).

#### Choix du modèle de smartphone
Vous choisirez un modèle précis en fonction de la/des fonction(s) que vous recherchez. There are two archived spreadsheets of compatible [smartphones](https://docs.google.com/spreadsheets/d/1zO-Vf3wv0jji5Gflk6pe48oi348ApF5RvMcI6NG5TnY/edit#gid=2097219952) and [smartphones and watches](https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit#gid=698881435). Ces tableaux ne sont plus mis à jour au vu du grand nombre de modèles possibles. Nous suggérons donc maintenant de faire une recherche dans les groupes de support (Facebook ou Discord) avec "phone", ou le modèle précis que vous envisagez d'acheter. Créez un nouveau post avec vos questions à ce sujet si vous avez encore besoin de davantage d'informations.

To make a donation of smartphone or smartwatch models that still need testing, please email [donations@androidaps.org](mailto:donations@androidaps.org).

- [List of tested phones](../CompatiblePhones/ListOfTestedPhones.md)
- [Jelly Settings](../CompatiblePhones/Jelly.md)
- [Huawei Settings](../CompatiblePhones/Huawei.md)

Les utilisateurs sont encouragés à faire les mises à jour de version Android sur leur téléphone, y compris avec les mises à jour de sécurité. However, if you are new with **AAPS** or are not a technical expert you might want to delay updating your phone until others have done so and confirmed it is safe to do so, on our various forums.

```{admonition} delaying Samsung phones updates
:class: warning
Samsung has an unfortunate track record of forcing updates of their phones which cause bluetooth connectivity issues. To disable these forced updates you need to switch the phone to "developper mode" by:
 go to settings and about then software information, then tap build number u til it confirms you have unlocked developer mode. Got back to main settings menu and you should see a new developer options menu item. Open developer options and scroll to find auto system update and turn it off
```

```{admonition} Google Play Protect potential Issue
:class: warning
There have been several reports of **AAPS** being shut down arbitrarily by Google Play Protect every morning. If this happens you will have to go to the google play options and disable “Google Play Protect”. Not all  phone models or all Android versions are affected..
```

