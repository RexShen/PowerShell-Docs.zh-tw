---
ms.date: 09/13/2016
ms.topic: reference
title: OutputType 屬性宣告
description: OutputType 屬性宣告
ms.openlocfilehash: b5e33346e9ac29c13323781d62daffab892573a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646459"
---
# <a name="outputtype-attribute-declaration"></a>OutputType 屬性宣告

`OutputType`屬性會識別 Cmdlet、函式或腳本所傳回的 .NET Framework 類型。

## <a name="syntax"></a>語法

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>參數

輸入 (`string[]` 或 `Type[]`) 需要。 指定 Cmdlet 函數或腳本所傳回的類型。

ParameterSetName (string [] ) 選擇性。 指定傳回參數中所指定類型的參數集 `type` 。

providerCmdlet 選擇性。 指定可傳回參數中所指定類型的提供者 Cmdlet `type` 。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
