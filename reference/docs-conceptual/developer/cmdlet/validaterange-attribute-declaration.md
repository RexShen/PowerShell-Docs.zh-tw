---
title: ValidateRange 屬性聲明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369127"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange 屬性宣告

ValidateRange 屬性會指定 Cmdlet 參數引數的最小和最大值（範圍）。 Windows PowerShell 函數也可以使用這個屬性。

## <a name="syntax"></a>語法

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>參數

需要 `MinRange` （[system.object](/dotnet/api/system.object)）。 指定允許的最小值。

需要 `MaxRange` （[system.object](/dotnet/api/system.object)）。 指定允許的最大值。

## <a name="remarks"></a>備註

- 當 `MinRange` 參數的值大於 `MaxRange` 參數的值時，Windows PowerShell 執行時間會擲回結構錯誤。

- 在下列情況下，Windows PowerShell 執行時間會擲回驗證錯誤：

    - 當引數的值小於 `MinRange` 限制或大於 `MaxRange` 的限制時。

    - 當引數與 `MinRange` 和 @no__t 1 參數的類型不同時。

- ValidateRange 屬性是由[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)類別所定義。

## <a name="see-also"></a>另請參閱

[Validaterangeattribute。](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
