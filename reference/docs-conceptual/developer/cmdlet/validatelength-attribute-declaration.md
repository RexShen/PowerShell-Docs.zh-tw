---
title: ValidateLength 屬性聲明 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.openlocfilehash: 7145dde55e79eeea6e3ceb91dfc1c93043a8857c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786300"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength 屬性宣告

ValidateLength 屬性會指定 Cmdlet 參數引數的最小和最大字元數。 Windows PowerShell 函數也可以使用這個屬性。

## <a name="syntax"></a>語法

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>參數

`MinLength`需要 ([system.object](/dotnet/api/System.Int32)) 。 指定允許的最小字元數。

`MaxLength`需要 ([system.object](/dotnet/api/System.Int32)) 。 指定允許的最大字元數。

## <a name="remarks"></a>備註

- 如需如何宣告此屬性的詳細資訊，請參閱[如何宣告輸入驗證規則](./how-to-validate-parameter-input.md)。

- 未使用此屬性時，對應的參數引數可以是任何長度。

- 在下列情況下，Windows PowerShell 執行時間會擲回錯誤：

  - 當屬性參數的值 `MaxLength` 小於屬性參數的值時 `MinLength` 。

  - 當 `MaxLength` 屬性參數設為0時。

  - 當引數不是字串時。

- ValidateLength 屬性是由[Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)類別所定義。

## <a name="see-also"></a>另請參閱

[Validatelengthattribute。](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
