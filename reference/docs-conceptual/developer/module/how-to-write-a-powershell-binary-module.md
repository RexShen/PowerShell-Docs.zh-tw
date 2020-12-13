---
ms.date: 09/13/2016
ms.topic: reference
title: 如何撰寫 PowerShell 二進位模組
description: 如何撰寫 PowerShell 二進位模組
ms.openlocfilehash: 1d5cea474ac418f78cc782360b7c23b7614d6669
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92663061"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="55b19-103">如何撰寫 PowerShell 二進位模組</span><span class="sxs-lookup"><span data-stu-id="55b19-103">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="55b19-104">二進位模組可以是包含 Cmdlet 類別 ( .dll) 的任何元件。</span><span class="sxs-lookup"><span data-stu-id="55b19-104">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="55b19-105">根據預設，匯入二進位模組時，會匯入元件中的所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55b19-105">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="55b19-106">不過，您可以藉由建立根模組是元件的模組資訊清單來限制匯入的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55b19-106">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="55b19-107"> (例如，資訊清單的 CmdletsToExport 索引鍵只能用來匯出所需的 Cmdlet。 ) 此外，二進位模組也可以包含其他檔案、目錄結構，以及單一 Cmdlet 無法使用的其他有用的管理資訊。</span><span class="sxs-lookup"><span data-stu-id="55b19-107">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="55b19-108">下列程式說明如何建立和安裝 PowerShell 二進位模組。</span><span class="sxs-lookup"><span data-stu-id="55b19-108">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="55b19-109">如何建立和安裝 PowerShell 二進位模組</span><span class="sxs-lookup"><span data-stu-id="55b19-109">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="55b19-110">建立二進位 PowerShell 解決方案 (例如以 c # ) 撰寫的 Cmdlet，以及您所需的功能，並確保它能正常執行。</span><span class="sxs-lookup"><span data-stu-id="55b19-110">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="55b19-111">從程式碼的觀點來看，二進位模組的核心只是一個 Cmdlet 元件。</span><span class="sxs-lookup"><span data-stu-id="55b19-111">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="55b19-112">事實上，在載入和卸載的過程中，PowerShell 會將單一 Cmdlet 元件視為模組，而不會對開發人員進行額外的工作。</span><span class="sxs-lookup"><span data-stu-id="55b19-112">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="55b19-113">如需撰寫 Cmdlet 的詳細資訊，請參閱 [撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="55b19-113">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="55b19-114">如有必要，請建立解決方案的其餘部分： (其他 Cmdlet、XML 檔案等) 並使用模組資訊清單加以描述。</span><span class="sxs-lookup"><span data-stu-id="55b19-114">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="55b19-115">除了描述您解決方案中的 Cmdlet 元件之外，模組資訊清單也可以描述您要如何匯出和匯入模組、要公開哪些 Cmdlet，以及模組中會有哪些其他檔案。</span><span class="sxs-lookup"><span data-stu-id="55b19-115">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="55b19-116">如先前所述，PowerShell 可以將二進位 Cmdlet 視為模組，而不需要額外投入。</span><span class="sxs-lookup"><span data-stu-id="55b19-116">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="55b19-117">因此，模組資訊清單主要適用于將多個檔案結合成單一封裝，或針對指定的元件明確地控制發行集。</span><span class="sxs-lookup"><span data-stu-id="55b19-117">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="55b19-118">如需詳細資訊，請參閱 [如何撰寫 PowerShell 模組資訊清單](how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="55b19-118">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="55b19-119">下列程式碼是非常簡單的 c # 程式碼區塊，其中包含在相同檔案中可當做模組使用的三個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55b19-119">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="55b19-120">封裝您的解決方案，並將套件儲存至 PowerShell 模組路徑中的某個位置。</span><span class="sxs-lookup"><span data-stu-id="55b19-120">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="55b19-121">`PSModulePath`全域環境變數描述 PowerShell 將用來尋找您模組的預設路徑。</span><span class="sxs-lookup"><span data-stu-id="55b19-121">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="55b19-122">例如，在系統上儲存模組的常見路徑是 `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>` 。</span><span class="sxs-lookup"><span data-stu-id="55b19-122">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="55b19-123">如果您未使用預設路徑，則必須在安裝期間明確陳述模組的位置。</span><span class="sxs-lookup"><span data-stu-id="55b19-123">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="55b19-124">請務必建立資料夾來儲存您的模組，因為您可能需要資料夾來儲存解決方案的多個元件和檔案。</span><span class="sxs-lookup"><span data-stu-id="55b19-124">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="55b19-125">請注意，技術上而言，您不需要在任何位置安裝模組，它們 `PSModulePath` 只是 PowerShell 將為您的模組尋找的預設位置。</span><span class="sxs-lookup"><span data-stu-id="55b19-125">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="55b19-126">不過，除非您有充分的理由將模組儲存在其他位置，否則會被視為最佳做法。</span><span class="sxs-lookup"><span data-stu-id="55b19-126">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="55b19-127">如需詳細資訊，請參閱 [安裝 Powershell 模組](./installing-a-powershell-module.md) 和 [修改 Powershell 模組安裝路徑](./modifying-the-psmodulepath-installation-path.md)。</span><span class="sxs-lookup"><span data-stu-id="55b19-127">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="55b19-128">使用 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)的呼叫，將模組匯入 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="55b19-128">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="55b19-129">呼叫 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 會將您的模組載入至使用中記憶體。</span><span class="sxs-lookup"><span data-stu-id="55b19-129">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="55b19-130">如果您使用 PowerShell 3.0 和更新版本，只要在程式碼中呼叫模組的名稱，也會將它匯入;如需詳細資訊，請參閱匯 [入 PowerShell 模組](./importing-a-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="55b19-130">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="55b19-131">將嵌入式管理單元元件匯入為模組</span><span class="sxs-lookup"><span data-stu-id="55b19-131">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="55b19-132">存在於嵌入式管理單元元件中的 Cmdlet 和提供者，可以載入為二進位模組。</span><span class="sxs-lookup"><span data-stu-id="55b19-132">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="55b19-133">當嵌入式管理單元元件以二進位模組的形式載入時，嵌入式管理單元中的 Cmdlet 和提供者可供使用者使用，但會忽略元件中的嵌入式管理單元類別，而且不會註冊嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="55b19-133">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="55b19-134">如此一來，Windows PowerShell 提供的嵌入式管理單元 Cmdlet 就無法偵測到此嵌入式管理單元，即使會話可以使用 Cmdlet 和提供者也一樣。</span><span class="sxs-lookup"><span data-stu-id="55b19-134">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="55b19-135">此外，嵌入式管理單元所參考的任何格式或類型檔案都無法匯入為二進位模組的一部分。</span><span class="sxs-lookup"><span data-stu-id="55b19-135">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="55b19-136">若要匯入格式化和類型檔案，您必須建立模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="55b19-136">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="55b19-137">請參閱 [如何撰寫 PowerShell 模組資訊清單](how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="55b19-137">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55b19-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55b19-138">See Also</span></span>

[<span data-ttu-id="55b19-139">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="55b19-139">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
