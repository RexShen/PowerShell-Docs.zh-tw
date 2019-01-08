---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: 24a3f00987ff5ca4bf82d1a3206857ec3c4b3f09
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400630"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="7f084-103">如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="7f084-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="7f084-104">Tab 鍵自動完成功能可以在您在 [指令碼窗格] 或 [命令窗格] 中輸入時，自動為您提供協助。</span><span class="sxs-lookup"><span data-stu-id="7f084-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="7f084-105">使用下列步驟以利用這項功能︰</span><span class="sxs-lookup"><span data-stu-id="7f084-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="7f084-106">自動完成命令項目</span><span class="sxs-lookup"><span data-stu-id="7f084-106">To automatically complete a command entry</span></span>

<span data-ttu-id="7f084-107">在命令窗格或指令碼窗格中，輸入命令的幾個字元，然後按 TAB 鍵選取所需的完成文字。</span><span class="sxs-lookup"><span data-stu-id="7f084-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="7f084-108">如果有多個項目以您初始輸入的文字為開頭，請連續按 TAB 鍵，直到出現您想要的項目。</span><span class="sxs-lookup"><span data-stu-id="7f084-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="7f084-109">TAB 鍵自動完成可協助輸入 Cmdlet 名稱、參數名稱、變數名稱、物件屬性名稱或檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="7f084-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="7f084-110">在指令碼窗格中，只有在編輯 .ps1、.psd1 或 .psm1 檔案時，按 TAB 鍵才會自動完成命令。</span><span class="sxs-lookup"><span data-stu-id="7f084-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="7f084-111">任何時候當您在命令窗格中輸入時，都可以使用 TAB 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="7f084-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="7f084-112">自動完成 Cmdlet 參數項目</span><span class="sxs-lookup"><span data-stu-id="7f084-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="7f084-113">在命令窗格或指令碼窗格中輸入一個 Cmdlet，後面接著虛線，然後按 TAB 鍵。</span><span class="sxs-lookup"><span data-stu-id="7f084-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press TAB.</span></span>

<span data-ttu-id="7f084-114">例如，輸入 `Get-Process -`，然後按 TAB 鍵多次，輪流顯示 Cmdlet 的每個參數。</span><span class="sxs-lookup"><span data-stu-id="7f084-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f084-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f084-115">See Also</span></span>

- [<span data-ttu-id="7f084-116">Windows PowerShell ISE 簡介</span><span class="sxs-lookup"><span data-stu-id="7f084-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="7f084-117">如何建立 PowerShell 索引標籤</span><span class="sxs-lookup"><span data-stu-id="7f084-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
