- - -
orphan: true
- - -

# Dexcom G7 и ONE+


## Основательно и перспективно

Следует отметить, что системы G7 и ONE+, в отличие от G6, не сглаживают значения ГК ни в самом приложении, ни в считывателе. Подробнее об этом [здесь](https://www.dexcom.com/en-us/faqs/why-does-past-cgm-data-look-different-from-past-data-on-receiver-and-follow-app).

![G7 английский](../images/6fe30b84-227a-4bae-a9a5-527cee341dbf.png)

```{admonition} [Smoothing method](../CompatibleCgms/SmoothingBloodGlucoseData.md)
:class: предупреждение
**Среднее сглаживание или экспоненциальное сглаживание** **ДОЛЖНО быть включено для получения корректных значений G7 / ONE+.  
```

## 1. xDrip+ (прямое соединение с G7 или ONE+)

- Следуйте инструкциям здесь: [Xdrip+ G7](https://navid200.github.io/xDrip/docs/Dexcom/G7.html)
- В [Конфигураторе, Источник ГК](#Config-Builder-bg-source) выберите xDrip+.

- Отрегулируйте параметры xDrip+ в соответствии с пояснениями на странице настроек xDrip+  [настройки xDrip+](../CompatibleCgms/xDrip.md)

## 2.  Модифицированное приложение Dexcom G7 (DiAKEM)

**Примечание: Требуется AAPS 3.2.0.0 или выше! Недоступно для ONE+.**

### Установите новое модифицированное (!) приложение G7 и запустите сенсор

Модифицированное приложение Dexcom G7 (DiAKEM) обеспечивает доступ к данным Dexcom G7. Это приложение отличается от самостоятельно собранного приложения Dexcom BYODA; BYODA не может получать данные G7.

- Удалите оригинальное приложение Dexcom, если вы его использовали прежде (Рабочая сессия сенсора может продолжаться - запишите код сенсора перед удалением приложения!)

- Скачайте и установите установочный файл модифицированного приложения [здесь](https://github.com/authorgambel/g7/releases) или [здесь](https://github.com/emmatovar27/dexcom-g7-apk-patcher/releases).

- Введите код сенсора в модифицированном приложении.

- Следуйте общим рекомендациям по гигиене НМГ и установке сенсора, которые можно найти [здесь](../CompatibleCgms/GeneralCGMRecommendation.md).

- После фазы прогрева, данные ГК отображаются как обычно в приложении G7.

### Конфигурация в AAPS

- Выберите самостоятельно собранное приложение 'BYODA' в [конфигураторе, источник ГК](#Config-Builder-bg-source)- даже если это не BYODA!

- Если AAPS не получает данных ГК, переключитесь на другой источник ГК, а затем снова на 'BYODA'.

## 3. xdrip+ (режим спутника)

-   Скачайте и установите xDrip+: [xDrip](https://github.com/NightscoutFoundation/xDrip)
- В качестве источника данных в Xdrip должен быть выбран "Companion App" в разделе Менее распространенные настройки > Настройки Bluetooth > поставьте галочку рядом с "Companion Bluetooth".
-   В [Конфигураторе, Источник ГК](#Config-Builder-bg-source) выберите xDrip+.

-   Отрегулируйте параметры xDrip+ в соответствии с пояснениями на странице настроек xDrip+  [настройки xDrip+](../CompatibleCgms/xDrip.md) 
