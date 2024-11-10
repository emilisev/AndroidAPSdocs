(Extended-Carbs-extended-carbs-ecarbs)=
# פחמימות ממושכות

## מהן פחמימות ממושכות ומתי משתמשים בהן?

בטיפול רגיל במשאבה, בולוסים מושהים הם דרך טובה להתמודד עם ארוחות שומניות או ארוחות אחרות שנספגות לאט ומעלות את רמת הגלוקוז בדם זמן רב יותר מהשפעת האינסולין. עם זאת, בהקשר של לולאה, בולוסים מושהים אינם הגיוניים כל כך (ומציבים קשיים טכניים), מכיוון שהם בעצם מינון בזאלי זמני קבוע גבוה, הנוגד את אופן פעולת הלולאה, שהוא התאמה דינמית של המינון בזאלי. For details see [extended bolus](#extended-bolus-and-why-they-wont-work-in-closed-loop-environment) below.

אף על פי כן, נותר הצורך להתמודד עם ארוחות כאלה. לכן, החל מגרסה 2.0, AndroidAPS תומך בפחמימות ממושכות.

פחמימות ממושכות הן פחמימות שפרוסות על פני מספר שעות. בארוחות סטנדרטיות עם יותר פחמימות מאשר שומן\חלבון, רישום פחמימות מקדים (והפחתת הבולוס הראשוני במידת הצורך) מספיקה בדרך כלל כדי למנוע מתן אינסולין מוקדם מדי.  אבל עבור ארוחות איטיות יותר, בולוס על כל הפחמימות מראש גורם ליותר מדי אינסולין פעיל מ-SMB, ניתן להשתמש בפחמימות ממושכות כדי לדמות בצורה נכונה יותר את ספיגת הפחמימות (או המקבילה לפחמימות שתזינו עבור חלבון או שומן) והשפעתה על רמת הגלוקוז בדם. עם המידע הזה, הלולאה יכולה להזריק בולוסי SMB בהדרגה כדי להתמודד עם אותן פחמימות, אפשר לחשוב על כך כבולוס מושהה דינמי (זה אמור לעבוד גם ללא SMBs, אבל עם פחות יעילות).

**הערה:** פחמימות ממושכות אינן מוגבלות לארוחות כבדות העשירות בשומן או חלבון: ניתן להשתמש בהן גם כדי לעזור בכל מצב שבו יש השפעות שמעלות את רמת הסוכר בדם כמו שימוש בתרופות כגון קורטיקוסטרואידים.

## אופן השימוש בפחמימות ממושכות

בכדי להזין פחמימות ממושכות, הגדירו משך זמן בתיבת הדו-שיח *פחמימות* בלשונית הסקירה הכללית, את סך הפחמימות ובאופן אופציונלי היסט זמן (*המספרים למטה הם רק דוגמאות, תצטרכו לנסות את הערכים שלכם כדי להגיע לתגובת גלוקוז נכונה*):

![Enter carbs](../images/eCarbs_Dialog.png)

פחמימות ממושכות בלשונית סקירה כללית, שימו לב לפחמימות בסוגריים בשדה הפחמימות, המציג את הפחמימות העתידיות:

![eCarbs in graph](../images/eCarbs_Graph.png)

______________________________________________________________________

דרך לטפל בשומן וחלבון בעזרת תכונה זו מתוארת כאן: [https://adriansloop.blogspot.com/2018/04/page-margin-0.html](https://adriansloop.blogspot.com/2018/04/page-margin-0.html)

______________________________________________________________________

## תצורה מומלצת, תרחיש לדוגמה והערות חשובות

התצורה המומלצת היא להשתמש בתוסף OpenAPS SMB, כאשר בולוסי SMB מופעלים וכאשר האפשרות *הפעלת SMB עם פחמ' פעילות* מופעלת.

עבור פיצה ניתן לתת בולוס (חלקי) מראש באמצעות ה*מחשבון* ולאחר מכן להשתמש בלחצן *פחמימות* כדי להזין את הפחמימות הנותרות עם משך 4-6 שעות, החל לאחר שעה או שעתיים.

**הערות חשובות:** חובה לבדוק בעצמכם ולגלות מהם הערכים המתאימים לכם. תוכלו גם להתאים בזהירות את ההגדרה *מקסימום הדקות של בזאלי אליו SMB מוגבל* כדי לגרום לאלגוריתם להיות אגרסיבי יותר או פחות. בארוחות דלות פחמימות שעתירות שומן\חלבון זה עשוי להספיק להשתמש רק בפחמימות ממושכות ללא בולוסים מקדימים ידניים (ראו את הפוסט בבלוג למעלה). כאשר נוצר רישום פחמימות ממושכות, נוצרת גם תיעוד בנייטסקאוט לתיעוד כל התשומות, כדי להקל על איטרציה ושיפור התשומות.

(Extended-Carbs-extended-bolus-and-why-they-wont-work-in-closed-loop-environment)=
## בולוס מושהה ומדוע הוא לא יעבוד במערכת לולאה סגורה?

כפי שהוזכר לעיל בולוסים ממושכים או מרובי גלים לא באמת עובדים בסביבת לולאה סגורה. [See below](#why-extended-boluses-wont-work-in-a-closed-loop-environment) for details

(Extended-Carbs-extended-bolus-and-switch-to-open-loop-dana-and-insight-pump-only)=
### בולוס מושהה ומעבר ללולאה פתוחה - משאבת Dana ו-Insight בלבד

חלק מהאנשים ביקשו אפשרות להשתמש בבולוס מושהה ב-AAPS בכל זאת מכיוון שהם רצו להתייחס למזונות מיוחדים כפי שהיו רגילים בעבר.

לכן החל מגרסה 2.6 ישנה אפשרות לבולוס מושהה למשתמשי משאבות Dana ו-Insight.

- לולאה סגורה תיעצר אוטומטית ותעבור למצב לולאה פתוחה למשך זמן פעילות הבולוס הממושך.
- יחידות הבולוס, הזמן הנותר והזמן הכולל יוצגו במסך הבית.
- On Insight pump extended bolus is *not available* if [TBR emulation](#Accu-Chek-Insight-Pump-settings-in-aaps) is used.

![Extended bolus in AAPS 2.6](../images/ExtendedBolus2_6.png)

(Extended-Carbs-why-extended-boluses-won-t-work-in-a-closed-loop-environment)=
### הסיבה לכך שבולוסים מושהים לא יעבדו בלולאה סגורה

1. הלופ קובע שיש לספק עכשיו 1.55 יח'\שעה. לאלגוריתם לא משנה אם המינון הזה יוזרק כבולוס מושהה או כמינון בזאלי זמני. למעשה, חלק מהמשאבות משתמשות בבולוס המושהה. מה צריך לקרות? רוב המשאבות מפסיקות את הבולוס המושהה -> לא היינו צריכים להפעיל אותו.

2. אם הזנו בולוס מושהה מראש, מה צריך לקרות באלגוריתם?

   1. האם זה אמור להיות מחושב כנייטרלי יחד עם המינון הבזאלי בחישוב של הלולאה? ואז הלולאה אמורה להיות מסוגלת גם להפחית את הבולוס אם למשל יורדים מדי וכל האינסולין ה"נייטרלי" נלקח?
   2. האם פשוט להוסיף את הבולוס המושהה? אז פשוט צריך לתת ללופ להמשיך? אפילו בהיפו הכי חריף? זהו אינו פיתרון טוב, יש היפו צפוי אבל אסור למנוע אותו?

3. השפעת האינסולין הפעיל שהמצטבר בגלל הבולוס המושהה מתממשת לאחר 5 דקות במדידה הבאה. בהתאם, הלולאה תיתן פחות בזאלי. כך אין הרבה שינויים, חוץ משנבחרה האפשרות בה יש הימנעות מהיפוגליקמיה.