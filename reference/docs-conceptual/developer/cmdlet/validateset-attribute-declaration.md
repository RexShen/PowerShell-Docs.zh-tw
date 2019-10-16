---
title: ValidateSet 屬性聲明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364277"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet 屬性宣告

ValidateSetAttribute 屬性會指定 Cmdlet 參數引數的一組可能值。 Windows PowerShell 函數也可以使用這個屬性。

當指定這個屬性時，Windows PowerShell 執行時間會判斷 Cmdlet 參數所提供的引數是否符合所提供元素集中的元素。 只有當參數引數符合集合中的元素時，才會執行此 Cmdlet。 如果找不到相符的結果，Windows PowerShell 執行時間會擲回錯誤。

## <a name="syntax"></a>語法

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>參數

需要 `ValidValues` （[system.string](/dotnet/api/System.String)）。 指定有效的參數元素值。 下列範例示範如何指定一個或多個元素。

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。 @No__t-0 的預設值表示會忽略大小寫。 值為 `false` 會使 Cmdlet 區分大小寫。

## <a name="remarks"></a>備註

- 每個參數只能使用此屬性一次。

- 如果參數值為數組，則陣列的每個元素都必須符合屬性集的專案。

- ValidateSetAttribute 屬性是由[ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)類別所定義。

## <a name="see-also"></a>另請參閱

[Validatesetattribute。](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
