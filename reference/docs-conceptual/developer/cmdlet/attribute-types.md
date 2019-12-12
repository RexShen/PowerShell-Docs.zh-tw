---
title: 屬性類型 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364577"
---
# <a name="attribute-types"></a>屬性類型

Cmdlet 屬性可以依功能分組。
下列各節描述可用的屬性，並描述叫用屬性時執行時間的功能。

## <a name="cmdlet-attributes"></a>Cmdlet 屬性

### <a name="cmdlet"></a>Cmdlet

將 .NET Framework 類別識別為 Cmdlet。
這是必要的基底屬性。
如需詳細資訊，請參閱[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告。

## <a name="parameter-attributes"></a>參數屬性

### <a name="parameter"></a>參數

將 Cmdlet 類別中的公用屬性識別為 Cmdlet 參數。
如需詳細資訊，請參閱[參數屬性](./parameter-attribute-declaration.md)宣告。

### <a name="alias"></a>別名

為參數指定一或多個別名。
如需詳細資訊，請參閱[Alias 屬性](./alias-attribute-declaration.md)宣告。

## <a name="argument-validation-attributes"></a>引數驗證屬性

### <a name="validatecount"></a>ValidateCount

指定 Cmdlet 參數所允許之引數的最小和最大數目。
如需詳細資訊，請參閱[ValidateCount 屬性](./validatecount-attribute-declaration.md)宣告。

### <a name="validatelength"></a>ValidateLength

指定 Cmdlet 參數引數的最小和最大字元數。
如需詳細資訊，請參閱[ValidateLength 屬性](./validatelength-attribute-declaration.md)宣告。

### <a name="validatepattern"></a>ValidatePattern

指定 Cmdlet 參數引數必須符合的正則運算式模式。
如需詳細資訊，請參閱[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告。

### <a name="validaterange"></a>ValidateRange

指定 Cmdlet 參數引數的最小和最大值。
如需詳細資訊，請參閱[ValidateRange 屬性](./validaterange-attribute-declaration.md)宣告。

### <a name="validateset"></a>ValidateSet

為 Cmdlet 參數引數指定一組有效的值。
如需詳細資訊，請參閱[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
