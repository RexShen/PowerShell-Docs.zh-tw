---
ms.date: 09/13/2016
ms.topic: reference
title: 定義物件的預設成員集合
description: 定義物件的預設成員集合
ms.openlocfilehash: 919f7ba65322c6a56a27e046fb211bde151abf7d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653128"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="4c571-103">定義物件的預設成員集合</span><span class="sxs-lookup"><span data-stu-id="4c571-103">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="4c571-104">Windows PowerShell 使用 PSStandardMembers 成員集來定義物件的預設屬性集。</span><span class="sxs-lookup"><span data-stu-id="4c571-104">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="4c571-105">預設的屬性集可供命令使用，例如格式化 Cmdlet，只顯示內容集所定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="4c571-105">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="4c571-106">預設屬性集會包含 DefaultDisplayProperty、DefaultDisplayPropertySet 和 DefaultKeyPropertySet。</span><span class="sxs-lookup"><span data-stu-id="4c571-106">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="4c571-107">Windows PowerShell 會忽略所有其他成員集，以及加入至 PSStandardMembers 成員集的任何其他屬性集。</span><span class="sxs-lookup"><span data-stu-id="4c571-107">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="4c571-108">System. Process 的成員集</span><span class="sxs-lookup"><span data-stu-id="4c571-108">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="4c571-109">在下列範例中，PSStandardMembers 成員集會定義 DefaultDisplayPropertySet 屬性集，以供 [處理](/dotnet/api/System.Diagnostics.Process) 物件之用。</span><span class="sxs-lookup"><span data-stu-id="4c571-109">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="4c571-110">[格式清單](/powershell/module/Microsoft.PowerShell.Utility/Format-List)Cmdlet 會使用這個屬性集。</span><span class="sxs-lookup"><span data-stu-id="4c571-110">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="4c571-111">下列輸出顯示 [格式清單](/powershell/module/Microsoft.PowerShell.Utility/Format-List) Cmdlet 所傳回的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="4c571-111">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="4c571-112">只 `Id` `Handles` `CPU` `Name` 會針對每個處理常式物件傳回、、和屬性。</span><span class="sxs-lookup"><span data-stu-id="4c571-112">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4c571-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c571-113">See Also</span></span>

[<span data-ttu-id="4c571-114">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4c571-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
