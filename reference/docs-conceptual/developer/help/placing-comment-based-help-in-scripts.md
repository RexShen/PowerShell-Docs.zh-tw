---
title: 在腳本中放置以批註為基礎的說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361177"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="7d173-102">將註解型說明置於指令碼</span><span class="sxs-lookup"><span data-stu-id="7d173-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="7d173-103">本主題說明如何為腳本放置以批註為基礎的說明，讓 `Get-Help` Cmdlet 將以批註為基礎的說明主題與腳本，而不是腳本中任何可能的函式相關聯。</span><span class="sxs-lookup"><span data-stu-id="7d173-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="7d173-104">在何處放置腳本的批註型說明</span><span class="sxs-lookup"><span data-stu-id="7d173-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="7d173-105">在指令檔的開頭。</span><span class="sxs-lookup"><span data-stu-id="7d173-105">At the beginning of the script file.</span></span> <span data-ttu-id="7d173-106">腳本說明只能透過批註和空白行放在腳本的前面。</span><span class="sxs-lookup"><span data-stu-id="7d173-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="7d173-107">在指令檔的結尾。</span><span class="sxs-lookup"><span data-stu-id="7d173-107">At the end of the script file.</span></span>

  <span data-ttu-id="7d173-108">如果腳本主體中的第一個專案（在說明後面）是函式宣告，腳本說明結尾和函式宣告之間必須至少有兩行空白行。</span><span class="sxs-lookup"><span data-stu-id="7d173-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="7d173-109">否則，說明會被解釋為函數的說明，而不是腳本的說明。</span><span class="sxs-lookup"><span data-stu-id="7d173-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="7d173-110">腳本中的說明位置範例</span><span class="sxs-lookup"><span data-stu-id="7d173-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="7d173-111">下列範例會顯示腳本的批註式說明的每個放置選項。</span><span class="sxs-lookup"><span data-stu-id="7d173-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="7d173-112">腳本開頭的說明</span><span class="sxs-lookup"><span data-stu-id="7d173-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="7d173-113">下列範例會顯示以批註為基礎的腳本開頭。</span><span class="sxs-lookup"><span data-stu-id="7d173-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="7d173-114">腳本結尾的說明</span><span class="sxs-lookup"><span data-stu-id="7d173-114">Help at the End of a Script</span></span>

 <span data-ttu-id="7d173-115">下列範例會顯示以批註為基礎的腳本結尾。</span><span class="sxs-lookup"><span data-stu-id="7d173-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```