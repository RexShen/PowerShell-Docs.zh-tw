---
title: 如何撰寫 PowerShell 二進位模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082221"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="d4ea1-102">如何撰寫 PowerShell 二進位模組</span><span class="sxs-lookup"><span data-stu-id="d4ea1-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="d4ea1-103">二進位模組可以包含 cmdlet 類別之任何組件 (.dll)。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="d4ea1-104">根據預設，匯入的二進位模組時，會匯入組件中的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="d4ea1-105">不過，您可以限制會藉由建立根模組是組件的模組資訊清單匯入的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="d4ea1-106">（例如，資訊清單的 CmdletsToExport 索引鍵可用來匯出只在需要的 cmdlet。）此外，二進位模組可以包含其他檔案、 目錄結構和其他項單一 cmdlet 無法有用的管理資訊。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="d4ea1-107">下列程序描述如何建立和安裝 PowerShell 二進位模組。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="d4ea1-108">如何建立和安裝 PowerShell 二進位模組</span><span class="sxs-lookup"><span data-stu-id="d4ea1-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="d4ea1-109">建立二進位 PowerShell 解決方案 (例如撰寫的 cmdlet C#)，功能，也確保正常執行。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="d4ea1-110">程式碼的觀點而言，二進位模組的核心是只要 cmdlet 的組件。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="d4ea1-111">事實上，PowerShell 會視為單一 cmdlet 組件的模組，以載入和卸載，與開發人員執行任何額外的工作。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="d4ea1-112">如需有關如何撰寫 cmdlet 的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="d4ea1-113">如有必要，建立您的解決方案的其餘部分: （其他 cmdlet、 XML 檔案等等），並描述其使用模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="d4ea1-114">除了描述在您的方案中的指令程式組件時，模組資訊清單可以描述，請決定要如何匯出和匯入模組、 指令程式將會公開，和其他檔案將會移到模組。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span> <span data-ttu-id="d4ea1-115">如先前所述不過，PowerShell 可以處理像透過任何額外的模組二進位 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span> <span data-ttu-id="d4ea1-116">因此，模組資訊清單是主要用於將多個檔案結合成單一封裝中，或是明確控制針對指定的組件的發行集時才有用。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span> <span data-ttu-id="d4ea1-117">如需詳細資訊，請參閱 <<c0> [ 如何撰寫 PowerShell 模組資訊清單](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-117">For more information, see [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

   <span data-ttu-id="d4ea1-118">下列程式碼應用程式非常簡單C#包含三個 cmdlet，在相同的檔案，可用做為模組的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

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

3. <span data-ttu-id="d4ea1-119">封裝您的方案，並將封裝儲存至某處 PowerShell 模組路徑中。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="d4ea1-120">`PSModulePath`全域環境變數描述 PowerShell 用來尋找您的模組的預設路徑。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="d4ea1-121">比方說，是常見的路徑，以在系統上儲存模組`%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="d4ea1-122">如果您未使用的預設路徑，您必須明確在安裝期間指定模組的位置。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="d4ea1-123">請務必建立一個資料夾來儲存您的模組中，因為您可能需要儲存多個組件和您的解決方案檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="d4ea1-124">請注意，技術上您不需要在任何地方安裝您的模組`PSModulePath`-這些是只會尋找 PowerShell 模組的預設位置。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="d4ea1-125">不過，它會被視為最佳的作法，除非您有很好的理由來儲存您的模組其他地方。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="d4ea1-126">如需詳細資訊，請參閱 <<c0> [ 安裝 PowerShell 模組](./installing-a-powershell-module.md)並[修改 PowerShell 模組的安裝路徑](./modifying-the-psmodulepath-installation-path.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="d4ea1-127">在 PowerShell 匯入您的模組，藉由呼叫[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="d4ea1-128">若要呼叫[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)會將您的模組載入使用中記憶體。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="d4ea1-129">如果您使用 PowerShell 3.0 和更新版本中，只要呼叫程式碼中的 模組的名稱也會匯入它;如需詳細資訊，請參閱 <<c0> [ 匯入 PowerShell 模組](./importing-a-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="d4ea1-130">匯入做為模組的嵌入式管理單元的組件</span><span class="sxs-lookup"><span data-stu-id="d4ea1-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="d4ea1-131">可以做為二進位模組載入 Cmdlet 和嵌入式管理單元的組件中存在的提供者。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="d4ea1-132">二進位模組以載入嵌入式管理單元的組件時，cmdlet 和嵌入式管理單元的提供者會提供給使用者，嵌入式管理單元中的類別組件會被忽略，但不登錄嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="d4ea1-133">如此一來，Windows PowerShell 所提供的嵌入式管理單元 cmdlet 無法偵測嵌入式管理單元中，即使 cmdlet 與提供者可用於工作階段。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="d4ea1-134">此外，任何格式或類型檔案所參考的嵌入式管理單元無法匯入二進位模組的一部分。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span> <span data-ttu-id="d4ea1-135">若要匯入的格式和類型的檔案中，您必須建立模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-135">To import the formatting and types files you must create a module manifest.</span></span> <span data-ttu-id="d4ea1-136">查看，請[如何撰寫 PowerShell 模組資訊清單](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)。</span><span class="sxs-lookup"><span data-stu-id="d4ea1-136">See, [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4ea1-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4ea1-137">See Also</span></span>

[<span data-ttu-id="d4ea1-138">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="d4ea1-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
