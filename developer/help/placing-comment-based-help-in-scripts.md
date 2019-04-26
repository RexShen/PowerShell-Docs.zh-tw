---
title: 在 指令碼中放置註解型說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083224"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="19ef7-102">將註解型說明置於指令碼</span><span class="sxs-lookup"><span data-stu-id="19ef7-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="19ef7-103">本主題說明的指令碼的註解型說明的位置，讓`Get-Help`cmdlet 與指令碼而非與可能的指令碼中的任何函式，將註解為基礎的 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="19ef7-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="19ef7-104">如需指令碼的註解型說明的位置</span><span class="sxs-lookup"><span data-stu-id="19ef7-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="19ef7-105">在指令碼檔案開頭。</span><span class="sxs-lookup"><span data-stu-id="19ef7-105">At the beginning of the script file.</span></span> <span data-ttu-id="19ef7-106">指令碼說明可以是指令碼中僅前面加上註解和空白的行。</span><span class="sxs-lookup"><span data-stu-id="19ef7-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="19ef7-107">在指令碼檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="19ef7-107">At the end of the script file.</span></span>

  <span data-ttu-id="19ef7-108">如果函式宣告 （之後的說明） 的指令碼主體中的第一個項目，必須有至少兩個空白的行之間的指令碼說明函式宣告。</span><span class="sxs-lookup"><span data-stu-id="19ef7-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="19ef7-109">否則，說明會解譯為所說明的函式而言不指令碼的說明。</span><span class="sxs-lookup"><span data-stu-id="19ef7-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="19ef7-110">在指令碼中的說明位置的範例</span><span class="sxs-lookup"><span data-stu-id="19ef7-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="19ef7-111">下列範例會顯示每個指令碼的註解型說明的放置選項。</span><span class="sxs-lookup"><span data-stu-id="19ef7-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="19ef7-112">協助在指令碼的開頭</span><span class="sxs-lookup"><span data-stu-id="19ef7-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="19ef7-113">下列範例會示範註解為基礎的指令碼開頭。</span><span class="sxs-lookup"><span data-stu-id="19ef7-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="19ef7-114">在指令碼結尾處的協助</span><span class="sxs-lookup"><span data-stu-id="19ef7-114">Help at the End of a Script</span></span>

 <span data-ttu-id="19ef7-115">下列範例會示範註解為基礎的指令碼結尾。</span><span class="sxs-lookup"><span data-stu-id="19ef7-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```