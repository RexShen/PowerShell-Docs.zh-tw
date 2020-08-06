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
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="b84d2-102">OutputType 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="b84d2-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="b84d2-103">`OutputType`屬性會識別 Cmdlet、函數或腳本所傳回的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="b84d2-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="b84d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="b84d2-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="b84d2-105">參數</span><span class="sxs-lookup"><span data-stu-id="b84d2-105">Parameters</span></span>

<span data-ttu-id="b84d2-106">輸入 (`string[]` 或 `Type[]` 必要) 。</span><span class="sxs-lookup"><span data-stu-id="b84d2-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="b84d2-107">指定 Cmdlet 函數或腳本所傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="b84d2-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="b84d2-108">ParameterSetName (string [] ) 選擇性。</span><span class="sxs-lookup"><span data-stu-id="b84d2-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="b84d2-109">指定傳回參數中指定之類型的參數集 `type` 。</span><span class="sxs-lookup"><span data-stu-id="b84d2-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="b84d2-110">providerCmdlet 選擇性。</span><span class="sxs-lookup"><span data-stu-id="b84d2-110">providerCmdlet Optional.</span></span> <span data-ttu-id="b84d2-111">指定傳回參數中所指定類型的提供者 Cmdlet `type` 。</span><span class="sxs-lookup"><span data-stu-id="b84d2-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="b84d2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b84d2-112">See Also</span></span>

[<span data-ttu-id="b84d2-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b84d2-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
