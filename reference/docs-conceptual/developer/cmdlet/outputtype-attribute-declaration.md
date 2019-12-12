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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365337"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="eb7da-102">OutputType 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="eb7da-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="eb7da-103">`OutputType` 屬性會識別 Cmdlet、函數或腳本所傳回的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="eb7da-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb7da-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb7da-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="eb7da-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb7da-105">Parameters</span></span>

<span data-ttu-id="eb7da-106">需要類型（`string[]` 或 `Type[]`）。</span><span class="sxs-lookup"><span data-stu-id="eb7da-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="eb7da-107">指定 Cmdlet 函數或腳本所傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="eb7da-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="eb7da-108">ParameterSetName （string []）選擇性。</span><span class="sxs-lookup"><span data-stu-id="eb7da-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="eb7da-109">指定傳回 `type` 參數中指定之類型的參數集。</span><span class="sxs-lookup"><span data-stu-id="eb7da-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="eb7da-110">providerCmdlet 選擇性。</span><span class="sxs-lookup"><span data-stu-id="eb7da-110">providerCmdlet Optional.</span></span> <span data-ttu-id="eb7da-111">指定傳回 `type` 參數中指定之類型的提供者 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eb7da-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb7da-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb7da-112">See Also</span></span>

[<span data-ttu-id="eb7da-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb7da-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
