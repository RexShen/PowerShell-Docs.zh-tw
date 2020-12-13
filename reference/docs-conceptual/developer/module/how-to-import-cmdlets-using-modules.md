---
ms.date: 08/28/2019
ms.topic: reference
title: 如何使用模組來匯入 Cmdlet
description: 如何使用模組來匯入 Cmdlet
ms.openlocfilehash: 485a4be4d2accaf050a6536e7f92a0673f62a30b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657289"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="b4647-103">如何使用模組來匯入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4647-103">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="b4647-104">本文說明如何使用二進位模組將 Cmdlet 匯入至 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="b4647-104">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="b4647-105">模組的成員可以包含 Cmdlet、提供者、函式、變數、別名等等。</span><span class="sxs-lookup"><span data-stu-id="b4647-105">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="b4647-106">嵌入式管理單元只能包含 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="b4647-106">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="b4647-107">如何使用模組載入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4647-107">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="b4647-108">建立模組資料夾，其名稱與用來執行 Cmdlet 的元件檔相同。</span><span class="sxs-lookup"><span data-stu-id="b4647-108">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="b4647-109">在此程式中，模組資料夾會建立在 Windows `system32` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b4647-109">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="b4647-110">請確定 `PSModulePath` 環境變數包含新模組資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="b4647-110">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="b4647-111">根據預設，系統資料夾已新增至 `PSModulePath` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="b4647-111">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="b4647-112">若要查看 `PSModulePath` ，請輸入： `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="b4647-112">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="b4647-113">將 Cmdlet 元件複製到模組資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b4647-113">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="b4647-114">將模組資訊清單檔 (`.psd1`) 新增至模組的根資料夾。</span><span class="sxs-lookup"><span data-stu-id="b4647-114">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="b4647-115">PowerShell 會使用模組資訊清單來匯入您的模組。</span><span class="sxs-lookup"><span data-stu-id="b4647-115">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="b4647-116">如需詳細資訊，請參閱 [如何撰寫 PowerShell 模組資訊清單](../module/how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="b4647-116">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="b4647-117">執行下列命令以將 Cmdlet 新增至會話：</span><span class="sxs-lookup"><span data-stu-id="b4647-117">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="b4647-118">此程式可用於測試您的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b4647-118">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="b4647-119">它會將元件中的所有 Cmdlet 新增至會話。</span><span class="sxs-lookup"><span data-stu-id="b4647-119">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="b4647-120">如需模組的詳細資訊，請參閱 [撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="b4647-120">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4647-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4647-121">See also</span></span>

[<span data-ttu-id="b4647-122">如何撰寫 PowerShell 模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="b4647-122">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="b4647-123">匯入 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="b4647-123">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="b4647-124">Import-Module</span><span class="sxs-lookup"><span data-stu-id="b4647-124">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="b4647-125">安裝模組</span><span class="sxs-lookup"><span data-stu-id="b4647-125">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="b4647-126">修改 PSModulePath 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="b4647-126">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="b4647-127">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b4647-127">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
