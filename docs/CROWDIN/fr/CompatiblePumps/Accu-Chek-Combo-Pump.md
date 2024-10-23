# Pompe Accu-Chek Combo

**This software is part of a DIY solution and is not a product, but requires YOU to read, learn and understand the system including how to use it. Ce logiciel ne fait pas toute la gestion de votre diabète pour vous, mais il peut améliorer votre diabète et votre qualité de vie si vous êtes prêt à y consacrer le temps nécessaire. Ne vous précipitez pas, mais laissez vous le temps d’apprendre. You alone are responsible for what you do with it.**

(Accu-Chek-Combo-Pump-hardware-requirements)=
## Configuration matérielle requise

* Une pompe Roche Accu-Chek Combo (avec n’importe quel firmware, ils fonctionnent tous)
* Un dispositif Accu-Chek Smartpix V1 ou Accu-Chek Realtyme, ainsi que le logiciel de configuration Accu-Chek 360. (Sur demande Roche envoie gratuitement ces dispositifs Smartpix et la configuration logiciel à leurs clients, sauf en France ou il faut contacter son prestataire).
* Un téléphone compatible : un smarphone Android avec comme système LineageOS 14.1 (anciennement CyanogenMod) ou Android 8.1 (Oreo). Depuis AAPS 3.0, Android 9 est obligatoire. See [release notes](../Maintenance/ReleaseNotes.md#android-version-and-aaps-version) for details.
* Avec LineageOS 14.1, il doit être une version récente d’au moins juin 2017 car les changements nécessaires pour se connecter à la pompe Combo ont été mis en œuvre seulement à ce moment-là.
* A list of phones can be found in the [AAPS Phones](https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit) document.
* Cette liste n’est pas une liste complète. Elle reflète l’expérience personnelle de quelques utilisateurs. Nous vous encourageons à partager également votre expérience et ainsi aider les autres.
* Ayez bien en tête que bien qu'Android 8.1 autorise la communication avec le Combo, il y a toujours des problèmes avec AAPS sur 8.1.
* Pour les utilisateurs avancés, il est possible d'effectuer l'appairage sur un téléphone rooté et de le transférer vers un autre téléphone qui doit également être rooté pour l'utiliser avec Ruffy/AAPS. This allows using phones with Android < 8.1 but has not been widely tested: https://github.com/gregorybel/combo-pairing/blob/master/README.md

## Limitations

* Extended bolus and multiwave bolus are not supported (see [Extended Carbs](../DailyLifeWithAaps/ExtendedCarbs.md) instead).
* Seulement un profil de basal est pris en charge.
* Sélectionner un profil de basal autre que 'Basal1' sur la pompe, ou délivrer via la pompe des bolus 'carré' et 'mixte', interfère avec les DBT et force la boucle en mode 'AGB' pendant 6 heures car la boucle ne peut pas fonctionner en toute sécurité dans ces conditions.
* It's currently not possible to set the time and date on the pump, so [daylight saving time changes](../DailyLifeWithAaps/TimezoneTraveling-DaylightSavingTime.md#time-adjustment-daylight-savings-time-dst) have to be performed manually (you may disable the phone's automatic clock update in the evening and change it back in the morning together with the pump clock to avoid an alarm during the night).
* Actuellement, seuls les débits de basals de 0,05 à 10 U/h sont supportés. Ceci s'applique également lors de la modification du profil, par exemple, lorsqu'il augmente à 200%, le taux basal le plus élevé ne doit pas dépasser 5 U/h car il sera doublé. De même, en réduisant à 50%, le taux basal le plus bas doit être au moins 0,10 U/h.
* Si la boucle demande l'annulation d'un DBT en cours, le Combo fixera un DBT de 90% ou 110% pendant 15 minutes à la place. C'est parce que l'annulation d'un DBT provoque une alerte sur la pompe qui cause beaucoup de vibrations.
* Occasionnellement (tous les deux jours ou plus), AndroidAPS risque de ne pas annuler automatiquement une alerte 'TBR CANCELLED', donc l’utilisateur doit s’en occuper (en appuyant sur le bouton actualiser dans AndroidAPS afin de transférer l’alarme à AAPS, ou en confirmant l’alerte sur la pompe).
* La stabilité de la connexion Bluetooth varie en fonction des téléphones utilisés. La perte de connection provoque des alertes "pompe injoignable", pendant laquelle aucune connexion avec la pompe n'est établie.
* Si cette erreur survient, assurez-vous que Bluetooth est activé, puis appuyez sur le bouton Rafraichir dans l'onglet Combo pour voir si cela a été causé par un problème intermittent. Si aucune connexion n'est encore établie, le redémarrage du téléphone devrait normalement corriger cela.
* Il y a une autre solution si le redémarrage du téléphone n'a pas aidé. Il s'agit de presser un bouton sur la pompe (pour réinitialiser le Bluetooth de la pompe) afin que celle-ci accepte de nouveau les connexions du téléphone.
* A ce stade, il n’y a plus de solution pour remédier à la perte de connections. Si vous voyez souvent ces erreurs, votre seule option est d'acquérir un autre téléphone connu pour fonctionner correctement avec AAPS et le Combo (voir ci-dessus).
* Un bolus délivré à partir de la pompe ne sera pas toujours détecté immédiatement (il faut vérifier à chaque fois qu'AndroidAPS est bien connecté à la pompe), et cela peut prendre jusqu'à 20 minutes dans le pire des cas.
* Les bolus sur la pompe sont toujours vérifiés avant un DBT élevé ou un bolus délivré par AAPS, mais en raison des limitations, AAPS refusera ensuite de délivrer le DBT/Bolus comme il a été calculé sous de fausses prédictions. (-> Don't bolus from the Pump! See chapter [Usage](#usage) below)
* Le paramétrage d'un DBT sur la pompe doit être évité puisque la boucle assure le contrôle des DBT. La détection d'un nouveau DBT sur la pompe peut prendre jusqu'à 20 minutes et l'effet du DBT est seulement comptabilisé à l’instant où il est détecté, donc dans le pire des cas, il peut y avoir 20 minutes d’un DBT qui n’est pas pris en compte dans l’IA.

## Paramètres

* Configurez la pompe en utilisant le logiciel de configuration Accu-Chek 360.
* Si vous n’avez pas le logiciel, veuillez contacter votre prestataire en france ou la hotline Accu-Chek dans les autres pays. Ils envoient généralement aux utilisateurs enregistrés un CD ou une clé USB avec le logiciel de configuration de la pompe et un périphérique de connexion infrarouge USB SmartPix (le périphérique Realtyme fonctionne aussi si vous en avez).
* **Required settings** (marked green in screenshots):

   * Choisissez ou laissez la configuration du menu sur "Standard", cela affichera uniquement les menus et actions pris en charge sur la pompe, et masquera ceux qui ne sont pas supportés par AAPS (bolus duo/carré, débits de base multiples) et qui entraînent une limitation du fonctionnement de la boucle lors de leurs utilisation, et donc ne permet pas une exécution sécurisée de la boucle.
   * Verify the _Quick Info Text_ is set to "QUICK INFO" (without the quotes, found under _Insulin Pump Options_).
   * Set TBR _Maximum Adjustment_ to 500%
   * Disable _Signal End of Temporary Basal Rate_
   * Set TBR _Duration increment_ to 15 min
   * Activez le Bluetooth

* **Recommended settings** (marked blue in screenshots)

   * Définissez une alarme de cartouche basse à votre convenance
   * Configurez un bolus max adapté à votre thérapie afin de se protéger contre les bugs logiciel et matériel
   * De même, configurez une durée maximale de débit de basal temporaire DBT en tant que protection. Autorisez au moins 3 heures, puisque l'option de déconnecter la pompe pendant 3 heures défini un DBT à 0% pendant 3 heures.
   * Activez le verrouillage des touches sur la pompe pour empêcher les bolus via la pompe, surtout si la pompe a déjà été utilisée et que vous aviez l'habitude d'utiliser les bolus rapides.
   * Définissez un délai d'affichage et de menu aux valeurs minimales respectivement de 5,5s et 5s. Cela permet à AAPS de récupérer plus rapidement de situations d’erreur et réduit la quantité de vibrations qui peuvent se produire pendant ces erreurs.

![Screenshot of user menu settings](../images/combo/combo-menu-settings.png)

![Screenshot of TBR settings](../images/combo/combo-tbr-settings.png)

![Screenshot of bolus settings](../images/combo/combo-bolus-settings.png)

![Screenshot of insulin cartridge settings](../images/combo/combo-insulin-settings.png)

- Install AAPS as described in the [AAPS wiki](https://androidaps.readthedocs.io/)
- Assurez vous de bien lire le wiki pour comprendre comment configurer AAPS.
- Select the MDI plugin in AAPS, not the Combo plugin at this point to avoid the Combo plugin from interfering with ruffy during the pairing process.
- Clone ruffy via git from [MilosKozak/ruffy](https://github.com/MilosKozak/ruffy). At the moment, the primary branch is the `combo` branch, in case of problems you might also try the 'pairing' branch (see below).
- Construisez et Installez Ruffy et utilisez le pour appairer la pompe. If it doesn't work after multiple attempts, switch to the `pairing` branch, pair the pump and then switch back the original branch. If the pump is already paired and can be controlled via ruffy, installing the `combo` branch is sufficient. Note that the pairing processing is somewhat fragile (but only has to be done once) and may need a few attempts; quickly acknowledge prompts and when starting over, remove the pump device from the Bluetooth settings beforehand. Another option to try is to go to the Bluetooth menu after initiating the pairing process (this keeps the phone's Bluetooth discoverable as long as the menu is displayed) and switch back to ruffy after confirming the pairing on the pump, when the pump displays the authorization code. Si vous n’avez pas réussi l’appairage de la pompe (disons après 10 tentatives), essayez d’attendre jusqu'à 10s avant de confirmer l’appairage sur la pompe (lorsque le nom du téléphone est affiché sur la pompe). Si vous avez configuré ci-dessus le délai d'affichage du menu à 5s, vous devez l'augmenter à nouveau. Certains utilisateurs ont signalé qu'ils avaient eu besoin de le faire. Enfin, envisagez de passer dans une autre pièce en cas d’interférence avec des ondes radio. Au moins un utilisateur a immédiatement résolu les problèmes d'appairage en changeant simplement de pièce.
- Quand AAPS utilise Ruffy, l'application Ruffy ne peut pas être utilisée. The easiest way is to just reboot the phone after the pairing process and let AAPS start ruffy in the background.
- Si la pompe est complètement nouvelle, vous devez faire un bolus sur la pompe pour que celle-ci crée une première entrée dans l'historique.
- Before enabling the Combo plugin in AAPS make sure your profile is set up correctly and activated(!) and your basal profile is up to date as AAPS will sync the basal profile to the pump. Ensuite, activez le plugin Combo. Press the _Refresh_ button on the Combo tab to initialize the pump.
- To verify your setup, with the pump **disconnected**, use AAPS to set a TBR of 500% for 15 min and issue a bolus. La pompe doit normalement avoir un DBT en cours et un bolus dans l'historique. AAPS doit aussi de son côté montrer le DBT actif et le bolus délivré.

(Accu-Chek-Combo-Pump-why-pairing-with-the-pump-does-not-work-with-the-app-ruffy)=
## Pourquoi l'appairage avec la pompe ne fonctionne pas avec l'application "Ruffy"?
Il y a plusieurs raisons possibles. Essayez les étapes suivantes :

1.  Insert a **fresh or full battery** into the pump. Consultez la section "Considérations relatives à la pile" pour plus de détails. Assurez-vous que la pompe est très proche du smartphone.

![Combo should be next to phone](../images/Combo_next_to_Phone.png)

2. Désactivez ou supprimez tous les autres périphériques bluetooth afin qu'ils ne soient pas en mesure d'établir une connexion au téléphone pendant que l'appairage est en cours. Toute communication bluetooth parallèle ou demande de connexions peut perturber le processus d'appairage.

3.  Delete already connected devices in the Bluetooth menu of the pump: **BLUETOOTH SETTINGS / CONNECTION / REMOVE** until **NO DEVICE** is shown.
4.  Delete a pump already connected to the phone via Bluetooth: Under Settings / Bluetooth, remove the paired device "**SpiritCombo**"
5.  Assurez-vous que AAPS n'exécute pas la boucle en arrière-plan. Désactiver la boucle dans AAPS.
6.  Try using the '**pairing**' branch from the [MilosKozak/ruffy](https://github.com/MilosKozak/ruffy/tree/pairing) repository to establish the connection
7.  Maintenant, démarrez ruffy sur le téléphone. Vous pouvez appuyer sur Reset! et supprimez l'ancienne connexion. Then hit **Connect!**.
8.  In the Bluetooth menu of the pump, go to **ADD DEVICE / ADD CONNECTION**. Appuyez sur **CONNECTER !**
    * Les trois étapes suivantes sont sensibles au timing, donc vous devrez essayer différentes pauses / vitesses si le jumelage échoue. Lisez la séquence complète avant de l'essayer.
9.  A présent, la pompe doit afficher le nom BT du téléphone à sélectionner pour l'appairage. Here it is importand to wait at least 5s before you hit the select button on Pump. Sinon, la Pompe n'enverra pas correctement la demande d'appairage au téléphone.

    * Si le délai d'affichage de l'écran de la pompe Combo est défini sur 5s, vous pouvez faire le test avec 40s (paramètre d'origine). From experiance the time between pump is showing up in phone until select phone is around 5-10s. In many other cases pairing just times out without successfully pair. Ultérieurement, vous devrez le redéfinir sur 5 s pour répondre aux paramètrage du combo dans AAPS et accélérer les connexions.
    * If the pump does not show the phone as a pairing device at all, your phone's Bluetooth stack is probably not compatible with the pump. Make sure you are running a new **LineageOS ≥ 14.1** or **Android ≥ 8.1 (Oreo)**. If possible, try another smartphone. You can find a list of already successfully used smartphones under \[AAPS Phones\] (https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit#gid=698881435).

10.  Parfois, le téléphone demande un code PIN bluetooth (typiquement 4 chiffres) qui n'est pas lié au PIN à 10 chiffres affiché plus tard sur la pompe. Habituellement, Ruffy défini ce code PIN automatiquement, mais cela ne fonctionne pas toujours. If a request for a Bluetooth pairing PIN appears on the phone before any code is shown on the pump, you need to enter **}gZ='GD?gj2r|B}>** as the PIN. C'est plus facile si vous copiez ce texte de 16 caractères dans le presse-papiers avant de commencer la séquence d'appairage et juste coller dans la boîte de dialogue à cette étape. See related [Github issue](https://github.com/MilosKozak/ruffy/issues/14) for details.
11.  Ensuite la pompe doit afficher un code de sécurité à 10 chiffres, et Ruffy affiche un écran pour le renseigner. And Ruffy shold show a screen to enter it. So enter the code in Ruffy and you should be ready to go.
12.  Si l'appairage a échoué et que vous avez obtenu un message hors délai sur la pompe, vous devrez redémarrer le processus de zéro.
13.  Si vous avez utilisé la branche 'appairage' pour construire l'application Ruffy, installez maintenant la version de version à partir de la branche 'combo' au-dessus de celle-ci. Assurez-vous que vous avez utilisé les mêmes clés lors de la signature des deux versions de l'application pour conserver tous les paramètres et les données, car elles contiennent aussi les propriétés de connexion.
14.  Redémarrer le téléphone.
15.  Maintenant, vous pouvez redémarrer la boucle AAPS.

(Accu-Chek-Combo-Pump)=

## Utilisation

- Keep in mind that this is not a product, esp. in the beginning the user needs to monitor and understand the system, its limitations and how it can fail. It is strongly advised NOT to use this system when the person using it is not able to fully understand the system.
- Read the OpenAPS documentation https://openaps.org to understand the loop algorithm AAPS is based upon.
- Lisez la documentation en ligne pour en savoir plus sur AAPS https://androidaps.readthedocs.io/
- Cette intégration utilise la même fonctionnalité que le lecteur fournit avec le Combo. Le lecteur permet de reproduire l'écran de la pompe et de transférer à la pompe les appuis sur les touches. The connection to the pump and this forwarding is what the ruffy app does. A `scripter` component reads the screen and automates entering boluses, TBRs etc and making sure inputs are processed correctly. AAPS interagit ensuite avec l'automate pour appliquer les commandes de la boucle et pour administrer des bolus. This mode has some restrictions: it's comparatively slow (but well fast enough for what it is used for), and setting a TBR or giving a bolus causes the pump to vibrate.
- The integration of the Combo with AAPS is designed with the assumption that all inputs are made via AAPS. Boluses entered on the pump directly will be detected by AAPS, but it can take up to 20 min before AAPS becomes aware of such a bolus. Reading boluses delivered directly on the pump is a safety feature and not meant to be regularly used (the loop requires knowledge of carbs consumed, which can't be entered on the pump, which is another reason why all inputs should be done in AAPS).
- Ne faites pas ou n'annulez pas de DBT sur la pompe. La boucle assure le contrôle des DBT et ne peut pas fonctionner de manière fiable autrement, car il n'est pas possible de déterminer l'heure exacte du début d'un DBT qui a été défini par l'utilisateur sur la pompe.
- Le profil 1 de la pompe pour les débits de basal est lu au démarrage de l'application et est mis à jour par AAPS. The basal rate should not be manually changed on the pump, but will be detected and corrected as a safety measure (don't rely on safety measures by default, this is meant to detect an unintended change on the pump).
- It's recommended to enable key lock on the pump to prevent bolusing from the pump, esp. when the pump was used before and using the "quick bolus" feature was a habit. Also, with keylock enabled, accidentally pressing a key will NOT interrupt active communication between AAPS and pump.
- When a BOLUS/TBR CANCELLED alert starts on the pump during bolusing or setting a TBR, this is caused by a disconnect between pump and phone, which happens from time to time. AAPS will try to reconnect and confirm the alert and then retry the last action (boluses are NOT retried for safety reasons). Therefore, such an alarm can be ignored as AAPS will confirm it automatically, usually within 30s (cancelling it is not problem, but will lead to the currently active action to have to wait till the pump's display turns off before it can reconnect to the pump). If the pump's alarm continues, automatic corfirmation failed, in which case the user needs to confirm the alarm manually.
- When a low cartridge or low battery alarm is raised during a bolus, they are confirmed and shown as a notification in AAPS. If they occur while no connection is open to the pump, going to the Combo tab and hitting the Refresh button will take over those alerts by confirming them and show a notification in AAPS.
- When AAPS fails to confirm a TBR CANCELLED alert, or one is raised for a different reason, hitting Refresh in the Combo tab establishes a connection, confirms the alert and shows a notification for it in AAPS. This can safely be done, since those alerts are benign - an appropriate TBR will be set again during the next loop iteration.
- For all other alerts raised by the pump: connecting to the pump will show the alert message in the Combo tab, e.g. "State: E4: Occlusion" as well as showing a notification on the main screen. Une erreur déclenchera une notification urgente. AAPS never confirms serious errors on the pump, but let's the pump vibrate and ring to make sure the user is informed of a critical situation that needs action.
- After pairing, ruffy should not be used directly (AAPS will start in the background as needed), since using ruffy at AAPS at the same time is not supported.
- If AAPS crashes (or is stopped from the debugger) while AAPS and the pump were communicating (using ruffy), it might be necessary to force close ruffy. Le fait de redémarrer AAPS redémarrera à nouveau Ruffy. Restarting the phone is also an easy way to resolve this if you don't know how to force kill an app.
- Don't press any buttons on the pump while AAPS communicates with the pump (Bluetooth logo is shown on the pump).
