---
title: 修改 PSModulePath 安裝路徑 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082204"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="3b0d7-102">修改 PSModulePath 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="3b0d7-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="3b0d7-103">`PSModulePath`環境變數會儲存在磁碟上已安裝的模組位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="3b0d7-104">Windows PowerShell 會在使用者未指定模組的完整路徑，請找出模組使用此變數。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="3b0d7-105">此變數中的路徑會以其出現的順序進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="3b0d7-106">Windows PowerShell 啟動時，`PSModulePath`會建立系統環境變數包含下列的預設值為： `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="3b0d7-107">若要檢視 PSModulePath 變數</span><span class="sxs-lookup"><span data-stu-id="3b0d7-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="3b0d7-108">若要檢視中所指定的路徑`PSModulePath`變數中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="3b0d7-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="3b0d7-109">若要將位置加入至 PSModulePath 變數</span><span class="sxs-lookup"><span data-stu-id="3b0d7-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="3b0d7-110">若要將路徑新增至這個變數，使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="3b0d7-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="3b0d7-111">若要新增暫存值，可僅針對目前的工作階段，請在命令列執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3b0d7-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="3b0d7-112">若要新增為可用，每當開啟工作階段時的永續性值，請在 Windows PowerShell 設定檔中新增下列命令：</span><span class="sxs-lookup"><span data-stu-id="3b0d7-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="3b0d7-113">如需有關設定檔的詳細資訊，請參閱 < [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) Microsoft TechNet library 中。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="3b0d7-114">若要登錄中新增永續性的變數，建立新的使用者環境變數，呼叫`PSModulePath`使用中的環境變數編輯器**系統屬性**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="3b0d7-115">若要使用指令碼中新增永續性的變數，請使用**SetEnvironmentVariable**環境類別上的方法。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="3b0d7-116">例如，下列指令碼"C:\Program Files\Fabrikam\Module 將路徑加入至電腦的 PSModulePath 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="3b0d7-117">若要將路徑新增至使用者 PSModulePath 環境變數，將目標設定為 「 使用者 」。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="3b0d7-118">若要移除 PSModulePath 位置</span><span class="sxs-lookup"><span data-stu-id="3b0d7-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="3b0d7-119">您可以移除變數使用類似的方法中的路徑： 例如，`$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"`將會移除**c:\ModulePath**目前工作階段的路徑。</span><span class="sxs-lookup"><span data-stu-id="3b0d7-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b0d7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b0d7-120">See Also</span></span>

[<span data-ttu-id="3b0d7-121">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="3b0d7-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
