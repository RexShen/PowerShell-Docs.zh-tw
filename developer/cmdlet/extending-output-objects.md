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
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861924"
---
# <a name="extending-output-objects"></a>延伸輸出物件

您可以擴充.NET Framework 物件所使用的類型檔案 (.ps1xml) 傳回的 cmdlet、 函數和指令碼。 類型檔案是以 XML 為基礎，可讓您將屬性和方法新增至現有的物件。 比方說，Windows PowerShell 會提供將元素加入至數個現有的.NET Framework 物件的 Types.ps1xml 檔案。 Types.ps1xml 檔案位於 Windows PowerShell 安裝目錄 (`$pshome`)。 您可以建立您自己的類型檔案以進一步擴充這些物件或擴充其他物件。 當您擴充物件所使用的類型檔案時，物件的任何執行個體已擴充與新的項目。

## <a name="extending-the-systemarray-object"></a>擴充 System.Array 物件

下列範例示範如何擴充 Windows PowerShell [System.Array](/dotnet/api/System.Array) Types.ps1xml 檔案中的物件。 根據預設， [System.Array](/dotnet/api/System.Array)物件具有`Length`列出陣列中的物件數目的屬性。 不過，因為名稱 「 長度 」 不會清楚地描述屬性，Windows PowerShell 新增`Count`別名屬性，它會顯示相同的值`Length`屬性。 下列 XML 會新增`Count`屬性，以[System.Array](/dotnet/api/System.Array)型別。

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

若要查看這個新的別名屬性，請使用[Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)命令上任何的陣列，如下列範例所示。

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
您可以使用`Count`屬性或`Length`屬性來判斷陣列中有多少物件。 例如：

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

## <a name="custom-types-files"></a>自訂類型的檔案

若要建立自訂的類型檔案時，先複製現有的類型檔案。 新的檔案可以有任何名稱，但它必須有副檔名為.ps1xml 檔案。 當您將檔案複製，您可以將新的檔案放在可以存取 Windows PowerShell 的任何目錄，但您最好將檔案放在 Windows PowerShell 安裝目錄 (`$pshome`) 或的安裝目錄的子目錄中。

將您自己的延伸的類型新增至檔案，新增您想要擴充的每個物件的型別項目。 下列主題提供範例。

- 如需新增屬性和屬性集的詳細資訊，請參閱[擴充屬性](./extending-properties-for-objects.md)

- 如需有關加入方法的詳細資訊，請參閱[擴充方法](./defining-default-methods-for-objects.md)。

- 如需有關如何新增成員集的詳細資訊，請參閱[擴充成員設定](./defining-default-member-sets-for-objects.md)。

定義您自己的延伸的類型之後，使用其中一種下列方法可讓您擴充的物件：

- 若要讓您延伸的類型的檔案目前的工作階段，請使用[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet 來新增新的檔案。 如果您想要您的型別中所定義的型別中的優先順序高於其他類型檔案 （包括 Types.ps1xml 檔案），請使用`PrependData`的參數[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet。
- 若要將您的延伸的類型檔案提供給所有未來的工作階段，新增至模組的類型檔案、 匯出目前的工作階段，或新增[Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData)命令到您的 Windows PowerShell 設定檔。

## <a name="signing-types-files"></a>簽章類型檔案

應該數位簽章類型的檔案，以避免遭到竄改，因為 XML 可以包含指令碼區塊。 如需有關新增數位簽章的詳細資訊，請參閱[about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>另請參閱

[定義物件的預設屬性](./extending-properties-for-objects.md)

[定義物件的預設方法](./defining-default-methods-for-objects.md)

[為物件定義預設成員集](./defining-default-member-sets-for-objects.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
