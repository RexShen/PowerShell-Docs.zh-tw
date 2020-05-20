---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 從管線中移除物件 Where Object
ms.openlocfilehash: 370e7745341b70c0794352a690d5750d21f53ac2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737180"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>從管線中移除物件 (Where-Object)

在 PowerShell 中，您通常會產生並沿著管線傳遞比所需更多的物件。 您可以使用 `Format-*` Cmdlet 來指定要顯示的特定物件屬性，但這樣做並無法解決從顯示中移除整個物件的問題。 您可能需要在結束管線之前篩選物件，以便只對初始產生的物件子集執行動作。

PowerShell 包含了 `Where-Object` Cmdlet，可讓您測試管線中的每個物件，並只在符合特定測試條件時才沿著管線傳遞。 未通過測試的物件會從管線中移除。 您需提供測試條件作為 **FilterScript** 參數的值。

## <a name="performing-simple-tests-with-where-object"></a>使用 Where-Object 執行簡單的測試

**FilterScript** 的值是評估為 true 或 false 的「指令碼區塊」  (以大括弧 `{}` 括住的一或多個 PowerShell 命令)。 這些指令碼區塊可以很簡單，但若要建立它們，需要了解另一個 PowerShell 概念：比較運算子。 比較運算子會比較出現在運算子兩側的項目。 比較運算子是以連字號字元 (`-`) 開頭，後面接著名稱。 基本比較運算子適用於幾乎任何類型的物件。 更進階的比較運算子只適用於文字或陣列。

> [!NOTE]
> 根據預設，搭配文字使用時，PowerShell 比較運算子不區分大小寫。

基於剖析考量，不會使用 `<`、`>` 和 `=` 等符號作為比較運算子。 相反地，比較運算子是由字母所組成。 下表列出基本比較運算子。

| 比較運算子 |                  意義                   |    範例 (傳回 true)    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| -eq                 | 等於                                | 1 -eq 1                      |
| -ne                 | 不等於                            | 1 -ne 2                      |
| -lt                 | 小於                               | 1 -lt 2                      |
| -le                 | 小於或等於                   | 1 -le 2                      |
| -gt                 | 大於                            | 2 -gt 1                      |
| -ge                 | 大於或等於                | 2 -ge 1                      |
| -like               | 像是 (文字的萬用字元比較)     | "file.doc" -like "f*.do?"    |
| -notlike            | 不像是 (文字的萬用字元比較) | "file.doc" -notlike "p*.doc" |
| -contains           | 包含                                   | 1,2,3 -contains 1            |
| -notcontains        | 不包含                           | 1,2,3 -notcontains 4         |

`Where-Object` 指令碼區塊使用特殊變數 `$_` 來參照管線中目前的物件。 以下示範其運作方式。 如果您有一份數字清單，而且只想要傳回小於 3 的數字，您可以輸入下列命令以使用 `Where-Object` 來篩選數字︰

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>根據物件屬性篩選

因為 `$_` 參照了目前的管線物件，所以我們可以針對測試來存取其屬性。

舉例來說，我們可以檢視 WMI 中的 **Win32_SystemDriver** 類別。 一部系統上可能會有數百個系統驅動程式，但您可能只對某一組系統驅動程式感興趣，例如目前執行中的驅動程式。 針對 **Win32_SystemDriver** 類別，相關屬性為 **State**。 您可以輸入下列命令來篩選系統驅動程式，只選取執行中的驅動程式︰

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

這仍會產生一長串清單。 您可以一併測試 **StartMode** 值，以篩選成只選取設定為自動啟動的驅動程式：

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

因為我們知道驅動程式正在執行，所以這會提供許多不再需要的資訊。
事實上，我們此時可能只需要名稱和顯示名稱資訊。 下列命令只會包含這兩個屬性，以產生更簡單的輸出︰

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

上述命令中有兩個 `Where-Object` 元素，但可使用 `-and` 邏輯運算子以單一 `Where-Object` 元素來表示它們，就像這樣︰

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

下表列出標準邏輯運算子。

| 邏輯運算子 |                 意義                  |  範例 (傳回 true)  |
| ---------------- | ---------------------------------------- | ------------------------ |
| -and             | 邏輯 and；若兩側為 true 即為 true | (1 -eq 1) -and (2 -eq 2) |
| -or              | 邏輯 or；若任一側為 true 即為 true  | (1 -eq 1) -or (1 -eq 2)  |
| -not             | 邏輯 not；將 true 與 false 反轉     | -not (1 -eq 2)           |
| \!               | 邏輯 not；將 true 與 false 反轉     | \!(1 -eq 2)              |
