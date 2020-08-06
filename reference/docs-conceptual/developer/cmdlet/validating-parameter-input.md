---
title: 驗證參數輸入 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.openlocfilehash: e12c715cfa24edfff958b12be1f3517b2f545256
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783988"
---
# <a name="validating-parameter-input"></a>驗證參數輸入

PowerShell 可以用數種方式驗證傳遞給 Cmdlet 參數的引數。
PowerShell 可以驗證長度、範圍，以及引數字元的模式。
它可以驗證 (計數) 可用的引數數目。
這些驗證規則是由使用 Cmdlet 類別的公用屬性上的參數屬性所宣告的驗證屬性所定義。

若要驗證參數引數，PowerShell 執行時間會使用驗證屬性所提供的資訊，在執行 Cmdlet 之前確認參數的值。
如果參數輸入無效，使用者會收到錯誤訊息。
每個驗證參數都會定義 PowerShell 強制執行的驗證規則。

PowerShell 會根據下列屬性來強制執行驗證規則。

### <a name="validatecount"></a>ValidateCount

指定參數可以接受之引數的最小和最大數目。
如需詳細資訊，請參閱[ValidateCount 屬性](./validatecount-attribute-declaration.md)宣告。

### <a name="validatelength"></a>ValidateLength

指定參數引數中的最小和最大字元數。
如需詳細資訊，請參閱[ValidateLength 屬性](./validatelength-attribute-declaration.md)宣告。

### <a name="validatepattern"></a>ValidatePattern

指定驗證參數引數的正則運算式。
如需詳細資訊，請參閱[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告。

### <a name="validaterange"></a>ValidateRange

指定參數引數的最小和最大值。
如需詳細資訊，請參閱[ValidateRange 屬性](./validaterange-attribute-declaration.md)宣告。

### <a name="validateset"></a>ValidateSet

指定參數引數的有效值。
如需詳細資訊，請參閱[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告。

## <a name="see-also"></a>另請參閱

[如何驗證參數輸入](./how-to-validate-parameter-input.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
