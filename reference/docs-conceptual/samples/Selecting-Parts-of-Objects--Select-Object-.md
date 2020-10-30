---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 選取物件的組件 Select Object
description: 您可以使用 `Select-Object` Cmdlet 來建立新的自訂 PowerShell 物件，其中包含從管線上物件所選取的屬性。
ms.openlocfilehash: 92635ac54ea1469739bcb228c5e9a0a8dbfc648b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501026"
---
# <a name="selecting-parts-of-objects-select-object"></a>選取物件的組件 (Select-Object)

您可以使用 `Select-Object` Cmdlet 來建立新的自訂 PowerShell 物件，這些物件包含從用來建立它們的物件中選取的屬性。 輸入下列命令，以建立只包括 **Win32_LogicalDisk** WMI 類別之 **Name** 和 **FreeSpace** 屬性的新物件：

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

您可以使用 `Select-Object` 來建立計算的屬性。 因此，您可以用 GB 而不是位元組來顯示 **FreeSpace** 。

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  Select-Object -Property Name, @{
    label='FreeSpace'
    expression={($_.FreeSpace/1GB).ToString('F2')}
  }
```

```Output
Name    FreeSpace
----    ---------
C:      47.18
```
