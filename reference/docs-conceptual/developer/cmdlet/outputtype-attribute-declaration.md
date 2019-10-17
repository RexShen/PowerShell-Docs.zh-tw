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
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="616ed-102">OutputType 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="616ed-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="616ed-103">@No__t-0 屬性會識別 Cmdlet、函數或腳本所傳回的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="616ed-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="616ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="616ed-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="616ed-105">參數</span><span class="sxs-lookup"><span data-stu-id="616ed-105">Parameters</span></span>

<span data-ttu-id="616ed-106">需要類型（`string[]` 或 `Type[]`）。</span><span class="sxs-lookup"><span data-stu-id="616ed-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="616ed-107">指定 Cmdlet 函數或腳本所傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="616ed-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="616ed-108">ParameterSetName （string []）選擇性。</span><span class="sxs-lookup"><span data-stu-id="616ed-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="616ed-109">指定傳回 `type` 參數中指定之類型的參數集。</span><span class="sxs-lookup"><span data-stu-id="616ed-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="616ed-110">providerCmdlet 選擇性。</span><span class="sxs-lookup"><span data-stu-id="616ed-110">providerCmdlet Optional.</span></span> <span data-ttu-id="616ed-111">指定傳回 `type` 參數中指定之類型的提供者 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="616ed-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="616ed-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="616ed-112">See Also</span></span>

[<span data-ttu-id="616ed-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="616ed-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)