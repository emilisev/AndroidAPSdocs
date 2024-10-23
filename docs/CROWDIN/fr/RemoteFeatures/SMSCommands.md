# Commandes SMS

```{admonition} Documentation
:class: note

This section may contain outdated content. Please also see the page [SMS Commands](../RemoteFeatures/RemoteControl.md#1-sms-commands)).

```

## La sécurité avant tout
.
- AAPS vous permet de controler le téléphone d’un enfant à distance via un SMS. Si vous activez le Communicateur SMS, rappelez-vous toujours que le téléphone configuré pour donner des commandes distantes pourrait être volé. Donc, toujours le protéger au minimum par un code PIN. Un mot de passe robuste ou une identification biométrique sont recommandés.
- Additionally it is recommended to allow a [second phone number](../RemoteFeatures/SMSCommands.md#authorized-phone-numbers) for SMS commands. So you can use second number to [temporary disable](../RemoteFeatures/SMSCommands.md#other) SMS communicator in case your main remote phone gets lost or stolen.
- AAPS vous informera également par SMS si vos commandes à distance, comme un bolus ou un changement de profil, ont été effectuées. Il est conseillé de le configurer de sorte que les SMS de confirmation soient envoyés à au moins deux numéros de téléphone différents au cas où l'un des téléphones destinataires serait volé.
- **If you bolus through SMS Commands you must enter carbs through Nightscout (AAPSClient, Website...)!** If you fail to do so IOB would be correct with too low COB potentially leading to not performed correction bolus as AAPS assumes that you have too much active insulin.
- Depuis AndroidAPS version 2.7, une application d'authentification avec un mot de passe à usage unique basé sur l'heure doit être utilisée pour augmenter la sécurité lors de l'utilisation des commandes SMS.

## Paramétrer les commandes SMS

![SMS Commands Setup](../images/SMSCommandsSetup.png)

- Most of the adjustments of temp targets, following AAPS etc. can be done on [AAPSClient app](../RemoteFeatures/RemoteMonitoring.md) on an Android phone with an internet connection.
- Les bolus ne peuvent pas être donnés à partir de Nightscout, mais vous pouvez utiliser des commandes SMS.
- Si vous utilisez un iPhone comme suiveur (follower) et ne pouvez donc pas utiliser AAPSClient il y a des commandes SMS supplémentaires disponibles.
- In your android phone setting go to Applications > AndroidAPS > Permissions and enable SMS

### Numéros de tél autorisés

- In AAPS go to **Preferences > SMS Communicator** and enter the phone number(s) that you will allow SMS commands to come from (separated by semicolons - i.e. +6412345678;+6412345679)

- Notez que le "+" devant le numéro peut être nécessaire ou non en fonction de votre localisation. Pour déterminer cela, envoyez un exemple de texte qui montrera le format reçu dans l'onglet Communicator SMS.

- Activez 'Autoriser les commandes distantes par SMS'.

- Si vous voulez utiliser plus d'un numéro :

  - Entrez seulement un numéro.

  - Vérifiez le bon fonctionnement de ce numéro unique en envoyant et en confirmant une commande SMS.

  - Entrez le(s) numéro(s) supplémentaire(s) séparé(s) par un point-virgule, pas d'espace.

    ![SMS Commands Setup multiple numbers](../images/SMSCommandsSetupSpace2.png)

### Délai entre les commandes bolus

- Vous pouvez définir un délai minimum entre deux bolus envoyés par SMS.
- Pour des raisons de sécurité, vous devez ajouter au moins deux numéros de téléphone autorisés pour modifier cette valeur.

### Code PIN obligatoire à la fin de l'OTP

- Pour des raisons de sécurité, le code de réponse doit être suivi d'un code PIN.

- Règles du code PIN :

  - 3 à 6 chiffres
  - ne pas utiliser les mêmes chiffres (par ex. 1111)
  - ne pas utiliser des chiffres qui se suivent (par ex. 1234)

### Configuration de l'Authentificateur

- L'authentification à deux facteurs est utilisée pour améliorer la sécurité.

- Vous pouvez utiliser n'importe quelle application d'authentification qui prend en charge les jetons TOTP RFC 6238. Les applications gratuites populaires sont :

  - [Authy](https://authy.com/download/)
  - Google Authenticator - [Android](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2) / [iOS](https://apps.apple.com/de/app/google-authenticator/id388497605)
  - [LastPass Authenticator](https://lastpass.com/auth/)
  - [FreeOTP Authenticator](https://freeotp.github.io/)

- Installez l'application d'authentification de votre choix sur votre téléphone follower et scannez le QR code affiché dans AAPS.

- Testez le mot de passe à usage unique en entrant le jeton affiché dans votre application d'authentification et le code PIN que vous venez de configurer dans AAPS. Par exemple :

  - Votre code PIN obligatoire est 2020
  - Le jeton TOTP de l'application d'authentification est 457051
  - Entrez 4570512020

- The red text "WRONG PIN" will change **automatically** to a green "OK" if the entry is correct. **There is no button you can press!**

- L'heure des deux téléphones doit être synchronisée. Les mieux est de définir l'heure automatiquement à partir du réseau. Les différences d'heures peuvent entraîner des problèmes d'authentification.

- Utilisez le bouton "RESET AUTHENTICATORS" si vous voulez supprimer les autorisations effectuées.  (En réinitialisant l'authentificateur, vous rendez TOUS les authentificateurs déjà configurés non valides. Vous devrez les configurer à nouveau)

## Utiliser les commandes SMS

- Send a SMS to the phone with AAPS running from your approved phone number(s) using any of the [commands](#commands) below.

- Le téléphone AAPS répondra pour confirmer le succès de la commande ou du statut demandé.

- Confirmez la commande en envoyant le code si nécessaire. Par exemple :

  - Votre code PIN obligatoire est 2020
  - Le jeton TOTP de l'application d'authentification est 457051
  - Entrez 4570512020

**Hint**: It can be useful to have unlimited SMS on your phone plan (for each phone used) if a lot of SMS will be sent.

## Commandes

Commands must be sent in English, the response will be in your local language if the response string is already [translated](../SupportingAaps/Translations#translate-strings-for-aaps-app).

![SMS Commands Example](../images/SMSCommands.png)

### Loop

- LOOP STOP/DISABLE \* Response: Loop has been disabled

- LOOP START/ENABLE \* Response: Loop has been enabled

- LOOP STATUS

  - La réponse dépend du statut réel

    - La Boucle est désactivée
    - La Boucle est activée
    - Suspendu (10 min)

- LOOP SUSPEND 20 \* Response: Loop suspended for 20 minutes

- LOOP RESUME \* Response: Loop resumed

- LOOP CLOSED \* Response: Current loop mode: Closed Loop

- LOOP LGS \* Response: Current loop mode: Low Glucose Suspend

### Données MGC

- BG \* Response: Last BG: 5.6 4min ago, Delta: -0,2 mmol, IOB: 0.20U (Bolus: 0.10U Basal: 0.10U)
- CAL 5.6 \* Response: To send calibration 5.6 reply with code from Authenticator app for User followed by PIN \* Response after correct code was received: Calibration sent (**If xDrip is installed. Accepting calibrations must be enabled in xDrip+**)

### Basal

- BASAL STOP/CANCEL \* Response: To stop temp basal reply with code from Authenticator app for User followed by PIN
- BASAL 0.3 \* Response: To start basal 0.3U/h for 30 min reply with code from Authenticator app for User followed by PIN
- BASAL 0.3 20 \* Response: To start basal 0.3U/h for 20 min reply with code from Authenticator app for User followed by PIN
- BASAL 30% \* Response: To start basal 30% for 30 min reply with code from Authenticator app for User followed by PIN
- BASAL 30% 50 \* Response: To start basal 30% for 50 min reply with code from Authenticator app for User followed by PIN

### Bolus

Un bolus à distance n'est pas possible dans les 15 minutes suivant le dernier bolus dans AAPS ou à distance (vous ne pouvez ajuster la durée que si au moins 2 numéros de téléphone sont entrés) ! La réponse dépend donc du moment où le dernier bolus a été administré.

- BOLUS 1.2 \* Response A: To deliver bolus 1.2U reply with code from Authenticator app for User followed by PIN \* Response B: Remote bolus not available. Réessayez plus tard.
- BOLUS 0.60 MEAL \* If you specify the optional parameter MEAL, this sets the Temp Target MEAL (default values are: 90 mg/dL, 5.0 mmol/l for 45 mins). \* Response A: To deliver meal bolus 0.60U reply with code from Authenticator app for User followed by PIN \* Response B: Remote bolus not available.
- CARBS 5 \* Response: To enter 5g at 12:45 reply with code from Authenticator app for User followed by PIN
- CARBS 5 17:35/5:35PM \* Response: To enter 5g at 17:35 reply with code from Authenticator app for User followed by PIN
- EXTENDED STOP/CANCEL \* Response: To stop extended bolus reply with code from Authenticator app for User followed by PIN
- EXTENDED 2 120 \* Response: To start extended bolus 2U for 120 min reply with code from Authenticator app for User followed by PIN

### Profile

- PROFILE STATUS \* Response: Profile1
- PROFILE LIST \* Response: 1.\`Profile1\` 2.\`Profile2\`
- PROFILE 1 \* Response: To switch profile to Profile1 100% reply with code from Authenticator app for User followed by PIN
- PROFILE 2 30 \* Response: To switch profile to Profile2 30% reply with code from Authenticator app for User followed by PIN


### Autres

- TREATMENTS REFRESH \* Response: Refresh treatments from NS
- NSClient RESTART \* Response: NSCLIENT RESTART SENT
- PUMP \* Response: Last conn: 1 min ago Temp: 0.00U/h @11:38 5/30min IOB: 0.5U Reserv: 34U Batt: 100
- PUMP CONNECT \* Response: Pump reconnected
- PUMP DISCONNECT *30* \* Response: To disconnect pump for *30* minutes reply with code from Authenticator app for User followed by PIN
- SMS DISABLE/STOP \* Response: To disable the SMS Remote Service reply with code Any. Gardez à l'esprit que vous ne pourrez le réactiver que directement à partir de l'application AAPS du smartphone maitre.
- TARGET MEAL/ACTIVITY/HYPO \* Response: To set the Temp Target MEAL/ACTIVITY/HYPO reply with code from Authenticator app for User followed by PIN
- TARGET STOP/CANCEL \* Response: To cancel Temp Target reply with code from Authenticator app for User followed by PIN
- HELP \* Response: BG, LOOP, TREATMENTS, .....
- HELP BOLUS \* Response: BOLUS 1.2 BOLUS 1.2 MEAL

## Troubleshooting

### SMS multiples

Si vous recevez toujours le même message (par ex. changement de profil) vous avez probablement mis en place une boucle infinie avec d'autres applications. Cela peut être xDrip+, par exemple. Si c'est le cas, assurez-vous que xDrip+ (ou toute autre application) ne télécharge pas les traitements dans NS.

Si l'autre application est installée sur plusieurs téléphones assurez-vous de désactiver le téléchargement NS sur chacun d'eux.

### Les commandes SMS ne fonctionnent pas sur les téléphones Samsung

Il y a eu un signalement sur les commandes SMS s'arrêtant après une mise à jour sur le téléphone Galaxy S10. Peut être résolu en désactivant 'envoyer en tant que message chat'.

![Disable SMS as chat message](../images/SMSdisableChat.png)
### Application de messages Android

Si vous rencontrez des problèmes pour envoyer ou recevoir des commandes par SMS avec l'application Messages Android, désactivez le cryptage de bout en bout à la fois sur les téléphones des soignants et des enfants.
 - ouvrir la conversation SMS spécifique dans les Messages
 - Sélectionner les paramètres dans le coin supérieur droit
 - sélectionnez "Détails"
 - Activer "Envoyer uniquement les SMS et les MMS"
