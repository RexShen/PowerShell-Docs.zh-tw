---
title: 屬性型別 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863804"
---
# <a name="attribute-types"></a>屬性類型

Cmdlet 屬性可以依功能分組。
下列各節說明可用的屬性，並描述項目執行階段會叫用的屬性時。

## <a name="cmdlet-attributes"></a>Cmdlet 屬性

### <a name="cmdlet"></a>Cmdlet

指令程式會識別.NET Framework 類別。
這是必要的基底屬性。
如需詳細資訊，請參閱 < [Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。

## <a name="parameter-attributes"></a>參數屬性

### <a name="parameter"></a>參數

Cmdlet 參數的形式會識別在 cmdlet 類別中的公用屬性。
如需詳細資訊，請參閱 <<c0> [ 參數的屬性宣告](./parameter-attribute-declaration.md)。

### <a name="alias"></a>別名

指定一或多個參數的別名。
如需詳細資訊，請參閱 <<c0> [ 別名屬性宣告](./alias-attribute-declaration.md)。

## <a name="argument-validation-attributes"></a>引數驗證屬性

### <a name="validatecount"></a>ValidateCount

指定允許針對 cmdlet 參數的引數的最小和最大數目。
如需詳細資訊，請參閱 < [ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)。

### <a name="validatelength"></a>ValidateLength

指定最小和最大的字元數的 cmdlet 參數引數。
如需詳細資訊，請參閱 < [ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)。

### <a name="validatepattern"></a>ValidatePattern

指定 cmdlet 參數引數必須符合規則運算式模式。
如需詳細資訊，請參閱 < [ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)。

### <a name="validaterange"></a>ValidateRange

指定 cmdlet 參數引數的最小和最大值。
如需詳細資訊，請參閱 < [ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)。

### <a name="validateset"></a>ValidateSet

指定一組 cmdlet 參數引數的有效值。
如需詳細資訊，請參閱 < [ValidateSet 屬性宣告](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
