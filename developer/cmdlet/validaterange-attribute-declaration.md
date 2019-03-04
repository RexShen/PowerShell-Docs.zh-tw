---
title: ValidateRange 屬性宣告 |Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857034"
---
# <a name="validaterange-attribute-declaration"></a>ValidateRange 屬性宣告

ValidateRange 屬性指定的最小和最大值 （範圍） 的 cmdlet 參數引數。 這個屬性也可用 Windows PowerShell 函式。

## <a name="syntax"></a>語法

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>參數

`MinRange` ([System.Object](/dotnet/api/system.object)) 所需。 指定允許的最小值。

`MaxRange` ([System.Object](/dotnet/api/system.object)) 所需。 指定允許的最大值。

## <a name="remarks"></a>備註

- Windows PowerShell 執行階段會擲回建構錯誤時的值`MinRange`參數的值大於`MaxRange`參數。

- Windows PowerShell 執行階段會擲回下列情況下的驗證錯誤：

    - 當引數的值是小於`MinRange`限制或大於`MaxRange`限制。

    - 當引數不是相同的型別`MinRange`而`MaxRange`參數。

- ValidateRange 屬性所定義[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)類別。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
