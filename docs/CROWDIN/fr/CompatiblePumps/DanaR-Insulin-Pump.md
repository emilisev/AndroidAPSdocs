# Pompe DanaR

_These instructions are for configuring the app and your pump if you have a DanaR.  Visit [DanaRS Insulin Pump](./DanaRS-Insulin-Pump.md) if you have the DanaRS launched in 2017 instead._

* In the pump go to Main Menu > Setting > User Option
* Activer "8. Bolus étendu"

![DanaR pump](../images/danar1.png)

* Go to Main Menu > Setting > Discovery
* Dans le menu Paramètres du téléphone, aller à Bluetooth, scanner les périphériques proches, sélectionner et entrer le numéro de série de votre DanaR et saisir votre mot de passe (le mot de passe de l’appairage est 0000).  Si la DanaR n’apparaît pas en scannant, alors redémarrer le téléphone et enlever la batterie de la DanaR , replacer la et recommencer ces deux étapes.

* Dans AndroidAPS, allez dans la Configuration et sélectionnez le modèle de DanaR que vous possédez (DanaR, DanaR coréenne ou DanaRv2)
* Sélectionnez le Menu en appuyant sur les 3 points en haut à droite. Sélectionnez le menu Préférences.
* Sélectionnez le périphérique Bluetooth Dana R, puis cliquez sur votre numéro de série de DanaR.
* Rentrer le mot de passe de la pompe et saisir votre mot de passe. (le mot de passe par défaut est 1234)
* If you want AAPS to allow basal rate above 200%, enable Use extended boluses for >200%. Notez que cela signifie que vous ne pouvez pas opérer en boucle avec des traitements Cible Temporaire Haute tout en utilisant des bolus prolongés pour se nourrir.
* Dans le menu Préférences sous paramètres de pompe de DanaR, vous pouvez modifier la vitesse de bolus par défaut utilisée (12 sec par 1 Unité, 30 sec par 1 Unité ou 60 sec par 1 Unité).
* Régler l'incrément basal sur la pompe à 0.01 U/h
* Régler l'incrément bolus sur la pompe à 0,1 U/h
* Activez les Bolus Étendus sur la pompe

## Voyager avec différents fuseaux horaires avec la pompe DanaR

For information on traveling across time zones see section [Timezone traveling with pumps](../DailyLifeWithAaps/TimezoneTraveling-DaylightSavingTime.md#danarv2-danars).
