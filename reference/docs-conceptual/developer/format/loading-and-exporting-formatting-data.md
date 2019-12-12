---
title: 載入和匯出格式化資料 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365117"
---
# <a name="loading-and-exporting-formatting-data"></a><span data-ttu-id="89f40-102">載入及匯出格式設定資料</span><span class="sxs-lookup"><span data-stu-id="89f40-102">Loading and Exporting Formatting Data</span></span>

<span data-ttu-id="89f40-103">建立格式檔案之後，您必須將檔案載入目前的會話，以更新會話的格式資料。</span><span class="sxs-lookup"><span data-stu-id="89f40-103">Once you have created your formatting file, you need to update the format data of the session by loading your files into the current session.</span></span> <span data-ttu-id="89f40-104">（Windows PowerShell 所提供的格式化檔案是由目前會話開啟時註冊的嵌入式管理單元載入）。一旦更新了目前會話的格式資料，Windows PowerShell 就會使用該資料來顯示與已載入的格式檔案中所定義的視圖相關聯的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="89f40-104">(The formatting files provided by Windows PowerShell are loaded by snap-ins that are registered when the current session is opened.) Once the format data of the current session is updated, Windows PowerShell uses that data to display the .NET objects associated with the views defined in the loaded formatting files.</span></span> <span data-ttu-id="89f40-105">您可以載入目前會話的格式化檔案數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="89f40-105">There is no limit to the number of formatting files that you can load into the current session.</span></span> <span data-ttu-id="89f40-106">除了更新格式化資料以外，您還可以將目前會話中的格式資料匯出回格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="89f40-106">In addition to updating the formatting data, you can export the format data in the current session back to a formatting file.</span></span>

## <a name="loading-format-data"></a><span data-ttu-id="89f40-107">正在載入格式資料</span><span class="sxs-lookup"><span data-stu-id="89f40-107">Loading format data</span></span>

<span data-ttu-id="89f40-108">使用下列方法，可以將檔案格式化為目前的會話：</span><span class="sxs-lookup"><span data-stu-id="89f40-108">Formatting files can be loaded into the current session using the following methods:</span></span>

- <span data-ttu-id="89f40-109">您可以從命令列將格式化檔案匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="89f40-109">You can import the formatting file into the current session from the command line.</span></span> <span data-ttu-id="89f40-110">依照下列程式所述，使用[FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="89f40-110">Use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet as described in the following procedure.</span></span>

- <span data-ttu-id="89f40-111">您可以建立會參考您的格式化檔案的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="89f40-111">You can create a module manifest that references your formatting file.</span></span> <span data-ttu-id="89f40-112">模組可讓您封裝要散發的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="89f40-112">Modules allow you to package you formatting files for distribution.</span></span> <span data-ttu-id="89f40-113">使用[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet 來建立資訊清單，並使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 將模組載入目前的會話。</span><span class="sxs-lookup"><span data-stu-id="89f40-113">Use the [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet to create the manifest, and the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet to load the module into the current session.</span></span> <span data-ttu-id="89f40-114">如需模組的詳細資訊，請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="89f40-114">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="89f40-115">您可以建立一個嵌入式管理單元來參考您的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="89f40-115">You can create a snap-in that references your formatting file.</span></span> <span data-ttu-id="89f40-116">請使用[PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn.Formats)格式來參考您的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="89f40-116">Use the [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) to reference your formatting files.</span></span> <span data-ttu-id="89f40-117">強烈建議使用模組來封裝 Cmdlet，以及任何相關聯的格式化和類型檔案以進行散發。</span><span class="sxs-lookup"><span data-stu-id="89f40-117">It is strongly encouraged to use modules to package cmdlets, and any associated formatting and types files for distribution.</span></span> <span data-ttu-id="89f40-118">如需模組的詳細資訊，請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="89f40-118">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="89f40-119">如果您以程式設計方式叫用命令，可以將格式化檔案專案新增至執行命令之運行時的初始會話狀態。</span><span class="sxs-lookup"><span data-stu-id="89f40-119">If you are invoking commands programmatically, you can add a formatting file entry to the initial session state of the runspace where the commands are run.</span></span> <span data-ttu-id="89f40-120">如需用來新增格式化檔案之 .NET 類型的詳細資訊，請參閱[Sessionstateformatentry？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry)類別。</span><span class="sxs-lookup"><span data-stu-id="89f40-120">For more information about .NET type used to add the formatting file, see the [System.Management.Automation.Runspaces.Sessionstateformatentry?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) class.</span></span>

<span data-ttu-id="89f40-121">當格式化檔案已載入時，它會新增至內部清單，Windows PowerShell 會使用它來決定在命令列顯示物件時所要使用的視圖。</span><span class="sxs-lookup"><span data-stu-id="89f40-121">When a formatting file is loaded, it is added to an internal list that Windows PowerShell uses to determine which view to use when displaying objects at the command line.</span></span> <span data-ttu-id="89f40-122">您可以在清單的開頭加上您的格式化檔案，也可以將它附加至清單結尾。</span><span class="sxs-lookup"><span data-stu-id="89f40-122">You can prepend your formatting file to the beginning of the list, or you can append it to the end of the list.</span></span> <span data-ttu-id="89f40-123">如果您要載入的格式檔案定義的是已定義現有視圖之物件的視圖，例如當您想要變更 Windows PowerShell core Cmdlet 所傳回物件的方式時，要知道您的格式化檔案新增到此清單的位置是很重要的： 看到.</span><span class="sxs-lookup"><span data-stu-id="89f40-123">Knowing where your formatting file is added to this list is important if you are loading formatting file that defines a view for an object that has an existing view defined, such as when you want to change how an object that is returned by a Windows PowerShell core cmdlet is displayed.</span></span> <span data-ttu-id="89f40-124">如果您要載入定義物件唯一視圖的格式化檔案，您可以使用先前所述的任何方法。</span><span class="sxs-lookup"><span data-stu-id="89f40-124">If you are loading a formatting file that defines the only view for an object, you can use any of the methods described previously.</span></span>  <span data-ttu-id="89f40-125">如果您要載入為物件定義另一個視圖的格式化檔案，您必須使用 FormatData 指令[程式](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData)，並在清單的開頭加上您的檔案。</span><span class="sxs-lookup"><span data-stu-id="89f40-125">If you are loading a formatting file that defines another view for an object, you must use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet and prepend your file to the beginning of the list.</span></span>

## <a name="storing-your-formatting-file"></a><span data-ttu-id="89f40-126">儲存您的格式化檔案</span><span class="sxs-lookup"><span data-stu-id="89f40-126">Storing Your Formatting File</span></span>

<span data-ttu-id="89f40-127">您的格式化檔案儲存在磁片上的位置並不需要。</span><span class="sxs-lookup"><span data-stu-id="89f40-127">There is no requirement for where your formatting files are stored on disk.</span></span> <span data-ttu-id="89f40-128">不過，強烈建議您將它們儲存在下列資料夾中： `user\documents\windowspowershell\`</span><span class="sxs-lookup"><span data-stu-id="89f40-128">However, it is strongly suggested that you store them in the following folder: `user\documents\windowspowershell\`</span></span>

#### <a name="loading-a-format-file-using-import-formatdata"></a><span data-ttu-id="89f40-129">使用匯入 FormatData 載入格式檔案</span><span class="sxs-lookup"><span data-stu-id="89f40-129">Loading a format file using Import-FormatData</span></span>

1. <span data-ttu-id="89f40-130">將您的格式化檔案儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="89f40-130">Store your formatting file to disk.</span></span>

2. <span data-ttu-id="89f40-131">使用下列其中一個命令來執行[FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="89f40-131">Run the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet using one of the following commands.</span></span>

   <span data-ttu-id="89f40-132">若要將您的格式化檔案新增至清單的前端，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="89f40-132">To add your formatting file to the front of the list use this command.</span></span> <span data-ttu-id="89f40-133">如果您要變更物件的顯示方式，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="89f40-133">Use this command if you are changing how an object is displayed.</span></span>

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   <span data-ttu-id="89f40-134">若要將您的格式化檔案新增至清單結尾，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="89f40-134">To add your formatting file to the end of the list use this command.</span></span>

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   <span data-ttu-id="89f40-135">當您使用[FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet 新增檔案之後，當會話開啟時，就無法從清單中移除該檔案。</span><span class="sxs-lookup"><span data-stu-id="89f40-135">Once you have added a file using the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, you cannot remove the file from the list while the session is open.</span></span> <span data-ttu-id="89f40-136">您必須關閉會話，才能從清單中移除格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="89f40-136">You must close the session to remove the formatting file from the list.</span></span>

## <a name="exporting-format-data"></a><span data-ttu-id="89f40-137">匯出格式資料</span><span class="sxs-lookup"><span data-stu-id="89f40-137">Exporting format data</span></span>

<span data-ttu-id="89f40-138">在此插入區段主體。</span><span class="sxs-lookup"><span data-stu-id="89f40-138">Insert section body here.</span></span>
