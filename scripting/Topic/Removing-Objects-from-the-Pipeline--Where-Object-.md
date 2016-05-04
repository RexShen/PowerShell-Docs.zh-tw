---
title: 從管線中移除物件 (Where-Object)
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
---
# 從管線中移除物件 (Where-Object)
在 Windows PowerShell 中，您通常會產生並沿著管線傳遞比所需更多的物件。 您可以使用 **Format** Cmdlet 指定要顯示的特定物件屬性，但這樣做並無法解決從顯示中移除整個物件的問題。 您可能需要在結束管線之前篩選物件，以便只對初始產生的物件子集執行動作。

Windows PowerShell 包含 **Where-Object** Cmdlet，可讓您測試管線中的每個物件，並只在符合特定測試條件時才沿著管線傳遞。 未通過測試的物件會從管線中移除。 您會將測試條件當做 **Where-ObjectFilterScript** 參數的值來提供。

### 使用 Where-Object 執行簡單的測試
**FilterScript** 的值是評估為 true 或 false 的*指令碼區塊* (以大括弧 {} 括住的一或多個 Windows PowerShell 命令)。 這些指令碼區塊可以很簡單，但建立時需要了解另一個 Windows PowerShell 概念：比較運算子。 比較運算子會比較出現在運算子兩側的項目。 比較運算子是以 '-' 字元為開頭，後面接著名稱。 基本比較運算子適用於幾乎任何類型的物件。 更進階的比較運算子只適用於文字或陣列。

> [!NOTE]
> 根據預設，搭配文字使用時，Windows PowerShell 比較運算子不會區分大小寫。

基於剖析考量，不會使用 <、> 和 = 等符號作為比較運算子。 相反地，比較運算子是由字母所組成。 下表列出基本比較運算子。

|比較運算子|意義|範例 (傳回 true)|
|-----------------------|-----------|--------------------------|
|-eq|等於|1 -eq 1|
|-ne|不等於|1 -ne 2|
|-lt|小於|1 -lt 2|
|-le|小於或等於|1 -le 2|
|-gt|大於|2 -gt 1|
|-ge|大於或等於|2 -ge 1|
|-like|像是 (文字的萬用字元比較)|"file.doc" -like "f*.do?"|
|-notlike|不像是 (文字的萬用字元比較)|"file.doc" -notlike "p*.doc"|
|-contains|包含|1,2,3 -contains 1|
|-notcontains|不包含|1,2,3 -notcontains 4|

Where-Object 指令碼區塊使用特殊變數 '$_' 來參照管線中的目前物件。 以下示範其運作方式。 如果您有一份數值清單，並且只想要傳回小於 3 的數值，您可以輸入下列命令使用 Where-Object 來篩選數值︰

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### 根據物件屬性篩選
因為 $_ 參照了目前的管線物件，所以我們可以存取其屬性進行測試。

例如，我們可以檢視 WMI 中的 Win32_SystemDriver 類別。 一部系統上可能會有數百個系統驅動程式，但您可能只對某一組系統驅動程式感興趣，例如目前執行中的驅動程式。 如果您使用 Get-Member 檢視 Win32_SystemDriver 成員 (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType 屬性**)，您會看到相關屬性為 State，而且當驅動程式正在執行時，其值為 "Running"。 您可以輸入下列命令來篩選系統驅動程式，只選取執行中的驅動程式︰

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"}
```

這仍會產生一長串清單。 您可能還想要進行篩選，只選取要藉由測試 StartMode 值自動啟動的驅動程式︰

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

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
```

因為我們知道驅動程式正在執行，所以這會提供許多不再需要的資訊。 事實上，我們此時可能只需要名稱和顯示名稱資訊。 下列命令只會包含這兩個屬性，以產生更簡單的輸出︰

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

上述命令中有兩個 Where-Object 項目，但可使用 -and 邏輯運算子以單一 Where-Object 項目來表示，就像這樣︰

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq "Running") -and ($_.StartMode -eq "Manual") } | Format-Table -Property Name,DisplayName
```

下表列出標準邏輯運算子。

|邏輯運算子|意義|範例 (傳回 true)|
|--------------------|-----------|--------------------------|
|-and|邏輯 and；若兩側為 true 即為 true|(1 -eq 1) -and (2 -eq 2)|
|-or|邏輯 or；若任一側為 true 即為 true|(1 -eq 1) -or (1 -eq 2)|
|-not|邏輯 not；將 true 與 false 反轉|-not (1 -eq 2)|
|\!|邏輯 not；將 true 與 false 反轉|!(1 -eq 2)|



<!--HONumber=Apr16_HO1-->


