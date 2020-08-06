---
title: 將屬性宣告為參數 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 63113f541df534b1f720ceb06e14b5031f2311b2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774638"
---
# <a name="declaring-properties-as-parameters"></a>將屬性宣告為參數

本主題提供您在宣告 Cmdlet 的參數之前必須瞭解的基本資訊。

若要在您的 Cmdlet 類別中宣告 Cmdlet 的參數，請定義代表每個參數的公用屬性，然後將一個或多個參數屬性加入至每個屬性。 Windows PowerShell 執行時間會使用參數屬性，將屬性識別為 Cmdlet 參數。 宣告參數屬性的基本語法為 `[Parameter()]` 。

以下是定義為必要參數之屬性的範例。

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

以下是有關參數的一些注意事項。

- 參數必須明確標示為公用。 未標示為公用的參數預設為內部，Windows PowerShell 執行時間將找不到。

- 參數應該定義為 Microsoft .NET Framework 類型，以提供更佳的參數驗證。 例如，限制為一組值以外一個值的參數，應定義為列舉類型。 採用統一資源識別項 (URI) 值的參數，應為[system.string 類型。](/dotnet/api/System.Uri)

- 針對所有但自由格式的文字屬性，請避免基本的字串參數。

- 您可以將參數新增至任意數目的參數集合。 如需參數集的詳細資訊，請參閱[Cmdlet 參數集](./cmdlet-parameter-sets.md)。

Windows PowerShell 也會提供一組可自動提供給每個 Cmdlet 的通用參數。 如需這些參數和其別名的詳細資訊，請參閱[Cmdlet 一般參數](./common-parameter-names.md)。

## <a name="see-also"></a>另請參閱

[Cmdlet 一般參數](./common-parameter-names.md)

[Cmdlet 參數的類型](./types-of-cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
