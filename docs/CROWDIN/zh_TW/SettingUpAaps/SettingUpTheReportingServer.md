# 設置報告伺服器

目前有兩個報告伺服器可供 **AAPS** 使用：

- [Nightscout](https://nightscout.github.io/)
- [Tidepool](https://www.tidepool.org/)

![報告伺服器](../images/Building-the-App/ReportingServer.png)

我們推薦使用Nightscout。

## Nightscout

Nightscout是一個強大的平台，多年來已經整合進了 **AAPS**。 他使用戶和照護者能夠近乎實時地追蹤病患的糖尿病資料（如果所有相關組件之間有足夠的網際網路連線，資料接收和提供之間只會有幾分鐘的延遲）。 他還允許照護者向 **AAPS** 發送遠端指令。

Nightscout是一個開源軟體。 任何人都可以使用免費或付費服務建立和運作一個Nightscout伺服器。

### 選項1 - 自行設置你的Nightscout伺服器

建立你的Nightscout報告伺服器可能需要一個或多個基於網路的應用程式，這些應用程式需要維護。 為了獲得完全免費的服務，當提供商移除免費方案時，你可能需要遷移你的Nightscout網站和資料。

有關如何設置Nightscout及各種操作選項的優缺點的描述，包括成本估算，可以在[這裡](https://nightscout.github.io/nightscout/new_user/#free-diy)找到。

### 選項2 - 付費使用託管Nightscout服務

也有不同服務提供商提供的託管Nightscout選項，按月收費。 成本是可負擔的，託管選項的好處是你無需具備IT知識或任何操作基礎設施。

現有的Nightscout用戶可以不時重新考慮Nightscout伺服器的託管方式，並根據需要切換到更合適的選項。

一些託管Nightscout服務列在[這裡](https://nightscout.github.io/nightscout/new_user/#vendors-comparison-table)。

### Further configuration of Nightscout

One you have your Nightscout instance up and running, see [Nightscout configuration page](../SettingUpAaps/Nightscout.md) for additional considerations.

## Tidepool

Tidepool自 **AAPS** 3.2版本（2023年末釋出）以來才可用。

```{admonition} Tidepool with **AAPS** is only for reporting
:class: danger  
由於使用 **AAPS** 時資料進來和資料報告之間有三小時的延遲，Tidepool 不適合用來與照護者分享即時資訊。
另一方面，如果 Nightscout 不是被接受的解決方案，Tidepool 可以是與病人的內分泌科醫生共享報告的絕佳方案。
```

Tidepool是一個[開源](https://github.com/tidepool-org)專案。 他提供在Tidepool伺服器上免費運作帳號的選項。

More information about setting up Tidepool with AAPS [here](../SettingUpAaps/Tidepool.md).

```{admonition} **AAPS** has a the uploader for Tidepool integrated
:class: note
你**不需要**使用上傳應用程式到 Tidepool：**AAPS** 會為你上傳血糖、治療和基礎胰島素。你只需擁有一個 Tidepool 的個人帳號即可。請勿使用單獨的 Tidepool 上傳工具來上傳你的資料，因為這會導致重複的數值。
```

## Next step

Once you have set up your reporting server, you can now either set up a [dedicated Google account for AAPS use](../SettingUpAaps/DedicatedGoogleAccountForAaps.md), or go straight to [building the AAPS app](../SettingUpAaps/BuildingAaps.md).