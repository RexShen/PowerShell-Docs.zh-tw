---
title: ValidateLength 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735101"
---
# <a name="validatelength-attribute-declaration"></a>ValidateLength 屬性宣告

ValidateLength 屬性會指定最小和最大的字元數的 cmdlet 參數引數。 這個屬性也可用 Windows PowerShell 函式。

## <a name="syntax"></a>語法

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>參數

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) 所需。 指定允許的字元數目下限。

`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) 所需。 指定允許的字元數目上限。

## <a name="remarks"></a>備註

- 如需如何宣告這個屬性的詳細資訊，請參閱[宣告輸入驗證規則如何](./how-to-validate-parameter-input.md)。

- 不使用這個屬性時，對應參數的引數可以是任何長度。

- Windows PowerShell 執行階段會擲回錯誤，在下列情況下：

    - 當 windows 7`MaxLength`屬性的參數小於值`MinLength`屬性參數。

    - 當`MaxLength`屬性參數設定為 0。

    - 當引數不是字串。

- ValidateLength 屬性所定義[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)類別。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
