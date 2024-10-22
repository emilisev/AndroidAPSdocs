# **Freestyle Libre 3**

Libre 3 Freestyle (FSL3) требует уникальной настройки для получения ГК в AAPS. Есть два возможных способа получения ГК с Freestyle Libre 3 (FSL3) в AAPS.

![FL3](../images/d912c1d3-06d2-4b58-ad7c-025ca1980fae.jpeg)

**Версия 3.2.0.1 AndroidAPS не поддерживает 1-минутные значения. Ускорение и сглаживание не работает с 1-минутными значениями.**

Ниже приведены способы достижения этой цели с при помощи приложения Juggluco. Эти методы основаны на том, что Juggluco получает с сенсора необработанные данные с 1-минутным интервалом, которые затем передаются в xDrip+ или AAPS. Новые сенсоры можно запустить с помощью приложения Libre 3 или непосредственно в Juggluco. В инструкции ниже показан процесс запуска сенсора в приложении Juggluco. Если сенсор был запущен в системе с учетной записи Libreview, то также можно переключаться между приложениями Juggluco и Libre 3 в качестве приемника.

При запуске сенсора в приложении Libre 3 Juggluco также может передавать данные LibreView для обмена с медицинскими учреждениями.

В рамках программы xDrip+ сенсор может быть откалиброван в диапазоне от -40 мг/дл до +20 мг/дл (-2.2 ммоль/л до +1.1 ммоль/л) для корректировки различий между замерами глюкометра и показаниями сенсора.

## Метод 1: 1-минутные замеры
Версия 3.2.0.1 AndroidAPS не поддерживает 1-минутные значения. Ускорение и сглаживание не работает с 1-минутными значениями.

![Juggluco broadcast to AAPS](../images/Juggluco_AAPS.png)


## Метод 2: 5-минутные замеры
Каждую минуту Juggluco получает необработанные данные с сенсора, которые затем передаются xDrip+ для сглаживания в 5-минутном интервале, которые в свою очередь передаются в AAPS.

### Шаг 1: Настройка Juggluco
Скачайте и установите приложение Juggluco [отсюда](https://www.juggluco.nl/Juggluco/download.html). Следуйте [этой](https://www.juggluco.nl/Juggluco/libre3/) инструкции

Убедитесь, что данные ГК отправляются в Xdrip+: В настройках Juggluco можно выбрать отправку значений глюкозы другим приложениям. Juggluco может отправить три типа трансляций: Трансляция **Librelink** изначально использовалась модифицированным приложением Librelink и может отправлять значения Гк в xDrip+

![Трансляция Juggluco в xDrip+](../images/Juggluco_xDrip.png)

### Шаг 2: Настройка xDrip

Приложение xDrip+ получает значения ГК на телефоне.

- If not already set up then download [xDrip+](https://github.com/NightscoutFoundation/xDrip) and follow the instructions on [xDrip+ settings page](../CompatibleCgms/xDrip.md).
- В xDrip+ в качестве источника данных выберите "Libre (patched app)".
- При необходимости введите "BgReading:d, xdrip libr_receiver:v" в разделе Менее распространенные настройки -Дополнительные настройки журналирования- Дополнительные теги для добавления в журнал. Это позволит записывать дополнительные сообщения об ошибках для устранения неисправностей.

![xDrip+ LibreLink журналы](../images/Libre2_Tags.png)

- Технически, текущее значение сахара в крови передается на xDrip + каждую минуту. По умолчанию фильтр средневзвешенного значения вычисляет сглаженное значение за последние 25 минут. Этот период можно изменить в меню функций сканирования NFC.

  → Сэндвич-меню → Настройки →Функция сканирования NFC→ Сглаживать данные libre 3 при использовании метода xxx

  ![xDrip + дополнительные параметры Libre 2 & необработанные данные](../images/xDrip_Libre3_Smooth.png)



### Шаг 3: Запуск сенсора в xDrip

В xDrip+ запустите сенсор с помощью "Start Sensor" и "not today". Нет необходимости прикладывать мобильный телефон к сенсору. На самом деле "Запуск сенсора" физически не запускает сенсор Libre3 и не начинает взаимодействие с ним. Это нужно для того, чтобы указать xDrip+, что новый сенсор начал передавать данные ГК. Если доступно, введите два замера крови для начальной калибровки. Теперь значения глюкозы крови должны отображаться в xDrip+ каждые 5 минут. Пропущенные данные, например из-за того, что вы были далеко от телефона, не будут восстановлены.

Подождите не менее 15-20 минут, если данных нет.

После смены сенсора xDrip+ автоматически определит новый и удалит все данные калибровки. После активации измерьте ГК и сделайте первоначальную калибровку.

### Шаг 4: Настройка AndroidAPS

- Select xDrip+ in [ConfigBuilder, BG Source](../SettingUpAaps/ConfigBuilder.md#bg-source).

- Если AndroidAPS не получает значения BG, когда телефон находится в режиме авиаперелета, проверьте, заполнено ли поле «Идентифицировать приемник»
- Выключите сглаживание (уже сделано в Xdrip+)

На данный момент при использовании Libre 3 в качестве источника ГК в алгоритме SMB невозможно включить опцию "Всегда включать SMB" и "Включать SMB после углеводов". Значения ГК Libre 3 недостаточно сглажены для безопасного пользования.



## Последующие замены сенсора

1. Откройте Juggluco и посмотрите серийный номер текущего сенсора

![Серийный номер Libre](../images/libre3/step_13.jpg)

2. Теперь просто сканируйте новый сенсор с помощью NFC телефона. Juggluco покажет уведомление, если процесс запущен успешно.
3. Когда вы готовы деактивировать старый сенсор, откройте меню Juggluco, щелкнув в любом месте в левом верхнем углу экрана.
4. Выберите истекший сенсор и нажмите "Прервать"

![Завершить работу сенсора](../images/libre3/step_14.jpg)

Примечание: Когда активны два сенсора, Juggluco будет отправлять наиболее свежие значения с любого сенсора на xDrip+. Если сенсоры не откалиброваны и соответствующим образом считывают ГК, это может вызвать скачущие значения в xDrip+. Если вы остановите неправильный сенсор, то сможете снова активировать его, просто просканировав сенсор.

## Переключение сенсора между Libre 3 и Juggluco

Если сенсор был запущен в системе с учетной записи Libreview, то также можно переключаться между приложениями Juggluco и Libre 3 в качестве приемника. Для этого требуются следующие шаги:

1. Установите приложение Libre 3 из Google Play
2. Настройте приложение Libre 3 с помощью учетной записи Libreview, которой активирован сенсор.
3. В настройках Android принудительно остановите Juggluco.
4. В меню Libre 3 нажмите кнопку "Запустить сенсор", выберите "Да", "Далее" и отсканируйте сенсор.
5. Через несколько минут данные ГК должны быть видны в приложении Libre 3.

Чтобы перейти с приложения Libre 3 на Juggluco, нужно принудительно остановить Libre 3 через настройки Android и перейти к Шагу 1 & 2.

## Опыт и устранение неполадок

### Устранение неполадок Libre3 -> Подключение Juggluco

- Убедитесь, что используете текущую версию приложения Juggluco
- Проверьте настройки в соответствии с этой инструкцией
- Иногда вам придется принудительно остановить приложение Libre 3 и/или Juggluco и перезапустить его/их.
- Отключите Bluetooth, подождите 10 секунд и снова включите его
- Подождите некоторое время или попробуйте закрыть Juggluco
- Более старые версии Juggluco (ниже 2.9.6) не посылают последующие данные с сенсора Libre3 на подключенные устройства (например, Juggluco на WearOS). Может потребоваться нажать кнопку «Повторно отправить данные» в модифицированном приложении Libre3 (из меню Juggluco).

### Дальнейшая помощь

Оригинальная инструкция: [jkaltes website](https://www.juggluco.nl/Juggluco/libre3/)

Дополнительный репозиторий на Github: [ссылка на Github](https://github.com/maheini/FreeStyle-Libre-3-patch)