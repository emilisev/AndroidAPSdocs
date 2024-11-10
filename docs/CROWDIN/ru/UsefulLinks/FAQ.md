# Часто задаваемые вопросы по работе ИПЖ

How to add questions to the FAQ: Follow the these [instructions](../SupportingAaps/HowToEditTheDocs.md)

## General

### Can I just download the AAPS installation file?

Нет. Для AndroidAPS не предоставляется загружаемый файл apk. You have to [build](../SettingUpAaps/BuildingAaps.md) it yourself. Причина вот в чем:

AndroidAPS создан для управления помпой и подачи инсулина. В соответствии с действующим Европейским законодательством, все системы, классифицируемые как IIa или IIb, являются медицинскими устройствами, подлежащими обязательной сертификации (получение знака CE), что в свою очередь требует соответствующих исследований и одобрений. Распространение несертифицированных устройств незаконно. Аналогичные законы существуют и в других частях мира.

Это положение не ограничивается торговлей, но относится к любому виду распространения (даже безвозмездному). Создание медицинского устройства для себя является единственным вариантом, не затрагиваемым этими правилами.

Именно поэтому распространение в виде готовых приложений (apk) недоступно.

(FAQ-how-to-begin)=

### How to begin?

Прежде всего, нужно **подготовить компоненты, которые работают с ипж**:

- A [supported insulin pump](../Getting-Started/CompatiblePumps.md), 
- an [Android smartphone](../Getting-Started/Phones.md) (Apple iOS is not supported by AAPS - you can check [iOS Loop](https://loopkit.github.io/loopdocs/)) and
- a [continuous glucose monitoring system](../Getting-Started/CompatiblesCgms.md). 

Secondly, you have to **setup your software components**: [AAPS](../SettingUpAaps/BuildingAaps.md), [CGM/FGM source](../Getting-Started/CompatiblesCgms.md) and a [reporting server](../SettingUpAaps/SettingUpTheReportingServer.md).

Thirdly, you have to learn and **understand the OpenAPS reference design to check your treatment factors**. The founding principle of closed looping is that your [basal rate and carb ratio](../SettingUpAaps/YourAapsProfile.md) are accurate. Все рекомендации, выдаваемые ИПЖ предполагают, что ваши базовые потребности в инсулине удовлетворены и любые пики и провалы характеристики ГК - следствие других факторов, требующих дополнительных настроек ( нагрузка, стресс и пр.). В настройках ИПЖ введены ограничения безопасности (см. максимально допустимый базальный уровень в [Архитектуре OpenAPS](https://openaps.org/reference-design/)), которые означают, что вам не придется тратить допустимые дозировки на исправление неправильной базы. Например, если перед едой вы часто ставите временную цель на пониженный уровень ГК, вам, скорее всего, требуется настройка базы. You can use [Autotune](https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/autotune.html#phase-c-running-autotune-for-suggested-adjustments-without-an-openaps-rig) to consider a large pool of data to suggest whether and how basals and/or ISF need to be adjusted, and also whether carb ratio needs to be changed. Or you can test and set your basal the [old-fashioned way](https://integrateddiabetes.com/basal-testing/).

### What practicalities of looping do I have?

#### Password protection

Если вы считаете необходимым исключить несанкционированное изменение настроек ИПЖ, вы можете закрыть паролем настройку, выбрав в меню "Пароль для настроек" и установив пароль на этот раздел. В следующий раз, когда вы войдете в это меню, система запросит пароль и не позволит поменять его без корректного ввода. Если в дальнейшем вы хотите удалить пароль, зайдите в это меню снова и удалите текст.

#### Android Wear Smartwatches

Если вы планируете использовать Android Wear для изменения болюса или настроек, нужно убедиться, что сообщения от AAPS не блокируются. Подтверждение действий происходит через уведомление.

(FAQ-disconnect-pump)=

#### Disconnect pump

Если вы снимаете помпу на время душа, купания, занятия спортом или других действий, то, чтобы активный инсулин IOB правильно отражался в системе, следует проинформировать AAPS, что инсулин не вводится,.

The pump can be disconnected using the Loop Status icon on the [AAPS Home Screen](#AapsScreens-loop-status).

#### Recommendations not only based on one single CGM reading

Для безопасности, рекомендации системы делаются не на одном показании ГК, а на среднем из последних значений (с учетом скользящей дельты). Поэтому, если пропущено несколько показаний, понадобится время на то, чтобы AAPS снова начал компенсацию ГК в режиме замкнутого цикла.

#### Further readings

Вот несколько блогов с полезными советами, которые помогут понять практику работы ИПЖ:

- [Подробные Настройки ](https://seemycgm.com/2017/10/29/fine-tuning-settings/) (см.мой мониторинг)
- [Почему так важна длительность работы инсулина DIA](https://seemycgm.com/2017/08/09/why-dia-matters/) (см. мой мониторинг)
- [Как ограничить пики после питания](https://diyps.org/2016/07/11/picture-this-how-to-do-eating-soon-mode/) #DIYPS
- [Гормоны и autosens](https://seemycgm.com/2017/06/06/hormones-2/) (см.мой мониторинг)

### What emergency equipment is recommended to take with me?

Прежде всего, вам необходимо иметь стандартный набор для больного диабетом 1го типа. При пользовании AAPS настоятельно рекомендуется также иметь:

- Банк батарей и кабель для зарядки смартфона, часов и (если это необходимо) BT reader или Link device
- Батарейки для помпы
- Current [apk](../SettingUpAaps/BuildingAaps.md) and [preferences files](../Maintenance/ExportImportSettings.md) for AAPS and any other apps you use (e.g. xDrip+, BYO Dexcom) both locally and in the cloud (Dropbox, Google Drive).

### How can I safely and securely attach the CGM/FGM?

Его можно закрепить лейкопластырем. Существует несколько предварительно перфорированных 'накладок' для распространенных систем мониторинга (искать в Google, eBay. Amazon. Озон, Wildberries и т. п.). Некоторые пользователи ИПЖ применяют более дешевые стандартные кинезезиотейпы или лейкопластыри.

Его можно закрепить держателем. В продаже есть держатели CGM/FGM с повязками (поиск Google, eBay Amazon, Озон, Wildberries).

## AAPS settings

Этот список поможет оптимизировать настройки. Начните сверху и двигайтесь вниз. Старайтесь выверить одну настройку прежде чем переходить к другой. Двигайтесь небольшими шагами, не вносите большие изменения сразу. Можно использовать автонастройку [Autotune](https://autotuneweb.azurewebsites.net/) которая даст общее направление, но принимайте рекомендации не вслепую и не во всех ситуациях. Обратите внимание, что настройки дополняют друг друга - вы можете иметь "неправильные" настройки, которые в некоторых обстоятельствах работают хорошо (например, если слишком высокий базал установлен одновременно со слишком высоким углеводным коэффициентом CR), но в других не работают. Это означает, что нужно учитывать все настройки и убедиться, что они совместно работают в различных обстоятельствах.

### Duration of insulin activity (DIA)

#### Description & testing

Длительность времени, которое инсулин падает до нуля.

Довольно часто задается слишком коротким. Правильная настройка для большинства - не менее 5 часов, иногда 6 или 7.

(FAQ-impact)=

#### Impact

Слишком малое значение продолжительности действия инсулина DIA может привести к низкой ГК. И наоборот.

Если DIA слишком короткий, AAPS слишком рано решит, что предыдущий болюс израсходован, и, при все еще высокой ГК, добавит инсулин. (Фактически, алгоритм не выжидает, а продолжает добавлять инсулин, предсказывая, что произойдет). Это, по сути, создает «затоваривание инсулина», о котором AAPS не знает.

Пример слишком короткого DIA - это высокая ГК, за которой следует избыточная коррекция и в результате - низкая ГК.

### Basal rate schedule (U/h)

#### Description & testing

Количество инсулина в заданном часовом блоке для поддержания ГК на стабильном уровне.

Проверьте настройки базы, приостановив цикл и пропуская приемы пищи, чтобы контролировать изменения ГК в течение 5 часов после еды. Повторите несколько раз.

Если ГК падает, то уровень базы слишком велик. И наоборот.

#### Impact

Повышенная скорость подачи базала может привести к низкому уровню ГК. И наоборот.

AAPS по умолчанию строит свой алгоритм отталкиваясь от скорости базала. Если базал слишком высокий, то «нулевая временная скорость» будет определяться при большем отрицательном значении активного инсулина IOB, чем нужно. Это приведет к тому, что AAPS будет давать больше коррекций, чем следует, чтобы привести активный инсулин IOB к нулю.

Таким образом, слишком высокая скорость подачи базала создаст низкую ГК как на стандартной базе, так и несколько часов спустя, так как AAPS еще корректирует к цели.

И наоборот, слишком низкая скорость базы может привести к высоким ГК, и невозможности снизить уровень до целевого.

### Insulin sensitivity factor (ISF) (mmol/l/U or mg/dl/U)

#### Description & testing

Ожидаемое снижение ГК после подачи 1ед. инсулина.

Если база рассчитана верно, вы можете определить ISF, приостановив цикл и убедившись что IOB равен нулю, принять несколько таблеток глюкозы, чтобы получить стабильно «высокую» гликемию.

Затем введите предполагаемое количество инсулина (по текущему соотношению 1/ISF), чтобы прийти к целевой ГК.

Будьте осторожны, так как довольно часто величина слишком занижена. Слишком низкая ГК означает, что 1 ед опустит ГК быстрее, чем ожидалось.

#### Impact

**Более низкий ISF** (например, 40 вместо 50) означает, что каждая единица инсулина меньше опускает ГК. Это приводит к более агрессивной / сильной коррекции со стороны алгоритма с **бОльшим количеством инсулина**. Если она слишком мала, можно получить низкий уровень ГК.

**Более высокий ISF** (например, 45 вместо 35) означает, что каждая единица инсулина более значительно опускает ГК. Это приводит к менее агрессивной коррекции со стороны алгоритма с **меньшим количеством инсулина**. Если ISF слишком велик, можно получить высокий уровень ГК.

**Пример:**

- ГК - 190 мг/дл (10,5 ммол/л), а цель - 100 мг/дл (5,6 ммол/л). 
- Нужно скорректировать 90 мг/дл (= 190 - 100).
- Чувствитльность ISF = 30 -> 90 / 30 = 3 единицы инсулина
- Чувствитльность ISF = 45 -> 90 / 45 = 2 единицы инсулина

Слишком низкая заданная чувствительность (бывает нередко) может привести к "чрезмерной коррекции" ГК, поскольку AAPS будет считать, что ему нужно больше инсулина для корректировки высокой гликемии, чем на самом деле. Это может привести к «американским горкам» (особенно при голодании). В этом случае нужно увеличить ISF. Тогда ААПС уменьшит корректирующие дозы, что позволит избежать чрезмерной коррекции, которая приводит к низкой ГК.

В то же время, задание слишком высокой чувствительности ISF может привести к недостаточной коррекции, когда ГК останется выше цели, это особенно заметно за ночь.

### Insulin to carb ratio (IC) (g/U)

#### Description & testing

Углеводы в граммах на каждую единицу инсулина.

Некоторые пользователи также используют I:C в качестве сокращения вместо IC или говорят о коэффициенте углеводов (carb ratio, CR).

Полагая, что база задана верно, можно проверить этот коэффициент, убедившись в отсутствии активного инсулина IOB при нормальной гликемии. Для этого надо съесть известную пищу с известным количеством углеводов и подав на нее расчетное количество инсулина, основываясь на текущем соотношении IC. Лучше всего есть пищу, которую вы обычно едите в это время дня и точно посчитать ее углеводы.

> **ПРИМЕЧАНИЕ:**
> 
> В некоторых европейских странах для определения количества инсулина, необходимого для компенсации пищи, использовались т. н. хлебные единицы. В начале 1 хлебная единица равнялась 12г углеводов, позже некоторые стали считать ее как 10 г.
> 
> В такой модели подсчетов количество углеводов было фиксированной величиной, а количество инсулина-переменной. ("Сколько инсулина нужно для того, чтобы компенсировать одну хлебную единицу?")
> 
> При использовании коэффициента инсулин-углеводы IC количество инсулина фиксируется, а количество углеводов становится величиной переменной. ("Сколько грамм углеводов может компенсироваться одной единицей инсулина?")
> 
> Пример:
> 
> Множитель хлебной единицы (ХЕ = 12г. углеводов): 2,4 ед./ХЕ -> Требуется 2,4 ед. инсулина для компенсации одной ХЕ.
> 
> Соответствующее соотношение инсулин-углеводы IC: 12г /2,4 ед -> 5,0 г. углеводов можно компенсировать одной единицей инсулина.
> 
> Множитель ХЕ 2,4 ед/12g ===> IC = 12 г/2,4 ед = 5,0 г/ед
> 
> Таблицы преобразования доступны в Интернете: [ здесь ](https://www.mylife-diabetescare.com/files/media/03_Documents/11_Software/FAS/SOF_FAS_App_KI-Verha%CC%88ltnis_MSTR-DE-AT-CH.pdf).

#### Impact

**Более низкий углеводный коэффициент IC** = меньше еды на единицу инсулина, то есть вы получаете больше инсулина на фиксированное количество углеводов. Может также назваться «более агрессивным».

**Более высокий углеводный коэффициент IC** = больше еды на единицу инсулина, то есть вы получаете меньше инсулина на фиксированное количество углеводов. Может также назваться «менее агрессивным».

Если после усваивания пищи и возвращения активного инсулина IOB к нулю, ГК остается выше чем до еды, высока вероятность того, что IC слишком велик. И наоборот, если ГК ниже, чем перед едой, IC слишком мал.

## APS algorithm

### Why does it show "dia:3" in the "OPENAPS AMA"-tab even though I have a different DIA in my profile?

![Мастер болюса AMA 3 часа](../images/Screenshot_AMA3h.png)

В помощнике болюса AMA "DIA" не означает "длительность действия инсулина". Этот параметр раньше привязывался к длительности действия инсулина DIA. Теперь же он означает, 'время, за которое нужно завершить коррекцию'. Он не имеет ничего общего с расчетом активного инсулина IOB. В алгоритме OpenAPS SMB больше нет необходимости в этом параметре.

### Profile

#### Why using min. 5h DIA (insulin end time) instead of 2-3h?

Хорошо объяснено в [этой статье](https://www.diabettech.com/insulin/why-we-are-regularly-wrong-in-the-duration-of-insulin-action-dia-times-we-use-and-why-it-matters/). Не забудьте `АКТИВИРОВАТЬ ПРОФИЛЬ` после изменения продолжительности действия инсулина DIA.

#### What causes the loop to frequently lower my BG to hypoglycemic values without COB?

В первую очередь, проверьте значения скорости подачи базала и проверьте работу базы безуглеводным test'ом. Если все верно, то такое поведение обычно вызвано слишком низким значением чувствительности к инсулину ISF. Слишком низкая чувствительность ISF обычно выглядит так.

![Чувствительность ISF слишком низкая](../images/isf.jpg)

#### What causes high postprandial peaks in closed loop?

В первую очередь, проверьте значения скорости подачи базала и проверьте работу базы безуглеводным test'ом. Если все правильно, и гликемия падает до целевого значения после полного усвоения углеводов, попробуйте за некоторое время до еды установить временную цель "ожидаемый прием пищи" в AAPS или продумайте подходящее время преболюса с эндокринологом. Если гликемия слишком высока после еды и после полного усваивания углеводов, подумайте о снижении углеводного коэффициента ( соотношения инсулин/углеводы) IC с эндокринологом. Если гликемия слишком высока во время усвоении углеводов COB и слишком низка после их полного усвоения, подумайте об увеличении углеводного коэффициента IC и о надлежащем времени преболюса с эндокринологом.

## Other settings

### Nightscout settings

#### AAPSClient says 'not allowed' and does not upload data. What can I do?

В клиенте NSClient проверьте 'Настройки подключения'. Возможно, вы в закрытой для вас зоне WLAN или активировали опцию "подключаться только при зарядке", а ваш кабель зарядки не подключен.

### CGM settings

#### Why does AAPS say 'BG source doesn't support advanced filtering'?

Если у вас иной источник данных ГК чем Dexcom G5 или G6 в нативном режиме xDrip, вы получите это уведомление на вкладке OpenAPS. See [Smoothing blood glucose data](../CompatibleCgms/SmoothingBloodGlucoseData.md) for more details.

### Pump

#### Where to place the pump?

Есть многочисленные возможности размещения помпы. При этом неважно, пользуетесь вы приложениями ИПЖ или нет.

#### Batteries

Работа в замкнутом цикле быстрее расходует батарею поскольку система больше взаимодействует по блутусу чем обычная помпа в ручном режиме. Лучше менять батарею при 25% так как после этого связь становится труднее. Можно настроить предупредительные сигналы батареи помпы через переменную PUMP_WARN_BATT_P на сайте Nightscout. Способы увеличить срок жизни батареи включают:

- уменьшить длительность работы экрана LCD (в меню настроек помпы)
- уменьшить длительность работы подсветки (в меню настроек помпы)
- выбрать уведомления в виде звукового сигнала а не вибрации (в меню настроек помпы)
- Нажимать кнопки помпы только для перезагрузки; для просмотра журналов, уровня батареи и объема резервуара помпы пользоваться смартфоном с AAPS.
- На некоторых телефонах AAPS периодически закрывается для экономии энергии или высвобождения оперативной памяти. Когда AAPS вновь инициализируется, то при каждом старте устанавливает соединение Bluetooth с помпой и перечитывает текущую базальную скорость и журнал болюсов. Это расходует батарею. Чтобы увидеть, происходит ли это, перейдите в Настройки > NSClient и включите 'Отправлять запись о запуске приложения в NS'. Nightscout будет получать данные о событии при каждом перезапуске AAPS, что облегчит отслеживание проблемы. Чтобы уменьшить расход батареи при таких событиях, включите AAPS в список разрешенных приложений в настройках батареи телефона и тогда монитор расхода энергии перестанет выключать AAPS.
    
    Например, внести в белый список на смартфоне Samsung Android Pie:
    
    - Перейти к параметрам-> Уход за устройством-> Аккумулятор 
    - Прокрутите страницу пока не найдете AndroidAPS и выберите его
    - Снимите флажок с "Переводить приложение в спящий режим
    - Также зайдите в Настройки -> Приложения -> (символ три круга в правой верхней части экрана) выбираем "особый доступ" -> оптимизировать использование батареи
    - Прокрутите страницу до AndroidAPS и убедитесь, что галочка выбора снята.

- протирайте контакты батареи спиртовыми салфетками, чтобы на ней не оставались следы заводской смазки.

- for [Dana R/RS pumps](../CompatiblePumps/DanaRS-Insulin-Pump.md) the startup procedure draws a high current across the battery to purposefully break the passivation film (prevents loss of energy whilst in storage) but it doesn't always work to break it 100%. Либо удалите и заново вставьте батарею 2-3 раза до тех пор, пока на экране помпы заряд батареи не покажет 100%, либо замкните контакты батареи на долю секунды при помощи ключа батареи, чтобы удалить этот налет.
- see also more tips for [particular types of battery](#Accu-Chek-Combo-Tips-for-Basic-usage-battery-type-and-causes-of-short-battery-life)

#### Changing reservoirs and cannulas

Замена картриджей не может осуществляться через AAPS, ее следует как и раньше, делать непосредственно на помпе.

- Нажмите и удерживайте кнопку "Открытый цикл"/"Замкнутый цикл" на вкладке "Главный экран" AAAPS и выберите "Приостановка цикла на 1ч.'
- Отключите помпу и замените резервуар в соответствии с инструкцией помпы.
- Заполнить инфузионный набор можно и непосредственно с помпы. In this case use [PRIME/FILL button](#screens-action-tab) in the actions tab just to record the change.
- После переподключения помпы запустите цикл долгим нажатием на 'Приостановлено (X мин.)'.

Однако замена катетера происходит не через функцию "первичного заполнения инфузионного набора" на помпе, но заполняет катетер с помощью болюса, который не отражается в истории болюса. Это означает, что текущая временная скорость базала не прерывается. On the Actions (Act) tab, use the [PRIME/FILL button](#screens-action-tab) to set the amount of insulin needed to fill the infusion set and start the priming. Если этого количества недостаточно, повторите заполнение. Вы можете установить кнопки по умолчанию в Настройках > Другое > Заполнить/Инициировать стандартные количества инсулина. В инструкции к инфузионному набору вы найдете объемы единиц для первичного заполнения в зависимости от длины иглы и длины трубки.

### Wallpaper

You can find the AAPS wallpaper for your phone on the [phones page](#Phones-phone-wallpaper).

### Daily usage

#### Hygiene

##### What to do when taking a shower or bath?

Помпу можно снять при приеме душа или ванной. За этот короткий промежуток времени вам может не понадобиться, но вы должны сообщить AAPS о том, что отключились для того, чтобы вычисления IOB были правильными. See [description above](#FAQ-disconnect-pump).

#### Work

В зависимости от вида работы, возможно, вы используете иные методы терапии в рабочие дни. As a looper you should consider a [profile switch](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md) for your typical working day. Например, профиль больше 100% можно установить, если работа не очень тяжелая (напр. сидя за столом), или меньше 100%, если вы активны и на ногах весь день. You could also consider a high or low temporary target or a [time shift of your profile](#ProfileSwitch-ProfilePercentage-time-shift-of-the-circadian-percentage-profile) when working much earlier or later than regular, of if you work different shifts. Также можно создать второй профиль (например, дом' и 'работа') и при необходимости переключаться с профиля на профиль.

### Leisure activities

(FAQ-sports)=

#### Sports

Пересмотрите свои старые спортивные привычки доаппсовских времен. Если вы как и прежде съедаете один или несколько углеводов на спорт, теперь система замкнутого цикла распознает их и соответствующим образом скорректирует.

Итак, в организме будет больше углеводов, но в то же время петля будет противодействовать и подавать инсулин.

При работе с алгоритмом ИПЖ следует выполнить следующие действия:

- Make a [profile switch](../DailyLifeWithAaps/ProfileSwitch-ProfilePercentage.md) < 100%.
- Set an [activity temp target](#TempTargets-activity-temp-target) above your standard target.
- If you are using SMB make sure ["Enable SMB with high temp targets"](#Open-APS-features-enable-smb-with-high-temp-targets) and ["Enable SMB always"](#Open-APS-features-enable-smb-always) are disabled.

Важное значение имеет предварительная и последующая обработка этих настроек. Внесите изменения до занятий спортом и учитывайте эффект наполнения мышц.

If you do sports regularly at the same time (i.e. sports class in your gym) you can consider using [automation](../DailyLifeWithAaps/Automations.md) for profile switch and TT. Автоматизация на основе геолокации также неплохая идея, но делает предварительную обработку более сложной.

Процент изменения профиля, величина временной цели при нагрузках и наилучшее время для внесения изменений индивидуальны. Начните с более безопасных параметров (например с низким процентоом профиля и более высокими временными целями).

#### Sex

Можете снять помпу для "свободы" но следует проинформировать об этом AAPS, чтобы расчеты активного инсулина IOB были правильными. See [description above](#FAQ-disconnect-pump).

#### Drinking alcohol

Употребление алкоголя является рискованным в режиме замкнутого цикла, так как алгоритм ИПЖ не может правильно предсказать влияние алкоголя на ГК. Следует выработать свой собственный метод подхода к этому вопросу с помощью следующих функций в AndroidAPS:

- Деактивировать режим замкнутого цикла и разбираться с диабетом вручную или
- устанавливать высокие временные цели и отключать незапланированный прием пищи UAM, чтобы избежать увеличения активного инсулина IOB из-за непредусмотренной еды или
- переключить профиль на величину, заметно менее 100% 

При употреблении алкоголя всегда нужно следить за мониторингом, чтобы вручную избежать гипокликемии, съедая углеводы.

#### Sleeping

##### How can I loop during the night without mobile and WIFI radiation?

Многие пользователи ночью переводят телефон в режим авиаперелета. If you want the loop to support you when you are sleeping, proceed as follows (this will only work with a local BG-source such as xDrip+ or ['Build your own Dexcom App'](#DexcomG6-if-using-g6-with-build-your-own-dexcom-app), it will NOT work if you get the BG-readings via Nightscout):

1. Включите режим авиаперелета на вашем мобильном устройстве.
2. Подождите, пока режим авиаперелета не будет активирован.
3. Включите Блутус.

Теперь вы не принимаете звонки и не подключены к Интернету. Но цикл продолжает работу.

У некоторых пользователей обнаружились проблемы с локальной трансляцией (AAPS не получает данные от xDrip+) в режиме авиаперелета. Перейдите в Настройки xdrip+ > Inter-app settings > Identify receiver и введите `info.nightscout.androidaps`.

![xDrip+ Inter-app Settings Identify receiver](../images/xDrip_InterApp_NS.png)

#### Travelling

##### How to deal with time zone changes?

Если у вас DanaR или DanaR для корейского рынка делать ничего не надо. For other pumps see [time zone travelling](../DailyLifeWithAaps/TimezoneTraveling-DaylightSavingTime.md) page for more details.

### Medical topics

#### Hospitalization

Если вы хотите поделиться информацией об AndroidAPS и ИПЖ с врачами, можете распечатать [руководство по AAPS для медработников](../Resources/clinician-guide-to-AndroidAPS.md).

#### Medical appointment with your endocrinologist

##### Reporting

Вы можете либо распечатать отчеты вашего сайта Nightscout (https://вашсайт.com/report) или перейти в [Nightscout Reporter](https://nightscout-reporter.zreptil.de/).

## Frequent questions on Discord and their answers...

### My problem is not listed here.

[Информация о получении помощи.](../GettingHelp/WhereCanIGetHelp.md)

### My problem is not listed here but I found the solution

[Информация о получении помощи.](../GettingHelp/WhereCanIGetHelp.md)

**Напомните нам о добавлении вашего решения в этот список!**

### AAPS stops everyday around the same time.

Остановите защиту Google Play Protect. Проверьте "очистку" приложений (при помощи CCleaner и т. д.) и удалите их. AAPS / 3 точки меню / О программе / Перейдите по ссылке "Работать в фоновом режиме" и остановите все оптимизации батареи.

### How to organize my backups ?

Регулярно экспортируйте настройки: после замены каждого пода, после изменения профиля, когда подтверждено прохождение цели, если заменили помпу… Даже если ничего не изменится, экспортируйте настройки раз в месяц. Сохраняйте несколько старых файлов экспорта.

Скопируйте на интернет-диске (Dropbox, Google etc) : все приложения, которые использовали для установки приложений на телефон (AAPS, xDrip, BYODA, Patched LibreLink…), а также экспортированные настройки из всех этих приложений.

### I have problems, errors building the app.

Пожалуйста,

- check [Troubleshooting Android Studio](../GettingHelp/TroubleshootingAndroidStudio) for typical errors and
- [пошаговые инструкции](https://docs.google.com/document/d/1oc7aG0qrIMvK57unMqPEOoLt-J8UT1mxTKdTAxm8-po).

### I'm stuck on an objective and need help.

Сохраните экран вопросов и ответов. Отправьте сообщение на канал Discord AAPS. Не забудьте указать какие опции вы выбираете (или нет) и почему. Вы получите подсказки и помощь, но ответы надо найти самостоятельно.

### How to reset the password in AAPS v2.8.x ?

Откройте меню hamburger, запустите мастер настройки и введите новый пароль по запросу. Вы можете выйти из мастера после установки нового пароля.

### How to reset the password in AAPS v3.x

You find the documentation [here](#Update3_0-reset-master-password).

### My link/pump/pod is unresponsive (RL/OL/EmaLink…)

На некоторых телефонах Bluetooth разъединяется с Link (RL/OL/EmaL...).

Некоторые также отмечают плохую коммуникацию с RileyLink (AAPS сообщает, что они подключены, но не выполняют команды)

Самый простой способ заставить эти части работать - : 1/ Стереть Link из AAPS 2 / Отключить питание Link 3/выйти из AAPS через 3-точечное меню программы 4/ Долгое нажатие на значок AAPS, меню Android, информация о приложении AAPS, Принудительно остановить AAPS и затем очистить память кэша (Не удаляйте основную память !) 4bis/ Некоторым телефонам после этого может понадобиться перезагрузка здесь. Можно попробовать без перезагрузки. 5/ Включить Link 6/Запустить AAPS 7/Вкладка Pod, меню 3 точки, поиск и подключение (Riley)Link

### Build error: file name too long

Во время сборки программы получаю ошибку, что имя файла слишком длинное. Возможные решения: Переместите источники в директорию ближе к корневой директории диска (например "c:\src\AndroidAPS-EROS").

Из Android Studio: Убедитесь, что "Gradle" завершил синхронизацию и индексирование после открытия проекта с GitHub. Выполните Build->Clean Project прежде чем выполнять Rebuild Project. Выполните команду File>Инвалидация кэша и перезагрузите Android Studio.

### Alert: Running dev version. Closed loop is disabled

AAPS не работает в "режиме разработчика". AAPS показывает сообщение: "запуск dev версии. Замкнутый цикл отключен".

Убедитесь, что AAPS запущен в "режиме разработчика": Поместите файл с именем "engineering_mode" в папку "AAPS/extra". Любой файл подойдет если он назван правильно. Обязательно перезапустите AAPS, чтобы найти файл и перейти в "режим разработчика".

Совет: сделайте копию существующего лог-файла и переименуйте его в "engineering_mode" (примечание: без расширения!).

### Where can I find settings files?

Файлы настроек будут храниться во внутреннем хранилище телефона в каталоге "/AAPS/preferences". ВНИМАНИЕ: Убедитесь что помните пароль, без него вы не сможете импортировать зашифрованный файл настроек!

### How to configure battery savings?

Правильная настройка управления питанием важна для предотвращения остановки AAPS и связанных с ним приложений и служб, когда телефон не используется. Если не сделать этого, AAPS не сможет выполнить соединения по Bluetooth с сенсором и Rileylink (RL) может быть выключен, что приведет к "отключению "помпы" оповещений "помпа недоступна" и ошибкам связи. На телефоне перейдите в Настройки->Приложения и отключите экономию заряда батареи для AAPS xDrip или самостоятельно собранное приложение BYODA/Dexcom Системное приложение Bluetooth (возможно, необходимо сначала выбрать системные приложения) Или полностью отключить все энергосбережения на телефоне. В результате батарея может разряжаться быстрее, но вы смжете выяснить, не вызывается ли проблема экономией заряда аккумулятора. Способ экономии аккумулятора в значительной степени зависит от марки телефона, модели и/или версии операционной системы. Из-за этого почти невозможно дать инструкции по правильной настройке экономии заряда аккумулятора. Экспериментируйте, чтобы выяснить, какие настройки лучше для вас. Дополнительную информацию см. также в "Не закрывать приложение"

### Pump unreachable alerts several times a day or at night.

Ваш телефон может останавливать службы AAPS или даже Bluetooth, что приведет к потере соединения с RL (см. экономия батареи) Настройте оповещения о недоступносте на 120 минут, перейдя в верхнее правое меню, выберите Настройки->Локальные оповещения>Порог недоступности помпы[min].

### Where can I delete treatments in AAPS v3 ?

3 точки меню, выберите терапия, затем меню настроек, и получите различные возможные варианты.

### Configuring and Using the AAPSClient remote app

AAPS можно удаленно контролировать через приложение AAPSClient и, при необходимости, через связанное с ним приложение Wear, работающее на часах Android Wear. Обратите внимание, что приложение AAPSClient (дистанционное) отличается от конфигурации NSClient в AAPS, а приложение AAPSClient (дистанционное) Wear отличается от приложения AAPS Wear - для ясности приложения дистанционного управления будут называться 'AAPSClient дистанционный' и 'AAPS Wear дистанционный'.

Чтобы включить дистанционный функционал на AAPSClient дистанционном надо: 1) Установите приложение AAPSClient дистанционный (версия должна совпадать с используемой версией AAPS) 2) Запустите приложение AAPSClient и в мастере настройкипредоставить необходимые разрешения и настройки доступа к вашему сайту Nightscout. 3) На данном этапе вы можете отключить некоторые оповещения, и/или дополнительные настройки, которые регистрируют запуск дистанционного приложения AAPSClient на вашем сайте Nightscout. После этого, дистанционный AAPSClient загрузит данные профиля с сайта Nightscout, на вкладке «Обзор» будут отображаться данные CGM и некоторые данные AAPS, но может не отображать графические данные и указывать, что профиль еще не установлен. 4) Для активизации профиля:

- Включите дистанционную синхронизацию профиля в AAPS > NSClient > Опции
- Активируйте профиль в NSClient дистанционный > Профиль После этого, профиль будет установлен, и AAPSClient дистанционный должен отображать все данные из AAPS. Подсказка: Если график долго отсутствует, попробуйте изменить настройки готображения графика для вызова обновления. 5) Для включения дистанционного управления AAPSClient, выборочно включите настройки AAPS (изменения профиля, Временные Цели, Углеводы и т. д. которыми хотите дистанционно управлять с помощью AAPS > NSClient > Опции . После внесения этих изменений вы сможете дистанционно управлять AAPS с помощью Nightscout или AAPSClient дистанционного.

Если вы хотите контролировать AAPS с помощью приложения AAPSClient Wear дистанционнго, вам понадобится установить AAPSClient дистанционный и соответствующее приложение Wear. Чтобы скомпилировать дистанционное приложение AAPSClient Wear, следуйте стандартным инструкциям по установке/настройке приложения AAPS wear, но при компиляции, выберите вариант AAPSClient.

### I have a red triangle / AAPS won't enable closed loop / Loops stays in LGS / I have a yellow triangle

Красный и желтый треугольники являются функцией безопасности в AAPS v3.

Красный треугольник означает, что у вас есть дубликаты данных ГК, и AAPS не может точно рассчитать приращение (дельту). При этом невозможно замкнуть цикл. Чтобы очистить красный треугольник, нужно удалить каждое дублируемое значение ГК. Перейдите на вкладку BYODA или xDRIP, долгое нажатие на одну линию, которую вы хотите удалить, пометьте одну из строк, которые задвоены (или через 3 точки меню и Delete, в зависимости от вашей версии AAPS). Если слишком много двойных ГК потребуется сбросить базы данных AAPS,. При этом вы также потеряете статистику, IOB, COB, выбранный профиль.

Возможные причины проблемы: xDrip и/или NS достраивают пропущенные ГК.

Желтый треугольник означает нестабильную задержку между показаниями ГК. Вы не получаете данные каждые 5 минут или ГК отсутствуют. Это зачастую проблема Libre. Это также происходит, когда вы меняете трансмиттер G6. Если желтый треугольник связан с заменой трансмиттера G6, он уйдет сам по себе через несколько часов (около 24 часов). Если у вас Libre, желтый треугольник останется. Цикл может быть замкнут и будет работать правильно.

### Can I move an active DASH Pod to other hardware?

Это возможно. Обратите внимание, что такие действия "не поддерживаются" и "не протестированы", поэтому существует некоторый риск. Лучше всего попробовать процедуру, когда Pod заканчивает срок, так что если что-то пойдёт не так, потери будут невелики.

Критично то, что "состояние" помпы (которое включает в себя MAC-адрес) в AAPS и DASH совпадали при переподключении

### Procedure I follow in this:

1) Приостанавливаю DASH. Это гарантирует, что при потере соединения DASH не будет запущенных или отложенных команд, 2) Перевожу телефон в режим авиаперелета чтобы отключились BT ( а также WiFi и мобильные данные). Таким образом, гарантируется AAPS и DASH не будут обмениваться данными. 3) Выполняю экспорт настроек (включая состояние DASH) 4) Копирую файл настроек, только что экспортированный с телефона (так как он находится в режиме полета, который мы не хотим изменять, проще всего использовать USB-кабель) 5) Копирую файл настроек на другой телефон. 6) Импортирую настройки на другой телефон с AAPS. 7) Проверяю вкладку DASH, чтобы убедиться, что смартфон видит Pod. 8) Возобновляю работу Pod. 9) Проверяю вкладку DASH и убеждаюсь, что работает связь с Pod (использую кнопку обновления)

Поздравляем! Все получилось!

*Минутку!!* Ваш прежний телефон все еще считает, что он может подсоединиться к тому же DASH:

1) На главном телефоне выберите "деактивировать". Это безопасно, потому что телефон не имеет способа связи с DASH для фактического отключения Pod (он все еще находится режиме полета) 2. Деактивация приведет к ошибке связи - это ожидаемо. 3) Просто нажмите "повторить" пару раз до тех пор, пока AAPS не предложит опцию "Завершить пользование" POD'ом.

По завершении убедитесь, что AAPS на прежнем телефоне сообщает, что «Нет активного Pod». Теперь вы можете безопасно отключить режим полета.

### How do I import settings from earlier versions of AAPS into AAPS v3 ?

Можно импортировать только те настройки, которые были экспортированы с помощью AAPS v2.8 или v3.x), Если у вас версия AAPS старше v2,8x, или вам нужны настройки версии старше 2.8x,то сначала придется установить версию v2.8. Импортирeqnt старые настройки v2.x в v2.8. После проверки,что все в порядке, можно экспортировать настройки из v2.8 Установите AAPS v3 и импортируйте настройки v2.8 в v3.

Если вы используете один и тот же ключ для сборки v2.8 и v3, вам не придется импортировать настройки. Можно установить v3 поверх версии 2.8.

Появились новые цели. Нужно будет их подтвердить.