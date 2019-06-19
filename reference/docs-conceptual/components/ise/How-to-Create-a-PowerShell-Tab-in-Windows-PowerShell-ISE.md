---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中建立 PowerShell 索引標籤
ms.openlocfilehash: 7baf9a4051a196045d53eebf8ce5260bdc1bc55a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030597"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="1b537-103">如何在 Windows PowerShell ISE 中建立 PowerShell 索引標籤</span><span class="sxs-lookup"><span data-stu-id="1b537-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="1b537-104">Windows PowerShell 整合式指令碼環境 (ISE) 中的索引標籤讓您可以在同一個應用程式內，同時建立及使用數種執行環境。</span><span class="sxs-lookup"><span data-stu-id="1b537-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="1b537-105">每個 PowerShell 索引標籤會對應到不同的執行環境或工作階段。</span><span class="sxs-lookup"><span data-stu-id="1b537-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="1b537-106">您在一個索引標籤中建立的變數、函式和別名不會延續到另一個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b537-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="1b537-107">它們是不同的 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="1b537-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="1b537-108">使用下列步驟，在 Windows PowerShell 中開啟或關閉索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b537-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="1b537-109">若要重新命名索引標籤，可在 Windows PowerShell 索引標籤指令碼物件上設定 [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) 屬性。</span><span class="sxs-lookup"><span data-stu-id="1b537-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="1b537-110">建立及使用新的 PowerShell 索引標籤</span><span class="sxs-lookup"><span data-stu-id="1b537-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="1b537-111">在 **[檔案]** 功能表上，按一下 **[新增 PowerShell 索引標籤]** 。新的 PowerShell 索引標籤一律會以使用中視窗開啟。</span><span class="sxs-lookup"><span data-stu-id="1b537-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="1b537-112">PowerShell 索引標籤是依其開啟順序以累加方式編號。</span><span class="sxs-lookup"><span data-stu-id="1b537-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="1b537-113">每個索引標籤會與自己的 Windows PowerShell 主控台視窗建立關聯。</span><span class="sxs-lookup"><span data-stu-id="1b537-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="1b537-114">您一次最多可以開啟 32 個 PowerShell 索引標籤 (在 Windows PowerShell ISE 2.0 中僅限 8 個)，每個索引標籤會有自己的工作階段。</span><span class="sxs-lookup"><span data-stu-id="1b537-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="1b537-115">請注意，按一下工具列中的**新增**或**開啟**圖示，並不會建立新的索引標籤和個別工作階段。</span><span class="sxs-lookup"><span data-stu-id="1b537-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="1b537-116">相反地，這些按鈕會在目前使用中的索引標籤和工作階段中，開啟新的或現有的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="1b537-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="1b537-117">每個索引標籤和工作階段可以有多個開啟的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="1b537-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="1b537-118">當相關聯的工作階段為使用中時，工作階段的指令碼索引標籤只會出現在工作階段索引標籤下方。</span><span class="sxs-lookup"><span data-stu-id="1b537-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="1b537-119">若要將 PowerShell 索引標籤設為使用中，請按一下該索引標籤。若要從所有開啟的 PowerShell 索引標籤中進行選取，請在 **[檢視]** 功能表上，按一下您要使用的 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b537-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="1b537-120">建立及使用新的遠端 PowerShell 索引標籤</span><span class="sxs-lookup"><span data-stu-id="1b537-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="1b537-121">在 **[檔案]** 功能表上，按一下 **[新增遠端 PowerShell 索引標籤]** 在遠端電腦上建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="1b537-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="1b537-122">對話方塊隨即出現，並提示您輸入建立遠端連線所需的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1b537-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="1b537-123">遠端索引標籤的運作方式就像是本機 PowerShell 索引標籤，但命令和指令碼會在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="1b537-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="1b537-124">關閉 PowerShell 索引標籤</span><span class="sxs-lookup"><span data-stu-id="1b537-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="1b537-125">若要關閉索引標籤，您可以使用下列任一項技術：</span><span class="sxs-lookup"><span data-stu-id="1b537-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="1b537-126">按一下您要關閉的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b537-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="1b537-127">在 **[檔案]** 功能表上，按一下 **[關閉 PowerShell 索引標籤]** ，或在使用中的索引標籤上，按一下 [關閉] 按鈕 (**X**) 以關閉索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1b537-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="1b537-128">如果您在要關閉的 PowerShell 索引標籤中，有已開啟且未儲存的檔案，系統會提示您儲存或捨棄檔案。</span><span class="sxs-lookup"><span data-stu-id="1b537-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="1b537-129">如需如何儲存指令碼的詳細資訊，請參閱[如何儲存指令碼](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script)。</span><span class="sxs-lookup"><span data-stu-id="1b537-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b537-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b537-130">See Also</span></span>

- [<span data-ttu-id="1b537-131">Windows PowerShell ISE 簡介</span><span class="sxs-lookup"><span data-stu-id="1b537-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="1b537-132">如何在 Windows PowerShell ISE 中使用主控台窗格</span><span class="sxs-lookup"><span data-stu-id="1b537-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
