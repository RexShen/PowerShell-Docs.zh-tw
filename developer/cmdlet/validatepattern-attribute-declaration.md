---
title: ValidatePattern 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858874"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern 屬性宣告

ValidatePattern 屬性會指定驗證的 cmdlet 參數的引數的規則運算式模式。 這個屬性也可用 Windows PowerShell 函式。

ValidatePattern cmdlet 內叫用時，Windows PowerShell 執行階段將 cmdlet 參數的引數轉換為字串，然後比較該 ValidatePattern 屬性提供之模式的字串。 已轉換的字串表示的引數，而提供的模式比對時，才會執行 cmdlet。 如果不符，Windows PowerShell 執行階段會擲回錯誤。

## <a name="syntax"></a>語法

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>參數

`RegexString` ([System.String](/dotnet/api/System.String)) 所需。 指定驗證參數的引數的規則運算式。

選項 ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 選擇性具名參數。 指定的位元組合[System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)旗標，指定規則運算式選項。

## <a name="remarks"></a>備註

- 這個屬性可以用每個參數的一次。

- 您可以使用`Option`進一步定義模式之屬性的參數。 例如，您可以進行的模式區分大小寫。

- 如果這個屬性會套用至集合，集合中的每個項目必須符合的模式。

- 藉由定義 ValidatePattern 屬性[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)類別。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
