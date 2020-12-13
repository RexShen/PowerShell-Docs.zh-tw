---
ms.date: 09/13/2016
ms.topic: reference
title: ValidatePattern 屬性宣告
description: ValidatePattern 屬性宣告
ms.openlocfilehash: 364f63d2c52563eaefe64bcbb2bbae511bccb074
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646162"
---
# <a name="validatepattern-attribute-declaration"></a>ValidatePattern 屬性宣告

ValidatePattern 屬性會指定正則運算式模式，以驗證 Cmdlet 參數的引數。 Windows PowerShell 函數也可以使用這個屬性。

在 Cmdlet 中叫用 ValidatePattern 時，Windows PowerShell 執行時間會將 Cmdlet 參數的引數轉換成字串，然後將該字串與 ValidatePattern 屬性所提供的模式進行比較。 只有在引數的已轉換字串標記法和提供的模式相符時，才會執行此 Cmdlet。 如果兩者不相符，Windows PowerShell 執行時間會擲回錯誤。

## <a name="syntax"></a>語法

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>參數

`RegexString` 需要 ([system.string](/dotnet/api/System.String)) 。 指定驗證參數引數的正則運算式。

選項 ([>system.text.regularexpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) 選擇性的具名引數。 指定 [>system.text.regularexpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) 旗標的位元組合，這些旗標會指定正則運算式選項。

## <a name="remarks"></a>備註

- 此屬性每個參數只能使用一次。

- 您可以使用 `Option` 屬性的參數來進一步定義模式。 例如，您可以讓模式區分大小寫。

- 如果將這個屬性套用至集合，則集合中的每個元素都必須符合模式。

- ValidatePattern 屬性是由 [Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) 類別所定義。

## <a name="see-also"></a>另請參閱

[Validatepatternattribute。](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
