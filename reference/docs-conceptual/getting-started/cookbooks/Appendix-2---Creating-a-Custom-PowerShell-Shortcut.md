---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 附錄 2 建立自訂 PowerShell 捷徑
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="edcfb-103">附錄 2 - 建立自訂 PowerShell 捷徑</span><span class="sxs-lookup"><span data-stu-id="edcfb-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="edcfb-104">下列程序說明如何建立指向 Windows PowerShell 的捷徑，並在其中自訂幾個便利的選項。</span><span class="sxs-lookup"><span data-stu-id="edcfb-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="edcfb-105">建立指向 Powershell.exe 的捷徑。</span><span class="sxs-lookup"><span data-stu-id="edcfb-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="edcfb-106">以滑鼠右鍵按一下捷徑，然後按一下 [內容]。</span><span class="sxs-lookup"><span data-stu-id="edcfb-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="edcfb-107">按一下 **[選項]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="edcfb-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="edcfb-108">在 **[編輯選項]** 區段中，選取 **[快速編輯]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="edcfb-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="edcfb-109">此設定可讓您拖曳滑鼠左鍵，選取 Windows PowerShell 主控台視窗中的文字，也可讓您按 ENTER 鍵或按一下滑鼠右鍵，將文字複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="edcfb-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="edcfb-110">在 **[編輯選項]** 區段中，選取 **[插入模式]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="edcfb-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="edcfb-111">此設定可讓您以滑鼠右鍵按一下主控台視窗，自動貼上剪貼簿中的文字。</span><span class="sxs-lookup"><span data-stu-id="edcfb-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="edcfb-112">在 **[命令歷程記錄]** 區段的 **[緩衝區大小]** 方塊中，輸入或選取介於 1 到 999 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="edcfb-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="edcfb-113">這可設定將保留在主控台緩衝區中具類型的命令數目。</span><span class="sxs-lookup"><span data-stu-id="edcfb-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="edcfb-114">在 **[命令歷程記錄]** 區段中，選取 **[丟棄舊複本]** 核取方塊，以從主控台緩衝區中消除重複的命令。</span><span class="sxs-lookup"><span data-stu-id="edcfb-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="edcfb-115">按一下 **[配置]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="edcfb-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="edcfb-116">在 **[螢幕緩衝區]** 區段的 **[高度]** 方塊中，輸入介於 1 到 9999 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="edcfb-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="edcfb-117">高度表示已緩衝處理的輸出行數。</span><span class="sxs-lookup"><span data-stu-id="edcfb-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="edcfb-118">這是捲動主控台視窗時保留以供檢視的最大行數。</span><span class="sxs-lookup"><span data-stu-id="edcfb-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="edcfb-119">如果此數字低於 **[視窗大小]** 區段中所示的高度，視窗大小高度會自動縮減為相同的值。</span><span class="sxs-lookup"><span data-stu-id="edcfb-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="edcfb-120">在 **[視窗大小]** 區段中，針對寬度輸入介於 1 到 9999 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="edcfb-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="edcfb-121">這表示會橫跨主控台視窗顯示的字元數。</span><span class="sxs-lookup"><span data-stu-id="edcfb-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="edcfb-122">預設寬度為 80，Windows PowerShell 的輸出格式是針對此寬度所設計。</span><span class="sxs-lookup"><span data-stu-id="edcfb-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="edcfb-123">如果您想要將開啟的主控台放在桌面上的特定位置，請清除 **[視窗位置]** 區段中的 **[由系統安排視窗位置]** 核取方塊，然後在 **[視窗位置]** 區段中，變更 **[左]** 和 **[上]** 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="edcfb-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="edcfb-124">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="edcfb-124">Click **OK**.</span></span>