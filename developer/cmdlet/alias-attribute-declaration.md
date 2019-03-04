---
title: 別名屬性宣告 |Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855044"
---
# <a name="alias-attribute-declaration"></a>別名屬性宣告

Alias 屬性可讓使用者指定不同的 cmdlet 參數的名稱。 別名可以用來提供參數名稱的捷徑，或者他們可以提供不同的名稱，適用於不同的案例。

## <a name="syntax"></a>語法

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>參數

`aliasName` (String必要的。 指定一組 cmdlet 參數的逗號分隔的別名名稱。

## <a name="remarks"></a>備註

- Alias 屬性搭配參數屬性，當您指定的 cmdlet 參數。 如需如何宣告這些屬性的詳細資訊，請參閱[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)。

- 每個別名名稱必須是唯一 cmdlet。 Windows PowerShell 不會檢查重複的別名名稱。

- Alias 屬性使用一次，每個參數的 cmdlet 中。

- Alias 屬性所定義[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)類別。

## <a name="see-also"></a>另請參閱

[參數別名](./parameter-aliases.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
