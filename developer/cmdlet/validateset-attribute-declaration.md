---
title: ValidateSet 屬性宣告 |Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067056"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet 屬性宣告

ValidateSetAttribute 屬性會指定一組 cmdlet 參數引數的可能值。 這個屬性也可用 Windows PowerShell 函式。

當指定這個屬性時，Windows PowerShell 執行階段會判斷提供的引數，cmdlet 參數是否符合提供項目集合中的項目。 只有當參數引數符合集合中的項目，是執行 cmdlet。 如果找到相符項目，則 Windows PowerShell 執行階段會擲回錯誤。

## <a name="syntax"></a>語法

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>參數

`ValidValues` ([System.String](/dotnet/api/System.String)) 所需。 指定有效的參數項目值。 下列範例示範如何指定一個項目或多個項目。

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。 預設值`true`指出，忽略大小寫。 值為`false`會區分大小寫的 cmdlet。

## <a name="remarks"></a>備註

- 這個屬性可以用每個參數的一次。

- 如果參數值是陣列，陣列的每個項目必須符合屬性集合的項目。

- ValidateSetAttribute 屬性所定義[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)類別。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
