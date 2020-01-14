---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 選取物件的組件 Select Object
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737163"
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

您可以使用 `Select-Object` 來建立計算的屬性。 因此，您可以用 GB 而不是位元組來顯示 **FreeSpace**。

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
