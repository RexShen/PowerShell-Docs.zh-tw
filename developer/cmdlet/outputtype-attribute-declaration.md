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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067598"
---
# <a name="outputtype-attribute-declaration"></a>OutputType 屬性宣告

`OutputType`屬性識別的 cmdlet、 函數或指令碼傳回的.NET Framework 型別。

## <a name="syntax"></a>語法

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>參數

型別 (`string[]`或`Type[]`) 所需。 指定 cmdlet 的函式或指令碼所傳回的型別。

ParameterSetName (string [選擇性。 指定傳回型別中所指定的參數集`type`參數。

providerCmdlet 選擇性。 指定傳回的型別中所指定的提供者 cmdlet`type`參數。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
