---
ms.date: 09/12/2016
ms.topic: reference
title: 將註解型說明置於指令碼
description: 將註解型說明置於指令碼
ms.openlocfilehash: b0d32b7ab063269085899a643b0c3a17da2073fc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645443"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="2b3f2-103">將註解型說明置於指令碼</span><span class="sxs-lookup"><span data-stu-id="2b3f2-103">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="2b3f2-104">本主題說明如何為腳本放置以批註為基礎的說明，讓 `Get-Help` Cmdlet 將批註式說明主題與腳本產生關聯，而不是與腳本中可能的任何函式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="2b3f2-104">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="2b3f2-105">放置腳本 Comment-Based 說明的位置</span><span class="sxs-lookup"><span data-stu-id="2b3f2-105">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="2b3f2-106">指令檔的開頭。</span><span class="sxs-lookup"><span data-stu-id="2b3f2-106">At the beginning of the script file.</span></span>

  <span data-ttu-id="2b3f2-107">腳本說明可以在腳本中的前面加上批註和空白行。</span><span class="sxs-lookup"><span data-stu-id="2b3f2-107">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="2b3f2-108">指令檔的結尾。</span><span class="sxs-lookup"><span data-stu-id="2b3f2-108">At the end of the script file.</span></span>

  <span data-ttu-id="2b3f2-109">如果腳本主體中的第一個專案 (在 [說明]) 之後是函式宣告，則腳本說明和函式宣告的結尾必須至少有兩個空白行。</span><span class="sxs-lookup"><span data-stu-id="2b3f2-109">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="2b3f2-110">否則，說明會被視為函數的說明，而不是腳本的說明。</span><span class="sxs-lookup"><span data-stu-id="2b3f2-110">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="2b3f2-111">腳本中說明位置的範例</span><span class="sxs-lookup"><span data-stu-id="2b3f2-111">Examples of Help Placement in a Script</span></span>

<span data-ttu-id="2b3f2-112">下列範例會顯示腳本的批註式說明的每個放置選項。</span><span class="sxs-lookup"><span data-stu-id="2b3f2-112">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="2b3f2-113">腳本開頭的說明</span><span class="sxs-lookup"><span data-stu-id="2b3f2-113">Help at the Beginning of a Script</span></span>

<span data-ttu-id="2b3f2-114">下列範例顯示以批註為基礎的腳本開頭。</span><span class="sxs-lookup"><span data-stu-id="2b3f2-114">The following example shows comment-based at the beginning of a script.</span></span>

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="2b3f2-115">腳本結尾的說明</span><span class="sxs-lookup"><span data-stu-id="2b3f2-115">Help at the End of a Script</span></span>

 <span data-ttu-id="2b3f2-116">下列範例顯示以批註為基礎的腳本結尾。</span><span class="sxs-lookup"><span data-stu-id="2b3f2-116">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```
