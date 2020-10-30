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
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="ba15b-104">選取物件的組件 (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="ba15b-104">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="ba15b-105">您可以使用 `Select-Object` Cmdlet 來建立新的自訂 PowerShell 物件，這些物件包含從用來建立它們的物件中選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba15b-105">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="ba15b-106">輸入下列命令，以建立只包括 **Win32_LogicalDisk** WMI 類別之 **Name** 和 **FreeSpace** 屬性的新物件：</span><span class="sxs-lookup"><span data-stu-id="ba15b-106">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="ba15b-107">您可以使用 `Select-Object` 來建立計算的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba15b-107">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="ba15b-108">因此，您可以用 GB 而不是位元組來顯示 **FreeSpace** 。</span><span class="sxs-lookup"><span data-stu-id="ba15b-108">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

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
