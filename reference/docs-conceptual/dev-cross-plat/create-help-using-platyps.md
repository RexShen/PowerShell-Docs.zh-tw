---
title: 使用 PlatyPS 建立 XML 格式的說明
description: 使用 PlatyPS 建立 XML 格式其說明是快速且有效率的方式。
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972574"
---
# <a name="create-xml-based-help-using-platyps"></a><span data-ttu-id="4cd47-103">使用 PlatyPS 建立 XML 格式的說明</span><span class="sxs-lookup"><span data-stu-id="4cd47-103">Create XML-based help using PlatyPS</span></span>

<span data-ttu-id="4cd47-104">建立 PowerShell 模組時，強烈建議一併包含所建立 Cmdlet 的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="4cd47-104">When creating a PowerShell module, it is always recommended that you include detailed help for the cmdlets you create.</span></span> <span data-ttu-id="4cd47-105">如果在已編譯的程式碼中實作 Cmdlet ，即必須使用 XML 格式的說明。</span><span class="sxs-lookup"><span data-stu-id="4cd47-105">If your cmdlets are implemented in compiled code, you must use the XML-based help.</span></span> <span data-ttu-id="4cd47-106">此 XML 格式稱為 Microsoft 協助標記語言 (MAML)。</span><span class="sxs-lookup"><span data-stu-id="4cd47-106">This XML format is known as the Microsoft Assistance Markup Language (MAML).</span></span>

<span data-ttu-id="4cd47-107">舊版 PowerShell SDK 文件內容涵蓋建立封裝於模組內 PowerShell Cmdlet 的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="4cd47-107">The legacy PowerShell SDK documentation covers the details of creating help for PowerShell cmdlets packaged into modules.</span></span> <span data-ttu-id="4cd47-108">不過，PowerShell 不會提供任何工具來建立 XML 格式的說明。</span><span class="sxs-lookup"><span data-stu-id="4cd47-108">However, PowerShell does not provide any tools for creating the XML-based help.</span></span> <span data-ttu-id="4cd47-109">SDK 文件雖然會詳述 MAML 說明的結構，但將需要手動建立複雜且深度巢狀化的 MAML 內容。</span><span class="sxs-lookup"><span data-stu-id="4cd47-109">The SDK documentation explains the structure of MAML help, but leaves you the task of creating the complex, and deeply nested, MAML content by hand.</span></span>

<span data-ttu-id="4cd47-110">這就是 [PlatyPS][] 模組可提供協助的地方。</span><span class="sxs-lookup"><span data-stu-id="4cd47-110">This is where the [PlatyPS][] module can help.</span></span>

## <a name="what-is-platyps"></a><span data-ttu-id="4cd47-111">什麼是 PlatyPS？</span><span class="sxs-lookup"><span data-stu-id="4cd47-111">What is PlatyPS?</span></span>

<span data-ttu-id="4cd47-112">PlatyPS 是一種[開放原始碼][platyps-repo]工具，其以 _Hackathon_ 專案的形式啟動，讓建立與維護 MAML 變得更加輕鬆。</span><span class="sxs-lookup"><span data-stu-id="4cd47-112">PlatyPS is an [open-source][platyps-repo] tool that started as a _hackathon_ project to make the creation and maintenance of MAML easier.</span></span> <span data-ttu-id="4cd47-113">PlatyPS 記載參數集的語法，以及模組中每個 Cmdlet 的個別參數。</span><span class="sxs-lookup"><span data-stu-id="4cd47-113">PlatyPS documents the syntax of parameter sets and the individual parameters for each cmdlet in your module.</span></span> <span data-ttu-id="4cd47-114">PlatyPS 會建立包含語法資訊的結構化 [Markdown][] 檔案，</span><span class="sxs-lookup"><span data-stu-id="4cd47-114">PlatyPS creates structured [Markdown][] files that contain the syntax information.</span></span> <span data-ttu-id="4cd47-115">但無法建立描述或提供範例。</span><span class="sxs-lookup"><span data-stu-id="4cd47-115">It can't create descriptions or provide examples.</span></span>

<span data-ttu-id="4cd47-116">PlatyPS 會建立預留位置，以供填寫描述與範例。</span><span class="sxs-lookup"><span data-stu-id="4cd47-116">PlatyPS creates placeholders for you to fill in descriptions and examples.</span></span> <span data-ttu-id="4cd47-117">在新增必要資訊之後，PlatyPS 會將 Markdown 檔案編譯為 MAML 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-117">After adding the required information, PlatyPS compiles the Markdown files into MAML files.</span></span> <span data-ttu-id="4cd47-118">PowerShell 的說明系統也允許 (與主題相關的) 純文字概念說明檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-118">PowerShell's help system also allows for plain-text conceptual help files (about topics).</span></span> <span data-ttu-id="4cd47-119">PlatyPS 具有 Cmdlet，可為新的「關於」檔案建立結構化 Markdown 範本，但這些 `about_*.help.txt` 檔案必須以手動方式進行維護。</span><span class="sxs-lookup"><span data-stu-id="4cd47-119">PlatyPS has a cmdlet to create a structured Markdown template for a new _about_ file, but these `about_*.help.txt` files must be maintained manually.</span></span>

<span data-ttu-id="4cd47-120">您可將 MAML 與文字說明檔納入模組中。</span><span class="sxs-lookup"><span data-stu-id="4cd47-120">You can include the MAML and Text help files with your module.</span></span> <span data-ttu-id="4cd47-121">您也可使用 PlatyPS，將說明檔編譯成 CAB 套件，以託管可更新的說明。</span><span class="sxs-lookup"><span data-stu-id="4cd47-121">You can also use PlatyPS to compile the help files into a CAB package that can be hosted for updateable help.</span></span>

## <a name="get-started-using-platyps"></a><span data-ttu-id="4cd47-122">開始使用 PlatyPS</span><span class="sxs-lookup"><span data-stu-id="4cd47-122">Get started using PlatyPS</span></span>

<span data-ttu-id="4cd47-123">首先，您必須從 PowerShell 資源庫安裝 PlatyPS。</span><span class="sxs-lookup"><span data-stu-id="4cd47-123">First you must install PlatyPS from the PowerShell Gallery.</span></span>

```powershell
Install-Module platyps -Force
Import-Module platyps
```

<span data-ttu-id="4cd47-124">下列流程圖會概述建立或更新 PowerShell 參考內容的流程。</span><span class="sxs-lookup"><span data-stu-id="4cd47-124">The following flowchart outlines the process for creating or updating PowerShell reference content.</span></span>

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="使用 PlatyPS 建立以 XML 格式來說明的工作流程":::

##  <a name="create-markdown-content-for-a-powershell-module"></a><span data-ttu-id="4cd47-126">建立 PowerShell 模組的 Markdown 內容</span><span class="sxs-lookup"><span data-stu-id="4cd47-126">Create Markdown content for a PowerShell module</span></span>

1. <span data-ttu-id="4cd47-127">將新模組匯入至工作階段。</span><span class="sxs-lookup"><span data-stu-id="4cd47-127">Import your new module into the session.</span></span> <span data-ttu-id="4cd47-128">針對所需記載的每個模組重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="4cd47-128">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="4cd47-129">執行下列命令以匯入模組：</span><span class="sxs-lookup"><span data-stu-id="4cd47-129">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="4cd47-130">使用 PlatyPS 來為模組頁面以及模組內所有相關聯的 Cmdlet 產生 Markdown 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-130">Use PlatyPS to generate Markdown files for your module page and all associated cmdlets within the module.</span></span> <span data-ttu-id="4cd47-131">針對所需記載的每個模組重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="4cd47-131">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   <span data-ttu-id="4cd47-132">如果輸出資料夾不存在，`New-MarkdownHelp` 會加以建立。</span><span class="sxs-lookup"><span data-stu-id="4cd47-132">If the output folder does not exist, `New-MarkdownHelp` creates it.</span></span> <span data-ttu-id="4cd47-133">在此範例中，`New-MarkdownHelp` 會為模組中的每個 Cmdlet 建立 Markdown 檔案，</span><span class="sxs-lookup"><span data-stu-id="4cd47-133">In this example, `New-MarkdownHelp` creates a Markdown file for each cmdlet in the module.</span></span> <span data-ttu-id="4cd47-134">並且會在名為 `<ModuleName>.md` 的檔案中建立「模組頁面」。</span><span class="sxs-lookup"><span data-stu-id="4cd47-134">It also creates the _module page_ in a file named `<ModuleName>.md`.</span></span> <span data-ttu-id="4cd47-135">此模組頁面包含模組中的 Cmdlet 清單，以及**概要**描述的預留位置。</span><span class="sxs-lookup"><span data-stu-id="4cd47-135">This module page contains a list of the cmdlets contained in the module and placeholders for the **Synopsis** description.</span></span> <span data-ttu-id="4cd47-136">模組頁面中的中繼資料來自模組資訊清單，其由 PlatyPS 用來建立 HelpInfo XML 檔案 ([如下所述](#creating-an-updateable-help-package))。</span><span class="sxs-lookup"><span data-stu-id="4cd47-136">The metadata in the module page comes from the module manifest and is used by PlatyPS to create the HelpInfo XML file (as explained [below](#creating-an-updateable-help-package)).</span></span>

   <span data-ttu-id="4cd47-137">`New-MarkdownAboutHelp` 會建立名為 `about_topic_name.md` 的新「關於」檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-137">`New-MarkdownAboutHelp` creates a new _about_ file named `about_topic_name.md`.</span></span>

   <span data-ttu-id="4cd47-138">如需詳細資訊，請參閱 [New-MarkdownHelp][] 和 [New-MarkdownAboutHelp][]。</span><span class="sxs-lookup"><span data-stu-id="4cd47-138">For more information, see [New-MarkdownHelp][] and [New-MarkdownAboutHelp][].</span></span>

### <a name="update-existing-markdown-content-when-the-module-changes"></a><span data-ttu-id="4cd47-139">當模組變更時，更新現有的 Markdown 內容</span><span class="sxs-lookup"><span data-stu-id="4cd47-139">Update existing Markdown content when the module changes</span></span>

<span data-ttu-id="4cd47-140">PlatyPS 也可為模組更新現有的 Markdown 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-140">PlatyPS can also update existing Markdown files for a module.</span></span> <span data-ttu-id="4cd47-141">您可使用此步驟來更新現有的模組，其包含新的 Cmdlet、新的參數或已變更的參數。</span><span class="sxs-lookup"><span data-stu-id="4cd47-141">Use this step to update existing modules that have new cmdlets, new parameters, or parameters that have changed.</span></span>

1. <span data-ttu-id="4cd47-142">將新模組匯入至工作階段。</span><span class="sxs-lookup"><span data-stu-id="4cd47-142">Import your new module into the session.</span></span> <span data-ttu-id="4cd47-143">針對所需記載的每個模組重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="4cd47-143">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="4cd47-144">執行下列命令以匯入模組：</span><span class="sxs-lookup"><span data-stu-id="4cd47-144">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="4cd47-145">使用 PlatyPS 來更新模組登陸頁面以及模組內所有相關聯 Cmdlet 的 Markdown 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-145">Use PlatyPS to update Markdown files for your module landing page and all associated cmdlets within the module.</span></span> <span data-ttu-id="4cd47-146">針對所需記載的每個模組重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="4cd47-146">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   <span data-ttu-id="4cd47-147">`Update-MarkdownHelpModule` 會更新指定資料夾中的 Cmdlet 與模組 Markdown 檔案，</span><span class="sxs-lookup"><span data-stu-id="4cd47-147">`Update-MarkdownHelpModule` updates the cmdlet and module Markdown files in the specified folder.</span></span>
   <span data-ttu-id="4cd47-148">但不會更新 `about_*.md` 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-148">It does not update the `about_*.md` files.</span></span> <span data-ttu-id="4cd47-149">模組檔案 (`ModuleName.md`) 會接收所有已新增至 Cmdlet 檔案的**概要**文字。</span><span class="sxs-lookup"><span data-stu-id="4cd47-149">The module file (`ModuleName.md`) receives any new **Synopsis** text that has been added to the cmdlet files.</span></span> <span data-ttu-id="4cd47-150">Cmdlet 檔案的更新包含下列變更：</span><span class="sxs-lookup"><span data-stu-id="4cd47-150">Updates to cmdlet files include the following change:</span></span>

   - <span data-ttu-id="4cd47-151">新參數集</span><span class="sxs-lookup"><span data-stu-id="4cd47-151">New parameter sets</span></span>
   - <span data-ttu-id="4cd47-152">新參數</span><span class="sxs-lookup"><span data-stu-id="4cd47-152">New parameters</span></span>
   - <span data-ttu-id="4cd47-153">更新的參數中繼資料</span><span class="sxs-lookup"><span data-stu-id="4cd47-153">Updated parameter metadata</span></span>
   - <span data-ttu-id="4cd47-154">更新的輸入和輸出類型資訊</span><span class="sxs-lookup"><span data-stu-id="4cd47-154">Updated input and output type information</span></span>

   <span data-ttu-id="4cd47-155">如需詳細資訊，請參閱 [Update-MarkdownHelpModule][]。</span><span class="sxs-lookup"><span data-stu-id="4cd47-155">For more information, see [Update-MarkdownHelpModule][].</span></span>

## <a name="edit-the-new-or-updated-markdown-files"></a><span data-ttu-id="4cd47-156">編輯新的或已更新的 Markdown 檔案</span><span class="sxs-lookup"><span data-stu-id="4cd47-156">Edit the new or updated Markdown files</span></span>

<span data-ttu-id="4cd47-157">PlatyPS 記錄參數集和個別參數的語法，</span><span class="sxs-lookup"><span data-stu-id="4cd47-157">PlatyPS documents the syntax of the parameter sets and the individual parameters.</span></span> <span data-ttu-id="4cd47-158">但無法建立描述或提供範例。</span><span class="sxs-lookup"><span data-stu-id="4cd47-158">It can't create descriptions or provide examples.</span></span> <span data-ttu-id="4cd47-159">大括號內為需要填入內容的特定區域。</span><span class="sxs-lookup"><span data-stu-id="4cd47-159">The specific areas where content is needed are contained in curly braces.</span></span> <span data-ttu-id="4cd47-160">例如：`{{ Fill in the Description }}`</span><span class="sxs-lookup"><span data-stu-id="4cd47-160">For example: `{{ Fill in the Description }}`</span></span>

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="VS Code 中顯示預留位置的 Markdown 範本":::

<span data-ttu-id="4cd47-162">您需要新增概要、Cmdlet 的描述、每個參數的描述，以及至少一個範例。</span><span class="sxs-lookup"><span data-stu-id="4cd47-162">You need to add a synopsis, a description of the cmdlet, descriptions for each parameter, and at least one example.</span></span>

<span data-ttu-id="4cd47-163">如需撰寫 PowerShell 內容的詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="4cd47-163">For detailed information about writing PowerShell content, see the following articles:</span></span>

- [<span data-ttu-id="4cd47-164">PowerShell 樣式指南</span><span class="sxs-lookup"><span data-stu-id="4cd47-164">PowerShell style guide</span></span>](/powershell/scripting/community/contributing/powershell-style-guide)
- [<span data-ttu-id="4cd47-165">編輯參考文章</span><span class="sxs-lookup"><span data-stu-id="4cd47-165">Editing reference articles</span></span>](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> <span data-ttu-id="4cd47-166">PlatyPS 具有用於 Cmdlet 參考的特定結構描述。</span><span class="sxs-lookup"><span data-stu-id="4cd47-166">PlatyPS has a specific schema that is uses for cmdlet reference.</span></span> <span data-ttu-id="4cd47-167">該結構描述只允許文件中特定區段的某些 Markdown 區塊。</span><span class="sxs-lookup"><span data-stu-id="4cd47-167">That schema only allows certain Markdown blocks in specific sections of the document.</span></span> <span data-ttu-id="4cd47-168">如果將內容放在錯誤的位置，PlatyPS 建置步驟就會失敗。</span><span class="sxs-lookup"><span data-stu-id="4cd47-168">If you put content in the wrong location, the PlatyPS build step fails.</span></span> <span data-ttu-id="4cd47-169">如需詳細資訊，請參閱 PlatyPS 存放庫中的[結構描述][]文件。</span><span class="sxs-lookup"><span data-stu-id="4cd47-169">For more information, see the [schema][] documentation in the PlatyPS repository.</span></span> <span data-ttu-id="4cd47-170">如需正確格式 Cmdlet 參考的完整範例，請參閱 [Get-Item][]。</span><span class="sxs-lookup"><span data-stu-id="4cd47-170">For a complete example of well-formed cmdlet reference, see [Get-Item][].</span></span>

<span data-ttu-id="4cd47-171">提供每個 Cmdlet 所需的內容之後，您必須確定已更新模組登陸頁面。</span><span class="sxs-lookup"><span data-stu-id="4cd47-171">After providing the required content for each of your cmdlets, you need to make sure that you update the module landing page.</span></span> <span data-ttu-id="4cd47-172">請確認模組在 `<module-name>.md` 檔案的 YAML 中繼資料中具有正確 `Module Guid` 和 `Download Help Link` 值，</span><span class="sxs-lookup"><span data-stu-id="4cd47-172">Verify your module has the correct `Module Guid` and `Download Help Link` values in the YAML metadata of the `<module-name>.md` file.</span></span> <span data-ttu-id="4cd47-173">新增任何缺少的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4cd47-173">Add any missing metadata.</span></span>

<span data-ttu-id="4cd47-174">此外，您可能會注意到某些 Cmdlet 可能缺少 **概要** (「簡短描述」)。</span><span class="sxs-lookup"><span data-stu-id="4cd47-174">Also, you may notice that some cmdlets may be missing a **Synopsis** (_short description_).</span></span> <span data-ttu-id="4cd47-175">下列命令會使用**概要**描述文字來更新模組登陸頁面。</span><span class="sxs-lookup"><span data-stu-id="4cd47-175">The following command updates the module landing page with your **Synopsis** description text.</span></span> <span data-ttu-id="4cd47-176">開啟模組登陸頁面，以驗證描述。</span><span class="sxs-lookup"><span data-stu-id="4cd47-176">Open the module landing page to verify the descriptions.</span></span>

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

<span data-ttu-id="4cd47-177">現在已輸入所有內容，您可建立 MAML 說明檔，這些檔案會在 PowerShell 主控台中透過 `Get-Help` 顯示。</span><span class="sxs-lookup"><span data-stu-id="4cd47-177">Now that you have entered all the content, you can create the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

## <a name="create-the-external-help-files"></a><span data-ttu-id="4cd47-178">建立外部說明檔</span><span class="sxs-lookup"><span data-stu-id="4cd47-178">Create the external help files</span></span>

<span data-ttu-id="4cd47-179">此步驟會建立 MAML 說明檔，這些檔案會在 PowerShell 主控台中透過 `Get-Help` 顯示。</span><span class="sxs-lookup"><span data-stu-id="4cd47-179">This step creates the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

<span data-ttu-id="4cd47-180">請執行下列命令來建置 MAML 檔案：</span><span class="sxs-lookup"><span data-stu-id="4cd47-180">To build the MAML files, run the following command:</span></span>

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

<span data-ttu-id="4cd47-181">`New-ExternalHelp` 會將所有 Cmdlet Markdown 檔案轉換成一或多個 MAML 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-181">`New-ExternalHelp` converts all of the cmdlet Markdown files into one (or more) MAML files.</span></span> <span data-ttu-id="4cd47-182">「關於」檔案會轉換成具有下列名稱格式的純文字檔案：`about_topic_name.help.txt`。</span><span class="sxs-lookup"><span data-stu-id="4cd47-182">About files are converted to plain-text files with the following name format: `about_topic_name.help.txt`.</span></span>
<span data-ttu-id="4cd47-183">Markdown 內容必須符合 PlatyPS 結構描述的需求。</span><span class="sxs-lookup"><span data-stu-id="4cd47-183">The Markdown content must meet the requirement of the PlatyPS schema.</span></span> <span data-ttu-id="4cd47-184">當內容未遵循結構描述時，`New-ExternalHelp` 將會結束並發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cd47-184">`New-ExternalHelp` will exits with errors when the content does not follow the schema.</span></span> <span data-ttu-id="4cd47-185">您必須編輯檔案以修正結構描述違規。</span><span class="sxs-lookup"><span data-stu-id="4cd47-185">You must edit the files to fix the schema violations.</span></span>

> [!CAUTION]
> <span data-ttu-id="4cd47-186">PlatyPS 不善於將 `about_*.md` 檔案轉換成純文字。</span><span class="sxs-lookup"><span data-stu-id="4cd47-186">PlatyPS does a poor job converting the `about_*.md` files to plain text.</span></span> <span data-ttu-id="4cd47-187">您必須使用非常簡單的 Markdown，才能取得可接受的結果。</span><span class="sxs-lookup"><span data-stu-id="4cd47-187">You must use very simple Markdown to get acceptable results.</span></span> <span data-ttu-id="4cd47-188">您可能會希望以純文字 `about_topic_name.help.txt` 格式來維護檔案，而不是透過 PlatyPS 轉換這些檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-188">You may want to maintain the files in plain-text `about_topic_name.help.txt` format, rather than allowing PlatyPS to convert them.</span></span>

<span data-ttu-id="4cd47-189">完成此步驟之後，您會在目標輸出資料夾中看到 `*-help.xml` 與 `about_*.help.txt` 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-189">Once this step is complete, you will see `*-help.xml` and `about_*.help.txt` files in the target output folder.</span></span>

<span data-ttu-id="4cd47-190">如需詳細資訊，請參閱 [New-ExternalHelp][]</span><span class="sxs-lookup"><span data-stu-id="4cd47-190">For more information, see [New-ExternalHelp][]</span></span>

### <a name="test-the-compiled-help-files"></a><span data-ttu-id="4cd47-191">測試已編譯的說明檔</span><span class="sxs-lookup"><span data-stu-id="4cd47-191">Test the compiled help files</span></span>

<span data-ttu-id="4cd47-192">您可使用 [Get-HelpPreview][] Cmdlet 來驗證內容：</span><span class="sxs-lookup"><span data-stu-id="4cd47-192">You can verify the content with the [Get-HelpPreview][] cmdlet:</span></span>

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

<span data-ttu-id="4cd47-193">Cmdlet 會讀取已編譯的 MAML 檔案，並使用從 `Get-Help` 所收到的相同格式來輸出內容。</span><span class="sxs-lookup"><span data-stu-id="4cd47-193">The cmdlet reads the compiled MAML file and outputs the content in the same format you would receive from `Get-Help`.</span></span> <span data-ttu-id="4cd47-194">這可供檢查結果，以確認 Markdown 檔案已正確編譯並產生所要的結果。</span><span class="sxs-lookup"><span data-stu-id="4cd47-194">This allows you to inspect the results to verify that the Markdown files compiled correctly and produce the desired results.</span></span> <span data-ttu-id="4cd47-195">如果發現錯誤，請重新編輯 Markdown 檔案，並重新編譯 MAML。</span><span class="sxs-lookup"><span data-stu-id="4cd47-195">If you find an error, re-edit the Markdown files and recompile the MAML.</span></span>

<span data-ttu-id="4cd47-196">您現在已完成發佈說明檔的準備了。</span><span class="sxs-lookup"><span data-stu-id="4cd47-196">Now you are ready to publish your help files.</span></span>

## <a name="publishing-your-help"></a><span data-ttu-id="4cd47-197">發佈說明</span><span class="sxs-lookup"><span data-stu-id="4cd47-197">Publishing your help</span></span>

<span data-ttu-id="4cd47-198">現在已將 Markdown 檔案編譯成 PowerShell 說明檔，您可讓使用者使用這些檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-198">Now that you have compiled the Markdown files into PowerShell help files, you are ready to make the files available to users.</span></span> <span data-ttu-id="4cd47-199">您有兩種方式可在 PowerShell 主控台中提供說明。</span><span class="sxs-lookup"><span data-stu-id="4cd47-199">There are two options for providing help in the PowerShell console.</span></span>

- <span data-ttu-id="4cd47-200">使用模組來封裝說明檔</span><span class="sxs-lookup"><span data-stu-id="4cd47-200">Package the help files with the module</span></span>
- <span data-ttu-id="4cd47-201">建立可更新的說明套件，讓使用者透過 `Update-Help` Cmdlet 安裝</span><span class="sxs-lookup"><span data-stu-id="4cd47-201">Create an updateable help package that users install with the `Update-Help` cmdlet</span></span>

### <a name="packaging-help-with-the-module"></a><span data-ttu-id="4cd47-202">使用模組封裝說明</span><span class="sxs-lookup"><span data-stu-id="4cd47-202">Packaging help with the module</span></span>

<span data-ttu-id="4cd47-203">說明檔可封裝至模組內。</span><span class="sxs-lookup"><span data-stu-id="4cd47-203">The help files can be packaged with your module.</span></span> <span data-ttu-id="4cd47-204">如需資料夾結構的詳細資料，請參閱[撰寫模組的說明][]。</span><span class="sxs-lookup"><span data-stu-id="4cd47-204">See [Writing Help for Modules][] for details of the folder structure.</span></span> <span data-ttu-id="4cd47-205">在模組資訊清單內，會需將說明檔清單納入 **FileList** 索引鍵的值中。</span><span class="sxs-lookup"><span data-stu-id="4cd47-205">You should include the list of Help files in the value of the **FileList** key in the module manifest.</span></span>

### <a name="creating-an-updateable-help-package"></a><span data-ttu-id="4cd47-206">建立可更新的說明套件</span><span class="sxs-lookup"><span data-stu-id="4cd47-206">Creating an updateable help package</span></span>

<span data-ttu-id="4cd47-207">概括而言，建立可更新說明的步驟包含：</span><span class="sxs-lookup"><span data-stu-id="4cd47-207">At a high level, the steps to create updateable help include:</span></span>

1. <span data-ttu-id="4cd47-208">尋找可裝載說明檔的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="4cd47-208">Find an internet site to host your help files</span></span>
1. <span data-ttu-id="4cd47-209">將 **HelpInfoURI** 索引鍵新增至模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="4cd47-209">Add a **HelpInfoURI** key to your module manifest</span></span>
1. <span data-ttu-id="4cd47-210">建立 HelpInfo XML 檔案</span><span class="sxs-lookup"><span data-stu-id="4cd47-210">Create a HelpInfo XML file</span></span>
1. <span data-ttu-id="4cd47-211">建立 CAB 檔案</span><span class="sxs-lookup"><span data-stu-id="4cd47-211">Create CAB files</span></span>
1. <span data-ttu-id="4cd47-212">上傳檔案</span><span class="sxs-lookup"><span data-stu-id="4cd47-212">Upload your files</span></span>

<span data-ttu-id="4cd47-213">如需詳細資訊，請參閱[支援的可更新說明：逐步解說][step-by-step]。</span><span class="sxs-lookup"><span data-stu-id="4cd47-213">For more information, see [Supporting Updateable Help: Step-by-step][step-by-step].</span></span>

<span data-ttu-id="4cd47-214">PlatyPS 可協助執行上述部分步驟。</span><span class="sxs-lookup"><span data-stu-id="4cd47-214">PlatyPS assists you with  some of these steps.</span></span>

<span data-ttu-id="4cd47-215">**HelpInfoURI** 是一個 URL，其指向說明檔裝載在網際網路上的位置。</span><span class="sxs-lookup"><span data-stu-id="4cd47-215">The **HelpInfoURI** is a URL that points to location where your help files are hosted on the internet.</span></span> <span data-ttu-id="4cd47-216">這個值可在模組資訊清單中進行設定。</span><span class="sxs-lookup"><span data-stu-id="4cd47-216">This value is configured in the module manifest.</span></span> <span data-ttu-id="4cd47-217">`Update-Help` 會讀取模組資訊清單以取得此 URL，並下載可更新說明的內容。</span><span class="sxs-lookup"><span data-stu-id="4cd47-217">`Update-Help` reads the module manifest to get this URL and download the updateable help content.</span></span> <span data-ttu-id="4cd47-218">這個 URL 只應指向資料夾位置，而非個別檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-218">This URL should only point to the folder location and not to individual files.</span></span> <span data-ttu-id="4cd47-219">`Update-Help` 會根據模組資訊清單以及 HelpInfo XML 檔案中的其他資訊來建構待下載檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="4cd47-219">`Update-Help` constructs the filenames to download based on other information from the module manifest and the HelpInfo XML file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4cd47-220">**HelpInfoURI** 的結尾必須是斜線字元 (`/`)。</span><span class="sxs-lookup"><span data-stu-id="4cd47-220">The **HelpInfoURI** must end with a forward-slash character (`/`).</span></span> <span data-ttu-id="4cd47-221">如果沒有該字元，`Update-Help` 就無法建構正確的檔案路徑來下載內容。</span><span class="sxs-lookup"><span data-stu-id="4cd47-221">Without that character, `Update-Help` cannot construct the correct file paths to download the content.</span></span> <span data-ttu-id="4cd47-222">此外，大部分 HTTP 式的檔案服務都會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="4cd47-222">Also, most HTTP-based file services are case-sensitive.</span></span> <span data-ttu-id="4cd47-223">HelpInfo XML 檔案中的模組中繼資料必須包含適當的字母大小寫。</span><span class="sxs-lookup"><span data-stu-id="4cd47-223">It is important that the module metadata in the HelpInfo XML file contains the proper letter case.</span></span>

<span data-ttu-id="4cd47-224">`New-ExternalHelp` Cmdlet 會在輸出資料夾中建立 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-224">The `New-ExternalHelp` cmdlet creates the HelpInfo XML file in the output folder.</span></span> <span data-ttu-id="4cd47-225">HelpInfo XML 檔案是使用模組 Markdown 檔案 (`ModuleName.md`) 中所包含的 YAML 中繼資料來建立。</span><span class="sxs-lookup"><span data-stu-id="4cd47-225">The HelpInfo XML file is built using YAML metadata contained in the module Markdown files (`ModuleName.md`).</span></span>

<span data-ttu-id="4cd47-226">`New-ExternalHelpCab` Cmdlet 會建立 ZIP 和 CAB 檔案，並包含所編譯的 MAML 與 `about_*.help.txt` 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-226">The `New-ExternalHelpCab` cmdlet creates ZIP and CAB files containing the MAML and `about_*.help.txt` files you compiled.</span></span> <span data-ttu-id="4cd47-227">CAB 檔案與所有 PowerShell 版本皆相容，</span><span class="sxs-lookup"><span data-stu-id="4cd47-227">CAB files are compatible with all versions of PowerShell.</span></span>
<span data-ttu-id="4cd47-228">但 PowerShell 6 或更新版本才可使用 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cd47-228">PowerShell 6 and higher can use ZIP files.</span></span>

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

<span data-ttu-id="4cd47-229">建立 ZIP 和 CAB 檔案之後，請將 ZIP、CAB 以及 HelpInfo XML 檔案上傳到 HTTP 檔案伺服器。</span><span class="sxs-lookup"><span data-stu-id="4cd47-229">After creating the ZIP and CAB files, upload the ZIP, CAB, and HelpInfo XML files to your HTTP file server.</span></span> <span data-ttu-id="4cd47-230">將檔案放在 **HelpInfoURI** 所指示的位置。</span><span class="sxs-lookup"><span data-stu-id="4cd47-230">Put the files in the location indicated by the **HelpInfoURI**.</span></span>

<span data-ttu-id="4cd47-231">如需詳細資訊，請參閱 [New-ExternalHelpCab][]。</span><span class="sxs-lookup"><span data-stu-id="4cd47-231">For more information, see [New-ExternalHelpCab][].</span></span>

### <a name="other-publishing-options"></a><span data-ttu-id="4cd47-232">其他發佈選項</span><span class="sxs-lookup"><span data-stu-id="4cd47-232">Other publishing options</span></span>

<span data-ttu-id="4cd47-233">Markdown 是一種多樣化的格式，能夠輕易地轉換成其他格式來進行發佈。</span><span class="sxs-lookup"><span data-stu-id="4cd47-233">Markdown is a versatile format that is easy to transform to other formats for publishing.</span></span> <span data-ttu-id="4cd47-234">使用 [Pandoc][] 等工具即可將 Markdown 說明檔轉換成許多不同文件格式，包含純文字、HTML、PDF 以及 Office 文件格式。</span><span class="sxs-lookup"><span data-stu-id="4cd47-234">Using a tool like [Pandoc][], you can convert your Markdown help files to many different document formats, including plain text, HTML, PDF, and Office document formats.</span></span>

<span data-ttu-id="4cd47-235">此外，PowerShell 6 和更新版本中的 [ConvertFrom-Markdown][] 與 [Show-Markdown][] Cmdlet 可用來將 Markdown 轉換成 HTML，或在 PowerShell 主控台中建立彩色顯示。</span><span class="sxs-lookup"><span data-stu-id="4cd47-235">Also, the cmdlets [ConvertFrom-Markdown][] and [Show-Markdown][] in PowerShell 6 and higher can be used to convert Markdown to HTML or create a colorful display in the PowerShell console.</span></span>

## <a name="known-issues"></a><span data-ttu-id="4cd47-236">已知問題</span><span class="sxs-lookup"><span data-stu-id="4cd47-236">Known issues</span></span>

<span data-ttu-id="4cd47-237">對於所建立和編譯的 Markdown 檔案結構而言，PlatyPS 對其[結構描述][]非常敏感。</span><span class="sxs-lookup"><span data-stu-id="4cd47-237">PlatyPS is very sensitive to the [schema][] for the structure of the Markdown files it creates and compiles.</span></span> <span data-ttu-id="4cd47-238">撰寫出有效但違反其結構描述的 Markdown 是相當常見的情況。</span><span class="sxs-lookup"><span data-stu-id="4cd47-238">It is very easy write valid Markdown that violates this schema.</span></span> <span data-ttu-id="4cd47-239">如需詳細資訊，請參閱 [PowerShell 樣式指南][]與[編輯參考文章][]。</span><span class="sxs-lookup"><span data-stu-id="4cd47-239">For more information, consult the [PowerShell style guide][] and [Editing reference articles][].</span></span>

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Get-Item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Update-MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[PowerShell 樣式指南]: /powershell/scripting/community/contributing/powershell-style-guide
[PowerShell style guide]: /powershell/scripting/community/contributing/powershell-style-guide
[編輯參考文章]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Editing reference articles]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[撰寫模組的說明]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[Writing Help for Modules]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom-Markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Show-Markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
