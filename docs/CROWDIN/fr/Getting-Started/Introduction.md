# Introduction aux APS et à AAPS

## Qu'est ce qu'un "Système de Pancréas Artificiel” (APS)?

Un pancréas humain fait beaucoup de choses en plus de réguler la glycémie. However, the term **“Artificial Pancreas System” (APS)** usually refers to a system which works to automatically keep blood sugar levels within healthy limits.

The most basic way to do this is by detecting **glucose levels**, using these values to do **calculations**, and then delivering the (predicted) right amount of **insulin** to the body. Il répète le calcul régulièrement (quelques minutes), 24h/24, 7j/7. It uses **alarms** and **alerts** to inform the user if intervention or attention is needed. This system is typically made up of a **glucose sensor**, an **insulin pump** and an **app** on a phone.

Vous pouvez en savoir plus sur les différents systèmes de pancréas artificiels actuellement disponibles et en cours de développement dans cet article de synthèse de 2022 :

![Frontiers](../images/FRONTIERS_Logo_Grey_RGB.png) [Future Directions in Closed-Loop Technology](https://www.frontiersin.org/articles/10.3389/fendo.2022.919942/full#:~:text=Fully%20closed%2Dloop%20systems%2C%20unlike,user%20input%20for%20mealtime%20boluses).

Dans un avenir proche, certains systèmes dits de "double hormone" auront également la possibilité d'injecter du glucagon en plus de l'insuline, dans le but de prévenir les hypoglycémies sévères et de permettre un contrôle encore plus rigoureux de la glycémie.

An artificial pancreas can be thought of as an [“autopilot for your diabetes”](https://www.artificialpancreasbook.com/). What does that mean?

Dans un avion, un pilote automatique ne fait pas tout le travail du pilote humain, ainsi le pilote ne peut pas dormir pendant la totalité du vol. Le pilote automatique facilite le travail du pilote. Il soulage le pilote du fardeau de la surveillance permanente de l’avion, lui permettant de se concentrer de temps à autre sur une surveillance de plus haut niveau. Le pilote automatique reçoit des signaux de divers capteurs. Un ordinateur les évalue en même temps que les spécifications du pilote, puis il effectue les ajustements nécessaires, en informant le pilote de tout motif de préoccupation. Le pilote n'a plus à se soucier de prendre constamment des décisions.

![image](../images/autopilot.png)

## Que signifie "boucle fermée hybride" ?

La meilleure solution pour le diabète de type 1 serait un « traitement fonctionnel » (probablement un implant de cellules pancréatiques protégées du système immunitaire). En attendant son arrivée, un pancréas artificiel « boucle fermée complète » serait probablement le meilleur choix. Il s'agit d'un système technologique qui n'a besoin d'aucune entrée utilisateur (comme les bolus d'insuline pour les repas, ou l'annonce d'une activité physique), avec une bonne régulation des taux de glycémie. Pour le moment, il n'existe pas de systèmes largement disponibles qui soient en boucle fermée « complète », ces systèmes ont tous besoin de quelques informations entrées par l'utilisateur. Les systèmes actuellement disponibles sont appelés boucles fermées « hybrides », car ils utilisent une combinaison de technologie automatisée et d’informations entrées par l'utilisateur.

## Comment et pourquoi la boucle a-t-elle commencé ?

Le développement de technologies commerciales pour les personnes atteintes de diabète de type 1 (DT1) est très lent. En 2013, la communauté TD1 a fondé le mouvement #WeAreNotWaiting (#nous n'attendronspas). Ses membres ont mis au point eux-mêmes des systèmes utilisant des technologies déjà approuvées (pompes à insuline et capteurs de glycémie) pour améliorer le contrôle du taux de glycémie, la sécurité et la qualité de vie. Ces systèmes sont connus sous le nom de systèmes DIY (do-it-yourself) car ils ne sont pas officiellement approuvés par les organismes de santé (FDA, NHS, CE, FR, etc). There are four main DIY systems available: [OpenAPS](https://openaps.org/what-is-openaps/), **AAPS**, [Loop](https://loopkit.github.io/loopdocs/#what-is-loop) and [iAPS](https://github.com/Artificial-Pancreas/iAPS?fbclid=IwAR2fA9Y9YqYzpKSrtEsotfXl5b67UclDkKgyrv52tQLzYbOoBeNGRmjlJJI).

La lecture du livre de Dana Lewis « Automated Insuline Delivery » (Injection automatisée d'insuline) est un excellent moyen de comprendre les fondements de la boucle DIY. You can access it [here](https://www.artificialpancreasbook.com/) for free (or buy a hardcopy of the book). If you want to understand more about [OpenAPS](https://openaps.org/what-is-openaps/), which **AAPS** has developed from, the [OpenAPS website](https://openaps.org/what-is-openaps/) is a great resource.

Several commercial hybrid closed loop systems have been launched, the most recent of which are [CamAPS FX](https://camdiab.com/) (UK and EU) and [Omnipod 5](https://www.omnipod.com/en-gb/what-is-omnipod/omnipod-5) (USA and EU). Ceux-ci sont très différents des systèmes DIY principalement parce qu'ils incluent tous deux un « algorithme d'apprentissage » qui ajuste la quantité d'insuline délivrée en fonction de vos besoins d'insuline des jours précédents. De nombreuses membres de la communauté DIY ont déjà testé ces systèmes commerciaux et les ont comparés avec leur système de boucle DIY. You can find out more about how the different systems compare by asking on the dedicated Facebook groups for these systems, on the [AAPS Facebook group](https://www.facebook.com/groups/AndroidAPSUsers/) or on [Discord](https://discord.com/invite/4fQUWHZ4Mw).

## Qu'est-ce que Android APS (AAPS) ?

![image](../images/basic-outline-of-AAPS.png)

**Figure 1**. Description succinte du système APS d'Android (Artificial Pancréas System), AAPS.

Android APS (**AAPS**) is a hybrid closed loop system, or Artificial Pancreas System  (APS). It makes its insulin dosing calculations using established [OpenAPS](https://openaps.org/) algorithms (a set of rules) developed by the #WeAreNotWaiting type 1 diabetes community.

Since OpenAPS is only compatible with certain older insulin pumps, **AAPS** (which can be used with a wider range of insulin pumps) was developed in 2016 by Milos Kozak, for a family member with type 1 diabetes. Since those early days, **AAPS** has been continually developed and refined by a team of volunteer computer developers and other enthusiasts who have a connection to the type 1 diabetes world. Today, **AAPS** is used by approximately 10,000 people. C'est un système hautement personnalisable et polyvalent, et parce qu'il est open source, il est également facilement compatible avec de nombreux autres logiciels et plateformes open-source pour le diabète. The fundamental components of the current **AAPS** system are outlined in **Figure 1** above.



## Quels sont les composants de base d'AAPS ?

The “brain” of AAPS is an **app** which you build yourself. Des instructions détaillées sont fournies pour la construire. You then install the **AAPS  app** on a [compatible](https://docs.google.com/spreadsheets/d/1zO-Vf3wv0jji5Gflk6pe48oi348ApF5RvMcI6NG5TnY/edit?pli=1#gid=2097219952) **Android smartphone** (**1**). Un certain nombre d'utilisateurs préfèrent conserver leur boucle sur un téléphone distinct de leur téléphone principal. Vous pouvez donc par exemple utiliser un téléphone Android juste pour faire fonctionner votre boucle AAPS et utiliser votre téléphone habituel pour toutes vos autres activités.

The **Android smartphone** will also need to have another app installed on it as well as **AAPS**. This is either a modified Dexcom app called build-your-own dexcom app [**BYODA**](https://docs.google.com/forms/d/e/1FAIpQLScD76G0Y-BlL4tZljaFkjlwuqhT83QlFM5v6ZEfO7gCU98iJQ/viewform?fbzx=2196386787609383750&fbclid=IwAR2aL8Cps1s6W8apUVK-gOqgGpA-McMPJj9Y8emf_P0-_gAsmJs6QwAY-o0) or [**Xdrip+**](https://xdrip.readthedocs.io/en/latest/install/usethedoc/). This additional app receives glucose data from a sensor (**2**) by bluetooth, and then sends the data internally on the phone to the **AAPS app**.

The **AAPS app** uses a decision making process (**algorithm**) from OpenAPS. Beginners  start out using the basic **oref0** algorithm, but it is possible to switch to using the newer **oref1** algorithm as you progress with AAPS. Le choix de l'algorithme (oref0 ou oref1) sera à effectuer en fonction de celui qui correspondra le mieux à votre situation.  Dans les deux cas, l'algorithme prend en compte plusieurs facteurs, et effectue des calculs rapides chaque fois qu'une nouvelle lecture provient du capteur de glycémie. The algorithm then sends instructions to the insulin pump (**3**) on how much insulin to deliver by bluetooth. All the information can be sent by mobile data or wifi to the internet (**4**). Ces données peuvent également être partagées avec des abonnés, si souhaité, et/ou collectées pour analyse.

## Quels sont les avantages du système AAPS ?

The OpenAPS algorithm used by **AAPS** controls blood sugar levels in the absence of user input, according to the users’ defined parameters (important ones being basal rates, insulin sensitivity factors, insulin-to-carb ratios, duration of insulin activity etc.), reacting every 5 minutes to the new sensor data. Certains des avantages les plus appréciés de l'utilisation d'AAPS sont les options de réglage fin et adaptable à chaque personne, la possibilité de mise en place d'automatisations et une plus grande transparence du système pour le patient et le soignant. Ceci peut permettre un meilleur contrôle de votre diabète (ou de celui de la personne que vous assistez), pouvant amener à une meilleure qualité de vie et une plus grande tranquillité d'esprit.

### **Specific advantages include:**

#### 1) La sûreté d'abord
To read about the safety features of the algorithms, known as oref0 and oref1, [click here](https://openaps.org/reference-design/). L'utilisateur a la responsabilité de définir ses propres limites de sécurité.

#### 2) **Hardware flexibility**

**AAPS** works with a wide range of insulin pumps and sensors. Ainsi, par exemple, si vous développez une allergie à la colle du capteur Dexcom, vous pourrez à la place, basculer vers un capteur Freestyle libre. Cela offre de la flexibilité au fur et à mesure que votre vie évolue. You don't have to rebuild or reinstall the **AAPS** app, just tick a different box in the app to change your hardware. AAPS ne dépend pas d'un pilote de pompe particulier et contient également une "pompe virtuelle" afin que les utilisateurs puissent expérimenter en toute sécurité avant de l'utiliser sur eux-mêmes.

#### 3) **Highly customisable, with wide parameters**

Users can easily add or remove modules or functionality, and **AAPS** can be used in both open and closed loop mode. Here are some examples of the possibilities with the **AAPS** system:

 a) La possibilité de définir une cible glycémique plus basse 30 minutes avant un repas; la cible minimum que vous pouvez fixer est de 72 mg/dL (4.0 mmol/L).

 b) If you are insulin-resistant resulting in high blood sugars, **AAPS** allows you to set an **automation** rule  to activate when BG rises above 8 mmol/L (144 mg/dL), switching to (for example) a 120% profile (resulting in an 20% increase in basal and strengthening of other factors too, compared to your normal **profile** setting). L'automatisation prendra fin après la durée que vous aurez vous-même programmé. Une automatisation pourrait par exemple être configurée pour être active seulement certains jours de la semaine, ou certaines heures de la journée, ou même en certains lieux.

 c) If your child is on a trampoline with no advance notice, **AAPS** allows insulin  suspension for a set time period, directly via the phone.

 d) After reconnecting a tubed pump which has been disconnected for  swimming, **AAPS** will calculate the basal insulin you have missed while disconnected and deliver it carefully, according to your current BG. Toute insuline non requise peut être remplacée par une simple « annulation » de l'insuline basale correspondante.

 e) **AAPS** has the facility for you to set different profiles for different situations and easily switch between them. For example, features which make the algorithm quicker to bring down elevated BG (like supermicro boluses (“**SMB**”), unannounced meals, (“**UAM**”) can be set to only work during the daytime, if you are worried about night-time hypos.

These are all examples, the full range of features gives huge flexibility for daily life including sport, illness, hormone cycles _etc_. En résumé, c'est à l'utilisateur de décider comment utiliser cette flexibilité, et il n'y a pas une automatisation unique pour tout le monde.

#### 4) **Remote monitoring**
There are multiple possible monitoring channels (Sugarmate, Dexcom Follow, Xdrip+, Android Auto _etc._) which are useful for parents/carers and adults in certain scenarios (sleeping/driving) who need customisable alerts. Dans certaines applications (Xdrip+), vous pouvez également désactiver complètement les alarmes ce qui est génial si vous avez un nouveau capteur « en cours d'initialisation » ou en attente avec lequel vous ne voulez pas encore boucler.

#### 5) **Remote control**
A significant advantage of **AAPS** over commercial systems is that it is possible for followers, using authenticated text (SMS) commands or via an app ([Nightscout](https://nightscout.github.io/) or AAPSClient) to send a wide range of commands back to the **AAPS** system. Ce type de commande est largement utilisée par les parents d'enfants atteints de diabète de type 1 qui utilisent AAPS. C'est très utile par exemple quand votre enfant est occupé à jouer au parc et que vous voulez envoyer un pré-bolus pour une collation à partir de votre propre téléphone. It is possible to monitor the system (_e.g._ Fitbit), send basic commands (_e.g._ Samsung Galaxy watch 4), or even run the entire AAPS system from a high-spec smartwatch (**5**) (_e.g._ LEMFO LEM14). Dans ce dernier scénario, vous n’avez même pas besoin d’utiliser un téléphone pour exécuter AAPS. À mesure que la durée de vie de la batterie des montres s'améliore, cette dernière option va devenir de plus en plus intéressante.

#### 6) **No commercial constraints, due to open application interfaces**
Beyond the use of an open-source approach, which allows the source code of **AAPS** to be viewed at any time, the general principle of providing open programming interfaces gives other developers the opportunity to contribute new ideas too. **AAPS** is closely integrated with Nightscout. Cela accélère le développement et permet aux utilisateurs d'ajouter des fonctionnalités pour rendre la vie avec le diabète encore plus facile. Good examples for such integrations are [Nightscout](https://nightscout.github.io/), [Nightscout Reporter](https://nightscout-reporter.zreptil.de/), [Xdrip+](https://xdrip.readthedocs.io/en/latest/install/usethedoc/), [M5 stack](https://github.com/mlukasek/M5_NightscoutMon/wiki?fbclid=IwAR1pupoCy-2GuXLS7tIO8HRkOC_536YqSxTK7eF0UrKkM1PuucFYRyPFvd0) etc. La discussion est ouverte entre les développeurs de logiciels open-source et ceux qui développent des systèmes commerciaux. Many of the DIY innovations are gradually adopted by commercial systems, where developments are understandably slower, partly because interfaces between systems from different companies (pumps, apps, sensors _etc_) need to be carefully negotiated and licenced. Cela peut également ralentir les innovations qui sont utiles pour les patients (ou un sous-groupe de patients avec un besoin très spécifique) mais ne génèrent aucun profit important.

#### 7) **Detailed app interface**
With **AAPS** it is easy to keep track of things like: pump insulin levels, cannula age, sensor age, pump battery age, insulin-on-board _etc_. Many actions can be done through the **AAPS** app (priming the pump, disconnecting the pump _etc_.), instead of on the pump itself, which means the pump can stay in your (or your dependant's) pocket or belt.

#### 8) **Accessibility and affordability**
**AAPS** gives people who currently can’t afford to self-fund, or don’t have funding/insurance, access to a world-class hybrid closed looping system which is conceptually years ahead, in terms of development, of the commercial systems. You currently need to have a Nightscout account to set up **AAPS**, although the Nightscout account is not required for day-to-day running of the **AAPS** loop. De nombreuses personnes continuent d'utiliser Nightscout pour collecter leurs données et pour le contrôle à distance. Although **AAPS** itself is free, setting up Nightscout through one of the various platforms may incur a fee (€0 - €12), depending on what level of support you want (see comparison table) and whether you want to keep using Nightscout after setup or not. **AAPS** works with a wide range of affordable (starting from approx €150) Android phones. Different versions are available for specific locations and languages, and AAPS can also be used by people who are [blind](#accessibility-for-users-aaps-who-are-partially-or-completely-blind).

#### 9) **Support**
Aucun système d'administration d'insuline automatique n'est parfait. Les systèmes commerciaux et les systèmes open-source partagent de nombreux problèmes communs en matière de communications et de défaillances matérielles temporaires. There is support available from community of AAPS users on Facebook, Discord and GitHub who designed, developed and are currently using **AAPS**, all over the world. Il y a aussi du support surt des groupes Facebook et de l'aide provenant d'établissement de santé et d'entreprises commerciales pour les systèmes de boucles fermées commerciaux. Cela vaut la peine de parler aux utilisateurs, ou aux anciens utilisateurs de ces systèmes afin d'obtenir des retours d'expérience sur les bugs courants, la qualité du programme éducatif et le niveau de support continu fourni.

#### 10) **Predictability, transparency and safety**
**AAPS** is totally transparent, logical and predictable, which may make it easier to know when a setting is wrong, and to adjust it accordingly. Vous pouvez voir exactement ce que fait le système, pourquoi il le fait, et définissez ses limites opérationnelles, ce qui met le contrôle (et la responsabilité) entre vos mains. L'utilisateur peut gagner en assurance et bénéficier d'un sommeil plus tranquille.

#### 11) **Access to advanced features through development (dev) modes including full closed loop**
This **AAPS** documentation focuses on the mainstream **“master”** branch of **AAPS**. Cependant, la recherche et le développement n'arrêtent jamais. More experienced users may wish to explore the experimental features in the **development** branch. Cela inclut l'intégration du Dexcom G7 et l'ajustement automatique de l'injection d'insuline en fonction des changements de sensibilité à court terme (DYNISF). The development innovations focus on strategies for full closed looping (not having to bolus for meals _etc._), and generally trying to make life with type 1 diabetes as convenient as possible.

#### 12) **Ability to contribute yourself to further improvements**
Le diabète de type 1 peut être très frustrant et isole les personnes. Avoir le contrôle de votre propre système technologique pour votr diabète, avec la possibilité de contribuer à votre tour dès que vous faites des progrès en aidant les autres dans leur cheminement peut être vraiment gratifiant. Vous pouvez vous former, mettre au jour des obstacles, faire des recherches et même contribuer à de nouveaux développements et à la documentation. Vous trouverez d'autres personnes dans la communauté avec qui partager la même envie de progresser, avec qui réfléchir et travailler. C'est l'essence même du mouvement #WeAreNotWaiting.

## Comment marche AAPS en comparaison aux Multiples Injections Quotidiennes (MDI) et à la boucle ouverte ?

Multiple daily injections (MDI, (a) in **Figure 2** below) usually involve giving an injection of a long-lasting insulin (_e.g._ Tresiba) once a day, with injections of faster-acting insulin (_e.g._ Novorapid, Fiasp) at mealtimes, or for corrections. L'utilisation classique d'une pompe à insuline (boucle ouverte) (b) implique l'utilisation d'une pompe pour délivrer le basal à des taux pré-programmés d'insuline à action rapide, puis à effectuer un bolus via la pompe lors des repas ou pour des corrections. Le principe de base d'un système de boucle est que l'application utilise les données de glycémie pour envoyer à la pompe l'instruction d'arrêter l'injection d'insuline lorsqu'elle prévoit que vous allez bientôt être en hypoglycémie, et pour vous donner plus d'insuline si votre glycémie augmente et que vous allez être en hyperglycémie (c). Bien que ce schéma soit simplifié par rapport à la réalité, il vise à démontrer les principales différences entre ces approches. Il est possible d'arriver à un contrôle extrêmement bon de la glycémie avec n'importe laquelle de trois approches.

![21-06-23 AAPS glucose MDI etc](../images/basic-overview-mdi-open-and-closed-loop.png)


**Figure 2**. Aperçu simplifié de (a) Injections multiples quotidiennes ou MDI, (b) boucle ouverte et (c) boucle fermée hybride.

## Comment marche AAPS en comparaison aux autres systèmes de boucle?

As of June 25 2023, there are four major open source closed loop systems available: [OpenAPS](https://openaps.readthedocs.io/), **AAPS**, [Loop](https://loopkit.github.io/loopdocs/#what-is-loop) and [iAPS](https://github.com/Artificial-Pancreas/iAPS?fbclid=IwAR2fA9Y9YqYzpKSrtEsotfXl5b67UclDkKgyrv52tQLzYbOoBeNGRmjlJJI), (formerly FreeAPS X). Les caractéristiques des différents systèmes sont affichées dans le tableau ci-dessous :


| Type d'appareil | Nom                                                                 | [AAPS](https://wiki.aaps.app)             | [Loop](https://loopkit.github.io/loopdocs/) | [Open APS](https://openaps.readthedocs.io/en/latest/) | [iAPS](https://iaps.readthedocs.io/en/latest/) |
| --------------- | ------------------------------------------------------------------- | ----------------------------------------- | ------------------------------------------- | ----------------------------------------------------- | ---------------------------------------------- |
| Téléphone       | Android                                                             | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| Téléphone       | iPhone                                                              | ![unavailable](../images/unavailable.png) | ![available](../images/available.png)       | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| Rig             | tout petit ordinateur (1)                                           | ![unavailable](../images/unavailable.png) | ![unavailable](../images/unavailable.png)   | ![available](../images/available.png)                 | ![unavailable](../images/unavailable.png)      |
| POMPE           | [Dana I](../CompatiblePumps/DanaRS-Insulin-Pump.md)                 | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| POMPE           | [Dana RS](../CompatiblePumps/DanaRS-Insulin-Pump.md)                | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| POMPE           | [Dana R](../CompatiblePumps/DanaR-Insulin-Pump.md)                  | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| POMPE           | [Omnipod (Dash)](../CompatiblePumps/OmnipodDASH.md) (2)             | ![available](../images/available.png)     | ![available](../images/available.png)       | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| POMPE           | [Omnipod (Eros)](../CompatiblePumps/OmnipodEros.md)                 | ![available](../images/available.png)     | ![available](../images/available.png)       | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| POMPE           | [Diaconn G8](../CompatiblePumps/DiaconnG8.md)                       | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| POMPE           | [EOPatch 2](../CompatiblePumps/EOPatch2.md)                         | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| POMPE           | [Medtrum TouchCare Nano](../CompatiblePumps/MedtrumNano.md)         | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| POMPE           | [Medtrum TouchCare 300U](../CompatiblePumps/MedtrumNano.md)         | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| POMPE           | [Roche Combo](../CompatiblePumps/Accu-Chek-Combo-Pump.md)           | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| POMPE           | [Roche Insight](../CompatiblePumps/Accu-Chek-Insight-Pump.md)       | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| POMPE           | [Older Medtronic](../CompatiblePumps/MedtronicPump.md)              | ![available](../images/available.png)     | ![available](../images/available.png)       | ![available](../images/available.png)                 | ![available](../images/available.png)          |
| MGC             | [Dexcom G7](../CompatibleCgms/DexcomG7.md)                          | ![available](../images/available.png)     | ![available](../images/available.png)       | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| MGC             | [Dexcom One](../CompatibleCgms/DexcomG6.md)                         | ![available](../images/available.png)     | ![available](../images/available.png)       | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| MGC             | [Dexcom G6](../CompatibleCgms/DexcomG6.md)                          | ![available](../images/available.png)     | ![available](../images/available.png)       | ![available](../images/available.png)                 | ![available](../images/available.png)          |
| MGC             | [Dexcom G5](../CompatibleCgms/DexcomG5.md)                          | ![available](../images/available.png)     | ![available](../images/available.png)       | ![available](../images/available.png)                 | ![available](../images/available.png)          |
| MGC             | [Libre 3](../CompatibleCgms/Libre3.md)                              | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![unavailable](../images/unavailable.png)      |
| MGC             | [Libre 2](../CompatibleCgms/Libre2.md)                              | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| MGC             | [Libre 1](../CompatibleCgms/Libre1.md)                              | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| MGC             | [Eversense](../CompatibleCgms/Eversense.md)                         | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| MGC             | [MM640g/MM630g](../CompatibleCgms/MM640g.md)                        | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| MGC             | [PocTech](../CompatibleCgms/PocTech.md)                             | ![available](../images/available.png)     | ![unavailable](../images/unavailable.png)   | ![unavailable](../images/unavailable.png)             | ![available](../images/available.png)          |
| MGC             | [Nightscout as BG Source](../CompatibleCgms/CgmNightscoutUpload.md) | ![available](../images/available.png)     | ![available](../images/available.png)       | ![available](../images/available.png)                 | ![available](../images/available.png)          |

_Table notes:_
1. A **rig** is a small computer which you carry around with you, without a monitor. Un type d'appareil pris en charge est Intel Edison + Explorer Board et l'autre Raspberry Pi + Explorer HAT ou Adafruit RFM69HCW Bonnet. Les premiers APS étaient basés sur cette configuration, car les téléphones mobiles n'étaient pas capables d'exécuter les algorithmes nécessaires. L'utilisation de ces systèmes a régressé, car l'installation sur les téléphones mobiles est devenue plus facile et les téléphones ont un écran inclus. Intel a également arrêté de vendre l'Intel Edison. The excellent OpenAPS algorithms **oref0** and **oref1** are now incorporated in AAPS and iAPS.
2. Omnipod Dash est le successeur de Omnipod Eros. Il prend en charge la communication bluetooth et n'a pas besoin d'un accessoire intermédiaire pour communiquer avec le téléphone mobile. Si vous avez le choix, nous recommandons l'utilisation du Dash au lieu de l'Eros.


An international peer-reviewed consensus statement containing practical guidance on open source looping was written by and for health-care professionals, and published in a leading medical journal in 2022: [_Lancet Diabetes Endocrinol_, 2022; 10: 58–74](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8720075/)(_1_). Ce document est fort utile (y compris pour votre équipe médicale) et résume les principales différences techniques entre les différents systèmes open-source de boucle fermée hybride.

Il est difficile d'avoir un "ressenti" quel que soit le système sans l'utiliser soi-même, ou sans en parler à d'autres qui l'utilisent, alors n'hésitez pas à contacter et à demander des retours d'expériences à des utilisateurs sur Facebook/Discord. Most people find that **AAPS** is incredibly sophisticated in comparison to other hybrid closed loop systems (particularly the commercial systems), with a huge number of potentially customisable settings and features,  discussed above. Certaines personnes peuvent trouver cela un peu trop au début, mais il n'y a pas de précipitation à avoir pour étudier toutes les possibilités en même temps, vous pouvez progresser aussi lentement ou aussi vite que vous le souhaitez, et il y a de l'aide à chaque étape.


## AAPS utilise-t-il une intelligence artificielle ou un algorithme d’apprentissage ?

The current master version of **AAPS** (3.1.0.3) does not have any machine learning algorithms, multiple-parameter insulin response models, or artificial intelligence. En tant que tel, le système est ouvert et transparent dans son fonctionnement, et a la capacité d'être compris non seulement par les experts, mais aussi par les médecins et les patients. It also means that if you have a sharply varying schedule (maybe switching from a stressful week at work to a relaxing holiday) and are likely to need a significantly different amount of insulin, you can immediately switch **AAPS** to run a weaker/stronger customised profile. Un « système d'apprentissage » fera cet ajustement pour vous automatiquement, mais il est probable qu'il lui faille plus de temps pour ajuster la distribution d'insuline.

## Quel système est le plus approprié pour moi ou la personne que j'assiste ?

En pratique, votre choix de système est souvent restreint par la pompe que vous possédez déjà ou que vous pouvez obtenir auprès de votre médecin diabétologue et de votre choix de téléphone (Apple ou Android). Si vous n’avez pas encore de pompe, vous avez le plus grand choix de systèmes. La technologie est en constante évolution, la production ou vente de certaines pompes s'arréte et de nouvelles pompes et capteurs apparaissent. La plupart des systèmes open-source fonctionnent avec les capteurs principaux (Freestyle Libre et Dexcom) ou sont rapidement mis à jour pour utiliser de nouveaux capteurs environ un an après leur sortie (avec un peu de retard pour les tests de sécurité et de stabilité).

Most **AAPS** users report more time in range, HbA1c reductions, as well as quality of life improvements from having a system that can auto-adjust basal rates overnight during sleep, and this is true for most hybrid closed loop systems. Certaines personnes ont une préférence pour un système très simple qui n'est pas très personnalisable (ce qui signifie que vous pouvez préférer un système commercial), et d'autres personnes trouvent ce manque de contrôle très frustrant (vous pouvez préférer un système open-source). If you (or your dependant) are newly diagnosed, a common route is to get used to using MDI plus a glucose sensor first, then progress to a pump which has the potential for looping, then progress to **AAPS**, but some people (especially small kids) may go straight to a pump.

It is important to note that the **AAPS** user needs to be proactive to troubleshoot and fix problems themselves, with help from the community. C'est un état d'esprit très différent de celui correspondant à l'utilisation d'un système commercial. With **AAPS** a user has more control, but also the responsibility, and needs to be comfortable with that.

## Peut-on utiliser des systèmes open-source comme AAPS en toute sécurité ?

### Sûreté du système AAPS
A more accurate question is probably “is it safe **compared** with my current insulin delivery system?” since no method of insulin delivery is without risk. There are many checks and balances in place with **AAPS**. A recent [paper](https://www.liebertpub.com/doi/epub/10.1089/dia.2019.0375) looked at the use of **AAPS** in a computer simulated set-up, which was an effective way to unobjectively trial how safe and effective the system is. De manière plus générale, on estime que plus de 10 000 personnes dans le monde utilisent des systèmes de distribution d'insuline automatisée open-source, et que ce nombre continue d'augmenter à l'échelle mondiale.

N'importe quel périphérique qui utilise des communications radio peut être piraté, et c'est vrai aussi pour une pompe à insuline (sans boucle). À l'heure actuelle, nous ne connaissons personne qui tente de nuire aux personnes en piratant leur équipement médical lié au diabète. Cependant, il existe de multiples moyens de se protéger contre de tels risques :

1.  Dans les paramètres de la pompe, limitez à la fois le bolus max autorisé et le réglage de base temporaire max à des quantités qui, selon vous, sont les plus sûres. Ce sont des limites fortes que nous pensons non contournables par un pirate malveillant.

2.  Laissez actives vos alarmes de capteurs de glycémies MGC pour les hypos et les hypers.

3.  Surveillez votre injection d'insuline en ligne. Les utilisateurs Nightscout peuvent définir des alarmes supplémentaires pour les alerter pour une grande variété de conditions, y compris les celles qui sont beaucoup plus susceptibles de se produire qu'une attaque malveillante. En plus des hypos et hypers, Nightscout peut afficher des données de diagnostic utiles pour vérifier que la pompe fonctionne comme vous le souhaitez, incluant l'Insuline Active (IA) courante, l'historique des basales temporaires de la pompe, l'historique des bolus de la pompe. Il peut également être configuré pour avertir proactivement les utilisateurs de conditions indésirables, telles que : prévisions d'hypos et d'hypers, réservoir d'insuline faible et batterie faible de la pompe.

Si une attaque malveillante était effectuée contre votre pompe à insuline, ces stratégies atténueraient considérablement le risque. Every potential **AAPS** user needs to weigh the risks associated with using **AAPS**, versus the risks of using a different system.

#### Considérations de sécurité en lien avec l'amélioration trop rapide du contrôle de la glycémie

Une baisse rapide de l'HbA1c et un meilleur contrôle de la glycémie paraissent attirants. However, reducing average blood glucose levels _too fast_ by starting any closed loop system can cause permanent damage, including to the eyes, and painful neuropathy that never goes away. Ces atteintes peuvent être évitées simplement en baissant plus lentement les niveaux. Si vous avez actuellement un taux d'HbA1c élevé et que vous passez à AAPS (ou à tout autre système en boucle fermée), veuillez discuter de ce risque potentiel avec votre équipe médicale avant de commencer, et convenez d'un plan de mise en place avec elle. More general information on how to reduce your glucose levels safely, including links to medical literature is given in the [safety section [here](../Getting-Started/PreparingForAaps.md#safety-first).

#### Sûreté médicale autour des dispositifs, consommables et autres médicaments

Utilisez une pompe à insuline et un capteur de glycémie approuvés par la FDA ou la CE, testés et entièrement fonctionnels, pour une boucle de pancréas artificiel. Les modifications matérielles ou logicielles de ces composants peuvent entraîner un dosage incorrect de l'insuline, causant un risque significatif pour l'utilisateur. Si vous trouvez ou recevez des pompes à insuline ou des capteurs de glycémie cassés, modifiés ou fabriqués maison, ne les utilisez pas pour mettre en place un système AAPS.

Utilisez du matériel d'origine pour les applicateurs, cathéters et réservoirs d'insuline, approuvés par le fabricant de votre pompe et de votre MGC. L'utilisation de consommables non testés ou modifiés peut entraîner une imprécision du MGC et des erreurs de dosage de l'insuline. L'insuline peut s'avérer très dangereuse lorsqu'elle est mal dosée - ne jouez pas avec votre vie en bricolant votre matériel.

Do not take SGLT-2 inhibitors (gliflozins) when using **AAPS** as they incalculably lower blood sugar levels. Combining this effect with a system that lowers basal rates in order to increase BG is dangerous, there is more detail about this in the main [safety section](../Getting-Started/PreparingForAaps.md#safety-first).

(introduction-how-can-i-approach-discussing-aaps-with-my-clinical-team)=
## Comment puis-je aborder AAPS avec mon équipe médicale ?

Users are encouraged to speak with their clinicians about their intention to use **AAPS**. Please do not be afraid to have an honest conversation with your diabetes team if you intend to use **AAPS** (or any other DIY loop, for that matter). La transparence et la confiance entre le patient et le médecin sont primordiales.

### Approche suggérée :
Commencez par discuter avec votre docteur afin d'en savoir plus sur ses connaissances et son attitude vis-à-vis de la technologie utile aux diabétiques telle que les MGC, les pompes, les boucles hybrides et les boucles commerciales. Votre docteur/endocrinologue devrait être au fait des moyens techniques de base et être prêt à discuter avec vous des récentes avancées apportées par les produits de boucle commerciaux disponibles dans votre pays.

#### Antécédents locaux

Obtain your clinicians/endocrinologists’ views on DIY loop _vs_ commercial looping, and gauge their knowledge in this area. Are they familiar with **AAPS** and can they share with you any helpful experience of working with patients with DIY looping?

Demandez si l'équipe médicale suit des patients qui utilisent déjà une boucle DIY. En raison du secret médical, les médecins ne peuvent pas transmettre les informations d'autres patients sans obtenir le consentement de la personne. However, if you want to, you **can** ask them to pass **your** contact details to an existing DIY looping patient if there is one the clinician feels you might "click” with, suggesting that you would be happy for the patient to contact you to discuss DIY looping. Les docteurs n'ont aucune obligation de le faire, mais certains le feront avec plaisir, car ils ont conscience de l'importance du soutien entre pairs dans la gestion du diabète de type 1. Vous pourriez également trouver utile de rencontrer des boucleurs DIY à proximité de chez vous. Cela dépend bien sûr de vous, et n'est pas indispensable.

#### Antécédents nationaux et internationaux

If you feel unsupported by your team to loop with **AAPS**, the following discussion points may help:

a) The **AAPS** system has been designed BY patients and their caregivers. Il a été conçu avant tout pour la sûreté, mais aussi en s'inspirant de l'expérience "dans la vie réelle" des patients. There are currently around **10,000** AAPS users worldwide. Il est donc probable qu'il y ait d'autres personnes utilisant une boucle DIY parmi les patients que suit votre docteur (qu'il soit au courant ou non).

b) Recent peer-reviewed published guidance in the internationally leading medical journal [The Lancet](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8720075/pdf/nihms-1765784.pdf)_(1)_ has confirmed that DIY loops are **safe** and **effective at improving diabetic control**, including time in range. There are regular articles in leading journals like [Nature](https://doi.org/10.1038/d41586-023-02648-9)_(3)_ which highlight the progress of the DIY looping commmunity.

c) Starting with **AAPS** involves a _gradual_ migration from “open” loop pumping, through low-glucose suspend, through to hybrid “closed” looping, by completing a number of objectives. Il existe donc un programme structuré, exigeant de l'utilisateur qu'il démontre un niveau de compétence à chaque étape et qu'il ajuste ses paramètres de base (basal, SI et G/I) avant de pouvoir fermer la boucle.

d) Vous trouverez toujours le support technique dont vous avez besoin auprès de la communauté DIY via les groupes privés GitHub, Discord et Facebook.

e) You will be able to provide **both CGM and insulin looping/pumping information** as combined reports at clinic meetings (through Nightscout or Tidepool), either printed out or on-screen (if you bring a laptop/tablet). La mise en parallèle des données de glycémie et d'insuline permettra une utilisation plus efficace du temps de votre docteur lors de l'examen vos rapports et des discussions pour évaluer vos progrès.

f) If there is still strong objection from your team, hand your clinician printouts of the reference articles linked here in the text, and give them the link to the **AAPS** clinicians section: [For Clinicians – A General Introduction and Guide to **AAPS**](../Resources/clinician-guide-to-AndroidAPS.md)

#### Support pour la boucle DIY par d'autres docteurs

The paper published in the [Lancet Diabetes Endocrinology](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8720075/)(_1_)[ (co led by Kings’ and Guy’s and St Thomas’ NHS Foundation Trust, and co lead by Dr Sufyan Hussain, a consultant diabetologist and honorary senior lecturer from King’s in London) provides:

a) **Assurance** for professionals that DIY artificial pancreas systems/ open source as a “safe and effective treatment” option for type 1 diabetes and provides guidance on recommendations, discussions, supports, documentation;

b) **Recognition** that open-source automated insulin delivery (“AID”) systems can increase time in range (TIR) while reducing variability in blood glucose concentrations and the amount of hypo and hyperglycaemic episodes in various age groups, genders and communities;

c) **Recommendation** that healthcare workers should **support** type 1 patients or their caregivers who choose to manage their diabetes with an open source AID system;

d) La recommandation selon laquelle les professionnels de santé devraient essayer de se documenter sur toutes les possibilités de traitement qui pourraient bénéficier aux patients, y compris les systèmes de boucle open source disponibles.  If health care professionals do not have resources to educate themselves, or have legal or regulatory concerns, they should consider **cooperating, or teaming up with other healthcare professionals** who do;

e) Emphasis that all users of CGMs should have real-time and open-access to **their own health data** at all times

f) Souligne que ces systèmes open source n'ont pas subi les mêmes évaluations réglementaires que les technologies médicales disponibles commercialement, et qu'il n'y a pas de support technique commercial. However, **extensive community support is available**; and

g) A recommendation that **regulation and legal frameworks** should be updated to ensure clarity on permitting ethical and effective treatment of such open source systems.

Another paper in [Medical Law International, 2021](http://pure-oai.bham.ac.uk/ws/files/120241375/0968533221997510.pdf)(_4_) also highlights the UK General Medical Council’s ‘consent guidance’ places a strong emphasis on doctor and patients making decisions together. Les professionnels de santé devraient expliquer les avantages, risques, inconvénients et effets secondaires potentiels du système APS open-source et devraient pouvoir recommander une option particulière sans pour autant faire pression sur le patient pour qu'il l'adopte.

En fin de compte, il revient au patient de considérer ces facteurs, ainsi que tout problème non clinique pertinent pour lui, et de décider quelle option de traitement, le cas échéant, accepter.

Lorsqu'un médecin se rend compte que son patient boucle avec un système DIY, ça ne l'exonère pas de son obligation de suivre le patient, simplement parce qu'il n'a pas prescrit cet élément technologie particulière que le patient utilise; les professionels de santé doivent continuer de suivre leurs patients.

Les médecins (du moins au Royaume-Uni) n'ont pas l'interdiction de prescrire des médicaments non reconnus et peuvent utiliser leur discernement médical. Ils devraient donc faire usage de leur jugement médical pour décider si un système APS DIY convient à un patient spécifique, et discuter avec le patient de ce qu'ils y voient comme avantages et inconvénients.

#### Les articles référencés ci-dessus, ainsi que d'autres liens utiles et déclarations de position sont listés ci-dessous :

1. Open-source automated insulin delivery: international consensus statement and practical guidance for health-care professionals [_Lancet Diabetes Endocrinol_, (2022) _10_, 58–74](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8720075/)
2. [In Silico Trials of an Open-Source Android-Based Artificial Pancreas: A New Paradigm to Test Safety and Efficacy of Do-It-Yourself Systems, 2020](https://www.liebertpub.com/doi/epub/10.1089/dia.2019.0375)
3. Un ‘pancréas bionique’ révolutionne les soins du diabète — quelle est la prochaine étape ? [_Nature_ (2023), _620_, 940-941](https://doi.org/10.1038/d41586-023-02648-9)
4. Prescrire des dispositifs médicaux non approuvés ? The case of DIY artificial pancreas systems [_Medical law international_, (2021), _21_, 42-68](http://pure-oai.bham.ac.uk/ws/files/120241375/0968533221997510.pdf)
5. [Berlin Institute of Health position statement, 2022](https://www.bihealth.org/en/notices/do-it-yourself-solutions-for-people-with-diabetes-are-safe-and-recommended)
6. Do-It-Yourself Automated Insulin Delivery: A Health-care Practitioner User’s Guide (Diabetes Canada position and guide) [_Canadian Journal of Diabetes_, (2023)_47_, E8, 389-397](https://www.canadianjournalofdiabetes.com/article/S1499-2671(23)00138-7/fulltext)
7.  Netherlands (EN/NL) - for clinicians - [how to help people on open source automated insulin delivery systems](https://www.diabetotech.com/blog/how-to-help-people-on-open-source-automated-insulin-delivery-systems)
8. First Use of Open-Source Automated Insulin Delivery AndroidAPS in Full Closed-Loop Scenario: Pancreas4ALLRandomized Pilot Study [_Diabetes Technol. Ther._, 25, _5_, 2023](https://www.liebertpub.com/doi/pdf/10.1089/dia.2022.0562?casa_token=D13eFx5vCwwAAAAA:MYvO8hChbViXVJFgov1T11RXBPx2N_wOMThLHwl3TVUxbCuANegPrIFRC5R5VXx_S71FoQYW-qg)
9. Pre-school and school-aged children benefit from the switch from a sensor-augmented pump to an AndroidAPS hybrid closed loop: A retrospective analysis [_Pediatr. Diabetes_ 2021, _22_, 594-604. 2021](https://onlinelibrary.wiley.com/doi/epdf/10.1111/pedi.13190)
10. Publications du projet OPEN, un projet financé par l'UE étudiant la "preuve par le patient" avec une technologie de pancréas artificiel novatrice et open-source (https://www.open-diabetes.eu/publications)



## Pourquoi je ne peux pas simplement télécharger AAPS et l’utiliser immédiatement ?

The **AAPS** app is not provided in Google Play - you have to build it from source code by yourself for legal reasons. **AAPS** is unlicensed, meaning that it does not have approval by any regulatory body authority in any country. **AAPS** is deemed to be carrying out a medical experiment on yourself, and is carried out at the user’s own risk.

La mise en place du système nécessite de la patience, de la détermination et l'apprentissage progressif des connaissances techniques. Toutes les informations et le support peuvent être trouvés dans ces documents, ailleurs en ligne, ou auprès d'autres personnes qui l'ont déjà mis en place. Over 10,000 people have successfully built and are currently using **AAPS** worldwide.

The developers of **AAPS** take safety incredibly seriously, and want others to have a good experience of using **AAPS**. C'est pourquoi il est essentiel que chaque utilisateur (ou chaque parent si l'utilisateur est un enfant) :

- builds the AAPS system themself and works through the **objectives** so that they have reasonably good personalised settings and understand the basics of how **AAPS** works by the time they “close the loop”;

- sauvegarde leur système en exportant et en enregistrant des fichiers importants (comme les fichiers keystore et paramètres json) dans un lieu sécurisé, afin de pouvoir configurer rapidement le système si nécessaire;

- mette à jour les nouvelles versions master d'AAPS dès qu'elles sont disponibles; et

- gère et surveille le système pour s’assurer qu’il fonctionne correctement.

## Comment le système AAPS est-il interconnecté ?

**Figure 3 (below)** shows one example of the **AAPS** system for a user who do not require any followers interacting with the system. D'autres applications et plates-formes open-source, non illustrés ici, peuvent également être intégrés.

![21-06-23 AAPS connectivity no followers](../images/AAPS-connectivity-no-followers.png)


**Figure 4 (below)** shows the full potential of the **AAPS** system for a user who has followers and requires a monitor and send adjust the system remotely (like a child with type 1 diabetes). D'autres applications et plates-formes open-source, non illustrés ici, peuvent également être intégrés.

![21-06-23 AAPS overview with followers](../images/AAPS-overview-with-followers.png)

## Comment AAPS est-il développé et continuellement amélioré ?

Most **AAPS** users use the fully tested **master** version of AAPS, which has been tested for bugs and problems, before being released to the community. Behind the scenes, the developers try out new improvements, and test these out in “developer” (**dev**) versions of **AAPS** with a user community who are happy to do bug updates at short notice. If the improvements work well, they are then released as a new “master” version of **AAPS**. Any new master release is announced on the Facebook group, so that the mainstream **AAPS** users can read about and update to the new master version.

Some experienced and confident **AAPS** users conduct experiments with emerging technologies and with dev versions of the **AAPS** app, which can be interesting for the less adventurous users to read about, without having to do it themselves! Les gens ont tendance à partager ces expériences sur le groupe Facebook.

Vous pouvez en savoir plus sur certaines de ces expériences et discussions sur les technologies émergentes ici :

Tim Street [https://www.diabettech.com/](https://www.diabettech.com/)

David Burren [https://bionicwookie.com/](https://bionicwookie.com/)

## A qui AAPS peut-il être utile ?

| Type d'utilisateur                              |
| ----------------------------------------------- |
| ✔️ diabétique de type 1                         |
| ✔️ soignant ou parent d'un diabétique de type 1 |
| ✔️ utilisateurs aveugles diabétiques de type 1  |
| ✔️ *médecins et professionnels de la santé      |

La table ci-dessus suppose que l'utilisateur a accès à la fois à un capteur de glycémie et à une pompe à insuline.

*All data from **AAPS** can be made available to healthcare professionals via data sharing platforms, including Nightscout that provides logging and real time monitoring of CGM data, insulin delivery, carbohydrate entries, predictions and settings. Les dossiers Nightscout comprennent des rapports quotidiens et hebdomadaires qui peuvent aider les professionnels de la santé à discuter avec les patients diabétiques de type 1 pour améliorer le contrôle glycémiques et les comportements à adopter.

### Accessibilité pour les utilisateurs AAPS aveugles ou malvoyants

#### Utilisation quotidienne de AAPS :
AAPS peut également être utilisé par les personnes aveugles ou malvoyantes. Sur les appareils Android, le système d'exploitation propose une application appelée TalkBack. Cela permet de contrôler l'écran par la voix, directement via le système d'exploitation. En utilisant TalkBack, vous pouvez utiliser à la fois votre smartphone et AAPS sans avoir besoin de voir.

#### Compilation de l'application AAPS :
En tant qu'utilisateur, vous compilerez l'application AAPS dans Android Studio. Beaucoup utilisent Microsoft Windows pour cela, qui propose un lecteur d'écran, "Narrateur ", semblable à TalkBack. Comme Android Studio est une application Java, le composant "Java Access Bridge" doit être activé dans le Panneau de configuration. Dans le cas contraire, le lecteur d'écran du PC ne pourra pas fonctionner dans Android Studio.

Cela dépend de votre système d'exploitation, deux méthodes sont décrites ci-dessous :

1) In the Windows Start menu, enter “Control Panel” in the search field, open with Enter. Cela ouvre : "Tous les éléments du panneau de configuration”.

Open the "Ease of Access Centre".

Puis ouvrez "Utiliser l'ordinateur sans écran" en appuyant sur "Entrée".

Sous "Entendre le texte lu à haut voix", sélectionnez "Activer le narrateur" et "Activer la description audio", et cliquez sur "Appliquer"

ou :

2) Press Windows key and enter “Control Panel” in the search field, open with Enter. Cela ouvre : "Tous les éléments du panneau de configuration”.

Press the letter C to get to “Center for Ease of Use”, open with Enter.

Vous arrivez dans la section "Utiliser l'ordinateur sans écran".

En bas de cette page, vous trouverez la case à cocher "Activer Java Access Bridge", cochez-la.

Et voilà, vous pouvez fermer la fenêtre ! Le lecteur d'écran devrait fonctionner maintenant.



## En quoi AAPS peut-il m'être utile ?

With investment of your time, **AAPS** can potentially lead to:

- soulager le stress et la charge mentale de la gestion du diabète de type 1;

- réduire la multitude de décisions banales de la gestion au quotidien du diabète de type 1;

- fournir un débit adapté et personnalisé d'insuline basé sur des données en temps réel qui peuvent réduire le besoin de traitements d'hypoglycémie et réduire les épisodes d'hyperglycémie;

- avoir une meilleure connaissance de la gestion de l'insuline et de la confiance en soi pour mieux affiner vos paramètres;

- the ability to create automatic settings (**automations**) that are tailored to fit in with your lifestyle;

- améliorer la qualité de votre sommeil et de la réduction globale de la fréquence des interventions nocturnes;

- surveiller et administrer à distance la distribution d'insuline pour les accompagnants des diabétiques de type 1; et

- streamlining of all your portable diabetic equipment (continuous glucose monitor receiver and insulin controlling devices) by using an Android phone controlled by **AAPS**.

Ultimately, **AAPS** can empower individuals to better manage their diabetes, resulting in stable blood sugars and improved long term health outcomes.

Vous voulez en savoir plus sur comment démarrer l'installation d'AAPS ? Take a look at the [preparing](../Getting-Started/PreparingForAaps.md) section.
