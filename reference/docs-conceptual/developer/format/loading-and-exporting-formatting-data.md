---
ms.date: 09/13/2016
ms.topic: reference
title: 載入及匯出格式設定資料
description: 載入及匯出格式設定資料
ms.openlocfilehash: 38857526801051bf6d31d300d5be1a3fd2c80391
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666513"
---
# <a name="loading-and-exporting-formatting-data"></a><span data-ttu-id="e87d1-103">載入及匯出格式設定資料</span><span class="sxs-lookup"><span data-stu-id="e87d1-103">Loading and Exporting Formatting Data</span></span>

<span data-ttu-id="e87d1-104">建立格式化檔案之後，您必須將檔案載入目前的會話，以更新會話的格式資料。</span><span class="sxs-lookup"><span data-stu-id="e87d1-104">Once you have created your formatting file, you need to update the format data of the session by loading your files into the current session.</span></span> <span data-ttu-id="e87d1-105"> (Windows PowerShell 所提供的格式化檔案，是在目前會話開啟時註冊的嵌入式管理單元所載入。 ) 當目前會話的格式資料更新後，Windows PowerShell 會使用該資料來顯示與載入的格式化檔案中定義之視圖相關聯的 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="e87d1-105">(The formatting files provided by Windows PowerShell are loaded by snap-ins that are registered when the current session is opened.) Once the format data of the current session is updated, Windows PowerShell uses that data to display the .NET objects associated with the views defined in the loaded formatting files.</span></span> <span data-ttu-id="e87d1-106">在目前的會話中，您可以載入的格式化檔案數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="e87d1-106">There is no limit to the number of formatting files that you can load into the current session.</span></span> <span data-ttu-id="e87d1-107">除了更新格式化資料以外，您還可以將目前會話中的格式資料匯出回格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="e87d1-107">In addition to updating the formatting data, you can export the format data in the current session back to a formatting file.</span></span>

## <a name="loading-format-data"></a><span data-ttu-id="e87d1-108">載入格式資料</span><span class="sxs-lookup"><span data-stu-id="e87d1-108">Loading format data</span></span>

<span data-ttu-id="e87d1-109">您可以使用下列方法，將檔案格式化以載入目前的會話：</span><span class="sxs-lookup"><span data-stu-id="e87d1-109">Formatting files can be loaded into the current session using the following methods:</span></span>

- <span data-ttu-id="e87d1-110">您可以從命令列將格式化檔案匯入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="e87d1-110">You can import the formatting file into the current session from the command line.</span></span> <span data-ttu-id="e87d1-111">使用 [FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet，如下列程式所述。</span><span class="sxs-lookup"><span data-stu-id="e87d1-111">Use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet as described in the following procedure.</span></span>

- <span data-ttu-id="e87d1-112">您可以建立參考格式化檔案的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="e87d1-112">You can create a module manifest that references your formatting file.</span></span> <span data-ttu-id="e87d1-113">模組可讓您封裝格式化檔案以進行散發。</span><span class="sxs-lookup"><span data-stu-id="e87d1-113">Modules allow you to package you formatting files for distribution.</span></span> <span data-ttu-id="e87d1-114">使用 [ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) 資訊清單來建立資訊清單，並使用 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 將模組載入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="e87d1-114">Use the [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet to create the manifest, and the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet to load the module into the current session.</span></span> <span data-ttu-id="e87d1-115">如需模組的詳細資訊，請參閱 [撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="e87d1-115">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="e87d1-116">您可以建立參考格式化檔案的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="e87d1-116">You can create a snap-in that references your formatting file.</span></span> <span data-ttu-id="e87d1-117">使用 [PSSnapIn 格式](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) 來參考您的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="e87d1-117">Use the [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) to reference your formatting files.</span></span> <span data-ttu-id="e87d1-118">強烈建議您使用模組來封裝 Cmdlet，以及任何相關聯的格式和類型檔案來進行散發。</span><span class="sxs-lookup"><span data-stu-id="e87d1-118">It is strongly encouraged to use modules to package cmdlets, and any associated formatting and types files for distribution.</span></span> <span data-ttu-id="e87d1-119">如需模組的詳細資訊，請參閱 [撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="e87d1-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="e87d1-120">如果您以程式設計方式叫用命令，您可以在執行命令的運行時的初始會話狀態中新增格式化檔案專案。</span><span class="sxs-lookup"><span data-stu-id="e87d1-120">If you are invoking commands programmatically, you can add a formatting file entry to the initial session state of the runspace where the commands are run.</span></span> <span data-ttu-id="e87d1-121">如需有關用來新增格式化檔案之 .NET 類型的詳細資訊，請參閱 [Sessionstateformatentry？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) 類別。</span><span class="sxs-lookup"><span data-stu-id="e87d1-121">For more information about .NET type used to add the formatting file, see the [System.Management.Automation.Runspaces.Sessionstateformatentry?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) class.</span></span>

<span data-ttu-id="e87d1-122">載入格式化檔案時，它會新增至內部清單，Windows PowerShell 用來決定在命令列顯示物件時所要使用的視圖。</span><span class="sxs-lookup"><span data-stu-id="e87d1-122">When a formatting file is loaded, it is added to an internal list that Windows PowerShell uses to determine which view to use when displaying objects at the command line.</span></span> <span data-ttu-id="e87d1-123">您可以在清單的開頭加上格式化檔案，也可以將它附加至清單的結尾。</span><span class="sxs-lookup"><span data-stu-id="e87d1-123">You can prepend your formatting file to the beginning of the list, or you can append it to the end of the list.</span></span> <span data-ttu-id="e87d1-124">如果您要載入的格式檔案定義了已定義現有視圖的物件，例如，當您想要變更 Windows PowerShell core Cmdlet 所傳回之物件的顯示方式時，瞭解將格式化檔案新增到此清單的位置是很重要的。</span><span class="sxs-lookup"><span data-stu-id="e87d1-124">Knowing where your formatting file is added to this list is important if you are loading formatting file that defines a view for an object that has an existing view defined, such as when you want to change how an object that is returned by a Windows PowerShell core cmdlet is displayed.</span></span> <span data-ttu-id="e87d1-125">如果您要載入的格式化檔案定義物件的唯一觀點，您可以使用先前所述的任何方法。</span><span class="sxs-lookup"><span data-stu-id="e87d1-125">If you are loading a formatting file that defines the only view for an object, you can use any of the methods described previously.</span></span>  <span data-ttu-id="e87d1-126">如果您要載入為物件定義另一個視圖的格式化檔案，您必須使用 FormatData 指令 [程式](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) ，並在清單開頭加上您的檔案。</span><span class="sxs-lookup"><span data-stu-id="e87d1-126">If you are loading a formatting file that defines another view for an object, you must use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet and prepend your file to the beginning of the list.</span></span>

## <a name="storing-your-formatting-file"></a><span data-ttu-id="e87d1-127">儲存您的格式化檔案</span><span class="sxs-lookup"><span data-stu-id="e87d1-127">Storing Your Formatting File</span></span>

<span data-ttu-id="e87d1-128">您不需要將格式化檔案儲存在磁片上的位置。</span><span class="sxs-lookup"><span data-stu-id="e87d1-128">There is no requirement for where your formatting files are stored on disk.</span></span> <span data-ttu-id="e87d1-129">不過，強烈建議您將它們儲存在下列資料夾中： `user\documents\windowspowershell\`</span><span class="sxs-lookup"><span data-stu-id="e87d1-129">However, it is strongly suggested that you store them in the following folder: `user\documents\windowspowershell\`</span></span>

#### <a name="loading-a-format-file-using-import-formatdata"></a><span data-ttu-id="e87d1-130">使用 Import-FormatData 載入格式檔案</span><span class="sxs-lookup"><span data-stu-id="e87d1-130">Loading a format file using Import-FormatData</span></span>

1. <span data-ttu-id="e87d1-131">將您的格式化檔案儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="e87d1-131">Store your formatting file to disk.</span></span>

2. <span data-ttu-id="e87d1-132">使用下列其中一個命令來執行 [FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e87d1-132">Run the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet using one of the following commands.</span></span>

   <span data-ttu-id="e87d1-133">若要將格式化檔案新增至清單前面，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="e87d1-133">To add your formatting file to the front of the list use this command.</span></span> <span data-ttu-id="e87d1-134">如果您要變更物件的顯示方式，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="e87d1-134">Use this command if you are changing how an object is displayed.</span></span>

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   <span data-ttu-id="e87d1-135">若要將格式化檔案新增至清單結尾，請使用此命令。</span><span class="sxs-lookup"><span data-stu-id="e87d1-135">To add your formatting file to the end of the list use this command.</span></span>

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   <span data-ttu-id="e87d1-136">當您使用 [FormatData 指令程式](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) 新增檔案之後，您就無法在會話開啟時從清單中移除該檔案。</span><span class="sxs-lookup"><span data-stu-id="e87d1-136">Once you have added a file using the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, you cannot remove the file from the list while the session is open.</span></span> <span data-ttu-id="e87d1-137">您必須關閉會話，以從清單中移除格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="e87d1-137">You must close the session to remove the formatting file from the list.</span></span>

## <a name="exporting-format-data"></a><span data-ttu-id="e87d1-138">匯出格式資料</span><span class="sxs-lookup"><span data-stu-id="e87d1-138">Exporting format data</span></span>

<span data-ttu-id="e87d1-139">在此插入章節主體。</span><span class="sxs-lookup"><span data-stu-id="e87d1-139">Insert section body here.</span></span>
