---
title: Alias 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72370017"
---
# <a name="alias-attribute-declaration"></a>別名屬性宣告

Alias 屬性可讓使用者指定不同的 Cmdlet 參數名稱。 別名可以用來提供參數名稱的快捷方式，或者可以針對不同的案例提供不同的名稱。

## <a name="syntax"></a>語法

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>參數

需要 `aliasName` （String []）。 為 Cmdlet 參數指定一組以逗號分隔的別名名稱。

## <a name="remarks"></a>備註

- 當您指定 Cmdlet 參數時，Alias 屬性會與參數屬性搭配使用。 如需如何宣告這些屬性的詳細資訊，請參閱 how [To Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md)。

- 每個別名名稱在 Cmdlet 中都必須是唯一的。 Windows PowerShell 不會檢查重複的別名名稱。

- Alias 屬性會針對 Cmdlet 中的每個參數使用一次。

- Alias 屬性是由[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)類別所定義。

## <a name="see-also"></a>另請參閱

[參數別名](./parameter-aliases.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
