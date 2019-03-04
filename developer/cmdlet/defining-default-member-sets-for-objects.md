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
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859794"
---
# <a name="defining-default-member-sets-for-objects"></a>定義物件的預設成員集合

PSStandardMembers 成員集使用 Windows PowerShell 來定義物件的預設屬性集。 預設屬性集可供命令，例如格式化 cmdlet，只顯示這些屬性所定義的屬性集。 預設屬性集包含 DefaultDisplayProperty、 DefaultDisplayPropertySet 和 DefaultKeyPropertySet。 Windows PowerShell 會忽略所有其他成員集，並新增至 PSStandardMembers 成員集的任何其他屬性集。

## <a name="member-set-for-systemdiagnosticsprocess"></a>System.Diagnostics.Process 的成員集

在下列範例中，設定的 PSStandardMembers 成員定義 DefaultDisplayPropertySet 屬性集，以便[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。 設定這個屬性由[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。
在下列範例中，設定的 PSStandardMembers 成員定義 DefaultDisplayPropertySet 屬性集，以便[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。 設定這個屬性由[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。

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

下列的輸出會顯示所傳回的預設屬性[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。 只有`Id`， `Handles`， `CPU`，和`Name`屬性所傳回的每個處理程序物件。
下列的輸出會顯示所傳回的預設屬性[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。 只有`Id`， `Handles`， `CPU`，和`Name`屬性所傳回的每個處理程序物件。

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
