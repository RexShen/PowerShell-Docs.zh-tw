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
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="6d227-102">OutputType 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="6d227-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="6d227-103">`OutputType`屬性識別的 cmdlet、 函數或指令碼傳回的.NET Framework 型別。</span><span class="sxs-lookup"><span data-stu-id="6d227-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="6d227-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d227-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="6d227-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d227-105">Parameters</span></span>

<span data-ttu-id="6d227-106">型別 (`string[]`或`Type[]`) 所需。</span><span class="sxs-lookup"><span data-stu-id="6d227-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="6d227-107">指定 cmdlet 的函式或指令碼所傳回的型別。</span><span class="sxs-lookup"><span data-stu-id="6d227-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="6d227-108">ParameterSetName (string [選擇性。</span><span class="sxs-lookup"><span data-stu-id="6d227-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="6d227-109">指定傳回型別中所指定的參數集`type`參數。</span><span class="sxs-lookup"><span data-stu-id="6d227-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="6d227-110">providerCmdlet 選擇性。</span><span class="sxs-lookup"><span data-stu-id="6d227-110">providerCmdlet Optional.</span></span> <span data-ttu-id="6d227-111">指定傳回的型別中所指定的提供者 cmdlet`type`參數。</span><span class="sxs-lookup"><span data-stu-id="6d227-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d227-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d227-112">See Also</span></span>

[<span data-ttu-id="6d227-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6d227-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
