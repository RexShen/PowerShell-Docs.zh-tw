---
title: OutputType 屬性宣告 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a4cc874031bba092cfef6041bef0e19e6af3f09c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786538"
---
# <a name="outputtype-attribute-declaration"></a>OutputType 屬性宣告

`OutputType`屬性會識別 Cmdlet、函數或腳本所傳回的 .NET Framework 類型。

## <a name="syntax"></a>語法

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>參數

輸入 (`string[]` 或 `Type[]` 必要) 。 指定 Cmdlet 函數或腳本所傳回的類型。

ParameterSetName (string [] ) 選擇性。 指定傳回參數中指定之類型的參數集 `type` 。

providerCmdlet 選擇性。 指定傳回參數中所指定類型的提供者 Cmdlet `type` 。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
