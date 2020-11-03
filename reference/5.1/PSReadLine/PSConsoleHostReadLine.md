---
external help file: PSReadLine-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: 2dee8287558e9d5c001000fc5a57a859febee1a3
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208651"
---
# <span data-ttu-id="8186a-103">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="8186a-103">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="8186a-104">概要</span><span class="sxs-lookup"><span data-stu-id="8186a-104">SYNOPSIS</span></span>
<span data-ttu-id="8186a-105">此函數是 PSReadLine 的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="8186a-105">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="8186a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8186a-106">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="8186a-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8186a-107">DESCRIPTION</span></span>

<span data-ttu-id="8186a-108">`PSConsoleHostReadLine` 是 PSReadLine 模組的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="8186a-108">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="8186a-109">PowerShell 主控台主機會自動載入 PSReadLine 模組，並呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="8186a-109">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="8186a-110">在正常操作的情況下，此函式不適合從命令列使用。</span><span class="sxs-lookup"><span data-stu-id="8186a-110">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="8186a-111">擴充點 `PSConsoleHostReadLine` 是主控台主機的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="8186a-111">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="8186a-112">主機會使用此名稱呼叫任何別名、函數或腳本。</span><span class="sxs-lookup"><span data-stu-id="8186a-112">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="8186a-113">PSReadLine 會定義此函式，以便從主控台主機呼叫它。</span><span class="sxs-lookup"><span data-stu-id="8186a-113">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="8186a-114">範例</span><span class="sxs-lookup"><span data-stu-id="8186a-114">EXAMPLES</span></span>

### <span data-ttu-id="8186a-115">範例 1</span><span class="sxs-lookup"><span data-stu-id="8186a-115">Example 1</span></span>

<span data-ttu-id="8186a-116">此函式不適合從命令列使用。</span><span class="sxs-lookup"><span data-stu-id="8186a-116">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="8186a-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8186a-117">PARAMETERS</span></span>

## <span data-ttu-id="8186a-118">輸入</span><span class="sxs-lookup"><span data-stu-id="8186a-118">INPUTS</span></span>

### <span data-ttu-id="8186a-119">無</span><span class="sxs-lookup"><span data-stu-id="8186a-119">None</span></span>

## <span data-ttu-id="8186a-120">輸出</span><span class="sxs-lookup"><span data-stu-id="8186a-120">OUTPUTS</span></span>

### <span data-ttu-id="8186a-121">無</span><span class="sxs-lookup"><span data-stu-id="8186a-121">None</span></span>

## <span data-ttu-id="8186a-122">注意</span><span class="sxs-lookup"><span data-stu-id="8186a-122">NOTES</span></span>

## <span data-ttu-id="8186a-123">相關連結</span><span class="sxs-lookup"><span data-stu-id="8186a-123">RELATED LINKS</span></span>

[<span data-ttu-id="8186a-124">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="8186a-124">about_PSReadLine</span></span>](./About/about_PSReadLine.md)
