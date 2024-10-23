# Pompe DanaRS et Dana-i

_These instructions are for configuring the app and your pump if you have a DanaRS from 2017 onwards or the newer Dana-i. Visit [DanaR Insulin Pump](./DanaR-Insulin-Pump.md) if you have the original DanaR instead._

**New Dana RS firmware v3 can be used from AAPS version 2.7 onwards.**

**New Dana-i can be used from AAPS version 3.0 onwards.**

* Sur la pompe DanaRS/i, pompe « BASAL A » est utilisé par l'application. Les données existantes se font écrasé.

(DanaRS-Insulin-Pump-pairing-pump)=
## Appairage de la pompe

* Sur l'écran d'accueil AAPS, cliquez sur le menu hamburger en haut à gauche et allez dans la Configuration.
* Dans la section Pompe, sélectionnez 'Dana-i/RS'.
* Cliquez sur la roue crantée pour accéder directement aux paramètres de la pompe ou retourner à l'écran d'accueil.

  ![AAPS config builder Dana-i/RS](../images/DanaRS_i_ConfigB.png)

* Allez dans l'onglet 'DANA-i/RS'.
* Sélectionnez le Menu des préférences en appuyant sur le menu 3 points en haut à droite.
* Sélectionnez 'Préférences Dana-i/R'.
* Cliquez sur "Pompe sélectionnée".
* Dans la fenêtre d'appairage, cliquez sur l'entrée correspondant à votre pompe.

  ![AAPS pair Dana-i/RS](../images/DanaRS_i_Pairing.png)

* **You have to confirm the pairing on the pump!** That's just the way you are used to from other bluetooth pairings (i.e. smartphone and car audio).

  ![Dana RS confirmation pairing](../images/DanaRS_Pairing.png)

* Suivez le processus d'appairage basé sur le type et le firmware de votre pompe :

   * Pour DanaRS v1, sélectionnez le mot de passe de la pompe dans les préférences et définissez votre mot de passe.
   * Pour DanaRS v3, vous devez taper 2 séquences de chiffres et de lettres affichées sur la pompe dans la boîte de dialogue d'appairage AAPS.
   * Pour Dana-i la boîte de dialogue d'appairage standard Android apparaît et vous devez entrer le numéro à 6 chiffres affiché sur la pompe.

* Sélectionner la vitesse de Bolus pour changer la vitesse de Bolus par défaut souhaitée (12 sec par 1 U, 30 sec par 1 U ou 60 sec par 1 U).
* Régler l'incrément Basale sur pompe à 0,01 U/h en utilisant le menu Médecin (voir le guide de l’utilisateur de la pompe).
* Régler l'incrément Bolus sur la pompe à 0,05 U/h en utilisant le menu de Médecin (voir le guide de l’utilisateur de la pompe).
* Activez les Bolus Étendus sur la pompe

(DanaRS-Insulin-Pump-default-password)=

### Mot de passe par défaut

* Pour les DanaRS avec le firmware v1 et v2, le mot de passe par défaut est 1234.
* Pour DanaRS avec firmware v3 ou Dana-i, le mot de passe par défaut est dérivé de la date de fabrication et calculé en tant que MMDD où MM est le mois et DD est le jour de production de la pompe (par exemple '0124' représentant le mois 01 et le jour 24).

  * À partir du MENU PRINCIPAL, sélectionnez REVISION puis ouvrez INFORMATIONS D'EXPÉDITION dans le sous-menu
  * Le numéro 3 est la date de fabrication.
  * Pour v3/i, ce mot de passe est utilisé uniquement pour verrouiller le menu sur la pompe. Il n'est pas utilisé pour la communication et il n'est pas nécessaire de le saisir dans AAPS.

(DanaRS-Insulin-Pump-change-password-on-pump)=
## Changer de mot de passe sur la pompe

* Appuyez sur le bouton OK de la pompe
* Dans le menu principal, sélectionnez "OPTION" (déplacer à droite en appuyant sur le bouton flèche plusieurs fois)

  ![DanaRS Main Menu](../images/DanaRSPW_01_MainMenu.png)

* Dans le menu Options, sélectionnez "OPTION UTILISATEUR"

  ![DanaRS Option Menu](../images/DanaRSPW_02_OptionMenu.png)

* Utilisez le bouton flèche pour faire défiler vers le bas jusqu'à " 11. Mot de passe "

  ![DanaRS 11. Password](../images/DanaRSPW_03_11PW.png)

* Appuyez sur OK pour saisir l'ancien mot de passe.

* Enter **old password** (Default password see [above](#default-password)) and press OK

  ![DanaRS Enter old password](../images/DanaRSPW_04_11PWenter.png)

* Si un mauvais mot de passe est entré ici, il n'y aura pas de message indiquant l'échec !
* Set **new password** (Change numbers with + & - buttons / Move right with arrow button).

  ![DanaRS New password](../images/DanaRSPW_05_PWnew.png)

* Confirmez avec le bouton OK.
* Appuyez sur OK pour enregistrer les paramètres.

  ![DanaRS Save new password](../images/DanaRSPW_06_PWnewSave.png)

* Déplacer vers le bas jusqu'à "14. QUITTEZ" et appuyez sur le bouton OK pour fermer.

  ![DanaRS Exit](../images/DanaRSPW_07_Exit.png)

(DanaRS-Insulin-Pump-dana-rs-specific-errors)=
## Erreurs spécifiques à DanaRS

### Erreur lors de la distribution de l'insuline
Dans le cas où la connexion entre AAPS et DanaRS est perdue pendant un bolus d'insuline (par ex. vous vous éloignez de votre téléphone alors que la DanaRS est en train de délivrer de l'insuline), vous verrez le message suivant et vous entendrez une alarme sonore.

![Alarm insulin delivery](../images/DanaRS_Error_bolus.png)

* Dans la plupart des cas c'est juste un problème de communication et la quantité d'insuline délivrée est correcte.
* Check in pump history (either on the pump or through Dana tab > pump history > boluses) if correct bolus is given.
* Delete error entry in [treatments tab](../DailyLifeWithAaps/AapsScreens.md#carb-correction) if you wish.
* Le montant réel est lu et enregistré lors de la prochaine connexion. Pour forcer cette mise à jour, appuyez sur l'icône BT dans l'onglet dana ou attendez juste la prochaine connexion.

## Remarque spéciale lors du changement de téléphone

Lors du passage à un nouveau téléphone, les étapes suivantes sont nécessaires :
* [Export settings](../Maintenance/ExportImportSettings.md) on your old phone
* Transférez les paramètres de l'ancien vers le nouveau téléphone

### DanaRS v1
* **Manually pair** Dana RS with the new phone
* Comme les paramètres de connexion de la pompe sont également importés dans AAPS sur votre nouveau téléphone, il va déjà "connaître" la pompe et donc ne démarrera pas une analyse bluetooth. Par conséquent, le nouveau téléphone et la pompe doivent être appairés manuellement.
* Installez AAPS sur le nouveau téléphone.
* [Import settings](../Maintenance/ExportImportSettings.md) on your new phone

### DanaRS v3, Dana-i
* Start pairing procedure like decribed [above](#pairing-pump).
* Il est parfois nécessaire d'effacer les informations d'appairage dans AAPS en faisant un clic long sur l'icône BT dans l'onglet Dana-i/RS.

## Voyager avec différents fuseaux horaires avec la pompe DanaR

For information on traveling across time zones see section [Timezone traveling with pumps](../DailyLifeWithAaps/TimezoneTraveling-DaylightSavingTime.md#danarv2-danars).
