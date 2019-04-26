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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067173"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 屬性宣告

ValidateCount 屬性會指定允許針對 cmdlet 參數的引數的最小和最大數目。

## <a name="syntax"></a>語法

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>參數

`MinLength` ([System.Int32][]) 所需。 指定引數的數目下限。

`MaxLength`([System.Int32][]) 所需。 指定的引數的數目上限。

## <a name="remarks"></a>備註

- 如需如何宣告這個屬性的詳細資訊，請參閱[如何驗證引數計數][]。

- 無法叫用這個屬性時，對應的 cmdlet 參數可以有任意數目的引數。

- Windows PowerShell 執行階段會擲回錯誤，在下列情況下：

    - `MinLength`並`MaxLength`屬性參數不是型別[System.Int32][]。

    - 值`MaxLength`屬性的參數小於值`MinLength`屬性參數。

- ValidateCount 屬性所定義[System.Management.Automation.ValidateCountAttribute][]類別。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.ValidateCountAttribute][]

[如何驗證引數計數][]

[撰寫 Windows PowerShell Cmdlet][]

[如何驗證引數計數]: how-to-validate-an-argument-count.md
[撰寫 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
