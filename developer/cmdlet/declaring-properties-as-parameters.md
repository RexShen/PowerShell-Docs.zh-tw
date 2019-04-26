---
title: 宣告做為參數的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068261"
---
# <a name="declaring-properties-as-parameters"></a>將屬性宣告為參數

本主題提供宣告之參數的 cmdlet 之前，必須了解的基本資訊。

若要宣告 cmdlet 類別內的 cmdlet 的參數，定義公用屬性，代表每個參數，然後再新增一或多個參數屬性對每個屬性。 Windows PowerShell 執行階段會使用參數屬性來識別做為指令程式參數的屬性。 宣告參數屬性的基本語法是`[Parameter()]`。

以下是定義為必要的參數屬性的範例。

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

以下是參數時，必須注意的事項。

- 參數必須明確標示為公用。 未標示為公用的預設值為 internal，並將找不到 Windows PowerShell 執行階段的參數。

- 參數應定義為 Microsoft.NET Framework 型別，以提供更好的參數驗證。 比方說，會限制為一個值，超出一組值的參數應該定義為列舉型別。 使用統一資源識別元 (URI) 值的參數必須是類型[System.Uri](/dotnet/api/System.Uri)。

- 避免以外的所有自由格式文字屬性的基本字串參數。

- 您可以將參數新增至任何數目的參數集合。 如需參數集的詳細資訊，請參閱[指令程式參數設定](./cmdlet-parameter-sets.md)。

Windows PowerShell 也提供一組通用參數，會自動提供給每個 cmdlet。 如需有關這些參數和其別名的詳細資訊，請參閱 <<c0> [ 一般參數的 Cmdlet](./common-parameter-names.md)。

## <a name="see-also"></a>另請參閱

[指令程式的一般參數](./common-parameter-names.md)

[Cmdlet 參數的類型](./types-of-cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
