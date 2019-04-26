---
title: 函式中放置註解型說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083190"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="1649a-102">將註解型說明置於函式</span><span class="sxs-lookup"><span data-stu-id="1649a-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="1649a-103">本主題說明函式的註解型說明的位置，讓`Get-Help`cmdlet 關聯正確的函式中的註解為基礎的 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="1649a-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="1649a-104">函式的註解型說明的位置</span><span class="sxs-lookup"><span data-stu-id="1649a-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="1649a-105">函式主體的開頭。</span><span class="sxs-lookup"><span data-stu-id="1649a-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="1649a-106">在函式主體結束。</span><span class="sxs-lookup"><span data-stu-id="1649a-106">At the end of the function body.</span></span>

- <span data-ttu-id="1649a-107">之前`Function`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1649a-107">Before the `Function` keyword.</span></span> <span data-ttu-id="1649a-108">指令碼或指令碼模組中函式時，不能有一個以上的空白行之間最後一行的註解型說明和`Function`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1649a-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="1649a-109">否則，`Get-Help`產生關聯的說明，使用指令碼，而非與函式。</span><span class="sxs-lookup"><span data-stu-id="1649a-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="1649a-110">說明放置函式中的範例</span><span class="sxs-lookup"><span data-stu-id="1649a-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="1649a-111">下列範例會顯示每個函式的註解型說明的三個的放置選項。</span><span class="sxs-lookup"><span data-stu-id="1649a-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="1649a-112">協助在函式主體的開頭</span><span class="sxs-lookup"><span data-stu-id="1649a-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="1649a-113">下列範例會示範註解為基礎的函式主體開頭。</span><span class="sxs-lookup"><span data-stu-id="1649a-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="1649a-114">協助函式主體的結尾</span><span class="sxs-lookup"><span data-stu-id="1649a-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="1649a-115">下列範例會示範註解為基礎，函式主體的結尾。</span><span class="sxs-lookup"><span data-stu-id="1649a-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="1649a-116">在 Function 關鍵字前面說明</span><span class="sxs-lookup"><span data-stu-id="1649a-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="1649a-117">下列範例顯示在 function 關鍵字前面的行註解為基礎。</span><span class="sxs-lookup"><span data-stu-id="1649a-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```