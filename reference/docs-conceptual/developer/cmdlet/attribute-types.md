---
ms.date: 09/13/2016
ms.topic: reference
title: 屬性類型
description: 屬性類型
ms.openlocfilehash: 65640f2f8449887dedb9fae137eb16b6252f1d57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667108"
---
# <a name="attribute-types"></a>屬性類型

Cmdlet 屬性可以依功能分組。
下列各節描述可用的屬性，並描述叫用屬性時執行時間的功能。

## <a name="cmdlet-attributes"></a>Cmdlet 屬性

### <a name="cmdlet"></a>Cmdlet

將 .NET Framework 類別識別為 Cmdlet。
這是必要的基底屬性。
如需詳細資訊，請參閱 [Cmdlet 屬性聲明](./cmdlet-attribute-declaration.md)。

## <a name="parameter-attributes"></a>參數屬性

### <a name="parameter"></a>參數

將 Cmdlet 類別中的公用屬性識別為 Cmdlet 參數。
如需詳細資訊，請參閱 [參數屬性聲明](./parameter-attribute-declaration.md)。

### <a name="alias"></a>Alias

為參數指定一或多個別名。
如需詳細資訊，請參閱 [別名屬性聲明](./alias-attribute-declaration.md)。

## <a name="argument-validation-attributes"></a>引數驗證屬性

### <a name="validatecount"></a>ValidateCount

指定 Cmdlet 參數允許的最小和最大引數數目。
如需詳細資訊，請參閱 [ValidateCount 屬性聲明](./validatecount-attribute-declaration.md)。

### <a name="validatelength"></a>ValidateLength

指定 Cmdlet 參數引數的最小和最大字元數。
如需詳細資訊，請參閱 [ValidateLength 屬性聲明](./validatelength-attribute-declaration.md)。

### <a name="validatepattern"></a>ValidatePattern

指定 Cmdlet 參數引數必須符合的正則運算式模式。
如需詳細資訊，請參閱 [ValidatePattern 屬性聲明](./validatepattern-attribute-declaration.md)。

### <a name="validaterange"></a>ValidateRange

指定 Cmdlet 參數引數的最小值和最大值。
如需詳細資訊，請參閱 [ValidateRange 屬性聲明](./validaterange-attribute-declaration.md)。

### <a name="validateset"></a>ValidateSet

為 Cmdlet 參數引數指定一組有效的值。
如需詳細資訊，請參閱 [ValidateSet 屬性聲明](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
