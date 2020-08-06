---
title: 定義物件的預設成員集 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 80e1f54890d3aac1702414699ead16fcf38271e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774621"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="c4fdf-102">定義物件的預設成員集合</span><span class="sxs-lookup"><span data-stu-id="c4fdf-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="c4fdf-103">Windows PowerShell 會使用 PSStandardMembers 成員集來定義物件的預設屬性集。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="c4fdf-104">預設的屬性集可供命令（例如格式化 Cmdlet）用來顯示內容集所定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="c4fdf-105">預設的屬性集包括 DefaultDisplayProperty、DefaultDisplayPropertySet 和 DefaultKeyPropertySet。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="c4fdf-106">Windows PowerShell 會忽略所有其他成員集，以及加入至 PSStandardMembers 成員集的任何其他屬性集。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="c4fdf-107">System. Diagnostics 的成員集</span><span class="sxs-lookup"><span data-stu-id="c4fdf-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="c4fdf-108">在下列範例中，PSStandardMembers 成員集會定義針對 system.servicemodel 物件所[設定的 DefaultDisplayPropertySet](/dotnet/api/System.Diagnostics.Process)屬性。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="c4fdf-109">此屬性集是由[格式清單](/powershell/module/Microsoft.PowerShell.Utility/Format-List)Cmdlet 所使用。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

<span data-ttu-id="c4fdf-110">下列輸出顯示[格式清單](/powershell/module/Microsoft.PowerShell.Utility/Format-List)Cmdlet 傳回的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="c4fdf-111">只有 `Id` 、 `Handles` 、 `CPU` 和 `Name` 屬性會針對每個進程物件傳回。</span><span class="sxs-lookup"><span data-stu-id="c4fdf-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a><span data-ttu-id="c4fdf-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4fdf-112">See Also</span></span>

[<span data-ttu-id="c4fdf-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c4fdf-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
