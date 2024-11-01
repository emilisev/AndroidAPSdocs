# Component Overview

**AAPS** is not just a (self-built) application, it is but one of several modules of your closed loop system. Before deciding for components, it would be a good idea to have a look at the component documentation.

![Components overview](../images/modules.png)

```{note}
**IMPORTANT SAFETY NOTICE**

The foundation of **AAPS** safety features discussed in this documentation is built on the safety features of the hardware used to build your system. For closing an automated insulin dosing loop, it is critically important that you only use an insulin pump and CGM that are tested, fully functioning and approved by the official instances of your country. Οι τροποποιήσεις υλικού ή λογισμικού σε αυτά τα εξαρτήματα μπορεί να προκαλέσουν απροσδόκητη δόση ινσουλίνης, προκαλώντας σημαντικό κίνδυνο για τον χρήστη. If you find or get offered broken, modified or self-made insulin pumps or CGM receivers, **do not use** these for creating an **AAPS** system.

Επιπλέον, είναι εξίσου σημαντικό να χρησιμοποιείτε μόνο αυθεντικά προϊόντα όπως εισαγωγείς, κάνουλα και δοχεία ινσουλίνης εγκεκριμένα από τον κατασκευαστή για χρήση με την αντλία ή το CGM. Η χρήση μη δοκιμασμένων ή τροποποιημένων αναλωσίμων μπορεί να προκαλέσει ανακρίβεια CGM και σφάλματα δοσολογίας ινσουλίνης. Η ινσουλίνη είναι εξαιρετικά επικίνδυνη όταν δίνετε σε λάθος δοσολογία - παρακαλώ μην παίζετε με τη ζωή σας με μη εγκεκριμένες προμήθειες.

Last but not least, you must not take SGLT-2 inhibitors (gliflozins) as they incalculably lower blood sugar levels. The combination with a system that lowers basal rates in order to increase BG is especially dangerous as due to the gliflozin this rise in BG might not happen and a dangerous state of lack of insulin can happen. [More information here](../Getting-Started/PreparingForAaps.md#no-sglt-2-inhibitors).
```

## Necessary Modules

### Good individual dosage algorithm for your diabetes therapy

Even though this is not something to create or buy, this is the 'module' which is probably underestimated the most but essential. When you let an algorithm help manage your diabetes, it needs to know the right settings to not make severe mistakes. Even if you are still missing other modules, you can already verify and adapt your **Profile** in collaboration with your diabetes team.

The **Profile** includes:

- BR (Basal rates): provides background insulin;
- ISF (insulin sensitivity factor): how much your blood glucose level will be reduced by 1 unit of insulin;
- CR (carb ratio): how many grams of carbohydrate are covered by one unit of insulin;
- DIA (duration of insulin action).

Most loopers use circadian BR, ISF and CR, which adapt hormonal insulin sensitivity during the day.

More information about your **Profile** [on the dedicated page](../SettingUpAaps/YourAapsProfile.md).

### Phone

See the dedicated page [Phones](../Getting-Started/Phones.md).

### Αντλία ινσουλίνης

See the dedicated page [Compatible Pumps](../Getting-Started/CompatiblePumps.md).

**Advantages and disadvantages of some pump models**

The Combo, the Insight and the older Medtronic are solid pumps, and loopable. The Combo has the advantage of many more infusion set types to choose from as it has a standard Luer-Lock. And the battery is a default one you can buy at any gas station, 24-hour convenience store and if you really need one, you can steal/borrow it from the remote control in the hotel room ;-).

The advantages of the DanaR/RS and Dana-i vs. the Combo as the pump of choice however are:

- The Dana pumps connect to almost any phone with Android >= 5.1 without the need to flash lineage. If your phone breaks you usually can find easily any phone that works with the Dana pumps as quick replacement... not so easy with the Combo. (Αυτό μπορεί να αλλάξει στο μέλλον όταν το Android 8.1 γίνει πιο διαδεδομένο)
- Initial pairing is simpler with the Dana-i/RS. Επειδή όμως συνήθως αυτό γίνεται μόνο μία φορά, σας επηρεάζει μόνο όταν θέλετε να δοκιμάσετε ένα νέο χαρακτηριστικό με διαφορετικές αντλίες.
- Μέχρι στιγμής η αντλία Combo λειτουργεί με τεχνολογία οθόνης. Σε γενικές γραμμές αυτό λειτουργεί καλά αλλά είναι αργό. Για το κύκλωμα αυτό δεν έχει σημασία όσο όλα λειτουργούν στο παρασκήνιο. Still there is much more time you need to be connected so more time when the BT connection might break, which isn't so easy if you walk away from your phone whilst bolusing & cooking.
- The Combo vibrates on the end of TBRs, the DanaR vibrates (or beeps) on SMB. At nighttime, you are likely to be using TBRs more than SMB.  The Dana-i/RS is configurable so that it does neither beep nor vibrate.
- Reading the history on the Dana-i/RS in a few seconds with carbs makes it possible to switch phones easily while offline and continue looping as soon a soon as some CGM values are in.
- All pumps **AAPS** can talk with are waterproof on delivery. Μόνο οι αντλίες Dana είναι επίσης "αδιάβροχες με εγγύηση" λόγω της σφραγισμένης θήκης των μπαταριών και του συστήματος πλήρωσης δεξαμενών.

### Πηγή BG

See the dedicated page [Compatible CGMs](../Getting-Started/CompatiblesCgms.md).

### **AAPS**-.apk file

The main component of the system. In order to install the app, you have to build the apk-file yourself first. Instructions are [here](../SettingUpAaps/BuildingAaps.md).

### Reporting server

A reporting server displays your glucose and treatment data, and creates reports for detailed analysis. There are currently two reporting servers available for use with AAPS : [Nightscout](../SettingUpAaps/SettingUpTheReportingServer.md#nightscout) and [Tidepool](../SettingUpAaps/SettingUpTheReportingServer.md#tidepool). They both provide ways to visualize your diabetes data over time, provide statistics about the **time in range** (TIR) and other measures.

The Reporting server is independent of the other modules. If you don’t want to use a reporting server, you should know that it is not mandatory for running **AAPS** in the long term. But you still need to set up one as it will be required to fulfill [**Objective 1**](../SettingUpAaps/CompletingTheObjectives.md#objective-1-setting-up-visualization-and-monitoring-analyzing-basals-and-ratios).

Additional information on how to set up your reporting server can be found [here](../SettingUpAaps/SettingUpTheReportingServer.md).

## Optional Modules

### Smartwatch

You can choose any smartwatch with Android WearOS 1.x up to 4.x. **Beware, WearOS 5.x is not compatible!**

The Sony Smartwatch 3 (SWR50) is commonly used amongst loopers as it is the only watch that can get readings from Dexcom G6/G5 when phone is out of range. Some other watches can be patched to work as a standalone receiver as well (see [this documentation](https://github.com/NightscoutFoundation/xDrip/wiki/Patching-Android-Wear-devices-for-use-with-the-G5) for more details).

Οι χρήστες δημιουργούν μία [λίστα με δοκιμασμένα κινητά τηλέφωνα και ρολόγια](https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit?usp=sharing). There are different watchfaces for use with **AAPS**, which you can find [here](../UsefulLinks/WearOsSmartwatch.md).

Για να εισάγετε ένα τηλέφωνο ή ρολόι το οποίο δεν είναι ήδη στη λίστα, παρακαλώ συμπληρώστε τη [φόρμα](https://docs.google.com/forms/d/e/1FAIpQLScvmuqLTZ7MizuFBoTyVCZXuDb__jnQawEvMYtnnT9RGY6QUw/viewform).

Any problems with the spreadsheet please email [hardware@androidaps.org](mailto:hardware@androidaps.org), any donations of phone/watch models that still need testing please email [donations@androidaps.org](mailto:donations@androidaps.org).

### xDrip+

Even if you don't need to have the [xDrip+ App](https://xdrip.readthedocs.io/en/latest/) as **BG Source**, you can still use it for _i.e._ alarms or a different blood glucose display. You can have as many alarms as you want, specify the time when the alarm should be active, if it can override silent mode, etc. Some xDrip+ information can be found [here](../CompatibleCgms/xDrip.md). Please be aware that the documentations to this app are not always up to date as its progress is quite fast.

## What to do while waiting for modules

It sometimes takes a while to get all the modules for closing the loop. But no worries, there are a lot of things you can do while waiting. It is **necessary** to check and (where appropriate) adapt basal rates (BR), insulin-carbratio (IC), insulin-sensitivity-factors (ISF) etc. And maybe open loop can be a good way to test the system and get familiar with **AAPS**. Using this mode, **AAPS** gives treatment recommendations you can manually execute.

You can keep on reading through the docs here, get in touch with other loopers online or offline, [read](../Where-To-Go-For-Help/Background-reading.md) documentations or what other loopers write (even if you have to be careful, not everything is correct or good for you to reproduce).

**Done?** If you have your **AAPS** components all together (congrats!) or at least enough to start in open loop mode, you should first read through the [Objective description](../SettingUpAaps/CompletingTheObjectives.md) before each new Objective and setup up your hardware.