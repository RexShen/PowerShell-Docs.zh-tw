# Convert-String
**Convert-String** 公開「像變魔術一樣取代」的功能。 提供範例說明您希望轉換前後文字長什麼樣子，**Convert-String** 就會自動設定文字的格式。 以下是示範，輸入某人的名字和姓氏，然後取代為姓氏、逗號、名字首字母和一個點。 試試看使用 Regex，就會知道要花多久時間。

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
<!--HONumber=Mar16_HO2-->
