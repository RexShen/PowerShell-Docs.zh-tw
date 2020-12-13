---
ms.date: 09/13/2016
ms.topic: reference
title: 延伸輸出物件
description: 延伸輸出物件
ms.openlocfilehash: 9fea476e3032002bd206609313581cc6373dfddc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652909"
---
# <a name="extending-output-objects"></a>延伸輸出物件

您可以使用 ( .ps1xml) 的類型檔案，擴充 Cmdlet、函式和腳本所傳回的 .NET Framework 物件。 類型檔案是以 XML 為基礎的檔案，可讓您將屬性和方法新增至現有的物件。 例如，Windows PowerShell 提供 Types.ps1的 xml 檔，這會將專案新增至數個現有的 .NET Framework 物件。 Types.ps1xml 檔案位於 Windows PowerShell 安裝目錄 (`$pshome`) 。 您可以建立自己的類型檔案，進一步擴充這些物件或擴充其他物件。 當您使用類型檔案來擴充物件時，會以新的元素擴充物件的任何實例。

## <a name="extending-the-systemarray-object"></a>擴充 System.object 陣列物件

下列範例顯示 Windows PowerShell 如何擴充 Types.ps1xml 檔案中的 [system.object](/dotnet/api/System.Array) 物件。 依預設， [system.object](/dotnet/api/System.Array) 物件有一個 `Length` 屬性，會列出陣列中的物件數目。 不過，因為名稱 "length" 並不清楚地描述屬性，Windows PowerShell 加入 `Count` alias 屬性，它會顯示與屬性相同的值 `Length` 。 下列 XML 會將 `Count` 屬性加入至 [system.object](/dotnet/api/System.Array) 型別。

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

若要查看這個新的別名屬性，請使用任何陣列上的 [Get 成員](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) 命令，如下列範例所示。

```powershell
Get-Member -InputObject (1,2,3,4)
```

此命令會傳回下列結果。

```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```

您可以使用 `Count` 屬性或 `Length` 屬性來判斷陣列中有多少物件。 例如：

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a>自訂類型檔案

若要建立自訂類型檔案，請從複製現有的類型檔案開始。 新檔案可以有任何名稱，但它的副檔名必須是 .ps1xml。 當您複製檔案時，可以將新檔案放在 Windows PowerShell 可存取的任何目錄中，但是將檔案放在 Windows PowerShell 安裝目錄 (`$pshome`) 或安裝目錄的子目錄中會很有用。

若要將您自己的擴充類型加入至檔案中，請為您想要擴充的每個物件加入類型元素。 下列主題提供範例。

- 如需加入屬性和屬性集的詳細資訊，請參閱 [擴充屬性](./extending-properties-for-objects.md)

- 如需新增方法的詳細資訊，請參閱 [擴充方法](./defining-default-methods-for-objects.md)。

- 如需新增成員集的詳細資訊，請參閱 [擴充成員集合](./defining-default-member-sets-for-objects.md)。

在您定義自己的擴充類型之後，請使用下列其中一種方法來讓您的擴充物件可供使用：

- 若要讓您的擴充類型檔案可用於目前的會話，請使用 [TypeData 指令程式](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) 來新增檔案。 如果您想要讓您的類型優先于其他類型檔案中定義的類型 (包括 Types.ps1xml 檔案) ，請使用 `PrependData` [TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet 的參數。
- 若要讓您的擴充類型檔案可供所有未來的會話使用，請將類型檔案新增至模組、匯出目前的會話，或將 [TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) 命令新增至您的 Windows PowerShell 設定檔。

## <a name="signing-types-files"></a>簽署類型檔案

類型檔案應經過數位簽署，以防止篡改，因為 XML 可以包含腳本區塊。 如需有關新增數位簽章的詳細資訊，請參閱 [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>另請參閱

[定義物件的預設屬性](./extending-properties-for-objects.md)

[定義物件的預設方法](./defining-default-methods-for-objects.md)

[定義物件的預設成員集合](./defining-default-member-sets-for-objects.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
