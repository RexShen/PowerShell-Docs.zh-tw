---
ms.date: 09/12/2016
ms.topic: reference
title: 將註解型說明置於函式
description: 將註解型說明置於函式
ms.openlocfilehash: 3bd72f0c71d8f6ad54c43c99f044423c072fdeeb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658198"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="1f0dd-103">將註解型說明置於函式</span><span class="sxs-lookup"><span data-stu-id="1f0dd-103">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="1f0dd-104">本主題說明如何為函式放置以批註為基礎的說明，讓 `Get-Help` Cmdlet 將批註式說明主題與正確的函式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-104">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="1f0dd-105">放置函式 Comment-Based 說明的位置</span><span class="sxs-lookup"><span data-stu-id="1f0dd-105">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="1f0dd-106">在函數主體的開頭。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-106">At the beginning of the function body.</span></span>

- <span data-ttu-id="1f0dd-107">在函數主體的結尾。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-107">At the end of the function body.</span></span>

- <span data-ttu-id="1f0dd-108">關鍵字之前 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-108">Before the `Function` keyword.</span></span> <span data-ttu-id="1f0dd-109">當函式在腳本或腳本模組中時，以批註為基礎的說明和關鍵字的最後一行之間不能有一個以上的空白行 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-109">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="1f0dd-110">否則，請 `Get-Help` 將說明與腳本產生關聯，而不是使用函數。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-110">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="1f0dd-111">函數中說明位置的範例</span><span class="sxs-lookup"><span data-stu-id="1f0dd-111">Examples of Help Placement in a Function</span></span>

<span data-ttu-id="1f0dd-112">下列範例會顯示函式之批註式說明的三個放置選項。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-112">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="1f0dd-113">函數主體開頭的說明</span><span class="sxs-lookup"><span data-stu-id="1f0dd-113">Help at the Beginning of a Function Body</span></span>

<span data-ttu-id="1f0dd-114">下列範例顯示以批註為基礎的函式主體開頭。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-114">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="1f0dd-115">函數主體結尾的說明</span><span class="sxs-lookup"><span data-stu-id="1f0dd-115">Help at the End of a Function Body</span></span>

 <span data-ttu-id="1f0dd-116">下列範例顯示以批註為基礎的函式主體結尾。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-116">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="1f0dd-117">Function 關鍵字之前的說明</span><span class="sxs-lookup"><span data-stu-id="1f0dd-117">Help Before the Function Keyword</span></span>

 <span data-ttu-id="1f0dd-118">下列範例會根據 function 關鍵字之前的行，顯示批註。</span><span class="sxs-lookup"><span data-stu-id="1f0dd-118">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```
