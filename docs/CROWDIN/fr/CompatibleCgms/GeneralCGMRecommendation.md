# Recommandations générales MGC

## Hygiène de la MGC

Quel que soit le système CGM que vous utilisez, si vous allez utiliser un calibrage effectué sur le sang, il existe des règles très claires que vous devriez appliquer, que vous utilisiez ou non le logiciel DIY CGM ou les applications officielles.

-   Assurez-vous que vos mains et le kit sont propres.
-   Try to calibrate when you have a series of dots with a flat arrow (15-30 minutes is usually enough)
-   Évitez de calibrer lorsque les glycémie montent ou descendent.
-   Do “enough” calibrations – on official apps, you will be prompted for once or twice per day checks. On DIY systems you may not be, and should be careful about continuing without calibrations.
-   For sensors not requiring or not allowing calibration, check at least daily real blood sugar. AAPS will be as safe as your sensor readings are reliable.
-   If it all possible, calibrate with some of your readings in a lower range (4-5mmol/l or 72-90mg/dl) and some at a slightly higher level (7-9mmol/l or 126-160mg/dl) as this provides a better range for the point/slope calibration.

## Réglage du capteur (G6)

Lors de la mise en place du capteur, il est recommandé de ne pas appuyer trop fermement sur le serteur pour éviter les saignements. The sensor contacts should not come into contact with blood.

Après la mise en place du capteur, l'émetteur peut être cliqué dans son support. Attention ! Cliquez d'abord sur le côté carré, puis appuyez sur le côté rond.

## Troubleshooting

### Problèmes de connexion

La connexion Bluetooth peut être perturbée par d'autres appareils Bluetooth voisins tels que des lecteurs de glycémie, des casques, des tablettes ou des appareils de cuisine tels que des fours à micro-ondes ou des plaques vitrocéramique. Dans ce cas, xdrip n'affiche aucune valeur de Gly. Lorsque la connexion bluetooth est rétablie les données sont comblées.

### Erreurs de capteur

Si des erreurs de capteur récurrentes se produisent, essayez de positionner votre capteur ailleurs sur votre corps. The sensor contacts should not come into contact with blood.

Souvent une "erreur de capteur" peut être corrigée en buvant immédiatement et en massant autour du capteur !

### Saut de valeurs

Vous pouvez essayer de modifier les paramètres de blocage du bruit dans xdrip (Paramètres - Inter-app settings - Noise Blocking) par ex". See also [Smoothing BG data](../Usage/Smoothing-Blood-Glucose-Data-in-xDrip.md).

### Âge du capteur négatif

![Negative sensor age](../images/Troubleshooting_SensorAge.png)

This occurs if there is either a double "CGM Sensor Insert" entry in [actions tab / menu](../DailyLifeWithAaps/AapsScreens.md#action-tab) or a sensor insert with wrong date. Go to treatments tab \> careportal and delete the wrong entry.
