---
title: 擴充輸出物件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 12a826363221b8a7ce06245c787a7bd0529e42f8
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690910"
---
# <a name="extending-output-objects"></a>延伸輸出物件

您可以使用類型檔案（. types.ps1xml）來擴充 Cmdlet、函式和腳本所傳回的 .NET Framework 物件。 類型檔案是以 XML 為基礎的檔案，可讓您將屬性和方法加入至現有的物件。 例如，Windows PowerShell 提供 types.ps1xml 檔案，它會將元素新增至數個現有的 .NET Framework 物件。 Types.ps1xml 檔案位於 Windows PowerShell 安裝目錄（ `$pshome` ）中。 您可以建立自己的類型檔案，進一步擴充這些物件或擴充其他物件。 當您使用類型檔案來擴充物件時，物件的任何實例都會以新元素擴充。

## <a name="extending-the-systemarray-object"></a>擴充 System.object 物件

下列範例顯示 Windows PowerShell 如何擴充 types.ps1xml 檔案中的[system.object](/dotnet/api/System.Array)物件。 根據預設， [system.object](/dotnet/api/System.Array)物件的 `Length` 屬性會列出陣列中的物件數目。 不過，因為名稱「長度」並未清楚描述屬性，所以 Windows PowerShell 會加入 `Count` alias 屬性，它會顯示與屬性相同的值 `Length` 。 下列 XML 會將 `Count` 屬性加入至[system.object](/dotnet/api/System.Array)類型。

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

若要查看這個新的別名屬性，請在任何陣列上使用[Get Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)命令，如下列範例所示。

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

若要建立自訂類型檔案，請先複製現有的類型檔案。 新檔案可以有任何名稱，但它的副檔名必須是 types.ps1xml。 當您複製檔案時，可以將新檔案放在 Windows PowerShell 可存取的任何目錄中，但將檔案放在 Windows PowerShell 安裝目錄（ `$pshome` ）或安裝目錄的子目錄中是很有用的。

若要將您自己的擴充類型新增至檔案，請為每個您要擴充的物件加入 types 元素。 下列主題提供範例。

- 如需新增屬性和屬性集的詳細資訊，請參閱[擴充屬性](./extending-properties-for-objects.md)。

- 如需新增方法的詳細資訊，請參閱[擴充方法](./defining-default-methods-for-objects.md)。

- 如需有關加入成員集的詳細資訊，請參閱[擴充成員集](./defining-default-member-sets-for-objects.md)。

定義您自己的擴充類型之後，請使用下列其中一種方法，讓擴充物件可供使用：

- 若要讓目前的會話能夠使用擴充類型檔案，請使用[TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet 來新增檔案。 如果您想要讓類型優先于其他類型檔案（包括 types.ps1xml 檔案）中定義的類型，請使用 `PrependData` [TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Cmdlet 的參數。
- 若要讓擴充類型檔案可供所有未來的會話使用，請將類型檔案新增至模組、匯出目前的會話，或將[TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData)命令新增至您的 Windows PowerShell 設定檔。

## <a name="signing-types-files"></a>簽署類型檔案

類型檔案應該以數位方式簽署，以防止進行篡改，因為 XML 可以包含腳本區塊。 如需新增數位簽章的詳細資訊，請參閱[about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>另請參閱

[定義物件的預設屬性](./extending-properties-for-objects.md)

[定義物件的預設方法](./defining-default-methods-for-objects.md)

[定義物件的預設成員集合](./defining-default-member-sets-for-objects.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
