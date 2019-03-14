---
title: ValidateCount 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794430"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 屬性宣告

ValidateCount 屬性會指定允許針對 cmdlet 參數的引數的最小和最大數目。

## <a name="syntax"></a>語法

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>參數

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) 所需。 指定引數的數目下限。

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) 所需。 指定的引數的數目上限。

## <a name="remarks"></a>備註

- 如需如何宣告這個屬性的詳細資訊，請參閱[宣告輸入驗證規則如何](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)。

- 無法叫用這個屬性時，對應的 cmdlet 參數可以有任意數目的引數。

- Windows PowerShell 執行階段會擲回錯誤，在下列情況下：

    - `MinLength`並`MaxLength`屬性參數不是型別[System.Int32](/dotnet/api/System.Int32)。

    - 值`MaxLength`屬性的參數小於值`MinLength`屬性參數。

- ValidateCount 屬性所定義[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)類別。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[如何宣告輸入的驗證規則](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
