---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateLength 屬性宣告
description: ValidateLength 屬性宣告
ms.openlocfilehash: b35fe24c6fc44aaca6a39d819d6e3fc2d8a2cade
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646193"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength 屬性宣告

ValidateLength 屬性會指定 Cmdlet 參數引數的最小和最大字元數。 Windows PowerShell 函數也可以使用這個屬性。

## <a name="syntax"></a>語法

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>參數

`MinLength` 需要 ([system.object](/dotnet/api/System.Int32)) 。 指定允許的最小字元數。

`MaxLength` 需要 ([system.object](/dotnet/api/System.Int32)) 。 指定允許的最大字元數。

## <a name="remarks"></a>備註

- 如需如何宣告這個屬性的詳細資訊，請參閱 [如何宣告輸入驗證規則](./how-to-validate-parameter-input.md)。

- 如果未使用此屬性，對應的參數引數可以是任何長度。

- 在下列情況下，Windows PowerShell 執行時間會擲回錯誤：

  - 當 attribute 參數的值 `MaxLength` 小於 attribute 參數的值時 `MinLength` 。

  - 當 `MaxLength` 屬性參數設定為0時。

  - 當引數不是字串時。

- ValidateLength 屬性是由 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) 類別所定義。

## <a name="see-also"></a>另請參閱

[Validatelengthattribute。](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
