(Open-APS-features-DynamicISF)=
## 動態胰島素敏感因子 (DynISF)
**動態 ISF** 在**AAPS** 版本 3.2 中添加，需要在啟動**動態 ISF**之前啟動目標 11。 在組態建置工具中選擇**動態 ISF**以啟用。 **動態 ISF** 只建議給**AAPS** 控制及監控有良好掌握的進階使用者。

要有效使用**動態 ISF**，**AAPS** 資料庫需要至少五天的 **AAPS** 資料。

**動態 ISF** 根據使用者的以下指標動態調整使用者的胰島素敏感性因子（**ISF**）：

- 每日胰島素總量（**TDD**）；以及
- 目前和預測的血糖值。

**動態 ISF** 使用 Chris Wilson 的模型來決定**ISF**，而不是用戶的靜態**設定檔**中的**ISF** 設定。

所實現的**動態 ISF**方程式為：ISF = 1800 / (TDD * Ln ((血糖 / 胰島素除數) +1 ))

![截圖 2024-10-19 145120](https://github.com/user-attachments/assets/472627ef-047f-438d-ba30-eba75eeaff97)





此實現使用上述方程計算當前的**ISF**，還有 oref1 針對**IOB**、**ZT** 和**UAM**的預測。 它不會用於**COB**。  進一步的討論可以在這裡找到：https://www.youtube.com/watch?v=oL49FhOts3c。

### TDD（每日總胰島素劑量）
TDD 將使用以下數值的組合：
1.  7 天平均**TDD**;
2.  前一天的**TDD**; 和
3.  最近八（8）小時的胰島素使用的加權平均值，推算為 24 小時。

上面方程中使用的**TDD**將對上述每個值各加權三分之一。

### 胰島素除數
胰島素除數取決於所使用胰島素的峰值，且與峰值時間成反比。 對於 Lyumjev，該值為 75；對於 Fiasp 為 65；對於普通速效胰島素則為 55。

### 動態胰島素敏感因子調整係數
調整因子允許用戶指定一個介於 1% 和 300% 之間的值。 這作為**TDD**值的乘數，導致**ISF**值變得*更小*（即需要更多胰島素以小幅度改變血糖水平），當該值超過 100% 時，以及*更大*（即需要較少的胰島素以小幅度改變血糖水平），當該值低於 100% 時。

調整因子位於「偏好設定」 > **AAPS**:

![截圖 2024-10-19 134558](https://github.com/user-attachments/assets/4b563c64-a924-49d3-904b-4e6fdb4dcc67)


### 未來胰島素敏感因子

未來**ISF** 將用於 oref1 制定的劑量決策。  未來的**ISF**使用與上述生成的相同**TDD**值，並考慮調整因子（如上所述）。 接著依據不同情況使用不同的血糖值：

* 如果血糖值穩定，在 +/- 3 mg/dl 之內，且預測的**BG**高於目標，則使用預測**BG**和當前**BG**的 50% 組合。

* 如果最終**BG**高於目標且血糖水平正在上升，或者最終**BG**高於當前**BG**，則使用當前**BG**。

否則，將使用最低預測的**BG**。

### 啟用基於 TDD 的敏感性比率來調整基礎胰島素和血糖目標

此設定取代 Autosens，並使用過去 24 小時**TDD** / 7D **TDD** 作為增加和減少基礎率的依據，與標準 Autosens 的做法相同。 若選項中啟用根據敏感性調整目標，則此計算值也會用來調整目標值。 與 Autosens 不同，此選項不調整**ISF**值。

### 小心 - 自動化或設定檔百分比增加
**自動化**應始終謹慎使用。 這對於**動態 ISF**尤其如此。

如果**動態 ISF**正在運作，用戶應重新考慮啟用任何臨時**設定檔**的增加作為**自動化**規則，或同樣啟動**設定檔百分比**，這可能使**動態 ISF**在校正注射上過於激烈，並可能導致低血糖。