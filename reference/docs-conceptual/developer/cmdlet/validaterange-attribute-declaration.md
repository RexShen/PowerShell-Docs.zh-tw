---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateRange 屬性宣告
description: ValidateRange 屬性宣告
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660595"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange 屬性宣告

ValidateRange 屬性會指定 Cmdlet 參數引數) 範圍 (的最小值和最大值。 Windows PowerShell 函數也可以使用這個屬性。

## <a name="syntax"></a>語法

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>參數

`MinRange` ([system.object](/dotnet/api/system.object)) 需要的物件。 指定允許的最小值。

`MaxRange` ([system.object](/dotnet/api/system.object)) 需要的物件。 指定允許的最大值。

## <a name="remarks"></a>備註

- 當參數的值大於參數的值時，Windows PowerShell 執行時間會擲回結構錯誤 `MinRange` `MaxRange` 。

- 在下列情況下，Windows PowerShell 執行時間會擲回驗證錯誤：

  - 當引數的值小於 `MinRange` 限制或大於 `MaxRange` 限制時。

  - 當引數與和參數的類型不同時 `MinRange` `MaxRange` 。

- ValidateRange 屬性是由 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) 類別所定義。

## <a name="see-also"></a>另請參閱

[Validaterangeattribute。](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
