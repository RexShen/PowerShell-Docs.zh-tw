---
title: ValidateCount 屬性聲明 |Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369227"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 屬性宣告

ValidateCount 屬性會指定 Cmdlet 參數所允許的最小和最大引數數目。

## <a name="syntax"></a>語法

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>參數

需要 `MinLength` （[System. Int32][]）。 指定引數的最小數目。

需要 `MaxLength` （[System. Int32][]）。 指定引數的最大數目。

## <a name="remarks"></a>備註

- 如需如何宣告這個屬性的詳細資訊，請參閱[如何驗證引數計數][]。

- 未叫用此屬性時，對應的 Cmdlet 參數可以有任意數目的引數。

- 在下列情況下，Windows PowerShell 執行時間會擲回錯誤：

    - @No__t-0 和 @no__t 1 屬性參數不是[System. Int32][]類型。

    - @No__t-0 屬性參數的值小於 `MinLength` 屬性參數的值。

- ValidateCount 屬性是由[ValidateCountAttribute。][]類別所定義。

## <a name="see-also"></a>另請參閱

[ValidateCountAttribute。][]

[如何驗證引數計數][]

[撰寫 Windows PowerShell Cmdlet][]

[如何驗證引數計數]: how-to-validate-an-argument-count.md
[撰寫 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[ValidateCountAttribute。]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
