---
title: 載入及匯出格式的資料 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054181"
---
# <a name="loading-and-exporting-formatting-data"></a><span data-ttu-id="9232f-102">載入及匯出格式設定資料</span><span class="sxs-lookup"><span data-stu-id="9232f-102">Loading and Exporting Formatting Data</span></span>

<span data-ttu-id="9232f-103">當您建立您格式化檔案之後時，您需要將目前的工作階段載入您的檔案更新的工作階段的格式資料。</span><span class="sxs-lookup"><span data-stu-id="9232f-103">Once you have created your formatting file, you need to update the format data of the session by loading your files into the current session.</span></span> <span data-ttu-id="9232f-104">（藉由開啟目前的工作階段時註冊的嵌入式管理單元會載入 Windows PowerShell 所提供的格式化檔案）。目前工作階段的格式資料更新之後，Windows PowerShell 會使用該資料來顯示載入的格式化檔案中定義的檢視相關聯的.NET 物件。</span><span class="sxs-lookup"><span data-stu-id="9232f-104">(The formatting files provided by Windows PowerShell are loaded by snap-ins that are registered when the current session is opened.) Once the format data of the current session is updated, Windows PowerShell uses that data to display the .NET objects associated with the views defined in the loaded formatting files.</span></span> <span data-ttu-id="9232f-105">沒有任何限制，您可以載入目前的工作階段的格式化檔案的數目。</span><span class="sxs-lookup"><span data-stu-id="9232f-105">There is no limit to the number of formatting files that you can load into the current session.</span></span> <span data-ttu-id="9232f-106">除了更新格式化資料，您可以回到格式化檔案目前的工作階段中匯出的格式資料。</span><span class="sxs-lookup"><span data-stu-id="9232f-106">In addition to updating the formatting data, you can export the format data in the current session back to a formatting file.</span></span>

## <a name="loading-format-data"></a><span data-ttu-id="9232f-107">正在載入格式資料</span><span class="sxs-lookup"><span data-stu-id="9232f-107">Loading format data</span></span>

<span data-ttu-id="9232f-108">格式檔案可以載入目前的工作階段使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="9232f-108">Formatting files can be loaded into the current session using the following methods:</span></span>

- <span data-ttu-id="9232f-109">您可以從命令列目前的工作階段，以匯入的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="9232f-109">You can import the formatting file into the current session from the command line.</span></span> <span data-ttu-id="9232f-110">使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，如下列程序中所述。</span><span class="sxs-lookup"><span data-stu-id="9232f-110">Use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet as described in the following procedure.</span></span>

- <span data-ttu-id="9232f-111">您可以建立模組資訊清單參考格式的檔案。</span><span class="sxs-lookup"><span data-stu-id="9232f-111">You can create a module manifest that references your formatting file.</span></span> <span data-ttu-id="9232f-112">模組可讓您將封裝格式化檔案中的散佈您。</span><span class="sxs-lookup"><span data-stu-id="9232f-112">Modules allow you to package you formatting files for distribution.</span></span> <span data-ttu-id="9232f-113">使用[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 來建立資訊清單中，而[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 將模組載入目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9232f-113">Use the [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet to create the manifest, and the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet to load the module into the current session.</span></span> <span data-ttu-id="9232f-114">如需有關模組的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="9232f-114">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="9232f-115">您可以建立一個嵌入式管理單元，參考您的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="9232f-115">You can create a snap-in that references your formatting file.</span></span> <span data-ttu-id="9232f-116">使用[System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats)來參考您的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="9232f-116">Use the [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) to reference your formatting files.</span></span> <span data-ttu-id="9232f-117">它是鼓勵使用散發套件 cmdlet 的模組，以及任何相關聯的格式和類型檔案。</span><span class="sxs-lookup"><span data-stu-id="9232f-117">It is strongly encouraged to use modules to package cmdlets, and any associated formatting and types files for distribution.</span></span> <span data-ttu-id="9232f-118">如需有關模組的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="9232f-118">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="9232f-119">如果您以程式設計方式叫用命令，您可以加入初始工作階段狀態的 runspace，執行命令來格式化的檔案項目。</span><span class="sxs-lookup"><span data-stu-id="9232f-119">If you are invoking commands programmatically, you can add a formatting file entry to the initial session state of the runspace where the commands are run.</span></span> <span data-ttu-id="9232f-120">如需有關用來新增的格式化檔案的.NET 類型的詳細資訊，請參閱[System.Management.Automation.Runspaces.Sessionstateformatentry 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry)類別。</span><span class="sxs-lookup"><span data-stu-id="9232f-120">For more information about .NET type used to add the formatting file, see the [System.Management.Automation.Runspaces.Sessionstateformatentry?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) class.</span></span>

<span data-ttu-id="9232f-121">載入格式化檔案時，它會加入內部清單來判斷何種檢視將顯示在命令列的物件時，使用 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9232f-121">When a formatting file is loaded, it is added to an internal list that Windows PowerShell uses to determine which view to use when displaying objects at the command line.</span></span> <span data-ttu-id="9232f-122">您可以在前面加上您的清單中，開頭的格式化檔案，或您可以將它附加至清單結尾。</span><span class="sxs-lookup"><span data-stu-id="9232f-122">You can prepend your formatting file to the beginning of the list, or you can append it to the end of the list.</span></span> <span data-ttu-id="9232f-123">了解您的格式化檔案新增至清單的位置是很重要，如果您載入格式化檔案，定義具有現有的檢視定義，例如當您想要變更 Windows PowerShell 核心 cmdlet 所傳回的物件有何物件的檢視 顯示此項目。</span><span class="sxs-lookup"><span data-stu-id="9232f-123">Knowing where your formatting file is added to this list is important if you are loading formatting file that defines a view for an object that has an existing view defined, such as when you want to change how an object that is returned by a Windows PowerShell core cmdlet is displayed.</span></span> <span data-ttu-id="9232f-124">如果您載入格式化檔案，定義物件的唯一檢視，您可以使用任何先前所述的方法。</span><span class="sxs-lookup"><span data-stu-id="9232f-124">If you are loading a formatting file that defines the only view for an object, you can use any of the methods described previously.</span></span>  <span data-ttu-id="9232f-125">如果您載入格式化檔案，定義物件的另一個檢視，您必須使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 並在前面加上您的檔案清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="9232f-125">If you are loading a formatting file that defines another view for an object, you must use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet and prepend your file to the beginning of the list.</span></span>

## <a name="storing-your-formatting-file"></a><span data-ttu-id="9232f-126">儲存您的格式化檔案</span><span class="sxs-lookup"><span data-stu-id="9232f-126">Storing Your Formatting File</span></span>

<span data-ttu-id="9232f-127">沒有格式檔案在磁碟上的儲存位置的需求。</span><span class="sxs-lookup"><span data-stu-id="9232f-127">There is no requirement for where your formatting files are stored on disk.</span></span> <span data-ttu-id="9232f-128">不過，強烈建議您將它們儲存在下列資料夾： `user\documents\windowspowershell\`</span><span class="sxs-lookup"><span data-stu-id="9232f-128">However, it is strongly suggested that you store them in the following folder: `user\documents\windowspowershell\`</span></span>

#### <a name="loading-a-format-file-using-import-formatdata"></a><span data-ttu-id="9232f-129">正在載入格式檔案使用匯入 FormatData</span><span class="sxs-lookup"><span data-stu-id="9232f-129">Loading a format file using Import-FormatData</span></span>

1. <span data-ttu-id="9232f-130">儲存您到磁碟的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="9232f-130">Store your formatting file to disk.</span></span>

2. <span data-ttu-id="9232f-131">執行[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 使用下列命令之一。</span><span class="sxs-lookup"><span data-stu-id="9232f-131">Run the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet using one of the following commands.</span></span>

   <span data-ttu-id="9232f-132">若要新增您的格式設定清單的最上層的檔案會使用此命令。</span><span class="sxs-lookup"><span data-stu-id="9232f-132">To add your formatting file to the front of the list use this command.</span></span> <span data-ttu-id="9232f-133">如果您要變更物件的顯示方式，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="9232f-133">Use this command if you are changing how an object is displayed.</span></span>

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   <span data-ttu-id="9232f-134">若要新增您的格式設定清單結尾的檔案會使用此命令。</span><span class="sxs-lookup"><span data-stu-id="9232f-134">To add your formatting file to the end of the list use this command.</span></span>

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   <span data-ttu-id="9232f-135">一旦您加入檔案，使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，您無法從清單移除檔案，開啟工作階段時。</span><span class="sxs-lookup"><span data-stu-id="9232f-135">Once you have added a file using the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, you cannot remove the file from the list while the session is open.</span></span> <span data-ttu-id="9232f-136">您必須關閉工作階段，若要從清單中移除的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="9232f-136">You must close the session to remove the formatting file from the list.</span></span>

## <a name="exporting-format-data"></a><span data-ttu-id="9232f-137">匯出格式資料</span><span class="sxs-lookup"><span data-stu-id="9232f-137">Exporting format data</span></span>

<span data-ttu-id="9232f-138">在此插入區段主體。</span><span class="sxs-lookup"><span data-stu-id="9232f-138">Insert section body here.</span></span>
