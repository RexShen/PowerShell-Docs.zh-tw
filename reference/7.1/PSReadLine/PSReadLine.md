---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: a404461e2b92f269d581b18c3ebe7643aa86c3a4
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "93206483"
---
# <span data-ttu-id="9a3d2-103">PSReadLine 模組</span><span class="sxs-lookup"><span data-stu-id="9a3d2-103">PSReadLine Module</span></span>

## <span data-ttu-id="9a3d2-104">描述</span><span class="sxs-lookup"><span data-stu-id="9a3d2-104">Description</span></span>

<span data-ttu-id="9a3d2-105">PSReadLine 模組包含可讓您在 PowerShell 中自訂命令列編輯環境的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-105">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="9a3d2-106">這些文章記載 PSReadLine v2.0。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-106">These articles documents PSReadLine v2.0.</span></span> <span data-ttu-id="9a3d2-107">此版本隨附于 PowerShell v6 和 Windows 10 2018 年10月更新 (組建 1809) 。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-107">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="9a3d2-108">從 PowerShell 7.0 開始，如果偵測到螢幕讀取程式，PowerShell 會略過在 Windows 上自動載入 PSReadLine。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-108">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="9a3d2-109">PSReadLine 目前無法與螢幕讀取器順利搭配運作。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-109">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="9a3d2-110">Windows 上 PowerShell 7.0 的預設轉譯和格式可正常運作。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-110">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="9a3d2-111">如有必要，您可以手動載入模組。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-111">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="9a3d2-112">PSReadLine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9a3d2-112">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="9a3d2-113">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="9a3d2-113">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="9a3d2-114">PSReadLine 的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-114">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="9a3d2-115">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9a3d2-115">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="9a3d2-116">取得 PSReadLine 模組的系結索引鍵函數。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-116">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="9a3d2-117">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="9a3d2-117">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="9a3d2-118">取得可設定之選項的值。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-118">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="9a3d2-119">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="9a3d2-119">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="9a3d2-120">此函數是 PSReadLine 的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-120">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="9a3d2-121">移除-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9a3d2-121">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="9a3d2-122">移除索引鍵系結。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-122">Removes a key binding.</span></span>

### [<span data-ttu-id="9a3d2-123">設定-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="9a3d2-123">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="9a3d2-124">將索引鍵系結至使用者定義或 PSReadLine 的索引鍵處理函式。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-124">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="9a3d2-125">設定-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="9a3d2-125">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="9a3d2-126">自訂 **PSReadLine** 中的命令列編輯行為。</span><span class="sxs-lookup"><span data-stu-id="9a3d2-126">Customizes the behavior of command line editing in **PSReadLine** .</span></span>

