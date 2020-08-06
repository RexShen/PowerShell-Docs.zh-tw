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
# <a name="defining-default-member-sets-for-objects"></a>定義物件的預設成員集合

Windows PowerShell 會使用 PSStandardMembers 成員集來定義物件的預設屬性集。 預設的屬性集可供命令（例如格式化 Cmdlet）用來顯示內容集所定義的屬性。 預設的屬性集包括 DefaultDisplayProperty、DefaultDisplayPropertySet 和 DefaultKeyPropertySet。 Windows PowerShell 會忽略所有其他成員集，以及加入至 PSStandardMembers 成員集的任何其他屬性集。

## <a name="member-set-for-systemdiagnosticsprocess"></a>System. Diagnostics 的成員集

在下列範例中，PSStandardMembers 成員集會定義針對 system.servicemodel 物件所[設定的 DefaultDisplayPropertySet](/dotnet/api/System.Diagnostics.Process)屬性。 此屬性集是由[格式清單](/powershell/module/Microsoft.PowerShell.Utility/Format-List)Cmdlet 所使用。

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

下列輸出顯示[格式清單](/powershell/module/Microsoft.PowerShell.Utility/Format-List)Cmdlet 傳回的預設屬性。 只有 `Id` 、 `Handles` 、 `CPU` 和 `Name` 屬性會針對每個進程物件傳回。

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
