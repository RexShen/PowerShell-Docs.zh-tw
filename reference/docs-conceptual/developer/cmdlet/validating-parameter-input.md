---
ms.date: 09/13/2016
ms.topic: reference
title: 驗證參數輸入
description: 驗證參數輸入
ms.openlocfilehash: a97b5c670e8c36463a85bbef1506f6311bdd5ec3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660406"
---
# <a name="validating-parameter-input"></a>驗證參數輸入

PowerShell 可以用數種方式驗證傳遞給 Cmdlet 參數的引數。
PowerShell 可以驗證引數字元的長度、範圍和字元模式。
它可以驗證 (計數) 可用的引數數目。
這些驗證規則是由以 Cmdlet 類別之公用屬性上的參數屬性宣告的驗證屬性所定義。

為了驗證參數引數，PowerShell 執行時間會使用驗證屬性所提供的資訊，在執行 Cmdlet 之前確認參數的值。
如果參數輸入無效，則使用者會收到錯誤訊息。
每個驗證參數都會定義 PowerShell 強制執行的驗證規則。

PowerShell 會根據下列屬性來強制執行驗證規則。

### <a name="validatecount"></a>ValidateCount

指定參數可以接受的引數數目下限和上限。
如需詳細資訊，請參閱 [ValidateCount 屬性聲明](./validatecount-attribute-declaration.md)。

### <a name="validatelength"></a>ValidateLength

指定參數引數中的最小和最大字元數。
如需詳細資訊，請參閱 [ValidateLength 屬性聲明](./validatelength-attribute-declaration.md)。

### <a name="validatepattern"></a>ValidatePattern

指定驗證參數引數的正則運算式。
如需詳細資訊，請參閱 [ValidatePattern 屬性聲明](./validatepattern-attribute-declaration.md)。

### <a name="validaterange"></a>ValidateRange

指定參數引數的最小值和最大值。
如需詳細資訊，請參閱 [ValidateRange 屬性聲明](./validaterange-attribute-declaration.md)。

### <a name="validateset"></a>ValidateSet

為參數引數指定有效的值。
如需詳細資訊，請參閱 [ValidateSet 屬性聲明](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[如何驗證參數輸入](./how-to-validate-parameter-input.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
