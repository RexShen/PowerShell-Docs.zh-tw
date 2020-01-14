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
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="154b7-103">選取物件的組件 (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="154b7-103">Selecting Parts of Objects (Select-Object)</span></span>

<span data-ttu-id="154b7-104">您可以使用 `Select-Object` Cmdlet 來建立新的自訂 PowerShell 物件，這些物件包含從用來建立它們的物件中選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="154b7-104">You can use the `Select-Object` cmdlet to create new, custom PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="154b7-105">輸入下列命令，以建立只包括 **Win32_LogicalDisk** WMI 類別之 **Name** 和 **FreeSpace** 屬性的新物件：</span><span class="sxs-lookup"><span data-stu-id="154b7-105">Type the following command to create a new object that includes only the **Name** and **FreeSpace** properties of the **Win32_LogicalDisk** WMI class:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

<span data-ttu-id="154b7-106">您可以使用 `Select-Object` 來建立計算的屬性。</span><span class="sxs-lookup"><span data-stu-id="154b7-106">With `Select-Object` you can create calculated properties.</span></span> <span data-ttu-id="154b7-107">因此，您可以用 GB 而不是位元組來顯示 **FreeSpace**。</span><span class="sxs-lookup"><span data-stu-id="154b7-107">So you can display **FreeSpace** in gigabytes rather than bytes.</span></span>

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
