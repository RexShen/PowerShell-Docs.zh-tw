---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "選取物件的組件 Select Object"
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 8c9633e80f63e1d474c46fa772108aee4f79751d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="selecting-parts-of-objects-select-object"></a><span data-ttu-id="64c84-103">選取物件的組件 (Select-Object)</span><span class="sxs-lookup"><span data-stu-id="64c84-103">Selecting Parts of Objects (Select-Object)</span></span>
<span data-ttu-id="64c84-104">您可以使用 **Select-Object** Cmdlet 來建立新的自訂 Windows PowerShell 物件，這些物件包含從用來建立它們的物件中選取的屬性。</span><span class="sxs-lookup"><span data-stu-id="64c84-104">You can use the **Select-Object** cmdlet to create new, custom Windows PowerShell objects that contain properties selected from the objects you use to create them.</span></span> <span data-ttu-id="64c84-105">輸入下列命令，以建立只包括 Win32_LogicalDisk WMI 類別的 Name 和 FreeSpace 屬性的新物件：</span><span class="sxs-lookup"><span data-stu-id="64c84-105">Type the following command to create a new object that includes only the Name and FreeSpace properties of the Win32_LogicalDisk WMI class:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

<span data-ttu-id="64c84-106">發出該命令之後會看不到資料類型；但是，如果您在 Select-Object 之後將結果輸送到 Get-Member，則可以分辨您有新類型的物件 (PSCustomObject)：</span><span class="sxs-lookup"><span data-stu-id="64c84-106">You cannot see the type of data after issuing that command, but if you pipe the result to Get-Member after the Select-Object, you can tell that you have a new type of object, a PSCustomObject:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

<span data-ttu-id="64c84-107">Select-Object 有許多用法。</span><span class="sxs-lookup"><span data-stu-id="64c84-107">Select-Object has many uses.</span></span> <span data-ttu-id="64c84-108">其中一種是複寫之後可以進行修改的資料。</span><span class="sxs-lookup"><span data-stu-id="64c84-108">One of them is replicating data that you can then modify.</span></span> <span data-ttu-id="64c84-109">我們現在可以處理上一節所發生的問題。</span><span class="sxs-lookup"><span data-stu-id="64c84-109">We can now handle the problem we ran across in the previous section.</span></span> <span data-ttu-id="64c84-110">我們可以更新新建立物件中的 FreeSpace 值，而且輸出將包括描述性標籤︰</span><span class="sxs-lookup"><span data-stu-id="64c84-110">We can update the value of FreeSpace in our newly-created objects and the output will include the descriptive label:</span></span>

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```

