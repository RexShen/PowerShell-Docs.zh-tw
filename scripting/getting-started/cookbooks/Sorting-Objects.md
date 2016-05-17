---
title:  排序物件
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  8530caa8-3ed4-4c56-aed7-1295dd9ba199
---

# 排序物件
我們會組織顯示的資料，讓您可以使用 **Sort-Object** Cmdlet 更輕鬆地進行掃描。 **Sort-Object** 會使用一或多個屬性的名稱作為排序依據，並傳回根據這些屬性值進行排序的資料。

請考慮列出 Win32_SystemDriver 執行個體的問題。 如果我們要依序根據 **State** 和 **Name** 來進行排序，則做法是輸入：

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

雖然這會是冗長的顯示，但是您可以看到以相同狀態群組在一起的項目︰

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

您也可以指定 **Descending** 參數，以相反順序來排序物件。 這會反轉排序順序，以反向字母順序排序名稱，並依遞減大小排序數字。

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```



<!--HONumber=May16_HO2-->


