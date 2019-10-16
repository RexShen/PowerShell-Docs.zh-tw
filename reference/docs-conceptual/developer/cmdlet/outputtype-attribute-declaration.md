---
title: OutputType 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365337"
---
# <a name="outputtype-attribute-declaration"></a>OutputType 屬性宣告

@No__t-0 屬性會識別 Cmdlet、函數或腳本所傳回的 .NET Framework 類型。

## <a name="syntax"></a>語法

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>參數

需要類型（`string[]` 或 `Type[]`）。 指定 Cmdlet 函數或腳本所傳回的類型。

ParameterSetName （string []）選擇性。 指定傳回 `type` 參數中指定之類型的參數集。

providerCmdlet 選擇性。 指定傳回 `type` 參數中指定之類型的提供者 Cmdlet。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
