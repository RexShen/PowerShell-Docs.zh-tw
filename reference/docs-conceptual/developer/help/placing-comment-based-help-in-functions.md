---
title: 在函式中放置以批註為基礎的協助 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367777"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="c5540-102">將註解型說明置於函式</span><span class="sxs-lookup"><span data-stu-id="c5540-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="c5540-103">本主題說明如何為函式放置以批註為基礎的協助，讓 `Get-Help` Cmdlet 將以批註為基礎的說明主題與正確的函式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c5540-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="c5540-104">要在何處放置函式以批註為基礎的說明</span><span class="sxs-lookup"><span data-stu-id="c5540-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="c5540-105">在函式主體的開頭。</span><span class="sxs-lookup"><span data-stu-id="c5540-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="c5540-106">在函式主體的結尾。</span><span class="sxs-lookup"><span data-stu-id="c5540-106">At the end of the function body.</span></span>

- <span data-ttu-id="c5540-107">`Function` 關鍵字之前。</span><span class="sxs-lookup"><span data-stu-id="c5540-107">Before the `Function` keyword.</span></span> <span data-ttu-id="c5540-108">當函式在腳本或腳本模組中時，以批註為基礎的說明和 `Function` 關鍵字的最後一行之間不能有一個以上的空白行。</span><span class="sxs-lookup"><span data-stu-id="c5540-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="c5540-109">否則，`Get-Help` 會將說明與腳本建立關聯，而不是與函式相關聯。</span><span class="sxs-lookup"><span data-stu-id="c5540-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="c5540-110">說明放置在函式中的範例</span><span class="sxs-lookup"><span data-stu-id="c5540-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="c5540-111">下列範例會顯示函式之以批註為基礎之說明的三個放置選項。</span><span class="sxs-lookup"><span data-stu-id="c5540-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="c5540-112">函式主體開頭的說明</span><span class="sxs-lookup"><span data-stu-id="c5540-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="c5540-113">下列範例會顯示在函式主體開頭的以批註為基礎。</span><span class="sxs-lookup"><span data-stu-id="c5540-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="c5540-114">函式主體結尾的說明</span><span class="sxs-lookup"><span data-stu-id="c5540-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="c5540-115">下列範例會顯示以批註為基礎的函式主體結尾。</span><span class="sxs-lookup"><span data-stu-id="c5540-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="c5540-116">Function 關鍵字之前的說明</span><span class="sxs-lookup"><span data-stu-id="c5540-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="c5540-117">下列範例會根據函式關鍵字前面的一行來顯示批註。</span><span class="sxs-lookup"><span data-stu-id="c5540-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```