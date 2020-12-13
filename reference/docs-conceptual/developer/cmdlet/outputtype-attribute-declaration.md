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
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="ce9da-103">OutputType 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="ce9da-103">OutputType Attribute Declaration</span></span>

<span data-ttu-id="ce9da-104">`OutputType`屬性會識別 Cmdlet、函式或腳本所傳回的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="ce9da-104">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="ce9da-105">語法</span><span class="sxs-lookup"><span data-stu-id="ce9da-105">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="ce9da-106">參數</span><span class="sxs-lookup"><span data-stu-id="ce9da-106">Parameters</span></span>

<span data-ttu-id="ce9da-107">輸入 (`string[]` 或 `Type[]`) 需要。</span><span class="sxs-lookup"><span data-stu-id="ce9da-107">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="ce9da-108">指定 Cmdlet 函數或腳本所傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="ce9da-108">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="ce9da-109">ParameterSetName (string [] ) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="ce9da-109">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="ce9da-110">指定傳回參數中所指定類型的參數集 `type` 。</span><span class="sxs-lookup"><span data-stu-id="ce9da-110">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="ce9da-111">providerCmdlet 選擇性。</span><span class="sxs-lookup"><span data-stu-id="ce9da-111">providerCmdlet Optional.</span></span> <span data-ttu-id="ce9da-112">指定可傳回參數中所指定類型的提供者 Cmdlet `type` 。</span><span class="sxs-lookup"><span data-stu-id="ce9da-112">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce9da-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce9da-113">See Also</span></span>

[<span data-ttu-id="ce9da-114">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce9da-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
