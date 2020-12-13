---
ms.date: 09/13/2016
ms.topic: reference
title: 別名屬性宣告
description: 別名屬性宣告
ms.openlocfilehash: f2fe49578da2c795643b1f80fa44deefe1dbff09
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668298"
---
# <a name="alias-attribute-declaration"></a>別名屬性宣告

Alias 屬性可讓使用者指定不同的 Cmdlet 參數名稱。 別名可以用來提供參數名稱的快捷方式，也可以提供適用于不同案例的不同名稱。

## <a name="syntax"></a>語法

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>參數

`aliasName` 需要 (String [] ) 。 針對 Cmdlet 參數指定一組以逗號分隔的別名名稱。

## <a name="remarks"></a>備註

- 當您指定 Cmdlet 參數時，別名屬性會與參數屬性搭配使用。 如需如何宣告這些屬性的詳細資訊，請參閱 [如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)。

- 每個別名名稱在 Cmdlet 內都必須是唯一的。 Windows PowerShell 不會檢查重複的別名名稱。

- 針對 Cmdlet 中的每個參數使用 Alias 屬性一次。

- Alias 屬性是由 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 類別所定義。

## <a name="see-also"></a>另請參閱

[參數別名](./parameter-aliases.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
