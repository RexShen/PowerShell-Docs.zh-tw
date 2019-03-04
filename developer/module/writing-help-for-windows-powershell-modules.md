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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854064"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="45b06-102">撰寫 Windows PowerShell 模組的說明</span><span class="sxs-lookup"><span data-stu-id="45b06-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="45b06-103">Windows PowerShell 模組可以包含有關模組和模組成員，例如 cmdlet、 提供者、 函式和指令碼的說明主題。</span><span class="sxs-lookup"><span data-stu-id="45b06-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="45b06-104">`Get-Help` Cmdlet 會顯示模組的 [說明] 主題相同的格式，它會顯示其他 Windows PowerShell 項目，說明，以及使用者使用標準`Get-Help`命令來取得 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="45b06-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="45b06-105">本文件說明的格式和模組說明主題，正確位置，並建議讓模組的說明內容的指導方針。</span><span class="sxs-lookup"><span data-stu-id="45b06-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="45b06-106">類型的模組說明</span><span class="sxs-lookup"><span data-stu-id="45b06-106">Types of Module Help</span></span>

<span data-ttu-id="45b06-107">模組可以包含下列類型的說明。</span><span class="sxs-lookup"><span data-stu-id="45b06-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="45b06-108">**指令程式說明**。</span><span class="sxs-lookup"><span data-stu-id="45b06-108">**Cmdlet Help**.</span></span> <span data-ttu-id="45b06-109">描述模組中的 cmdlet 的說明主題會使用命令的 XML 檔可幫助的結構描述</span><span class="sxs-lookup"><span data-stu-id="45b06-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="45b06-110">**提供者說明**。</span><span class="sxs-lookup"><span data-stu-id="45b06-110">**Provider Help**.</span></span> <span data-ttu-id="45b06-111">描述在模組中的提供者的說明主題會使用提供者的 XML 檔可幫助的結構描述。</span><span class="sxs-lookup"><span data-stu-id="45b06-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="45b06-112">**函式說明**。</span><span class="sxs-lookup"><span data-stu-id="45b06-112">**Function Help**.</span></span> <span data-ttu-id="45b06-113">說明 主題描述在模組中的函式可以是結構描述或函式，或在指令碼或指令碼模組的 註解式說明主題，協助使用命令的 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="45b06-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="45b06-114">**指令碼說明**。</span><span class="sxs-lookup"><span data-stu-id="45b06-114">**Script Help**.</span></span> <span data-ttu-id="45b06-115">描述指令碼模組中的 [說明] 主題可以是結構描述或指令碼或指令碼模組中的註解式說明主題，協助使用命令的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="45b06-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="45b06-116">**概念性 （「 關於 」） 說明**。</span><span class="sxs-lookup"><span data-stu-id="45b06-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="45b06-117">描述模組和其成員，並說明如何成員可同時執行工作時，您可以使用概念性 （「 關於 」） 說明主題。</span><span class="sxs-lookup"><span data-stu-id="45b06-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="45b06-118">概念性說明主題是以 Unicode (utf-8) 編碼的文字檔。</span><span class="sxs-lookup"><span data-stu-id="45b06-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="45b06-119">檔案名稱必須使用`about_<name>.help.txt`格式，例如 about_MyModule.help.txt。</span><span class="sxs-lookup"><span data-stu-id="45b06-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="45b06-120">根據預設，Windows PowerShell 包含超過 100 個概念的相關說明主題，而它們的格式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="45b06-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

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

## <a name="placement-of-module-help"></a><span data-ttu-id="45b06-121">位置的模組說明</span><span class="sxs-lookup"><span data-stu-id="45b06-121">Placement of Module Help</span></span>

<span data-ttu-id="45b06-122">`Get-Help` Cmdlet 會尋找模組的模組目錄中的特定語言子目錄中的 [說明] 主題檔案。</span><span class="sxs-lookup"><span data-stu-id="45b06-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="45b06-123">例如，下列目錄結構圖表會顯示 SampleModule 模組的 [說明] 主題的位置。</span><span class="sxs-lookup"><span data-stu-id="45b06-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="45b06-124">在範例中，  *\<ModulePath >* 預留位置，代表其中一個路徑中`PSModulePath`環境變數，例如 $home\Documents\Modules、 $pshome\Modules 或使用者指定的自訂路徑。</span><span class="sxs-lookup"><span data-stu-id="45b06-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="45b06-125">取得模組的說明</span><span class="sxs-lookup"><span data-stu-id="45b06-125">Getting Module Help</span></span>

<span data-ttu-id="45b06-126">當使用者將模組匯入到工作階段時，該模組的 [說明] 主題會匯入到隨著該模組的工作階段。</span><span class="sxs-lookup"><span data-stu-id="45b06-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="45b06-127">您可以列出說明主題中的檔案的模組資訊清單中的 FileList 索引鍵的值，但不是會影響 [說明] 主題`Export-ModuleMember`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45b06-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="45b06-128">您可以提供以不同語言的模組說明主題。</span><span class="sxs-lookup"><span data-stu-id="45b06-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="45b06-129">`Get-Help`指令程式會自動顯示模組的說明主題中針對目前的使用者，在 [地區及語言選項] 控制台項目中指定的語言。</span><span class="sxs-lookup"><span data-stu-id="45b06-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="45b06-130">在 Windows Vista 和更新版本的 Windows，`Get-Help`搜尋的模組目錄中建立 Windows 的語言後援標準符合的特定語言子目錄中的 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="45b06-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="45b06-131">在 Windows PowerShell 3.0 中，執行從`Get-Help`cmdlet 或函式的命令就會觸發自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="45b06-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="45b06-132">`Get-Help` Cmdlet 模組中立即顯示 [說明] 主題的內容。</span><span class="sxs-lookup"><span data-stu-id="45b06-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="45b06-133">如果模組沒有包含 [說明] 主題，而且不有任何使用者的電腦上的模組中命令的說明主題`Get-Help`顯示自動產生的說明。</span><span class="sxs-lookup"><span data-stu-id="45b06-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="45b06-134">自動產生的說明包含命令語法、 參數以及輸入和輸出類型，但不包含任何描述。</span><span class="sxs-lookup"><span data-stu-id="45b06-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="45b06-135">自動產生的說明包含文字，以指示使用者先嘗試使用`Update-Help`cmdlet 來從網際網路或檔案共用下載命令的說明。</span><span class="sxs-lookup"><span data-stu-id="45b06-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="45b06-136">它也會建議使用**線上**參數`Get-Help`cmdlet 來取得 [說明] 主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="45b06-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="45b06-137">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="45b06-137">Supporting Updatable Help</span></span>

<span data-ttu-id="45b06-138">使用者的 Windows PowerShell 3.0 和更新版本的 Windows PowerShell 可以下載並安裝模組的已更新的說明檔從網際網路或從本機檔案共用。</span><span class="sxs-lookup"><span data-stu-id="45b06-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="45b06-139">`Update-Help`和`Save-Help`cmdlet 會隱藏使用者管理詳細資料。</span><span class="sxs-lookup"><span data-stu-id="45b06-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="45b06-140">使用者執行`Update-Help`cmdlet，然後使用`Get-Help`cmdlet 來讀取該模組在 Windows PowerShell 命令提示字元的最新說明檔案。</span><span class="sxs-lookup"><span data-stu-id="45b06-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="45b06-141">使用者不需要重新啟動 Windows 或 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="45b06-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="45b06-142">背後的防火牆以及沒有網際網路存取的使用者也可以使用可更新的說明。</span><span class="sxs-lookup"><span data-stu-id="45b06-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="45b06-143">與網際網路的系統管理員存取使用`Save-Help`cmdlet 來下載並安裝最新說明檔案至檔案共用。</span><span class="sxs-lookup"><span data-stu-id="45b06-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="45b06-144">接著，使用者使用**路徑**參數`Update-Help`cmdlet 來取得最新說明檔案從檔案共用。</span><span class="sxs-lookup"><span data-stu-id="45b06-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="45b06-145">模組作者可以在模組中包含說明檔並使用可更新的說明更新說明檔，或省略從模組的說明檔，並使用可更新的說明來安裝並加以更新。</span><span class="sxs-lookup"><span data-stu-id="45b06-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="45b06-146">如需有關可更新說明的詳細資訊，請參閱 <<c0> [ 支援可更新說明](./supporting-updatable-help.md)。</span><span class="sxs-lookup"><span data-stu-id="45b06-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="45b06-147">支援線上說明</span><span class="sxs-lookup"><span data-stu-id="45b06-147">Supporting Online Help</span></span>

<span data-ttu-id="45b06-148">使用者無法或不安裝更新其電腦上的檔案通常會依賴模組說明主題的線上版本的說明。</span><span class="sxs-lookup"><span data-stu-id="45b06-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="45b06-149">**線上**參數`Get-Help`指令程式會在其預設網際網路瀏覽器中開啟指令程式或使用者的進階函式說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="45b06-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="45b06-150">`Get-Help` Cmdlet 會使用值**HelpUri** cmdlet 或函式來尋找說明主題的線上版本的屬性。</span><span class="sxs-lookup"><span data-stu-id="45b06-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="45b06-151">從 Windows PowerShell 3.0 開始，您可以協助使用者尋找 cmdlet 與函式的 [說明] 主題的線上版本，透過在 cmdlet 類別上定義的 HelpUri 屬性或**HelpUri**屬性**CmdletBinding**屬性。</span><span class="sxs-lookup"><span data-stu-id="45b06-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="45b06-152">屬性的值是值**HelpUri** cmdlet 或函式的屬性。</span><span class="sxs-lookup"><span data-stu-id="45b06-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="45b06-153">如需詳細資訊，請參閱 <<c0> [ 支援線上說明](./supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="45b06-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45b06-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45b06-154">See Also</span></span>

[<span data-ttu-id="45b06-155">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="45b06-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="45b06-156">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="45b06-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="45b06-157">支援線上說明</span><span class="sxs-lookup"><span data-stu-id="45b06-157">Supporting Online Help</span></span>](./supporting-online-help.md)