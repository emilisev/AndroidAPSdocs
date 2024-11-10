# ממשק AndroidAPS

```{contents}
:backlinks: entry
:depth: 2
```

(AapsScreens-the-homescreen)=

## The Homescreen

![Homescreen V2.7](../images/Home2020_Homescreen.png)

This is the first screen you will come across when you open **AAPS**, and it contains most of the information that you will need day to day.

### Section A - Tabs

* Navigate between the various **AAPS** modules.
* Alternatively you can change screens by swiping left or right.
* Displayed tabs can be selected in [config builder](#Config-Builder-tab-or-hamburger-menu).

### Section B - Profile & target

#### Current Profile

The current profile is displayed in the left bar.

Short press profile bar to view profile details. Long press profile bar to [switch between different profiles](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md).

![Profile switch remaining duration](../images/Home2020_ProfileSwitch.png)

1. Regular display with a standard profile activation.
2. Profile switch with a remaining duration of 59mn.
3. Profile switch with a specific percentage of 120%.
4. Profile switch with a specific percentage of 80% and a remaining duration of 59 mn.
5. Profile switch with a time shift of -1 hour.
6. Profile switch with a specific percentage of 120%, time shift of 1 hour, and a remaining duration of 59mn.

#### Target

![Temp target remaining duration](../images/Home2020_TT.png)

Current target blood glucose level is displayed in the right bar.

Short press target bar to set a **[Temporary Target](../DailyLifeWithAaps/TempTargets.md)**.

If a temp target is set, the bar turns yellow and the remaining time in minutes is shown in brackets.

(AapsScreens-visualization-of-dynamic-target-adjustment)=

#### Visualization of Dynamic target adjustment

![Visualization of dynamic target adjustment](../images/Home2020_DynamicTargetAdjustment.png)

When using the [SMB algorithm](#Config-Builder-aps) and [Autosens](#Open-APS-features-autosens) functionality, **AAPS** can dynamically adjust your target based on sensitivity.

Enable either one or both of the following options in [Preferences > OpenAPS SMB settings](#Preferences-openaps-smb-settings):

* "sensitivity raises target" and/or 
* "resistance lowers target" 

If **AAPS** detects resistance or sensitivity, the target will change from what is set from profile. When it alters the target glucose, the background will change to green.

(AapsScreens-section-c-bg-loop-status)=

### Section C - BG & loop status

#### Current blood glucose

The latest blood glucose reading from your CGM is shown on the left side.

The color of the BG value reflects the status to the defined [range](#Preferences-range-for-visualization).

* green = in range
* red = below range
* yellow = above range 

The greyish block in the middle shows minutes since last reading and changes since last reading, in the last 15 and 40 minutes.

(AapsScreens-loop-status)=

#### Loop status

![Loop status](../images/Home2020_LoopStatus.png)

On the right side, an icon shows the loop status:

1. Green circle = loop running
2. Green circle with dotted line = [low glucose suspend (LGS)](#objectives-objective6)
3. Red circled = loop disabled (not working permanently)
4. Yellow circle = loop suspended (temporarily paused but basal insulin will be given) - remaining time is shown below icon
5. Grey circle = pump disconnected (temporarily no insulin dosage at all) - remaining time is shown below icon
6. Orange circle = super bolus running - remaining time is shown below icon
7. Blue circle with dotted line = open loop

Short press or Long press the icon to open the Loop dialog to switch loop mode (Close, Low Glucose Suspend, Open or Disable), suspend / re-enable loop or disconnect / reconnect pump.

* If short press on Loop icon, a validation is required after selection in Loop Dialog
    
    ![Loop status menu](../images/Home2020_Loop_Dialog.png)

(aaps-screens-bg-warning-sign)=

#### BG warning sign

If for any reason, there are issues in the BG readings **AAPS** receives, you will get a warning signal beneath your BG number on the main screen.

##### Red warning sign: Duplicate BG data

The red warning sign is signaling you to get active immediately: You are receiving **duplicate BG data**, which does avoid the loop to do its work right. Therefore, your loop will be disabled until it is resolved.

    {admonition} Your loop is not running
    :class: note
    Your loop is not running until you solve this issue !

![Red BG warning](../images/bg_warn_red.png)

עליכם לברר מדוע יש כפילות:

* Is Dexcom bridge enabled on your Nightscout site? Disable the bridge by going to the administration panel of your Nightscout instance, edit the "enable" variable and remove the "bridge" part there. (ניתן למצוא [פרטים לגבי Heroku כאן](https://nightscout.github.io/troubleshoot/troublehoot/#heroku-settings))
* Do multiple sources upload your BG to Nightscout? If you use the BYODA app, enable the upload in **AAPS** but do not enable it in xDrip+, if you use that.
* Do you have any followers that might receive your BG but do also upload it again to your Nightscout site?
* Last resort: In **AAPS**, go to [Preferences > NSClient](#Preferences-nsclient), select the sync settings and disable the "Accept CGM data from NS" option.

To remove the warning immediately and get to loop running again, you need to manually delete a couple of entries from the Dexcom/xDrip+ tab.

אולם, כשיש הרבה כפילויות, אולי יהיה קל יותר:

* [backup your settings](../Maintenance/ExportImportSettings.md),
* לאתחל את מסד הנתונים שלכם בתפריט התחזוקה
* [import your settings](../Maintenance/ExportImportSettings.md) again

##### סימן אזהרה צהוב

The yellow warning signal is indicating that your BG arrived in irregular time intervals or that some BGs are missing. When pressing the sign, the message indicates “Recalculated data used”.

![Yellow BG warning](../images/bg_warn_yellow.png)

בדרך כלל אין צורך בנקיטת פעולה כלשהי. הלופ ימשיך לתפקד!

As a sensor change is interrupting the constant flow of BG data, a yellow warning sign after sensor change is normal and nothing to worry about.

Special note for Libre users:

* כל חיישן Libre מזייף בדקה או שתיים כל כמה שעות, כלומר לעולם אינך מקבל זרימה מושלמת עם מרווחים קבועים לחלוטין.
* Also, jumpy readings interrupt the continuous flow.
* Therefore, the yellow warning sign will be 'always on' for Libre users.

*Note*: Up to 30h hours are taken into accord for **AAPS** calculations. אז גם לאחר שפתרתם את בעיית המקור, עשויות לחלוף כ-30 שעות עד שהמשולש הצהוב ייעלם לאחר שהתרחש המרווח האחרון בנתונים.

### חלק D - אינסולין פעיל, פחמימות פעילות, מינונים בזאליים ורגישות

![Section D](../images/Home2020_TBR.png)

**Syringe**: insulin on board (IOB) - amount of active insulin inside your body

1. נתון האינסולין הפעיל יהיה אפס אם רק הבזאלי הסטנדרטי מהפרופיל פועל ולא נשאר אינסולין מבולוסים קודמים.
    
    * האינסולין הפעיל עשוי להיות שלילי אם היו לאחרונה תקופות של ירידה במינון הבזאלי.
    * לחצו על הסמל כדי לראות את הפיצול של הבולוס והאינסולין הבזאלי

2. **Grain**: [carbs on board (COB)](../DailyLifeWithAaps/CobCalculation.md) - yet unabsorbed carbs you have eaten before The icon pulses red if carbs are required (see [below](#aaps-screens-carbs-required))

3. **Purple line**: current basal rate. The icon changes to reflect temporary changes in basal rate (flat at 100%) 
    * לחצו על הסמל כדי לראות את המינון הבזאלי ופרטים של בזאלי זמני אם מופעל (כולל משך הזמן הנותר)
4. **Arrows up & down**: indicating actual [Autosens](#Open-APS-features-autosens) status (enabled or disabled) and value is shown below icon

(aaps-screens-carbs-required)=

#### דרושות פחמימות

![דרושות פחמימות](../images/Home2020_CarbsRequired.png)

בקשות לפחמימות ניתנות כאשר המערכת מזהה שנדרשות פחמימות.

This is when the oref algorithm thinks it can't rescue you by zero-temping, and you will need carbs to fix.

הבקשות לפחמימות מתוחכמות בהרבה מאלה שמופיעות במחשבון הבולוס. ייתכן שתראו בקשות לפחמימות בעוד שמחשבון בולוס אינו מראה שחסרות פחמימות.

הודעות של דרישה לפחמימות יכולות להישלח ל-Nightscout אם תרצו, ובמקרה זה תוצג ותשודר הודעה.

### חלק E - חיווי מצב

![Section E](../images/Home2020_StatusLights.png)

נורות הסטטוס נותנות חיווי ויזואלי עבור

* גיל הצינורית
* גיל אינסולין (משך השימוש במכל האינסולין הנוכחי)
* רמת המכל (יחידות)
* גיל חיישן
* גיל ורמת הסוללה (%)

אם חורגים מסף האזהרה, הערכים יוצגו בצהוב.

אם חורגים מסף האזהרה הקריטי, הערכים יוצגו באדום.

Settings can be changed in [Preferences > Overview > Status lights](#Preferences-status-lights).

Depending on the pump you use, you may not have all of these icons.

(aaps-screens-main-graph)=

### חלק F - גרף ראשי

![Section F](../images/Home2020_MainGraph.png)

The graph shows your blood glucose (BG) as read from your glucose monitor (CGM).

הערות שהוזנו בלשונית פעולות, כגון כיולים מבדיקות עם גלוקומטר וערכים של פחמימות וכן החלפות פרופיל מוצגות כאן.

Long press on the graph to change the timescale. אפשר לבחור 6, 12, 18 או 24 שעות.

האזור הירוק משקף את טווח המטרה.

Blue triangles show [SMB](#Open-APS-features-super-micro-bolus-smb) - if enabled in [Preferences > OpenAPS SMB](#Preferences-openaps-smb-settings).

(AapsScreens-activate-optional-information)=

#### הפעלת מידע אופציונלי

On the main graph, you can switch on these optional information:

* חיזוי
* בזאלי
* פעילות - עקומת פעילות אינסולין

To show this information, click the triangle on the right side of the main graph. עבור הגרף הראשי זמינות רק שלוש האפשרויות שמעל ל-"\---\---- גרף 1 \---\----".

![Main graph setting](../images/Home2020_MainGraphSetting.png)

(aaps-screens-prediction-lines)=

#### עקומי החיזוי

* **Orange** line: [COB](CobCalculation) (color is used generally to represent COB and carbs)
    
    This prediction line shows where your BG (not where COB itself!) will go based on the current **Profile** settings, assuming that the deviations due to carb absorption remain constant. עקום זה מופיע רק אם יש פחמימות פעילות ידועות.

* **Dark blue** line: IOB (color is used generally to represent IOB and insulin)
    
    This prediction line shows what would happen under the influence of insulin only. For example if you dialed in some insulin and then didn’t eat any carbs.

* עקום **כחול בהיר**: בזאלי אפס זמני (סוכר חזוי אם יוגדר קצב בזאלי זמני של 0%)
    
    This prediction line shows how the BG trajectory line would change if the pump stopped all insulin delivery (0% TBR).
    
    *This line appears only when the [SMB](#Config-Builder-aps) algorithm is used.*

* **Dark yellow** line: [UAM](#SensitivityDetectionAndCob-sensitivity-oref1) (un-announced meals)
    
    ארוחות לא מוכרזות מראש - זיהוי של עלייה משמעותית ברמות הסוכר עקב ארוחות, אדרנלין או השפעות אחרות. Prediction line is similar to the **orange COB line**, but it assumes that the deviations will taper down at a constant rate (by extending the current rate of reduction).
    
    *This line appears only when the [SMB](#Config-Builder-aps) algorithm is used.*

* **עקום כתום כהה**: ספיגת פחמימות מואצת
    
    דומה לפחמימות פעילות אז מניח שספיגת הפחמימות קבועה ב-10 מ"ג\ד"ל\5דק'. מיושן ובעל תועלת מוגבלת.
    
    *This line appears only when the older [AMA](#Config-Builder-aps) algorithm is used.*

בדרך כלל עקומת הסוכר האמיתית נמצאת באמצע בין העקומים הללו, או קרובה לזו שמניחה הנחות שהכי דומות למצבכם הנוכחי.

#### בזאלי

עקום **כחול מלא** מציג את הבזאלי הבסיסי מהמשאבה ומשקף את הבזאלי בפועל לאורך זמן.

הקו ה**כחול המקווקו** הוא המינון הבזאלי אם לא היה בזאלי זמני (TBR).

When the standard basal rate is given, the area under the curve is shown in dark blue. When the basal rate is temporarily adjusted (increased or decreased), the area under the curve is shown in light blue.

#### פעילות

העקום ה**צהוב הדק** מציג את פעילות האינסולין.

הוא מבוסס על הירידה הצפויה בסוכר בגלל אינסולין פעיל אם לא קיימים גורמים אחרים (כמו פחמימות).

(AapsScreens-section-g-additional-graphs)=

### חלק G - גרפים נוספים

ניתן להפעיל עד ארבעה גרפים נוספים מתחת לגרף הראשי.

To open settings for additional graphs click the triangle on the right side of the [main graph](#section-f---main-graph) and scroll down.

![Additional graph settings](../images/Home2020_AdditionalGraphSetting.png)

To add another graph check the box on the left side of its name (i.e. \---\---- Graph 1 \---\----).

Most users find the following configuration of additional graphs to be adequate :

* Graph 1 with IOB, COB, Sensitivity
* Graph 2 with Deviations and BGI.

#### אינסולין מוחלט

אינסולין פעיל כולל בולוסים **ואינסולין בזאלי**.

#### אינסולין פעיל

מראה את האינסולין הפעיל. הוא כולל אינסולין מבולוס ובזאלי זמני (**אך אינו כולל מינונים בזאליים שנקבעו בפרופיל**).

If there were no [SMBs](#Open-APS-features-super-micro-bolus-smb), no boluses and no TBR during DIA time this would be zero.

אינסולין פעיל יכול להיות שלילי אם אין בולוס או בזאלי זמני אפס/נמוך למשך זמן רב יותר.

Decaying depends on your [DIA and insulin profile settings](../SettingUpAaps/YourAapsProfile.md).

#### פחמימות פעילות

מראה את הפחמימות הפעילות, שעדיין לא דעכו. 

Decaying depends on the [deviations the algorithm detects](../DailyLifeWithAaps/CobCalculation.md).

אם הוא מזהה ספיגת פחמימות גבוהה מהצפוי, ינתן אינסולין וזה יגדיל את IOB (פחות או יותר, תלוי בהגדרות הבטיחות שלכם).

#### רגישות

Shows the sensitivity that [Autosens](#Open-APS-features-autosens) has detected.

חישוב רגישות לאינסולין כתוצאה מפעילות גופנית, תגובות הורמונליות וכו'.

Note, you need to be in [Objective 8](#objectives-objective8) in order to let Sensitivity Detection/[Autosens](#Open-APS-features-autosens) automatically adjust the amount of insulin delivered. Before reaching that objective, the line in your graph is displayed for information only.

#### Heart rate

This data may be available when using a [Garmin smartwatch](#Watchfaces-garmin).

#### סטיות

* **Grey** bars show a deviation due to carbs. 
* **Green** bars show that BG is higher than the algorithm expected it to be. Green bars are used to increase resistance in [Autosens](#Open-APS-features-autosens).
* **Red** bars show that BG is lower than the algorithm expected. Red bars are used to increase sensitivity in [Autosens](#Open-APS-features-autosens).
* **Yellow** bars show a deviation due to UAM.
* **Black** bars show small deviations not taken into account for sensitivity

#### Blood Glucose Impact

This line shows the degree to which BG ‘should’ rise or fall based on insulin activity alone.

![Homescreen buttons](../images/Screenshots_DEV_BGI.png)

It is a good combination to display this line along with the Deviation bars. They share the same scale, but it is a different one than the other optional data, so it is a good idea to display them on a separate graph, as shown above. Comparing the BGI line and the Deviation bars is another way to understand how **BG** fluctuates. Here, at the time marked **1**, the Deviation bars are greater than the BGI line, indicating that BG is rising. Later, during the hours marked **2**, BGI and DEV are pretty much in line, indicating that BG is stable.

### סעיף H - כפתורים

![Homescreen buttons](../images/Home2020_Buttons.png)

Buttons for Insulin, Carbs and Calculator are almost always visible. If the connection to the pump is lost, the insulin button will not be visible.

Other Buttons can be setup in [Preferences > Overview > Buttons](#Preferences-buttons).

About using the Insulin, Carbs and Calculator buttons : If enabled in the [Preferences > Overview](#Preferences-show-notes-field-in-treatments-dialogs), the **Notes** field allows you to enter text that will show on the main graph, and may be uploaded to Nightscout - depending on your settings for NS client.

#### אינסולין

![Insulin button](../images/Home2020_ButtonInsulin.png)

To give a certain amount of insulin without using the [bolus calculator](#bolus-wizard).

By checking the box **Start eating soon TT**, you can automatically start your [eating soon temp target](#TempTargets-eating-soon-temp-target).

If you do not want to bolus through the pump but record an insulin amount (i.e. insulin given by pen) check the corresponding box. When checking this box, you get an additional field “Time offset”, that you can use to record an insulin injection made in the past.

You can use the buttons to quickly increase the insulin quantity. The increment values can be changed in the [Preferences > Overview > Buttons](#Preferences-buttons).

#### פחמימות

![Carbs button](../images/Home2020_ButtonCarbs.png)

נועד לרישום פחמימות ללא בולוס.

Certain [pre-set temporary targets](#TempTargets-hypo-temp-target) can be set directly by checking the box.

**Time offset**: When will you / have you been eaten carbs (in minutes).

**Duration**: To be used for ["extended carbs"](ExtendedCarbs)

You can use the buttons to quickly increase the carb amount. The increment values can be changed in the [Preferences > Overview > Buttons](#Preferences-buttons).

#### מחשבון

See Bolus Wizard [section below](#bolus-wizard).

#### כיולים

שולח כיול ל- xDrip או פותח את חלון הכיול של אפליקציית Dexcom.

Must be activated in [Preferences > Overview > Buttons](#Preferences-buttons).

#### סנסור

פותח את xDrip+.

Back button returns to **AAPS**.

Must be activated in [Preferences > Overview > Buttons](#Preferences-buttons).

#### אשף מהיר

הזנה בקלות של כמות הפחמימות והגדרת נתוני החישוב.

Details are set up in [Preferences > Overview > QuickWizard settings](#Preferences-quick-wizard).

## אשף הבולוס

![Bolus wizard](../images/Home2020_BolusWizard_v2.png)

When you want to make a meal bolus, this is where you will normally make it from.

### חלק I

מציג את הבולוס המחושב.

אם כמות האינסולין הפעיל עולה על הבולוס המחושב, תוצג רק כמות הפחמימות הנדרשת.

(AapsScreens-section-j)=

### חלק J

שדה רמת הסוכר בדרך כלל כבר מאוכלס בקריאה האחרונה מהחיישן. אם אין לכם חיישן פעיל הוא יהיה ריק.

In the **Carbs** field, you add your estimate of the amount of carbs - or equivalent - that you want to bolus for.

The **Corr** field is if you want to modify the end dosage for some reason.

The **Carb time** field is for pre-bolusing so you can tell the system that there will be a delay before the carbs are to be expected. בכתיבת מספר שלילי בשדה זה אתם נותנים בולוס עבור פחמימות שנאכלו בעבר בעבר.

**Eating reminder** : For carbs in the future, the alarm checkbox can be selected (and is by default when a time in the future is entered) so that you can be reminded at the given time, when to eat the carbs you have input into **AAPS**.

![BolusWizard with Eating Reminder](../images/Home2021_BolusWizard_EatingReminder.png)

### חלק K

**Profile** allows you to select a different profile than the current one, to make the calculation for the insulin required. This profile selection applies only for the current bolus, it is not a profile change.

**Super Bolus** is where the basal insulin for the next two hours is added to the immediate bolus and a zero TBR is issued for the following two hours to take back the extra insulin. The option only shows when "Enable Superbolus in wizard" is set in the [Preferences > Overview > Advanced Settings](#Preferences-advanced-settings-overview). הרעיון הוא לספק את האינסולין מוקדם יותר ובתקווה להפחית עליות חדות ברמות הסוכר.

לפרטים עיינו ב-[diabetesnet.com](https://www.diabetesnet.com/diabetes-technology/blue-skying/super-bolus/).

### חלק L

Details of the wizard's bolus calculation.

You can deselect any that you do not want to include, but you normally wouldn't want to.

For safety reasons the **TT box must be ticked manually**, if you want the bolus wizard to calculate based on an existing temporary target.

#### שילובים של COB ו-IOB ומשמעותם

* For safety reasons, the IOB box cannot be unticked when COB box is ticked as you might run the risk of too much insulin as **AAPS** is not accounting for what’s already given.
* If you tick COB and IOB, unabsorbed carbs that are not already covered with insulin + all insulin that has been delivered as TBR or SMB will be taken into account.
* If you tick IOB without COB, **AAPS** takes account of already delivered insulin but won’t cover that off against any carbs still to be absorbed. מצב זה מוביל להודעת "פחמימות חסרות".
* אם מזריקים בולוס עבור **מזון נוסף** זמן קצר לאחר בולוס ארוחה (לדוגמה קינוח), ייתכן שכדאי יהיה **לבטל את הסימון בכל התיבות**. כך רק הפחמימות החדשות מתווספות מכיוון שהארוחה העיקרית לא בהכרח תיספג ולכן IOB לא יתאים ל-COB במדויק זמן קצר לאחר בולוס הארוחה.

![BolusWizard with Details](../images/Home2021_BolusWizard_Details.png)

The box near the eye allows you to choose between the detailed view, with the numbers entering the calculation for each item, or the simple view with icons. Pressing on an icon will enable / disable this entry from the calculation.

(AapsScreens-wrong-cob-detection)=

#### זיהוי שגוי של פחמימות פעילות

![Slow carb absorption](../images/Calculator_SlowCarbAbsorption.png)

If you see the warning above after using bolus wizard, **AAPS** has detected that the calculated COB value may be wrong. So, if you want to bolus again after a previous meal with COB, you should be aware of overdosing!

For details, see the hints on [COB calculation page](#CobCalculation-detection-of-wrong-cob-values).

(screens-action-tab)=

## לשונית פעולות

![Actions tab](../images/Home2021_Action.png)

### פעולות - חלק M

Button **[Profile switch](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md)** as an alternative to pressing the [current profile](#section-b---profile--target) on homescreen.

Button **[Temporary target](../DailyLifeWithAaps/TempTargets.md)** as an alternative to pressing the [current target](#section-b---profile--target) on homescreen.

לחצן להפעלה או ביטול של מינון בזאלי זמני. שימו לב שהלחצן משתנה מ-"בזאלי זמני" ל-"ביטול %x" כאשר מוגדר מינון בזאלי זמני.

Even though [extended boluses](#Extended-Carbs-extended-bolus-and-why-they-wont-work-in-closed-loop-environment) do not really work in a closed loop environment some people were asking for an option to use extended bolus anyway.

* אפשרות זו קיימת רק במשאבות Dana RS ו-Accu chek Insight. 
    * לולאה סגורה תיעצר אוטומטית ותעבור למצב לולאה פתוחה למשך זמן פעילות הבולוס הממושך.
    * Make sure to read the [details](../DailyLifeWithAaps/ExtendedCarbs.md) before using this option.

### פורטל הטיפולים - חלק N

Displays information on:

* sensor age & level (battery percentage)
* insulin age & level (units)
* cannula age
* pump battery age & level (percentage

Less information will be shown if **low resolution skin** is used ([Preferences > General > Skin](#Preferences-skin)).

(screens-sensor-level-battery)=

#### רמת טעינת סוללת החיישן

Works for CGM with an additional transmitter such as MiaoMiao 2. (טכנית, החיישן צריך לשלוח את המידע של רמת הסוללה לxDrip+.)

Thresholds can be set in [Preferences > Overview > Status lights](#Preferences-status-lights).

### פורטל הטיפולים - חלק O

BG check, prime/fill, sensor insert and pump battery change are the base for the data displayed in [section N](#careportal---section-n).

תיחול\מילוי מאפשר לתעד את החלפת מיקום חיבור צינורית המשאבה ואת החלפת מכל האינסולין.

חלק O משקף את פורטל הטיפולים שבנייטסקאוט. לכן התעמלות, הכרזות ושאלות הן סוגים מיוחדים של הערות.

### כלים - חלק P

#### דפדפן היסטוריה

Allows you to ride back in **AAPS** [history](../Maintenance/Reviewing.md).

#### TDD - סה"כ מינון אינסולין יומי

תצרוכת האינסולין הכללית (TDD=סיכום יומי של הבולוסים יחד עם המינונים הבזאליים)

רופאים לפעמים רושמים, במיוחד למשתמשי משאבה חדשים, יחס מינונים בזאליים-מינוני בולוסים של 50:50.

Therefore, ratio is calculated as TDD / 2 * TBB (Total base basal = sum of basal rate within 24 hours).

אחרים מעדיפים יחס של 32-37% מה-TDD ל-TBB.

לרוב כללי האצבע האלה תוקף מוגבל בפרקטיקה. הערה: הסוכרת שלכם עשויה להיות שונה!

(AapsScreens-insulin-profile)=

## פרופיל האינסולין

![פרופיל האינסולין](../images/Screenshot_insulin_profile.png)

This shows the activity profile of the insulin you have chosen in [config builder](#Config-Builder-insulin). The curves will vary based on the [DIA](#your-aaps-profile-duration-of-insulin-action) and the time to peak.

The **purple** line shows how much insulin remains after it has been injected as it decays with time and the **blue** line shows how active it is. The important thing to note is that the decay has a **long tail**. If you have been used to manual pumping, you have probably been used to assuming that insulin decays over about 3.5 hours. However, when you are looping, the long tail matters as the calculations are far more precise and these small amounts add up when they are subjected to the recursive calculations in the **AAPS** algorithm. Therefore, **AAPS** uses minimum 5h as DIA.

לדיון מפורט יותר על סוגי האינסולין השונים, פרופילי הפעילות שלהם ומדוע כל זה חשוב, אפשר לקרוא מאמר כאן על [הבנת עקומות החדשות של האינסולין הפעיל על סמך עקומות פעילות אקספוננציאליות](https://openaps.readthedocs.io/en/latest/docs/While%20You%20Wait%20For%20Gear/understanding-insulin-on-board-calculations.html#understanding-the-new-iob-curves-based-on-exponential-activity-curves)

ניתן גם לקרוא מאמר מצוין בבלוג על זה כאן: [מדוע אנחנו טועים באופן קבוע במשך פעולת האינסולין (DIA) ולמה זה חשוב…](https://www.diabettech.com/insulin/why-we-are-regularly-wrong-in-the-duration-of-insulin-action-dia-times-we-use-and-why-it-matters/)

And even more at: [Exponential Insulin Curves + Fiasp](https://web.archive.org/web/20220630154425/http://seemycgm.com/2017/10/21/exponential-insulin-curves-fiasp/)

## סטטוס המשאבה

![סטטוס המשאבה](../images/Screenshot_PumpStatus.png)

* מידעים שונים על מצב המשאבה. המידע המוצג תלוי בדגם המשאבה.
* See [pumps page](../Getting-Started/CompatiblePumps.md) for details.

## לולאה, AMA / SMB

These tabs show details about the algorithm's calculations and why **AAPS** acts the way it does.

Calculations are run each time the system gets a fresh reading from the CGM.

For more details see [APS section on config builder page](#Config-Builder-aps).

(aaps-screens-profile)=

## Profile

![Profile](../images/Screenshots_Profile.png)

Profile contains information on your individual diabetes settings, see the detailed **[Profile](../SettingUpAaps/YourAapsProfile.md)** page for more information.

The buttons on this page allow you to manage your profiles :

* **Green plus**: create new profile from scratch
* **Red X**: delete the profile currently on screen
* **Blue arrow**: duplicate the profile currently on screen

When you want to make any changes to a profile, make sure you are editing the correct profile. When you reach the profile tab, it may not show the current profile in use, but the first one in the list.

## אוטומציה

See the dedicated page [here](../DailyLifeWithAaps/Automations.md).

## NSClient

![NSClient](../images/Screenshots_NSClient.png)

This page displays the status of the connection with your Nightscout site.

Settings can be changed in [Preferences > NS Client](#Preferences-nsclient).

For troubleshooting see this [page](../GettingHelp/TroubleshootingNsClient.md).

## מקורות נתוני סוכר - xDrip+, BYODA...

![BG Source tab - here Nightscout](../images/Screenshots_BGSource.png)

Depending on your BG source settings, this tab is named differently.

Shows history of CGM readings and offers option to remove reading in case of failure (i.e. compression low) or duplicate readings.

(aaps-screens-treatments)=

## טיפולים

This view can be accessed by pressing the 3 dots on the right of the menu, then Treatments. It is not possible to show it in the main menu through the Config Builder. In this view, you can view and alter the history of the following treatments:

* Bolus & carbs
* [בולוס ממושך](#Extended-Carbs-extended-bolus-and-switch-to-open-loop-dana-and-insight-pump-only)
* מינון בזאלי זמני
* [ערך מטרה זמני](../DailyLifeWithAaps/TempTargets.md)
* [החלפת פרופיל](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md)
* Careportal: notes entered through action tab and notes in dialogues
* User entry: other notes that are not sent to Nightscout

In the last column, the data source for each line is displayed in blue. It can be :

* NS for Nightscout : the data comes from or has been recorded to Nightscout
* PH for Pump History : the data has been processed by the pump

(screens-bolus-carbs)=

### Bolus & carbs

![Carbs & bolus](../images/TreatmentsView1.png)

On this tab you can view the bolus and carbs log. Each bolus (line **1** and **4**) shows the remaining associated IOB next to the insulin amount. The origin of the bolus can be either :

* Meal (manually entered though the Insulin, Quick Wizard or Bolus Wizard buttons)
* SMB, when using the SMB Functionality

The carbs (line **2**) are only stored in Nightscout. If you have used the [Bolus Wizard](#bolus-wizard) to calculate insulin dosage, you can press the “Calc” text (line **3**) to show the details of how the bolus was calculated.

Depending on the pump used, insulin and carbs can be shown in one single line, or will result in multiple lines: one for the calculation detail, one for the carbs, one for the bolus itself.

The treatment tab can be used to correct faulty carb entries (*i.e.* you over- or underestimated carbs). Note that it is not possible to edit an existing entry, you need to follow the following process:

1. בדקו וזכרו את האינסולין והפחמימות הפעילים בפועל במסך הבית.
2. בהתאם למשאבה בלשונית הטיפולים פחמימות עשויות להיות מוצגות יחד עם אינסולין בשורה אחת או כערכים נפרדים (כלומר עם משאבת Dana RS).
3. Remove the entry with the faulty carb amount. (Latest versions have trashcan icon in treatments screen. Press the trashcan icon, select the lines to remove, and then press the trashcan icon again to finalize.)
4. ודאו שהפחמימות הוסרו בהצלחה על ידי בדיקה מחדש של הפחמימות הפעילות במסך הבית.
5. עשו את אותו הדבר עבור אינסולין פעיל אם יש רק שורה אחת בלשונית הטיפול כוללת פחמימות ואינסולין.
    
    → If carbs are not removed as intended, and you add additional carbs as explained here (6.), COB will be too high and that might lead to too high insulin delivery.

6. הזינו את כמות הפחמימות הנכונה דרך כפתור הפחמימות במסך הבית והקפידו להגדיר את מועד האירוע הנכון.

7. אם יש רק שורה אחת בלשונית הטיפולים הכוללת פחמימות ואינסולין, יש להוסיף גם את כמות האינסולין. הקפידו להגדיר את מועד האירוע הנכון ולבדוק את האינסולין הפעיל במסך הבית לאחר אישור הרשומה החדשה.

### Temp Basal

![Temp Basal](../images/TreatmentsView2.png)

The **temp basals** applied by the loop are shown here. When there is still an impact on the IOB for an entry, the information is shown in green. It can be:

* Positive IOB if the temp basal was higher than the one set in the Profile (line **2**)
* Negative IOB for a zero-temp or if the temp basal was lower than the one set in the Profile (line **1**)

Deleting the entries only affects your reports in Nightscout and will probably tamper your real IOB - it is not recommended.

On the left of a line, a red S means “Suspend” : it happens when basal is not currently delivered. This is a normal situation when in the process of changing a pod, for example.

### ערך מטרה זמני

![ערך מטרה זמני](../images/TreatmentsView3.png)

The history of temporary targets can be seen here.

### Profile Switch

![Profile Switch](../images/TreatmentsView4.png)

The history of profile switches can be seen here. You may see multiple entries each time you switch profile : line **1**, stored in Nightscout but not in Pump History, corresponds to the request of a profile switch made by the user. Line **2**, stored both in NS and PH, correspond to the actual switch.

Deleting the entries only affects your reports in Nightscout and will never actually change the current profile.

(aaps-screens-clone-profile-switch)=

#### החלפה לפרופיל משוכפל

ניתן בקלות ליצור פרופיל מקומי חדש מהפרופיל המוחלף\זמני. In this case, timeshift and percentage will be applied to the new local profile. Use the **Clone** button shown on line **1**.

You can now go to the [Profile tab](#profile) to edit the newly created Profile.

### Care portal

![Care portal](../images/TreatmentsView5.png)

This tab shows all notes and alerts recorded in Nightscout.

## דפדפן היסטוריה

This view can be accessed by pressing the 3 dots on the right of the menu, then History. It is not possible to put in the main menu through the Config Builder. It can also be accessed through a button at the bottom of the [Action tab](#action-tab).

Allows you to ride back in **AAPS** history.

## Profile Helper

This view can be accessed by pressing the 3 dots on the right of the menu, then Profile Helper. It is not possible to put in the main menu through the Config Builder. The [Profile Helper](../SettingUpAaps/ProfileHelper.md) can help you:

* build a profile from scratch for a kid
* compare two profiles
* clone a profile