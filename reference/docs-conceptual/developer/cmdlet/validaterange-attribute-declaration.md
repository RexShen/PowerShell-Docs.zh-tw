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
ms.openlocfilehash: 560fa105ac3f93ae6334df0112f5290dfa20576c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692003"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange 屬性宣告

ValidateRange 屬性會指定 Cmdlet 參數引數的最小和最大值（範圍）。 Windows PowerShell 函數也可以使用這個屬性。

## <a name="syntax"></a>語法

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>參數

`MinRange`（[系統物件](/dotnet/api/system.object)）必要。 指定允許的最小值。

`MaxRange`（[系統物件](/dotnet/api/system.object)）必要。 指定允許的最大值。

## <a name="remarks"></a>備註

- 當參數的值大於參數的值時，Windows PowerShell 執行時間會擲回結構錯誤 `MinRange` `MaxRange` 。

- 在下列情況下，Windows PowerShell 執行時間會擲回驗證錯誤：

  - 當引數的值小於 `MinRange` 限制或大於 `MaxRange` 限制時。

  - 當引數與和參數的類型不同時 `MinRange` `MaxRange` 。

- ValidateRange 屬性是由[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)類別所定義。

## <a name="see-also"></a>另請參閱

[Validaterangeattribute。](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
