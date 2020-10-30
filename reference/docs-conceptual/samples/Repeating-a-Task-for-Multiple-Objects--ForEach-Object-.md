---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 針對多個物件重複工作 ForEach Object
description: ForEach-Object 可讓您針對每個透過管線傳遞的物件重複執行一組命令。
ms.openlocfilehash: 7353be833dc8bf77dd18b7fc45bdd97e092ff6ef
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499950"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>針對多個物件重複工作 (ForEach-Object)

`ForEach-Object`Cmdlet 可針對目前的管線物件使用指令碼區塊和 `$_` 描述元，讓您能夠在管線中的每個物件上執行命令。 這可以用來執行一些複雜的工作。

一個可能適用的情況是操控資料，使其更加實用。 例如，您可以使用 WMI 中的 **Win32_LogicalDisk** 類別來傳回每個本機磁碟的可用空間資訊。 傳回的資料是以位元組為單位，不過這會很難閱讀︰

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

我們可以將 **FreeSpace** 值轉換成 MB，方法是將每個值除以 1 MB。 您可以輸入下列命令，在 `ForEach-Object` 指令碼區塊中執行這項操作︰

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

不過，輸出現在會是沒有相關聯標籤的資料。 因為此類 WMI 屬性是唯讀的，所以您無法直接轉換 **FreeSpace** 。 如果您輸入︰

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

您會收到錯誤訊息：

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

您可以使用一些進階技術來重新組織資料，但有一個較簡單的方法，就是使用 `Select-Object` 來建立新物件。
