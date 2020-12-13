---
ms.date: 09/13/2016
ms.topic: reference
title: ValidateSet 屬性宣告
description: ValidateSet 屬性宣告
ms.openlocfilehash: 7894d00561366ada492911e8147acbd8d3454a55
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660475"
---
# <a name="validateset-attribute-declaration"></a>ValidateSet 屬性宣告

ValidateSetAttribute 屬性會指定 Cmdlet 參數引數的一組可能值。 Windows PowerShell 函數也可以使用這個屬性。

當指定這個屬性時，Windows PowerShell 執行時間會判斷提供的 Cmdlet 參數所提供的引數是否符合提供之元素集內的專案。 只有當參數引數符合集合中的元素時，才會執行此 Cmdlet。 如果找不到相符項，Windows PowerShell 執行時間會擲回錯誤。

## <a name="syntax"></a>語法

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>參數

`ValidValues` 需要 ([system.string](/dotnet/api/System.String)) 。 指定有效的參數元素值。 下列範例示範如何指定一個專案或多個元素。

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。 的預設值 `true` 表示忽略大小寫。 的值 `false` 可讓 Cmdlet 區分大小寫。

## <a name="remarks"></a>備註

- 此屬性每個參數只能使用一次。

- 如果參數值是陣列，則陣列的每個元素都必須符合屬性集的元素。

- ValidateSetAttribute 屬性是由 [ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) 類別所定義。

## <a name="see-also"></a>另請參閱

[Validatesetattribute。](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
