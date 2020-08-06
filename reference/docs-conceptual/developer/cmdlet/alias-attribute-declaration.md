---
title: Alias 屬性宣告 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782407"
---
# <a name="alias-attribute-declaration"></a>別名屬性宣告

Alias 屬性可讓使用者指定不同的 Cmdlet 參數名稱。 別名可以用來提供參數名稱的快捷方式，或者可以針對不同的案例提供不同的名稱。

## <a name="syntax"></a>語法

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>參數

`aliasName`需要 (String [] ) 。 為 Cmdlet 參數指定一組以逗號分隔的別名名稱。

## <a name="remarks"></a>備註

- 當您指定 Cmdlet 參數時，Alias 屬性會與參數屬性搭配使用。 如需如何宣告這些屬性的詳細資訊，請參閱 how [To Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md)。

- 每個別名名稱在 Cmdlet 中都必須是唯一的。 Windows PowerShell 不會檢查重複的別名名稱。

- Alias 屬性會針對 Cmdlet 中的每個參數使用一次。

- Alias 屬性是由[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)類別所定義。

## <a name="see-also"></a>另請參閱

[參數別名](./parameter-aliases.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
