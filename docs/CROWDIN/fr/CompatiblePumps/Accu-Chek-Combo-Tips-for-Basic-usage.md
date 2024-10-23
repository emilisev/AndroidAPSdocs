# Accu-Chek Combo conseils pour une utilisation de base

**NOTE:** Starting with AAPS version 3.2, a [new Combo driver](../CompatiblePumps/Accu-Chek-Combo-Pump-v2.md) (referred to as "combov2" sometimes) has been added. L'ancien pilote est également appelé le "pilote avec Ruffy". Certaines parties de ce document ne s'appliquent qu'à l'ancien pilote. Celles-ci seront annotées en conséquence.

## Comment assurer les opérations en douceur

* Always **carry the smartphone with you**, leave it next to your bed at night. Comme votre pompe peut se poser derrière vous ou sous votre corps pendant que vous dormez, une position plus élevée (sur une tablette ou une étagère) fonctionne mieux.
* Always make sure that the pump battery is as full as possible. See the battery section for tipps regarding the battery.

* (Only applies to the old driver) It is best to **not touch the app ruffy** while the system is running. If the app is started again, the connection to the pump can break off. Once the pump is connected to ruffy, there is no need to re-connect. Even after a restart of the phone, the connection is automatically re-established. If possible, move the app to an unused screen or in a folder on your smartphone so you do not accidentally open it.
* (S'applique uniquement à l'ancien pilote) Si vous ouvrez involontairement l'application Ruffy pendant le bouclage, il est préférable de redémarrer le smartphone immédiatement.
* Whenever possible, only operate the pump via the AAPS app. To facilitate this, activate the key lock on the pump under **PUMP SETTINGS / KEY LOCK / ON**. Ce n'est que lorsque vous changez la pile ou la cartouche qu'il est nécessaire d'utiliser les touches de la pompe.

![Keylock](../images/combo/combo-tips-keylock.png)

## Pompe inaccessible. Que faire ?

### Activer l'alerte pompe inaccessible
* In AAPS, go to **Settings / Local Alarms** and activate **alarm when pump is unreachable** and set **pump not reachable limit [Min]** to **31** minutes.
* Cela vous donnera suffisamment de temps pour ne pas déclencher l'alarme quand vous quittez une pièce en laissant le téléphone sur le bureau, mais vous informe si la pompe n'est pas joignable pour une durée supérieure à celle d'un d'un débit de base temporaire.

### Restaurer l'accessibilité de la pompe

* When AAPS reports a **pump unreachable** alarm, first release the keylock and **press any key on the pump** (e.g. "down" button). As soon as the pump display has turned off, press **Refresh** on the **Combo Tab** in AAPS. La plupart du temps la communication fonctionnera à nouveau.
* If that does not help, reboot your smartphone. After the restart, AAPS will be reactivated and a new connection will be established with the pump. If you are using the old driver, ruffy will be reactivated as well.

* The tests with different smartphones have shown that certain smartphones trigger the "pump unreachable" error more often than others. [AAPS Phones](https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit) lists successfully tested smartphones.

### Causes racines et conséquences des fréquentes erreurs de communication
* On phones with **low memory** (or **aggressive power-saving** settings), AAPS is often shut down. Vous pouvez le constater par le fait que les boutons Bolus et Calculatrice sur l'écran d'accueil ne sont pas affichés lors de l'ouverture d'AAPS car le système est en cours d'initialisation. Cela peut déclencher une alerte "Pompe hors de portée" au démarrage. In the **Last Connection** field of the Combo tab, you can check when AAPS last communicated with the pump.

![Pump unreachable](../images/combo/combo-tips-pump-unreachable.png)

![No connection to pump (as shown in the old driver's tab)](../images/combo/combo-tips-no-connection-to-pump.png)

![No connection to pump (as shown in the new driver's tab)](../images/combo/combov2-tips-no-connection-to-pump.png)

* Cette erreur peut vider la pile de la pompe plus rapidement car le profil basal est lu à partir de la pompe lorsque l'application est redémarrée.
* Cela augmente également la probabilité de provoquer l'erreur qui amène la pompe à rejeter toutes les connexions entrantes jusqu'à ce qu'un bouton de la pompe soit enfoncé.

## Echec de l'annulation du débit de base temporaire
* Occasionally, AAPS can not automatically cancel a **TBR CANCELED** alert. Then you have to either press **UPDATE** in the AAPS **Combo tab** or the alarm on the pump will need to be confirmed.

## Considérations relatives à la pile

### Changer la pile
* After a **low battery** alarm, the battery should be changed as soon as possible to always have enough energy for a reliable Bluetooth communication with the smartphone, even if the phone is within a wider distance of the pump.
* Even after a **low battery** alarm, the battery might be used for a significant amount of time. Il est cependant recommandé de toujours avoir une pile neuve avec vous après une alarme "Niveau Batterie Bas".
* Before changing the battery, press on the **Loop** symbol on the main screen and select **Suspend loop for 1h**.
* Attendez que la pompe communique avec le téléphone et que le logo bluetooth sur la pompe ait disparu.

![Bluetooth enabled](../images/combo/combo-tips-compo.png)

* Déverrouillez les touches de la pompe, mettez la pompe à l'arrêt, confirmez si nécessaire l'annulation du débit de base temporaire et changez rapidement la pile.
* Lorsque vous utilisez l'ancien pilote, si l'horloge de la pompe ne survit pas au changement de pile, redéfinissez la date et l'heure de la pompe à exactement la même date/heure du téléphone exécutant AAPS. (Le nouveau pilote met à jour automatiquement la date et l'heure de la pompe.)
* Then put the pump back in run mode select **Resume** when pressing on the **Suspended Loop** icon on the main screen.
* AAPS will re-set a necessary temporary basal rate with the arrival of the next blood sugar value.

(Accu-Chek-Combo-Tips-for-Basic-usage-battery-type-and-causes-of-short-battery-life)=
### Type de pile et causes de faible autonomie
* As intensive Bluetooth communication consumes a lot of energy, only use **high-quality batteries** like Energizer Ultimate Lithium, the "power one"s from the "large" Accu-Chek service pack, or if you are going for a rechargeable battery, use Eneloop batteries.

![Energizer](../images/combo/combo-tips-energizer.jpg) ![OnePower](../images/combo/combo-tips-power-one.png)

Ranges for typical life time of the different battery types are as follows:
* **Energizer Ultimate Lithium**: 4 to 7 weeks
* **Power One Alkaline** (Varta) from the servcie pack: 2 to 4 weeks
* **Eneloop rechargeable** batteries (BK-3MCCE): 1 to 3 weeks

If your battery life is significantly shorter than the ranges given above, please check the following possible causes:
* (Only applies to the old driver) Versions of the [ruffy App](https://github.com/MilosKozak/ruffy) after vMarch 2018 significantly improved pump battery lifetime. Assurez-vous que vous êtes sur une version plus récente si vous avez des problèmes de durée de vie de la pile.
* Il y a quelques variantes du capuchon de pile de la pompe Combo, qui court-circuite partiellement les piles et les vide rapidement. Les capuchons sans ce problème sont reconnaissables par les contacts dorés.
* Si l'horloge interne de la pompe ne "survie" pas un changement de pile court, il est probable que le condensateur qui maintient l'horloge en marche soit cassé. Dans ce cas, un remplacement de la pompe par Roche vous aidera, ce qui n'est pas un problème pendant la période de garantie.
* Le hardwre et le software du smartphone (version de l'OS Android et de la puce bluetooth) ont aussi un impact sur la durée de vie de la pile de la pompe, même si les raisons exactes ne sont pas encore complètement connues actuellement. Si vous en avez l'occasion, essayez un autre smartphone et comparez la durée de vie de la pile.

## Changement d'heure (été ou hiver)

**NOTE**: The new driver automatically sets date and time and handles daylight saving time changes on its own. The steps below all only apply to the old driver.

* Actuellement, le pilote combo ne prend pas en charge l'ajustement automatique de l'heure de la pompe.
* Pendant la nuit d'un changement d'heure, l'heure du smartphone est mise à jour, mais l'heure de la pompe reste inchangé. Cela conduit à une alarme en raison du décalage des heures entre les systèmes à 3 heures du matin.
* If you do not want to be awakened at night, **deactivate the automatic daylight saving time changeover on the mobile phone** in the evening before the time changeover and adjust the times manually the next morning. Une bonne façon de gérer les changements d'heure est de passer à un autre fuseau horaire situé sur la même longitude que celle où vous êtes situé mais plus proche de l'équateur, où il n'y a généralement pas de changement d'heure. Exemple : Pour l'Europe centrale en période d'été (GMT+2), vous pouvez passer au fuseau horaire du Zimbabwe la nuit précédant le passage à l'heure d'hiver et ensuite revenir à l'heure d'Europe centrale GMT+1 le lendemain matin tout en changeant l'heure sur votre pompe en même temps. L'inverse, passez au fuseau horaire du Nigéria pendant l'heure d'hiver GMT+1 et revenez sur le fuseau de l'Europe centrale (GMT+2) le matin après le passage à l'heure d'été et changez l'heure de la pompe en conséquence. Consultez https://www.timeanddate.com/time/map/ pour trouver un pays approprié.

## Bolus étendus, bolus mixtes
The OpenAPS algorithm does not support a parallel extended bolus or multiwave bolus. But a similar treatment can be achieved by the following alternatives:
* Use **e-Carbs** when entering carbs or using the Calculator by entering the carbs of the full meal and the duration you expect the carbs to arrive as glucose in you blood. Le système calculera ensuite les petits glucides répartis de manière égale sur toute la durée de sorte que l'algorithme fournisse une dose d'insuline équivalente tout en vérifiant de façon permanente l'augmentation/diminution globale de la glycémie. Pour une approche de bolus mixte, vous pouvez également combiner un bolus immédiat plus petit avec des e-glucides.
* Before eating, on the **Actions tab** in AAPS set as a temporary **Eating Soon** goal with target glucose 80 for several hours. La durée doit être basée sur la durée que vous auriez choisi d'utiliser pour un bolus étendu. Cela permettra de garder votre cible inférieure à la normale et donc d'augmenter la quantité d'insuline délivrée.
* Then use the **CALCULATOR** to enter the full carbs of the meal, but do not directly apply the values suggested by the bolus calculator. Si un bolus de type mixte doit être administré, corrigez la quantité d'insuline. Selon le repas, l'algorithme doit maintenant fournir des SMB supplémentaires ou des débits de basal temporaires plus élevés pour contrer l'augmentation de la glycémie. Ici, la limitation de sécurité du débit basal (Max U/h, Les IA basales) maximales devraient être expérimentées avec beaucoup de soin et, si nécessaire, temporairement modifiées.

* If you are tempted to just use the extended or multiwave bolus directly on the pump, AAPS will penalize you with disabling the closed loop for the next six hours to ensure that no excess insulin dosage is calculated.

![Disabled loop after multiwave bolus](../images/combo/combo-tips-multiwave-bolus.png)

## Alarms at bolus delivery
* If AAPS detects that an identical bolus has been successfully delivered at the same minute, bolus delivery will be prevented with identical numer of insulin units. Si vous voulez vraiment faire deux bolus de suite avec la même quantité d'insuline, il suffit d'attendre deux minutes de plus, puis refaire le nouveau bolus. Si le premier bolus a été interrompu ou n'a pas été délivré pour d'autres raisons, vous pouvez refaire immédiatement le bolus depuis AAPS 2.0.
* L'alarme est un mécanisme de sécurité qui va lire l'historique des bolus de la pompe avant d'administrer un nouveau bolus pour calculer correctement l'insuline active (IA), même quand un bolus est administré directement sur la pompe. Pour cela, il faut éviter les entrées multiples identiques.

![Double bolus](../images/combo/combo-tips-doppelbolus.png)

* Ce mécanisme est également responsable d'une deuxième source d'erreur: si, lors de l'utilisation de la calculatrice, un autre bolus est administré via la pompe et donc l'historique des bolus change, la base du calcul du bolus est erronée et le bolus est abandonné.

![Canceled bolus](../images/combo/combo-tips-history-changed.png)
