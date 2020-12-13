---
ms.date: 04/10/2020
ms.topic: reference
title: 撰寫 PowerShell 模組的說明
description: 撰寫 PowerShell 模組的說明
ms.openlocfilehash: 3bef45c0dd8a7e63bc419bb3e5a7a1783810105b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654651"
---
# <a name="writing-help-for-powershell-modules"></a><span data-ttu-id="f1066-103">撰寫 PowerShell 模組的說明</span><span class="sxs-lookup"><span data-stu-id="f1066-103">Writing Help for PowerShell Modules</span></span>

<span data-ttu-id="f1066-104">PowerShell 模組可以包含有關模組的說明主題，以及模組成員的相關說明主題，例如 Cmdlet、提供者、函式和腳本。</span><span class="sxs-lookup"><span data-stu-id="f1066-104">PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="f1066-105">此 `Get-Help` Cmdlet 會以顯示其他 PowerShell 專案說明的相同格式顯示模組說明主題，而使用者會使用標準 `Get-Help` 命令來取得說明主題。</span><span class="sxs-lookup"><span data-stu-id="f1066-105">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="f1066-106">本檔說明模組說明主題的格式和正確位置，並建議模組說明內容的指導方針。</span><span class="sxs-lookup"><span data-stu-id="f1066-106">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="f1066-107">模組說明的類型</span><span class="sxs-lookup"><span data-stu-id="f1066-107">Types of Module Help</span></span>

<span data-ttu-id="f1066-108">模組可包含下列類型的說明。</span><span class="sxs-lookup"><span data-stu-id="f1066-108">A module can include the following types of Help.</span></span>

- <span data-ttu-id="f1066-109">**Cmdlet** 說明。</span><span class="sxs-lookup"><span data-stu-id="f1066-109">**Cmdlet Help**.</span></span> <span data-ttu-id="f1066-110">描述模組中 Cmdlet 的說明主題是使用命令說明架構的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="f1066-110">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="f1066-111">**提供者** 說明。</span><span class="sxs-lookup"><span data-stu-id="f1066-111">**Provider Help**.</span></span> <span data-ttu-id="f1066-112">描述模組中提供者的說明主題是使用提供者說明架構的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="f1066-112">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="f1066-113">**函數** 說明。</span><span class="sxs-lookup"><span data-stu-id="f1066-113">**Function Help**.</span></span> <span data-ttu-id="f1066-114">描述模組中之函式的說明主題可以是 XML 檔案，該檔案會使用函數或腳本或腳本模組中的命令說明架構或批註式說明主題。</span><span class="sxs-lookup"><span data-stu-id="f1066-114">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="f1066-115">**腳本** 說明。</span><span class="sxs-lookup"><span data-stu-id="f1066-115">**Script Help**.</span></span> <span data-ttu-id="f1066-116">描述模組中腳本的說明主題可以是 XML 檔案，該檔案會使用腳本或腳本模組中的命令說明架構或以批註為基礎的說明主題。</span><span class="sxs-lookup"><span data-stu-id="f1066-116">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="f1066-117">**概念 ( "About" )** 說明。</span><span class="sxs-lookup"><span data-stu-id="f1066-117">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="f1066-118">您可以使用概念 ( "about" ) 說明主題來描述模組和其成員，並說明如何搭配使用成員來執行工作。</span><span class="sxs-lookup"><span data-stu-id="f1066-118">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span>
  <span data-ttu-id="f1066-119">概念性說明主題是 Unicode (UTF-8) 編碼的文字檔。</span><span class="sxs-lookup"><span data-stu-id="f1066-119">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="f1066-120">檔案名必須使用 `about_<name>.help.txt` 格式，例如 `about_MyModule.help.txt` 。</span><span class="sxs-lookup"><span data-stu-id="f1066-120">The filename must use the `about_<name>.help.txt` format, such as `about_MyModule.help.txt`.</span></span> <span data-ttu-id="f1066-121">根據預設，PowerShell 包含上述有關說明主題的100以上概念，而且其格式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f1066-121">By default, PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```Output
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

<span data-ttu-id="f1066-122">所有的架構檔案都可以在資料夾中找到 `$PSHOME\Schemas\PSMaml` 。</span><span class="sxs-lookup"><span data-stu-id="f1066-122">All of the schema files can be found in the `$PSHOME\Schemas\PSMaml` folder.</span></span>

## <a name="placement-of-module-help"></a><span data-ttu-id="f1066-123">模組說明的位置</span><span class="sxs-lookup"><span data-stu-id="f1066-123">Placement of Module Help</span></span>

<span data-ttu-id="f1066-124">此 `Get-Help` Cmdlet 會在模組目錄的特定語言子目錄中尋找模組說明主題檔案。</span><span class="sxs-lookup"><span data-stu-id="f1066-124">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="f1066-125">例如，下列目錄結構圖顯示 SampleModule 模組之說明主題的位置。</span><span class="sxs-lookup"><span data-stu-id="f1066-125">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="f1066-126">在此範例中， `<ModulePath>` 預留位置代表環境變數中的其中一個路徑 `PSModulePath` ，例如 `$HOME\Documents\Modules` 、 `$PSHOME\Modules` 或使用者指定的自訂路徑。</span><span class="sxs-lookup"><span data-stu-id="f1066-126">In the example, the `<ModulePath>` placeholder represents one of the paths in the `PSModulePath` environment variable, such as `$HOME\Documents\Modules`, `$PSHOME\Modules`, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="f1066-127">取得模組說明</span><span class="sxs-lookup"><span data-stu-id="f1066-127">Getting Module Help</span></span>

<span data-ttu-id="f1066-128">當使用者將模組匯入會話時，該模組的說明主題會與模組一起匯入至會話。</span><span class="sxs-lookup"><span data-stu-id="f1066-128">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="f1066-129">您可以在模組資訊清單的 FileList 索引鍵值中列出說明主題檔案，但此 Cmdlet 不會影響說明主題 `Export-ModuleMember` 。</span><span class="sxs-lookup"><span data-stu-id="f1066-129">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="f1066-130">您可以提供不同語言的模組說明主題。</span><span class="sxs-lookup"><span data-stu-id="f1066-130">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="f1066-131">指令 `Get-Help` 程式會在主控台的 [地區及語言選項] 專案中，以目前使用者指定的語言自動顯示模組說明主題。</span><span class="sxs-lookup"><span data-stu-id="f1066-131">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="f1066-132">在 Windows Vista 和更新版本的 Windows 中，會 `Get-Help` 根據針對 Windows 建立的語言回溯標準，在模組目錄的特定語言子目錄中搜尋說明主題。</span><span class="sxs-lookup"><span data-stu-id="f1066-132">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="f1066-133">從 PowerShell 3.0 開始， `Get-Help` 執行 Cmdlet 或函式的命令會觸發自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="f1066-133">Beginning in PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="f1066-134">此 `Get-Help` Cmdlet 會立即顯示課程模組中的說明主題內容。</span><span class="sxs-lookup"><span data-stu-id="f1066-134">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="f1066-135">如果模組不包含說明主題，而且在使用者電腦上的模組中沒有命令的說明主題，則會 `Get-Help` 顯示自動產生的說明。</span><span class="sxs-lookup"><span data-stu-id="f1066-135">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="f1066-136">自動產生的說明包括命令語法、參數、輸入和輸出類型，但不包含任何描述。</span><span class="sxs-lookup"><span data-stu-id="f1066-136">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="f1066-137">自動產生的說明包含文字，可引導使用者嘗試使用 `Update-Help` 指令程式，從網際網路或檔案共用下載命令的說明。</span><span class="sxs-lookup"><span data-stu-id="f1066-137">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the internet or a file share.</span></span> <span data-ttu-id="f1066-138">此外，也建議您使用 Cmdlet 的 **online** 參數 `Get-Help` 來取得說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="f1066-138">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="f1066-139">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="f1066-139">Supporting Updatable Help</span></span>

<span data-ttu-id="f1066-140">PowerShell 3.0 和更新版本的 PowerShell 使用者可以從網際網路或本機檔案共用下載及安裝模組的已更新說明檔。</span><span class="sxs-lookup"><span data-stu-id="f1066-140">Users of PowerShell 3.0 and later versions of PowerShell can download and install updated help files for a module from the internet or from a local file share.</span></span> <span data-ttu-id="f1066-141">`Update-Help`和 `Save-Help` Cmdlet 會隱藏使用者的管理詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f1066-141">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="f1066-142">使用者執行 `Update-Help` Cmdlet，然後使用 `Get-Help` 指令程式，在 PowerShell 命令提示字元中讀取模組的最新說明檔案。</span><span class="sxs-lookup"><span data-stu-id="f1066-142">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the PowerShell command prompt.</span></span>
<span data-ttu-id="f1066-143">使用者不需要重新開機 Windows 或 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f1066-143">Users do not need to restart Windows or PowerShell.</span></span>

<span data-ttu-id="f1066-144">防火牆後方和沒有網際網路存取的使用者，也可以使用「可更新的說明」。</span><span class="sxs-lookup"><span data-stu-id="f1066-144">Users behind firewalls and those without internet access can use Updatable Help, as well.</span></span>
<span data-ttu-id="f1066-145">具有網際網路存取權的系統管理員可以使用 Cmdlet，將 `Save-Help` 最新的說明檔下載並安裝到檔案共用。</span><span class="sxs-lookup"><span data-stu-id="f1066-145">Administrators with internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="f1066-146">然後，使用者會使用 Cmdlet 的 **Path** 參數， `Update-Help` 從檔案共用取得最新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="f1066-146">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="f1066-147">模組作者可在模組中包含說明檔，並使用「可更新的說明」來更新說明檔，或省略模組的說明檔，並使用「可更新的說明」來安裝和更新它們。</span><span class="sxs-lookup"><span data-stu-id="f1066-147">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="f1066-148">如需「可更新的說明」的詳細資訊，請參閱 [支援可更新](./supporting-updatable-help.md)的說明。</span><span class="sxs-lookup"><span data-stu-id="f1066-148">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="f1066-149">支援線上說明</span><span class="sxs-lookup"><span data-stu-id="f1066-149">Supporting Online Help</span></span>

<span data-ttu-id="f1066-150">無法或未在其電腦上安裝已更新說明檔案的使用者，通常會依賴線上版本的模組說明主題。</span><span class="sxs-lookup"><span data-stu-id="f1066-150">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="f1066-151">Cmdlet 的 **online** 參數 `Get-Help` 會在其預設的網際網路瀏覽器中，開啟適用于使用者之 Cmdlet 或 advanced function 說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="f1066-151">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default internet browser.</span></span>

<span data-ttu-id="f1066-152">此 `Get-Help` Cmdlet 會使用 Cmdlet 或函式的 **HelpUri** 屬性值來尋找說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="f1066-152">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="f1066-153">從 PowerShell 3.0 開始，您可以在 Cmdlet 類別上定義 HelpUri 屬性或 **CmdletBinding** 屬性的 **HelpUri** 屬性，以協助使用者尋找線上版本的 Cmdlet 和函式說明主題。</span><span class="sxs-lookup"><span data-stu-id="f1066-153">Beginning in PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="f1066-154">屬性的值是 Cmdlet 或函式之 **HelpUri** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f1066-154">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="f1066-155">如需詳細資訊，請參閱 [支援線上說明](./supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="f1066-155">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1066-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1066-156">See Also</span></span>

[<span data-ttu-id="f1066-157">撰寫 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="f1066-157">Writing a PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="f1066-158">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="f1066-158">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="f1066-159">支援線上說明</span><span class="sxs-lookup"><span data-stu-id="f1066-159">Supporting Online Help</span></span>](./supporting-online-help.md)
