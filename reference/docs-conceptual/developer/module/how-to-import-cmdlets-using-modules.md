---
title: 如何使用模組匯入 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 840c5bc92d718ec4e54d864dc5e012cd33f83905
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811317"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="1770d-102">如何使用模組來匯入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1770d-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="1770d-103">本文說明如何使用二進位模組，將 Cmdlet 匯入 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="1770d-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="1770d-104">模組的成員可以包含 Cmdlet、提供者、函式、變數、別名等等。</span><span class="sxs-lookup"><span data-stu-id="1770d-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="1770d-105">嵌入式管理單元只能包含 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="1770d-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="1770d-106">如何使用模組載入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1770d-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="1770d-107">建立模組資料夾，其名稱與用來執行 Cmdlet 的元件檔案相同。</span><span class="sxs-lookup"><span data-stu-id="1770d-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="1770d-108">在此程式中，會在 Windows 資料夾中建立模組資料夾 `system32` 。</span><span class="sxs-lookup"><span data-stu-id="1770d-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="1770d-109">請確定 `PSModulePath` 環境變數包含新模組資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="1770d-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="1770d-110">根據預設，系統資料夾已新增至 `PSModulePath` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="1770d-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="1770d-111">若要查看 `PSModulePath` ，請輸入： `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="1770d-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="1770d-112">將 Cmdlet 元件複製到模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="1770d-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="1770d-113">`.psd1`在模組的根資料夾中新增模組資訊清單檔案（）。</span><span class="sxs-lookup"><span data-stu-id="1770d-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="1770d-114">PowerShell 會使用模組資訊清單來匯入您的模組。</span><span class="sxs-lookup"><span data-stu-id="1770d-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="1770d-115">如需詳細資訊，請參閱[如何撰寫 PowerShell 模組資訊清單](../module/how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="1770d-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="1770d-116">執行下列命令，將 Cmdlet 新增至會話：</span><span class="sxs-lookup"><span data-stu-id="1770d-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="1770d-117">此程式可以用來測試您的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1770d-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="1770d-118">它會將元件中的所有 Cmdlet 新增至會話。</span><span class="sxs-lookup"><span data-stu-id="1770d-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="1770d-119">如需模組的詳細資訊，請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="1770d-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1770d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1770d-120">See also</span></span>

[<span data-ttu-id="1770d-121">如何撰寫 PowerShell 模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="1770d-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="1770d-122">匯入 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="1770d-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="1770d-123">Import-module</span><span class="sxs-lookup"><span data-stu-id="1770d-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="1770d-124">安裝模組</span><span class="sxs-lookup"><span data-stu-id="1770d-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="1770d-125">修改 PSModulePath 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="1770d-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="1770d-126">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1770d-126">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
