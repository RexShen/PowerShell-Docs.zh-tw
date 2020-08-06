---
title: ValidatePattern 屬性聲明 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.openlocfilehash: 713fa7a46a8eeefdbfd679a5e8436285fac085f8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787796"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern 屬性宣告

ValidatePattern 屬性會指定正則運算式模式，以驗證 Cmdlet 參數的引數。 Windows PowerShell 函數也可以使用這個屬性。

在 Cmdlet 內叫用 ValidatePattern 時，Windows PowerShell 執行時間會將 Cmdlet 參數的引數轉換成字串，然後將該字串與 ValidatePattern 屬性所提供的模式進行比較。 只有當引數的轉換字串表示和提供的模式相符時，才會執行此 Cmdlet。 如果不相符，Windows PowerShell 執行時間會擲回錯誤。

## <a name="syntax"></a>語法

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>參數

`RegexString`需要 ([system.string](/dotnet/api/System.String)) 。 指定驗證參數引數的正則運算式。

Options ([system.text.regularexpressions.RegEx>. system.text.regularexpressions.RegExoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 選擇性的具名引數。 指定指定正則運算式選項的[System.text.regularexpressions.RegEx> system.text.regularexpressions.RegExoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)旗標的位元組合。

## <a name="remarks"></a>備註

- 每個參數只能使用此屬性一次。

- 您可以使用 `Option` 屬性的參數來進一步定義模式。 例如，您可以讓模式區分大小寫。

- 如果將這個屬性套用至集合，則集合中的每個元素都必須符合模式。

- ValidatePattern 屬性是由[Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)類別所定義。

## <a name="see-also"></a>另請參閱

[Validatepatternattribute。](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
