---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 基本概念
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: b21c6cd84ea29d5e8085ccf8df2a5a9199e1d859
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950527"
---
# <a name="windows-powershell-basics"></a><span data-ttu-id="9eb68-103">Windows PowerShell 基本概念</span><span class="sxs-lookup"><span data-stu-id="9eb68-103">Windows PowerShell Basics</span></span>
<span data-ttu-id="9eb68-104">圖形化使用者介面使用大部分電腦使用者熟知的一些基本概念。</span><span class="sxs-lookup"><span data-stu-id="9eb68-104">Graphical user interfaces use some basic concepts that are well known to most computer users.</span></span> <span data-ttu-id="9eb68-105">使用者會依賴對這些介面的熟悉度來完成工作。</span><span class="sxs-lookup"><span data-stu-id="9eb68-105">Users rely on the familiarity of those interfaces to accomplish tasks.</span></span> <span data-ttu-id="9eb68-106">作業系統會向使用者呈現可瀏覽項目的圖形化呈現，通常是使用下拉式功能表來存取特定功能，以及使用操作功能表來存取內容特定功能。</span><span class="sxs-lookup"><span data-stu-id="9eb68-106">Operating systems present users with a graphical representation of items that can be browsed, usually with drop-down menus for accessing specific functionality and context menus for accessing context-specific functionality.</span></span>

<span data-ttu-id="9eb68-107">命令列介面 (CLI) (例如 Windows PowerShell) 必須使用不同的方式來公開資訊，因為它沒有可協助使用者的功能表或圖形化系統。</span><span class="sxs-lookup"><span data-stu-id="9eb68-107">A command-line interface (CLI), such as Windows PowerShell, must use a different approach to expose information, because it does not have menus or graphical systems to help the user.</span></span> <span data-ttu-id="9eb68-108">您需要先知道命令名稱，才能使用它們。</span><span class="sxs-lookup"><span data-stu-id="9eb68-108">You need to know command names before you can use them.</span></span> <span data-ttu-id="9eb68-109">雖然您可以輸入相當於 GUI 環境中功能的複雜命令，但是您必須熟悉常用命令和命令參數。</span><span class="sxs-lookup"><span data-stu-id="9eb68-109">Although you can type complex commands that are equivalent to the features in a GUI environment, you must become familiar with commonly-used commands and command parameters.</span></span>

<span data-ttu-id="9eb68-110">大部分 CLI 沒有可協助使用者了解介面的模式。</span><span class="sxs-lookup"><span data-stu-id="9eb68-110">Most CLIs do not have patterns that can help the user to learn the interface.</span></span> <span data-ttu-id="9eb68-111">因為 CLI 是第一個作業系統殼層，所以會任意選取多個命令名稱和參數名稱。</span><span class="sxs-lookup"><span data-stu-id="9eb68-111">Because CLIs were the first operating system shells, many command names and parameter names were selected arbitrarily.</span></span> <span data-ttu-id="9eb68-112">一般會選擇簡短命令名稱，而非完整命令名稱。</span><span class="sxs-lookup"><span data-stu-id="9eb68-112">Terse command names were generally chosen over clear ones.</span></span> <span data-ttu-id="9eb68-113">雖然說明系統和命令設計標準已整合為大部分 CLI，但是它們通常是設計成與最早的命令相容，因此數十年以前所做的決定仍然會形成命令集。</span><span class="sxs-lookup"><span data-stu-id="9eb68-113">Although help systems and command design standards are integrated into most CLIs, they have been generally designed for compatibility with the earliest commands, so the command set is still shaped by decisions made decades ago.</span></span>

<span data-ttu-id="9eb68-114">Windows PowerShell 是設計成利用使用者過往對 CLI 的了解。</span><span class="sxs-lookup"><span data-stu-id="9eb68-114">Windows PowerShell was designed to take advantage of a user's historic knowledge of CLIs.</span></span> <span data-ttu-id="9eb68-115">在本章中，我們會討論一些可用來快速了解 Windows PowerShell 的基本工具和概念。</span><span class="sxs-lookup"><span data-stu-id="9eb68-115">In this chapter, we will talk about some basic tools and concepts that you can use to learn Windows PowerShell quickly.</span></span> <span data-ttu-id="9eb68-116">其中包括：</span><span class="sxs-lookup"><span data-stu-id="9eb68-116">They include:</span></span>

- <span data-ttu-id="9eb68-117">使用 [Get-Command](/powershell/module/Microsoft.PowerShell.Core/get-command)</span><span class="sxs-lookup"><span data-stu-id="9eb68-117">Using [Get-Command](/powershell/module/Microsoft.PowerShell.Core/get-command)</span></span>

- <span data-ttu-id="9eb68-118">使用 [Cmd.exe](/windows-server/administration/windows-commands/cmd) 和 [UNIX 命令](/windows/wsl/reference)</span><span class="sxs-lookup"><span data-stu-id="9eb68-118">Using [Cmd.exe](/windows-server/administration/windows-commands/cmd) and [UNIX commands](/windows/wsl/reference)</span></span>

- [<span data-ttu-id="9eb68-119">使用 Tab 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="9eb68-119">Using Tab-Completion</span></span>](../../core-powershell/console/using-tab-expansion.md)

- [<span data-ttu-id="9eb68-120">使用 Get-Help</span><span class="sxs-lookup"><span data-stu-id="9eb68-120">Using Get-Help</span></span>](./getting-detailed-help-information.md)