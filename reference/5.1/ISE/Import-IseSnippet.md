---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202479"
---
# <span data-ttu-id="123af-103">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="123af-103">Import-IseSnippet</span></span>

## <span data-ttu-id="123af-104">概要</span><span class="sxs-lookup"><span data-stu-id="123af-104">SYNOPSIS</span></span>
<span data-ttu-id="123af-105">將 ISE 程式碼片段匯入目前的工作階段</span><span class="sxs-lookup"><span data-stu-id="123af-105">Imports ISE snippets into the current session</span></span>

## <span data-ttu-id="123af-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="123af-106">SYNTAX</span></span>

### <span data-ttu-id="123af-107">FromFolder (預設值)</span><span class="sxs-lookup"><span data-stu-id="123af-107">FromFolder (Default)</span></span>

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### <span data-ttu-id="123af-108">FromModule</span><span class="sxs-lookup"><span data-stu-id="123af-108">FromModule</span></span>

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="123af-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="123af-109">DESCRIPTION</span></span>

<span data-ttu-id="123af-110">Cmdlet 會將 `Import-IseSnippet` 可重複使用的文字「程式碼片段」從模組或目錄匯入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="123af-110">The `Import-IseSnippet` cmdlet imports reusable text "snippets" from a module or a directory into the current session.</span></span> <span data-ttu-id="123af-111">Windows PowerShell ISE 中的程式碼片段可立即使用。</span><span class="sxs-lookup"><span data-stu-id="123af-111">The snippets are immediately available for use in Windows PowerShell ISE.</span></span> <span data-ttu-id="123af-112">這個 Cmdlet 只適用于 (ISE) 的 Windows PowerShell 整合式腳本環境。</span><span class="sxs-lookup"><span data-stu-id="123af-112">This cmdlet works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="123af-113">若要查看並使用匯入的程式碼片段，請在 Windows PowerShell ISE [ **編輯** ] 功能表中，按一下 [ **啟動程式碼片段** ]，或按 <kbd>Ctrl</kbd> + <kbd>J</kbd>。</span><span class="sxs-lookup"><span data-stu-id="123af-113">To view and use the imported snippets, from the Windows PowerShell ISE **Edit** menu, click **Start Snippets** or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="123af-114">匯入的程式碼片段僅適用於目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="123af-114">Imported snippets are available only in the current session.</span></span> <span data-ttu-id="123af-115">若要將程式碼片段匯入所有 Windows PowerShell ISE 會話，請將 `Import-IseSnippet` 命令新增至您的 Windows PowerShell 設定檔，或將程式碼片段檔案複製到您的本機程式碼片段目錄 `$home\Documents\WindowsPowershell\Snippets` 。</span><span class="sxs-lookup"><span data-stu-id="123af-115">To import the snippets into all Windows PowerShell ISE sessions, add an `Import-IseSnippet` command to your Windows PowerShell profile or copy the snippet files to your local snippets directory `$home\Documents\WindowsPowershell\Snippets`.</span></span>

<span data-ttu-id="123af-116">若要匯入程式碼片段，您必須在程式碼片段 XML 中正確格式化 Windows PowerShell ISE 程式碼片段，並將其儲存在 Snippet.ps1XML 檔案中。</span><span class="sxs-lookup"><span data-stu-id="123af-116">To import snippets, they must be properly formatted in the snippet XML for Windows PowerShell ISE snippets and saved in Snippet.ps1xml files.</span></span> <span data-ttu-id="123af-117">若要建立符合資格的程式碼片段，請使用 `New-IseSnippet` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="123af-117">To create eligible snippets, use the `New-IseSnippet` cmdlet.</span></span> <span data-ttu-id="123af-118">`New-IseSnippet``<SnippetTitle>.Snippets.ps1xml`在目錄中建立檔案 `$home\Documents\WindowsPowerShell\Snippets` 。</span><span class="sxs-lookup"><span data-stu-id="123af-118">`New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span> <span data-ttu-id="123af-119">您可以將程式碼片段移動或複製到 Windows PowerShell 模組的 Snippets 目錄或任何其他目錄。</span><span class="sxs-lookup"><span data-stu-id="123af-119">You can move or copy the snippets to the Snippets directory of a Windows PowerShell module, or to any other directory.</span></span>

<span data-ttu-id="123af-120">`Get-IseSnippet`Cmdlet 會在本機程式碼片段目錄中取得使用者建立的程式碼片段，而不會取得匯入的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="123af-120">The `Get-IseSnippet` cmdlet, which gets user-created snippets in the local snippets directory, does not get imported snippets.</span></span>

<span data-ttu-id="123af-121">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="123af-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="123af-122">範例</span><span class="sxs-lookup"><span data-stu-id="123af-122">EXAMPLES</span></span>

### <span data-ttu-id="123af-123">範例 1：從目錄匯入程式碼片段</span><span class="sxs-lookup"><span data-stu-id="123af-123">Example 1: Import snippets from a directory</span></span>

<span data-ttu-id="123af-124">此範例會將目錄中的程式碼片段匯入 `\\Server01\Public\Snippets` 至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="123af-124">This example imports the snippets from the `\\Server01\Public\Snippets` directory into the current session.</span></span> <span data-ttu-id="123af-125">它使用 **遞迴** 參數從程式碼片段目錄的所有子目錄中取得程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="123af-125">It uses the **Recurse** parameter to get snippets from all subdirectories of the Snippets directory.</span></span>

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### <span data-ttu-id="123af-126">範例 2：從模組匯入程式碼片段</span><span class="sxs-lookup"><span data-stu-id="123af-126">Example 2: Import snippets from a module</span></span>

<span data-ttu-id="123af-127">此範例會從 **SnippetModule** 模組匯入程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="123af-127">This example imports the snippets from the **SnippetModule** module.</span></span> <span data-ttu-id="123af-128">此命令會使用 **ListAvailable** 參數匯入程式碼片段（即使命令執行時 **SnippetModule** 模組未匯入使用者的會話）。</span><span class="sxs-lookup"><span data-stu-id="123af-128">The command uses the **ListAvailable** parameter to import the snippets even if the **SnippetModule** module is not imported into the user's session when the command runs.</span></span>

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### <span data-ttu-id="123af-129">範例 3：在模組中尋找程式碼片段</span><span class="sxs-lookup"><span data-stu-id="123af-129">Example 3: Find snippets in modules</span></span>

<span data-ttu-id="123af-130">此範例會取得 PSModulePath 環境變數中所有已安裝模組中的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="123af-130">This example gets snippets in all installed modules in the PSModulePath environment variable.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### <span data-ttu-id="123af-131">範例 4：匯入所有模組程式碼片段</span><span class="sxs-lookup"><span data-stu-id="123af-131">Example 4: Import all module snippets</span></span>

<span data-ttu-id="123af-132">此範例會將所有已安裝模組中的所有程式碼片段匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="123af-132">This example imports all snippets from all installed modules into the current session.</span></span> <span data-ttu-id="123af-133">一般來說，您不需要像這樣執行命令，因為具有程式碼片段的模組會在匯 `Import-IseSnippet` 入模組時使用 Cmdlet 將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="123af-133">Typically, you don't need to run a command like this because modules that have snippets will use the `Import-IseSnippet` cmdlet to import them for you when the module is imported.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### <span data-ttu-id="123af-134">範例 5：複製所有模組程式碼片段</span><span class="sxs-lookup"><span data-stu-id="123af-134">Example 5: Copy all module snippets</span></span>

<span data-ttu-id="123af-135">此範例會將所有已安裝模組中的程式碼片段檔案複製到目前使用者的程式碼片段目錄。</span><span class="sxs-lookup"><span data-stu-id="123af-135">This example copies the snippet files from all installed modules into the Snippets directory of the current user.</span></span> <span data-ttu-id="123af-136">不同於匯入的程式碼片段只會影響目前工作階段，複製的程式碼片段則是可用於每個 Windows PowerShell ISE 工作階段。</span><span class="sxs-lookup"><span data-stu-id="123af-136">Unlike imported snippets, which affect only the current session, copied snippets are available in every Windows PowerShell ISE session.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## <span data-ttu-id="123af-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="123af-137">PARAMETERS</span></span>

### <span data-ttu-id="123af-138">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="123af-138">-ListAvailable</span></span>

<span data-ttu-id="123af-139">指出此 Cmdlet 會從安裝在電腦上的模組取得程式碼片段（即使模組並未匯入目前的會話）。</span><span class="sxs-lookup"><span data-stu-id="123af-139">Indicates that this cmdlet gets snippets from modules that are installed on the computer, even if the modules are not imported into the current session.</span></span> <span data-ttu-id="123af-140">如果省略此參數，且 **模組** 參數指定的模組未匯入目前的會話，則嘗試從模組取得程式碼片段將會失敗。</span><span class="sxs-lookup"><span data-stu-id="123af-140">If this parameter is omitted, and the module that is specified by the **Module** parameter is not imported into the current session, the attempt to get the snippets from the module fails.</span></span>

<span data-ttu-id="123af-141">只有當命令中使用 **Module** 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="123af-141">This parameter is valid only when the **Module** parameter is used in the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="123af-142">-Module</span><span class="sxs-lookup"><span data-stu-id="123af-142">-Module</span></span>

<span data-ttu-id="123af-143">將指定模組中的程式碼片段匯入目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="123af-143">Imports snippets from the specified module into the current session.</span></span> <span data-ttu-id="123af-144">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="123af-144">Wildcard characters are not supported.</span></span>

<span data-ttu-id="123af-145">此參數會從模組路徑的程式碼片段子目錄中 Snippet.ps1xml 檔案匯入程式碼片段（例如） `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` 。</span><span class="sxs-lookup"><span data-stu-id="123af-145">This parameter imports snippets from Snippet.ps1xml files in the Snippets subdirectory in the module path, such as `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets`.</span></span>

<span data-ttu-id="123af-146">此參數是為了讓模組作者在啟動指令碼 (例如在模組資訊清單的 **ScriptsToProcess** 索引鍵中指定的指令碼) 中使用而設計的。</span><span class="sxs-lookup"><span data-stu-id="123af-146">This parameter is designed to be used by module authors in a startup script, such as a script specified in the **ScriptsToProcess** key of a module manifest.</span></span> <span data-ttu-id="123af-147">模組中的程式碼片段不會自動隨模組匯入，但您可以使用 `Import-IseSnippet` 命令將它們匯入。</span><span class="sxs-lookup"><span data-stu-id="123af-147">Snippets in a module are not automatically imported with the module, but you can use an `Import-IseSnippet` command to import them.</span></span>

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="123af-148">-Path</span><span class="sxs-lookup"><span data-stu-id="123af-148">-Path</span></span>

<span data-ttu-id="123af-149">指定此 Cmdlet 匯入程式碼片段的程式碼片段目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="123af-149">Specifies the path to the snippets directory in which this cmdlet imports snippets.</span></span>

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="123af-150">-Recurse</span><span class="sxs-lookup"><span data-stu-id="123af-150">-Recurse</span></span>

<span data-ttu-id="123af-151">指出此 Cmdlet 會從 **Path** 參數值的所有子目錄匯入程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="123af-151">Indicates that this cmdlet imports snippets from all subdirectories of the value of the **Path** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="123af-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="123af-152">CommonParameters</span></span>

<span data-ttu-id="123af-153">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="123af-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="123af-154">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="123af-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="123af-155">輸入</span><span class="sxs-lookup"><span data-stu-id="123af-155">INPUTS</span></span>

### <span data-ttu-id="123af-156">無</span><span class="sxs-lookup"><span data-stu-id="123af-156">None</span></span>

<span data-ttu-id="123af-157">此 Cmdlet 不接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="123af-157">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="123af-158">輸出</span><span class="sxs-lookup"><span data-stu-id="123af-158">OUTPUTS</span></span>

### <span data-ttu-id="123af-159">無</span><span class="sxs-lookup"><span data-stu-id="123af-159">None</span></span>

<span data-ttu-id="123af-160">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="123af-160">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="123af-161">注意</span><span class="sxs-lookup"><span data-stu-id="123af-161">NOTES</span></span>

- <span data-ttu-id="123af-162">您無法使用 `Get-IseSnippet` Cmdlet 來取得匯入的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="123af-162">You cannot use the `Get-IseSnippet` cmdlet to get imported snippets.</span></span> <span data-ttu-id="123af-163">`Get-IseSnippet` 只取得目錄中的程式碼片段 `$home\Documents\WindowsPowerShell\Snippets` 。</span><span class="sxs-lookup"><span data-stu-id="123af-163">`Get-IseSnippet` gets only snippets in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
- <span data-ttu-id="123af-164">`Import-IseSnippet`會使用 **ISESnippetCollection** 物件的 **Load** 靜態方法。</span><span class="sxs-lookup"><span data-stu-id="123af-164">`Import-IseSnippet` uses the **Load** static method of **Microsoft.PowerShell.Host.ISE.ISESnippetCollection** objects.</span></span> <span data-ttu-id="123af-165">您也可以在 Windows PowerShell ISE 物件模型中使用程式碼片段的 **Load** 方法： `$psISE.CurrentPowerShellTab.Snippets.Load()`</span><span class="sxs-lookup"><span data-stu-id="123af-165">You can also use the **Load** method of snippets in the Windows PowerShell ISE object model: `$psISE.CurrentPowerShellTab.Snippets.Load()`</span></span>
- <span data-ttu-id="123af-166">此 `New-IseSnippet` Cmdlet 會將使用者建立的新程式碼片段儲存在未簽署的 .ps1xml 檔案中。</span><span class="sxs-lookup"><span data-stu-id="123af-166">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="123af-167">因此，Windows PowerShell 無法將它們載入執行原則為 **AllSigned** 或 **Restricted** 的工作階段中。</span><span class="sxs-lookup"><span data-stu-id="123af-167">As such, Windows PowerShell cannot load them into a session in which the execution policy is **AllSigned** or **Restricted** .</span></span> <span data-ttu-id="123af-168">在 **Restricted** 或 **AllSigned** 工作階段中，您可以建立、取得和匯入使用者建立的未簽署程式碼片段，卻無法在工作階段中使用它們。</span><span class="sxs-lookup"><span data-stu-id="123af-168">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="123af-169">若要使用 Cmdlet 所傳回的未簽署使用者建立程式碼片段 `Import-IseSnippet` ，請變更執行原則，然後重新開機 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="123af-169">To use unsigned user-created snippets that the `Import-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="123af-170">如需 Windows PowerShell 執行原則的詳細資訊，請參閱[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="123af-170">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="123af-171">相關連結</span><span class="sxs-lookup"><span data-stu-id="123af-171">RELATED LINKS</span></span>

[<span data-ttu-id="123af-172">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="123af-172">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="123af-173">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="123af-173">New-IseSnippet</span></span>](New-IseSnippet.md)
