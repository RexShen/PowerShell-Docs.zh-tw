---
title: 撰寫 Windows PowerShell 模組的說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360557"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="176e2-102">撰寫 Windows PowerShell 模組的說明</span><span class="sxs-lookup"><span data-stu-id="176e2-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="176e2-103">Windows PowerShell 模組可以包含關於模組的說明主題以及模組成員，例如 Cmdlet、提供者、函式和腳本。</span><span class="sxs-lookup"><span data-stu-id="176e2-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="176e2-104">@No__t-0 Cmdlet 會以顯示其他 Windows PowerShell 專案說明的相同格式顯示模組說明主題，而使用者會使用標準的 `Get-Help` 命令來取得說明主題。</span><span class="sxs-lookup"><span data-stu-id="176e2-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="176e2-105">本檔說明模組說明主題的格式和正確位置，並建議模組說明內容的指導方針。</span><span class="sxs-lookup"><span data-stu-id="176e2-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="176e2-106">模組的類型說明</span><span class="sxs-lookup"><span data-stu-id="176e2-106">Types of Module Help</span></span>

<span data-ttu-id="176e2-107">模組可以包含下列類型的說明。</span><span class="sxs-lookup"><span data-stu-id="176e2-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="176e2-108">**Cmdlet**說明。</span><span class="sxs-lookup"><span data-stu-id="176e2-108">**Cmdlet Help**.</span></span> <span data-ttu-id="176e2-109">描述模組中 Cmdlet 的說明主題是使用命令說明架構的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="176e2-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="176e2-110">**提供者**說明。</span><span class="sxs-lookup"><span data-stu-id="176e2-110">**Provider Help**.</span></span> <span data-ttu-id="176e2-111">描述模組中提供者的說明主題，是使用提供者說明架構的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="176e2-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="176e2-112">**函數**說明。</span><span class="sxs-lookup"><span data-stu-id="176e2-112">**Function Help**.</span></span> <span data-ttu-id="176e2-113">描述模組中之函式的說明主題可以是 XML 檔案，這些檔案會使用函式或腳本或腳本模組中的命令說明架構或以批註為基礎的說明主題。</span><span class="sxs-lookup"><span data-stu-id="176e2-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="176e2-114">**腳本**說明。</span><span class="sxs-lookup"><span data-stu-id="176e2-114">**Script Help**.</span></span> <span data-ttu-id="176e2-115">描述模組中腳本的說明主題可以是使用腳本或腳本模組中的命令說明架構或以批註為基礎之說明主題的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="176e2-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="176e2-116">**概念性（"About"）** 說明。</span><span class="sxs-lookup"><span data-stu-id="176e2-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="176e2-117">您可以使用概念（「關於」）說明主題來描述模組及其成員，並說明如何將成員一起用來執行工作。</span><span class="sxs-lookup"><span data-stu-id="176e2-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="176e2-118">概念性說明主題是具有 Unicode （UTF-8）編碼的文字檔。</span><span class="sxs-lookup"><span data-stu-id="176e2-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="176e2-119">檔案名必須使用 `about_<name>.help.txt` 格式，例如 about_MyModule. help .txt。</span><span class="sxs-lookup"><span data-stu-id="176e2-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="176e2-120">根據預設，Windows PowerShell 包含超過100的關於說明主題的概念，其格式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="176e2-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
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
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="176e2-121">模組說明的位置</span><span class="sxs-lookup"><span data-stu-id="176e2-121">Placement of Module Help</span></span>

<span data-ttu-id="176e2-122">@No__t-0 Cmdlet 會在模組目錄的特定語言子目錄中尋找模組說明主題檔案。</span><span class="sxs-lookup"><span data-stu-id="176e2-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="176e2-123">例如，下列目錄結構圖表會顯示 SampleModule 模組的說明主題位置。</span><span class="sxs-lookup"><span data-stu-id="176e2-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="176e2-124">在範例中， *@no__t 1ModulePath >* 預留位置代表 @no__t 2 環境變數中的其中一個路徑，例如 $home \documents\modules、$pshome \modules 或使用者指定的自訂路徑。</span><span class="sxs-lookup"><span data-stu-id="176e2-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="176e2-125">取得模組說明</span><span class="sxs-lookup"><span data-stu-id="176e2-125">Getting Module Help</span></span>

<span data-ttu-id="176e2-126">當使用者將模組匯入會話時，該模組的說明主題會連同模組一起匯入到會話中。</span><span class="sxs-lookup"><span data-stu-id="176e2-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="176e2-127">在模組資訊清單中，您可以在 FileList 索引鍵的值中列出說明主題檔案，但說明主題不會受到 `Export-ModuleMember` Cmdlet 的影響。</span><span class="sxs-lookup"><span data-stu-id="176e2-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="176e2-128">您可以提供不同語言的模組說明主題。</span><span class="sxs-lookup"><span data-stu-id="176e2-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="176e2-129">@No__t-0 Cmdlet 會在 [控制台] 的 [地區及語言選項] 專案中，自動顯示針對目前使用者所指定語言的模組說明主題。</span><span class="sxs-lookup"><span data-stu-id="176e2-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="176e2-130">在 Windows Vista 和更新版本的 Windows 中，`Get-Help` 會根據針對 Windows 所建立的語言回溯標準，在模組目錄的特定語言子目錄中搜尋說明主題。</span><span class="sxs-lookup"><span data-stu-id="176e2-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="176e2-131">從 Windows PowerShell 3.0 開始，針對 Cmdlet 或函式執行 @no__t 0 命令，會觸發自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="176e2-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="176e2-132">@No__t-0 Cmdlet 會立即顯示模組中說明主題的內容。</span><span class="sxs-lookup"><span data-stu-id="176e2-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="176e2-133">如果模組不包含說明主題，而且使用者電腦上的模組中沒有命令的說明主題，`Get-Help` 會顯示自動產生的說明。</span><span class="sxs-lookup"><span data-stu-id="176e2-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="176e2-134">自動產生的說明包括命令語法、參數，以及輸入和輸出類型，但不包含任何描述。</span><span class="sxs-lookup"><span data-stu-id="176e2-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="176e2-135">自動產生的說明包含文字，可引導使用者嘗試使用 `Update-Help` Cmdlet，從網際網路或檔案共用下載命令的說明。</span><span class="sxs-lookup"><span data-stu-id="176e2-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="176e2-136">此外，也建議使用 `Get-Help` Cmdlet 的**online**參數來取得說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="176e2-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="176e2-137">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="176e2-137">Supporting Updatable Help</span></span>

<span data-ttu-id="176e2-138">Windows PowerShell 3.0 和更新版本的 Windows PowerShell 的使用者可以從網際網路或本機檔案共用下載並安裝模組的已更新說明檔。</span><span class="sxs-lookup"><span data-stu-id="176e2-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="176e2-139">@No__t-0 和 @no__t 1 Cmdlet 會隱藏使用者的管理詳細資料。</span><span class="sxs-lookup"><span data-stu-id="176e2-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="176e2-140">使用者執行 `Update-Help` Cmdlet，然後使用 `Get-Help` Cmdlet，在 Windows PowerShell 命令提示字元中讀取模組的最新說明檔案。</span><span class="sxs-lookup"><span data-stu-id="176e2-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="176e2-141">使用者不需要重新開機 Windows 或 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="176e2-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="176e2-142">防火牆後方的使用者和沒有網際網路存取的使用者，也可以使用「可更新的說明」。</span><span class="sxs-lookup"><span data-stu-id="176e2-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="176e2-143">具有網際網路存取權的系統管理員使用 `Save-Help` Cmdlet，將最新的說明檔下載並安裝到檔案共用。</span><span class="sxs-lookup"><span data-stu-id="176e2-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="176e2-144">然後，使用者會使用 `Update-Help` Cmdlet 的**Path**參數，從檔案共用取得最新的說明檔案。</span><span class="sxs-lookup"><span data-stu-id="176e2-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="176e2-145">模組作者可以在模組中包含說明檔，並使用可更新的說明來更新說明檔，或省略模組的說明檔，並使用可更新的說明來安裝和更新這些檔案。</span><span class="sxs-lookup"><span data-stu-id="176e2-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="176e2-146">如需「可更新的說明」的詳細資訊，請參閱[支援可更新的協助](./supporting-updatable-help.md)。</span><span class="sxs-lookup"><span data-stu-id="176e2-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="176e2-147">支援線上說明</span><span class="sxs-lookup"><span data-stu-id="176e2-147">Supporting Online Help</span></span>

<span data-ttu-id="176e2-148">無法或未在電腦上安裝已更新說明檔案的使用者，通常會依賴線上版本的模組說明主題。</span><span class="sxs-lookup"><span data-stu-id="176e2-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="176e2-149">@No__t-1 Cmdlet 的**online**參數會在使用者的預設網際網路瀏覽器中開啟 Cmdlet 或 advanced function 說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="176e2-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="176e2-150">@No__t-0 Cmdlet 會使用 Cmdlet 或函式的**HelpUri**屬性值來尋找說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="176e2-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="176e2-151">從 Windows PowerShell 3.0 開始，您可以透過在 Cmdlet 類別上定義 HelpUri 屬性或**CmdletBinding**屬性的**HelpUri**屬性，協助使用者找出線上版本的 Cmdlet 和功能說明主題。</span><span class="sxs-lookup"><span data-stu-id="176e2-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="176e2-152">屬性的值是 Cmdlet 或函式的**HelpUri**屬性值。</span><span class="sxs-lookup"><span data-stu-id="176e2-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="176e2-153">如需詳細資訊，請參閱[支援線上說明](./supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="176e2-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="176e2-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="176e2-154">See Also</span></span>

[<span data-ttu-id="176e2-155">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="176e2-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="176e2-156">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="176e2-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="176e2-157">支援線上說明</span><span class="sxs-lookup"><span data-stu-id="176e2-157">Supporting Online Help</span></span>](./supporting-online-help.md)