---
title: 定義預設成員設定為物件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794904"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="5180b-102">定義物件的預設成員集合</span><span class="sxs-lookup"><span data-stu-id="5180b-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="5180b-103">PSStandardMembers 成員集使用 Windows PowerShell 來定義物件的預設屬性集。</span><span class="sxs-lookup"><span data-stu-id="5180b-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="5180b-104">預設屬性集可供命令，例如格式化 cmdlet，只顯示這些屬性所定義的屬性集。</span><span class="sxs-lookup"><span data-stu-id="5180b-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="5180b-105">預設屬性集包含 DefaultDisplayProperty、 DefaultDisplayPropertySet 和 DefaultKeyPropertySet。</span><span class="sxs-lookup"><span data-stu-id="5180b-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="5180b-106">Windows PowerShell 會忽略所有其他成員集，並新增至 PSStandardMembers 成員集的任何其他屬性集。</span><span class="sxs-lookup"><span data-stu-id="5180b-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="5180b-107">System.Diagnostics.Process 的成員集</span><span class="sxs-lookup"><span data-stu-id="5180b-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="5180b-108">在下列範例中，設定的 PSStandardMembers 成員定義 DefaultDisplayPropertySet 屬性集，以便[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。</span><span class="sxs-lookup"><span data-stu-id="5180b-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="5180b-109">設定這個屬性由[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5180b-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="5180b-110">下列的輸出會顯示所傳回的預設屬性[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5180b-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="5180b-111">只有`Id`， `Handles`， `CPU`，和`Name`屬性所傳回的每個處理程序物件。</span><span class="sxs-lookup"><span data-stu-id="5180b-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5180b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5180b-112">See Also</span></span>

[<span data-ttu-id="5180b-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5180b-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
