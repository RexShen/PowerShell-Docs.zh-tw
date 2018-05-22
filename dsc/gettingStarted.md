---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 開始使用 PowerShell 預期狀態設定
ms.openlocfilehash: a449382c979e680ea311c887c86cb675ba6162b7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="c6e01-103">開始使用 PowerShell 預期狀態設定</span><span class="sxs-lookup"><span data-stu-id="c6e01-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="c6e01-104">本指南說明如何開始建立 PowerShell 預期狀態設定文件，並套用至電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e01-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="c6e01-105">本指南假設您大致熟悉 PowerShell Cmdlet、模組和函式。</span><span class="sxs-lookup"><span data-stu-id="c6e01-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span>


## <a name="create-a-configuration"></a><span data-ttu-id="c6e01-106">建立設定</span><span class="sxs-lookup"><span data-stu-id="c6e01-106">Create a Configuration</span></span> ##

<span data-ttu-id="c6e01-107">[**設定**](https://msdn.microsoft.com/powershell/dsc/configurations)是描述環境的文件。</span><span class="sxs-lookup"><span data-stu-id="c6e01-107">[**Configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="c6e01-108">環境包含「**節點**」，通常是虛擬或實體機器。</span><span class="sxs-lookup"><span data-stu-id="c6e01-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span>

<span data-ttu-id="c6e01-109">設定可以有各種形式。</span><span class="sxs-lookup"><span data-stu-id="c6e01-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="c6e01-110">建立新設定的最簡單作法是建立 .ps1 (PowerShell 指令碼) 檔案。</span><span class="sxs-lookup"><span data-stu-id="c6e01-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="c6e01-111">若要這樣做，請開啟您選擇的編輯器。</span><span class="sxs-lookup"><span data-stu-id="c6e01-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="c6e01-112">因為 PowerShell ISE 原本就了解 DSC，所以是不錯的選擇。</span><span class="sxs-lookup"><span data-stu-id="c6e01-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="c6e01-113">將下列項目儲存為 PS1：</span><span class="sxs-lookup"><span data-stu-id="c6e01-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="c6e01-114">設定的組件</span><span class="sxs-lookup"><span data-stu-id="c6e01-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="c6e01-115">**設定**是 PowerShell 4.0 中已加入的關鍵字，</span><span class="sxs-lookup"><span data-stu-id="c6e01-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="c6e01-116">表示一種特殊的預期狀態設定所使用的 PowerShell 函式。</span><span class="sxs-lookup"><span data-stu-id="c6e01-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="c6e01-117">在這個範例中，此函式稱為 myFirstConfiguration。</span><span class="sxs-lookup"><span data-stu-id="c6e01-117">In this example, the function is named myFirstConfiguration.</span></span>

<span data-ttu-id="c6e01-118">下一行是匯入陳述式，類似於匯入模組，</span><span class="sxs-lookup"><span data-stu-id="c6e01-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="c6e01-119">將在稍後討論。</span><span class="sxs-lookup"><span data-stu-id="c6e01-119">It will be discussed later on.</span></span>

<span data-ttu-id="c6e01-120">「節點」定義這個設定將產生作用的目標電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="c6e01-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="c6e01-121">雖然這項設定在本機進行編輯，設定仍可連接到遠端節點，並加以設定。</span><span class="sxs-lookup"><span data-stu-id="c6e01-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span>

<span data-ttu-id="c6e01-122">節點可以是電腦名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="c6e01-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="c6e01-123">在單一設定文件中可以有多個節點。</span><span class="sxs-lookup"><span data-stu-id="c6e01-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="c6e01-124">使用[設定資料](https://msdn.microsoft.com/powershell/dsc/configdata)時，您也可以將相同設定套用到多個節點。</span><span class="sxs-lookup"><span data-stu-id="c6e01-124">Using [configuration data](https://msdn.microsoft.com/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="c6e01-125">在此情況下，節點會是 "localhost"，表示本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c6e01-125">In this case, the node is "localhost" - which means the local computer.</span></span>

<span data-ttu-id="c6e01-126">下一個項目是[**資源**](https://msdn.microsoft.com/powershell/dsc/resources)。</span><span class="sxs-lookup"><span data-stu-id="c6e01-126">The next item is a [**resource**](https://msdn.microsoft.com/powershell/dsc/resources).</span></span> <span data-ttu-id="c6e01-127">資源是設定的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="c6e01-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="c6e01-128">每個資源都是模組，其中定義單一電腦層面的實作邏輯。</span><span class="sxs-lookup"><span data-stu-id="c6e01-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="c6e01-129">您也可以在 PowerShell 中執行 **Get-DscResource** 檢視電腦上的每個資源。</span><span class="sxs-lookup"><span data-stu-id="c6e01-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="c6e01-130">資源必須存在於本機電腦上，並先匯入，然後才可用於 **Import-DscResource** 的設定，其位於這項設定的第二行。</span><span class="sxs-lookup"><span data-stu-id="c6e01-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span>

<span data-ttu-id="c6e01-131">**制定設定**</span><span class="sxs-lookup"><span data-stu-id="c6e01-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="c6e01-132">如果上述指令碼是儲存並執行，將不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="c6e01-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="c6e01-133">這是因為設定不只是函式，而且上述指令碼已定義了函式，但尚未執行。</span><span class="sxs-lookup"><span data-stu-id="c6e01-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="c6e01-134">函式經定義之後，就必須叫用：</span><span class="sxs-lookup"><span data-stu-id="c6e01-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="c6e01-135">在執行設定函數時，設定函數會驗證設定是否有效，</span><span class="sxs-lookup"><span data-stu-id="c6e01-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="c6e01-136">不應有語法錯誤，資源應該定義所有必要的參數，而且應該在執行之前匯入所有資源。</span><span class="sxs-lookup"><span data-stu-id="c6e01-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="c6e01-137">一旦執行設定之後，它會對設定中每個節點建立一個設定名稱包含 **.MOF 檔案**的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c6e01-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="c6e01-138">.MOF 檔案是由 PowerShell DSC 使用，用來透過網路進行通訊、以標準為基礎的管理格式。</span><span class="sxs-lookup"><span data-stu-id="c6e01-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="c6e01-139">制定設定：</span><span class="sxs-lookup"><span data-stu-id="c6e01-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="c6e01-140">這會建立 PowerShell 工作，向外連到設定中的節點，並設定節點。</span><span class="sxs-lookup"><span data-stu-id="c6e01-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="c6e01-141">若要查看工作的輸出，請使用 -Wait。</span><span class="sxs-lookup"><span data-stu-id="c6e01-141">To see the output of the job, use -Wait.</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```