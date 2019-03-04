---
title: 如何匯入使用模組的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859144"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="c4f14-102">如何使用模組來匯入 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c4f14-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="c4f14-103">本主題描述如何使用二進位模組匯入 cmdlet 的 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="c4f14-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="c4f14-104">模組的成員可以包括 cmdlet、 提供者、 函式、 變數、 別名及更多。</span><span class="sxs-lookup"><span data-stu-id="c4f14-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="c4f14-105">嵌入式管理單元可以包含 cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="c4f14-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="c4f14-106">如何將使用模組的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="c4f14-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="c4f14-107">建立組件檔案中的 cmdlet 會實作為具有相同名稱的模組資料夾。</span><span class="sxs-lookup"><span data-stu-id="c4f14-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="c4f14-108">在此程序，在中建立的模組資料夾`system32`資料夾。</span><span class="sxs-lookup"><span data-stu-id="c4f14-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="c4f14-109">請確定`PSModulePath`環境變數包含在新的模組資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="c4f14-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="c4f14-110">根據預設，[系統] 資料夾已新增至`PSModulePath`環境變數。</span><span class="sxs-lookup"><span data-stu-id="c4f14-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="c4f14-111">將指令程式組件複製到模組資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c4f14-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="c4f14-112">執行下列命令以將 cmdlet 新增至工作階段：</span><span class="sxs-lookup"><span data-stu-id="c4f14-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="c4f14-113">此程序可用來測試您的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c4f14-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="c4f14-114">它會在工作階段的組件新增的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c4f14-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="c4f14-115">如需有關模組的詳細資訊，請查看不同類型的模組，不同的方式載入模組，以及如何限制會匯出模組的項目[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="c4f14-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4f14-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4f14-116">See Also</span></span>

[<span data-ttu-id="c4f14-117">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c4f14-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="c4f14-118">安裝模組</span><span class="sxs-lookup"><span data-stu-id="c4f14-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)