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
# <a name="defining-default-member-sets-for-objects"></a>定義物件的預設成員集合

Windows PowerShell 使用 PSStandardMembers 成員集來定義物件的預設屬性集。 預設的屬性集可供命令使用，例如格式化 Cmdlet，只顯示內容集所定義的屬性。 預設屬性集會包含 DefaultDisplayProperty、DefaultDisplayPropertySet 和 DefaultKeyPropertySet。 Windows PowerShell 會忽略所有其他成員集，以及加入至 PSStandardMembers 成員集的任何其他屬性集。

## <a name="member-set-for-systemdiagnosticsprocess"></a>System. Process 的成員集

在下列範例中，PSStandardMembers 成員集會定義 DefaultDisplayPropertySet 屬性集，以供 [處理](/dotnet/api/System.Diagnostics.Process) 物件之用。 [格式清單](/powershell/module/Microsoft.PowerShell.Utility/Format-List)Cmdlet 會使用這個屬性集。

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

下列輸出顯示 [格式清單](/powershell/module/Microsoft.PowerShell.Utility/Format-List) Cmdlet 所傳回的預設屬性。 只 `Id` `Handles` `CPU` `Name` 會針對每個處理常式物件傳回、、和屬性。

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

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
