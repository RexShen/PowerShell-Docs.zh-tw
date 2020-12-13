---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateCount 屬性宣告
description: ValidateCount 屬性宣告
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646272"
---
# <a name="validatecount-attribute-declaration"></a>ValidateCount 屬性宣告

ValidateCount 屬性會指定 Cmdlet 參數允許的最小和最大引數數目。

## <a name="syntax"></a>語法

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>參數

`MinLength` 需要 ([system.object][]) 。 指定引數的最小數目。

`MaxLength` 需要 ([system.object][]) 。 指定引數的最大數目。

## <a name="remarks"></a>備註

- 如需如何宣告這個屬性的詳細資訊，請參閱 [如何驗證引數計數][]。

- 如果未叫用此屬性，對應的 Cmdlet 參數可以有任意數目的引數。

- 在下列情況下，Windows PowerShell 執行時間會擲回錯誤：

  - `MinLength`和 `MaxLength` 屬性參數的類型不是[system.object][]。

  - Attribute 參數的值 `MaxLength` 小於 `MinLength` attribute 參數的值。

- ValidateCount 屬性是由 [ValidateCountAttribute][] 類別所定義。

## <a name="see-also"></a>另請參閱

[ValidateCountAttribute。][]

[如何驗證引數計數][]

[撰寫 Windows PowerShell Cmdlet][]

[如何驗證引數計數]: how-to-validate-an-argument-count.md
[撰寫 Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[ValidateCountAttribute。]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
