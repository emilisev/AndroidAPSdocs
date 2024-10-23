# Automatisation avec une application Android Automate tierce

**This article has been written before AAPS version 2.5. There is an [automation plugin in AAPS](../DailyLifeWithAaps/Automations.md) itself with AAPS version 2.5. For some, this here might be still useful, but should only be used by advanced users.**

As AAPS is a hybrid closed loop system, some user interaction is necessary though (e.g. tell the loop that you are walking, eating soon, lying on the sofa...). Frequent manual user inputs can be automated via external tools like Automate or IFTTT to extend the recent AAPS functionality.

## Application Android Automate
L'application gratuite Android™ Automate vous permet d'automatiser diverses tâches sur votre smartphone. Créez vos automatisations avec des diagrammes, faites que votre appareil change automatiquement les paramètres tels que Bluetooth, Wifi, NFC ou exécute des actions comme l'envoi de SMS, d'e-mail, en fonction de votre localisation, de l'heure du jour, ou de tout autre "déclencheur d'événement". Vous pouvez automatiser presque tout sur votre appareil, Automate même en charge les plug-ins conçus pour Tasker et Locale.

Using this tool you can easily create workflows to auto-treat your diabetes based on several conditions according to the principle of 'if this... and this... not this..., then do that... and that...'. Il y a des milliers de possibilités que vous pouvez configurer.

Until now it is **necessary to loop via Nightscout Profile**, as Automate executes the commands via HTTP-request directly in your nightscout website that subsequently syncs it to your AAPS app.

**Offline looping (direct communication between Automate and AAPS app) is not supported yet**, but technologically possible. Il y aura peut-être une solution à l'avenir. Si vous avez trouvé un moyen de le faire, veuillez l'ajouter à cette documentation ou contacter un développeur.

### Exigences de base

#### Application Automate
Download Android Automate in Google Play Store or at [https://llamalab.com/automate/](https://llamalab.com/automate/) and install it on your smartphone where AAPS runs.

In Automate, tap on hamburger menu on the upper left of the screen > Settings > Check 'Run on system startup'. Cela exécutera automatiquement vos Workflows au démarrage du système.

![Automate HTTP request](../images/automate-app2.png)


#### AAPS
In AAPS, tap on 3 dots menu on the upper right screen and go to Preferences > NSClient > Connection settings > Uncheck 'Use WiFi connection only' and 'Only if charging' as the automated treating does only work when AAPS has an actual nightscout connection.

![Nightscout connection preferences](../images/automate-aaps1.jpg)

In AAPS, tap on 3 dots menu on the upper right screen and go to Preferences > NSClient > Advanced Settings > Uncheck 'NS upload only (disabled sync)' and 'No upload to NS'.

Be aware of the [security issues](../SettingUpAaps/Nightscout.md#security-considerations) that might occure and be very careful if you are using an [Insight pump](../CompatiblePumps/Accu-Chek-Insight-Pump.md#settings-in-aaps).

![Nightscout download preferences](../images/automate-aaps2.jpg)

### Workflow examples

#### Exemple 1: Si une activité (par ex. marche ou course) est détectée, définir une CT élevée. Et si l'activité se termine, attendre 20 minutes puis annuler la CT
This workflow will listen to the smartphone sensors (pedometer, gravity sensor...) that detect the activity behavior. Si une activité récente comme la marche, la course ou du vélo est détectée, alors Automate définira une cible temp élevée d'une durée spécifiée par l'utilisateur. Si l'activité se termine, votre smartphone le détectera, il attendra 20 minutes, puis il fixera la cible à la valeur normale du profil.

Download the Automate script [https://llamalab.com/automate/community/flows/27808](https://llamalab.com/automate/community/flows/27808).

Edit the sling by tapping on the edit pencil > Flowchart

![Automate sling](../images/automate-app3.png)

Personnaliser le script en fonction de vos souhaits comme ceci :

![Automate sling](../images/automate-app6.png)

1. = Définir CT élevée
2. = Revenir à la cible normale 20 minutes après la fin de l'activité

1 ![Automate sling](../images/automate-app1.png)

2 ![Automate sling](../images/automate-app5.png)

URL de la requête : Votre URL-NS se terminant par /api/v1/treatments.json (par ex. https://my-cgm.herokuapp.com/api/v1/treatments.json)

Contenu de la requête :
* targetTop / targetBottom: La valeur de la CT haute (la valeur haute et basse doivent être les mêmes)
* duration: La durée de la CT haute (Après cette durée, il reviendra à la cible du profil standard sauf si l'activité se poursuit).
* secret : votre hachage SHA1 de l'API. Ce n'est PAS votre clé api ! You can convert your API key to SHA1 format at [http://www.sha1-online.com/](http://www.sha1-online.com/)

Save: Tap on 'Done' and on the hook

Start sling: Tap on Play button



#### Example 2: If xDrip+ alerts a BG high alarm, then set a low TT for ... minutes.
Ce script va écouter le canal de notification xDrip+. Si une alerte glycémie haute spécifiée par l'utilisateur est déclenchée, alors Automate définira une cible temp basse ayant un niveau et une durée spécifiée par l'utilisateur. Après un certain temps, une autre alerte prolongera si nécessaire la durée de la CT faible.

##### xDrip+
Vous devez d'abord ajouter une alerte haute dans xDrip + comme ceci :

![xDrip+ alert settings](../images/automate-xdrip1.png)

Nom de l'alerte : (Faire attention à lui !) Ce nom est essentiel pour déclencher le script. Il doit être clair et ne pas être similaire à tous les autres noms d'alertes. Par exemple : '180alarm' ne doit pas exister à côté d'une alerte '80alarm'.

Seuil : valeur GLY qui doit déclencher l'alerte élevé.

Snooze par défaut : renseignez la durée souhaitée de votre CT ici, comme cela si après cette durée l'alerte revient à nouveau, cela prolongera peut-être la durée du CT faible.

![xDrip+ alert settings](../images/automate-xdrip2.png)

##### Automate
Secondly, download the Automate script [https://llamalab.com/automate/community/flows/27809](https://llamalab.com/automate/community/flows/27809).

Edit the sling by tapping on the edit pencil > Flowchart

![Automate sling](../images/automate-app3.png)

Personnaliser le script en fonction de vos souhaits comme ceci :

Dans le déclencheur 'Notification posted?', vous devez mettre dans 'Title' le nom de l'alerte xDrip+ qui doit déclencher le script et ajouter un caractère * avant et après ce nom.

![Automate sling](../images/automate-app7.png)


![Automate sling](../images/automate-app4.png)

URL de la requête : Votre URL-NS se terminant par /api/v1/treatments.json (par ex. https://my-cgm.herokuapp.com/api/v1/treatments.json)

Contenu de la requête :
* targetTop / targetBottom : la valeur de la CT faible (les 2 doivent avoir la même valeur)
* duration : la durée de votre CT faible (après cette durée AAPS reviendra à la cible standard de votre profil). Il est recommandé de mettre la même valeur que 'Snooze par défaut' de l'alerte xDrip+
* secret : votre hachage SHA1 de l'API. Ce n'est PAS votre clé api ! You can convert your API key to SHA1 format at [http://www.sha1-online.com/](http://www.sha1-online.com/)

Save: Tap on 'Done' and on the hook

Start sling: Tap on Play button




#### Exemple 3: À vous de l'ajouter !!!
Please add further workflows by uploading .flo file to Automate community (under the keyword 'Nightscout') and describe it here by doing [Pull Request on AndroidAPSDocs repository](../SupportingAaps/HowToEditTheDocs.md).



## IF This, Then That (IFTTT)
N'hésitez pas à ajouter une aide sur comment faire avec un PR... 
