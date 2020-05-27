---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Windows PowerShell ISE 指令碼物件模型的用途
ms.openlocfilehash: 1f48df112bd19297baa311116e79d3d7603d7c81
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809744"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="427dc-103">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="427dc-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>

<span data-ttu-id="427dc-104">物件會關聯至 Windows PowerShell 整合式指令碼環境 (ISE) 的表單和函式。</span><span class="sxs-lookup"><span data-stu-id="427dc-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="427dc-105">物件模型參考提供有關成員屬性的詳細資料以及這些物件公開的方法。</span><span class="sxs-lookup"><span data-stu-id="427dc-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="427dc-106">我們將提供範例來示範您如何使用指令碼直接存取這些方法與屬性。</span><span class="sxs-lookup"><span data-stu-id="427dc-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="427dc-107">指令碼物件模型讓您更容易進行下列範圍內的工作。</span><span class="sxs-lookup"><span data-stu-id="427dc-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="427dc-108">自訂 Windows PowerShell ISE 的外觀</span><span class="sxs-lookup"><span data-stu-id="427dc-108">Customizing the appearance of Windows PowerShell ISE</span></span>

<span data-ttu-id="427dc-109">您可以使用物件模型來修改應用程式設定和選項。</span><span class="sxs-lookup"><span data-stu-id="427dc-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="427dc-110">例如，您可以使用如下方式來修改它們︰</span><span class="sxs-lookup"><span data-stu-id="427dc-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="427dc-111">變更錯誤、警告、詳細資訊輸出及偵錯輸出的色彩。</span><span class="sxs-lookup"><span data-stu-id="427dc-111">Change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>
- <span data-ttu-id="427dc-112">取得或設定命令窗格、輸出窗格及指令碼窗格的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="427dc-112">Get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>
- <span data-ttu-id="427dc-113">設定輸出窗格的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="427dc-113">Set the foreground color for the Output pane.</span></span>
- <span data-ttu-id="427dc-114">設定 Windows PowerShell ISE 的字型名稱和大小。</span><span class="sxs-lookup"><span data-stu-id="427dc-114">Set the font name and font size for Windows PowerShell ISE.</span></span>
- <span data-ttu-id="427dc-115">設定警告。</span><span class="sxs-lookup"><span data-stu-id="427dc-115">Configure warnings.</span></span> <span data-ttu-id="427dc-116">此設定包含在多個 PowerShell 索引標籤中開啟檔案時，或者在儲存檔案之前執行該檔案中的指令碼時所發出的警告。</span><span class="sxs-lookup"><span data-stu-id="427dc-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>
- <span data-ttu-id="427dc-117">在指令碼窗格和輸出窗格並排顯示的檢視，以及指令碼窗格位於輸出窗格上方的檢視之間進行切換。</span><span class="sxs-lookup"><span data-stu-id="427dc-117">Switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span>
- <span data-ttu-id="427dc-118">將命令窗格停駐於輸出窗格的下方或上方。</span><span class="sxs-lookup"><span data-stu-id="427dc-118">Dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="427dc-119">增強 Windows PowerShell ISE 功能</span><span class="sxs-lookup"><span data-stu-id="427dc-119">Enhancing the functionality of Windows PowerShell ISE</span></span>

<span data-ttu-id="427dc-120">您可以使用物件模型來增強 Windows PowerShell ISE 功能。</span><span class="sxs-lookup"><span data-stu-id="427dc-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="427dc-121">例如，您可以：</span><span class="sxs-lookup"><span data-stu-id="427dc-121">For example, you can:</span></span>

- <span data-ttu-id="427dc-122">新增和修改 Windows PowerShell ISE 本身的執行個體。</span><span class="sxs-lookup"><span data-stu-id="427dc-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="427dc-123">例如，若要變更功能表，您可以新增功能表項目，並將新的功能表項目對應至指令碼。</span><span class="sxs-lookup"><span data-stu-id="427dc-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>
- <span data-ttu-id="427dc-124">建立指令碼，來執行一些您可以在 Windows PowerShell ISE 中使用功能表命令和按鈕來執行的工作。</span><span class="sxs-lookup"><span data-stu-id="427dc-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="427dc-125">例如，您可以新增、移除或選取 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="427dc-125">For example, you can add, remove, or select a PowerShell tab.</span></span>
- <span data-ttu-id="427dc-126">可使用功能表命令和按鈕執行的補充工作。</span><span class="sxs-lookup"><span data-stu-id="427dc-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="427dc-127">例如，您可以重新命名 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="427dc-127">For example, you can rename a PowerShell tab.</span></span>
- <span data-ttu-id="427dc-128">管理與檔案相關聯之命令窗格、輸出窗格和指令碼窗格的文字緩衝區。</span><span class="sxs-lookup"><span data-stu-id="427dc-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="427dc-129">例如，您可以：</span><span class="sxs-lookup"><span data-stu-id="427dc-129">For example, you can:</span></span>
  - <span data-ttu-id="427dc-130">取得或設定所有文字。</span><span class="sxs-lookup"><span data-stu-id="427dc-130">Get or set all text.</span></span>
  - <span data-ttu-id="427dc-131">取得或設定文字選取範圍。</span><span class="sxs-lookup"><span data-stu-id="427dc-131">Get or set a text selection.</span></span>
  - <span data-ttu-id="427dc-132">執行指令碼或執行所選取的指令碼部分。</span><span class="sxs-lookup"><span data-stu-id="427dc-132">Run a script or run a selected portion of a script.</span></span>
  - <span data-ttu-id="427dc-133">捲動一行來檢視。</span><span class="sxs-lookup"><span data-stu-id="427dc-133">Scroll a line into view.</span></span>
  - <span data-ttu-id="427dc-134">在插入號位置插入文字。</span><span class="sxs-lookup"><span data-stu-id="427dc-134">Insert text at a caret position.</span></span>
  - <span data-ttu-id="427dc-135">選取文字區塊。</span><span class="sxs-lookup"><span data-stu-id="427dc-135">Select a block of text.</span></span>
  - <span data-ttu-id="427dc-136">取得最後一個行號。</span><span class="sxs-lookup"><span data-stu-id="427dc-136">Get the last line number.</span></span>
- <span data-ttu-id="427dc-137">執行檔案作業。</span><span class="sxs-lookup"><span data-stu-id="427dc-137">Perform file operations.</span></span> <span data-ttu-id="427dc-138">例如，您可以：</span><span class="sxs-lookup"><span data-stu-id="427dc-138">For example, you can:</span></span>
  - <span data-ttu-id="427dc-139">開啟檔案、儲存檔案，或使用不同名稱儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="427dc-139">Open a file, save a file, or save a file by using a different name.</span></span>
  - <span data-ttu-id="427dc-140">判斷檔案在上次儲存之後是否已變更。</span><span class="sxs-lookup"><span data-stu-id="427dc-140">Determine whether a file has been changed after it was last saved.</span></span>
  - <span data-ttu-id="427dc-141">取得檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="427dc-141">Get the file name.</span></span>
  - <span data-ttu-id="427dc-142">選取檔案。</span><span class="sxs-lookup"><span data-stu-id="427dc-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="427dc-143">自動化工作</span><span class="sxs-lookup"><span data-stu-id="427dc-143">Automating tasks</span></span>

<span data-ttu-id="427dc-144">您可以使用指令碼物件模型，針對經常執行的作業建立鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="427dc-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="427dc-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="427dc-145">See also</span></span>

- [<span data-ttu-id="427dc-146">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="427dc-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
