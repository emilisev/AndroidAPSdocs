# Pompe à insuline Diaconn G8

## Appairage Bluetooth de la pompe à insuline

- Cliquez sur le menu hamburger dans le coin supérieur gauche.

![image](../images/DiaconnG8/DiaconnG8_01.jpg)

- Cliquez sur Configuration.

![image](../images/DiaconnG8/DiaconnG8_02.jpg)

- Après avoir sélectionné la pompe Diaconn G8, cliquez sur l'icône Paramètres (roue crantée).

![image](../images/DiaconnG8/DiaconnG8_03.jpg)

- Choisissez la pompe sélectionnée.

![image](../images/DiaconnG8/DiaconnG8_04.jpg)

- Sélectionnez le numéro de modèle de votre pompe à insuline une fois qu'elle apparaît dans la liste.

![image](../images/DiaconnG8/DiaconnG8_05.jpg)

- Il y a deux options pour vérifier votre numéro de modèle :

1. Les 5 derniers chiffres du numéro SN au dos de la pompe.
2. Click on O button > Information > BLE > Last 5 digits.

![image](../images/DiaconnG8/DiaconnG8_06.jpg)

- Une fois que vous avez sélectionné votre pompe, une fenêtre apparaît pour demander un code PIN. Entrez le code PIN affiché sur votre pompe pour terminer la connexion.

 ![image](../images/DiaconnG8/DiaconnG8_07.jpg)

## Contrôle de l'état de la pompe et synchronisation des journaux

- Une fois que votre pompe est connectée, cliquez sur le symbole Bluetooth pour vérifier l'état et synchroniser les journaux.

![image](../images/DiaconnG8/DiaconnG8_08.jpg)

## Dépannage Bluetooth

**What to do in the case of an unstable Bluetooth connection with the pump.**

### Méthode 1) Vérifiez à nouveau la pompe une fois la connexion à AAPS terminée.

- Cliquez sur le menu 3 points en haut à droite.

![image](../images/DiaconnG8/DiaconnG8_09.jpg)

- Cliquez sur Quitter.

![image](../images/DiaconnG8/DiaconnG8_10.jpg)

### Méthode 2) Si la première méthode ne fonctionne pas, déconnectez Bluetooth puis reconnectez-vous.

- Appuyez et maintenez le bouton Bluetooth en haut pendant environ 3 secondes.

![image](../images/DiaconnG8/DiaconnG8_11.jpg)

- Cliquez sur le bouton Réglage de la pompe Diaconn G8 appairée.

![image](../images/DiaconnG8/DiaconnG8_12.jpg)

- Désappairage.

![image](../images/DiaconnG8/DiaconnG8_13.jpg)

- Répétez le processus d'appairage Bluetooth pour la pompe (voir ci-dessus).

## Informations complémentaires

### Réglage des options de pompe Diaconn G8

- Config manager > pump > Diaconn G8 > Settings
- DIACONN G8 at the top> 3 dots button on the top right > Diaconn G8 Preferences

![Diaconn G8 pump options](../images/DiaconnG8/DiaconnG8_14.jpg)

- If the **Log reservoir change** option is activated, the relevant details are automatically uploaded to the careportal when an “Insulin Change” event occurs.
- If the **Log needle change** option is activated, the relevant details are automatically uploaded to the careportal when a “Site Change” event occurs.
- If the **Log tube change** option is activated, the relevant details are automatically uploaded to the careportal when a “Tube Change” event occurs.
- If the **Log battery change** option is activated, the relevant details are automatically uploaded to the careportal when a “Battery Change” event occurs, and the PUMP BATTERY CHANGE button in the ACTION tab is deactivated. (Note: Pour changer la pile, veuillez arrêter toutes les fonctions d'injection en cours avant de continuer.)

![Diaconn G8 actions menu](../images/DiaconnG8/DiaconnG8_15.jpg)

### Fonction Bolus Étendu

- Si vous utilisez un bolus étendu, cela désactivera la boucle fermée.
- See [this page](../DailyLifeWithAaps/ExtendedCarbs.md#why-extended-boluses-wont-work-in-a-closed-loop-environment) for details why extended bolus does not work in a closed loop environment.
