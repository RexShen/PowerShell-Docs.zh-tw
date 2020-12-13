---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫 Windows PowerShell 模組
description: 撰寫 Windows PowerShell 模組
ms.openlocfilehash: 307241f0fb4d12c1a5cbd651a0ae4d5303098b27
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659432"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="d1dad-103">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="d1dad-103">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="d1dad-104">本檔是針對需要封裝和散發其 Windows PowerShell Cmdlet 的系統管理員、腳本開發人員和 Cmdlet 開發人員所撰寫。</span><span class="sxs-lookup"><span data-stu-id="d1dad-104">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="d1dad-105">藉由使用 Windows PowerShell 模組，您可以封裝和散發您的 Windows PowerShell 解決方案，而不需要使用編譯的語言。</span><span class="sxs-lookup"><span data-stu-id="d1dad-105">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="d1dad-106">Windows PowerShell 模組可讓您分割、組織及抽象化 Windows PowerShell 程式碼，使其成為獨立、可重複使用的單位。</span><span class="sxs-lookup"><span data-stu-id="d1dad-106">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="d1dad-107">使用這些可重複使用的單位，您可以輕鬆地與其他人共用您的模組。</span><span class="sxs-lookup"><span data-stu-id="d1dad-107">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="d1dad-108">如果您是腳本開發人員，也可以重新封裝協力廠商模組，以建立自訂的腳本架構應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1dad-108">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="d1dad-109">類似于其他指令碼語言（例如 Perl 和 Python）中模組的模組，可讓使用可重複使用之可轉散發元件的生產環境就緒腳本解決方案，還有額外的優點，可讓您重新封裝和抽象化多個元件以建立自訂解決方案。</span><span class="sxs-lookup"><span data-stu-id="d1dad-109">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="d1dad-110">在最基本的情況下，Windows PowerShell 會將任何儲存在 .psm1 檔案中的有效 Windows PowerShell 腳本程式碼視為模組。</span><span class="sxs-lookup"><span data-stu-id="d1dad-110">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="d1dad-111">PowerShell 也會自動將任何二進位 Cmdlet 元件視為模組。</span><span class="sxs-lookup"><span data-stu-id="d1dad-111">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="d1dad-112">不過，您也可以使用模組 (或更明確地使用模組資訊清單) 將整個方案組合在一起。</span><span class="sxs-lookup"><span data-stu-id="d1dad-112">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="d1dad-113">下列案例描述 Windows PowerShell 模組的一般用法。</span><span class="sxs-lookup"><span data-stu-id="d1dad-113">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="d1dad-114">程式庫</span><span class="sxs-lookup"><span data-stu-id="d1dad-114">Libraries</span></span>

<span data-ttu-id="d1dad-115">模組可以用來封裝和散發執行一般工作的一致函式程式庫。</span><span class="sxs-lookup"><span data-stu-id="d1dad-115">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="d1dad-116">一般而言，這些函式的名稱會共用一或多個名詞，以反映用於的一般工作。</span><span class="sxs-lookup"><span data-stu-id="d1dad-116">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="d1dad-117">這些函式也可以像 .NET Framework 類別一樣，因為它們可以有公用和私用成員。</span><span class="sxs-lookup"><span data-stu-id="d1dad-117">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="d1dad-118">例如，程式庫可以包含一組用於檔案傳輸的函式。</span><span class="sxs-lookup"><span data-stu-id="d1dad-118">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="d1dad-119">在此情況下，反映一般工作的名詞可能是 "file"。</span><span class="sxs-lookup"><span data-stu-id="d1dad-119">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="d1dad-120">組態</span><span class="sxs-lookup"><span data-stu-id="d1dad-120">Configuration</span></span>

<span data-ttu-id="d1dad-121">您可以藉由新增特定的 Cmdlet、提供者、函式和變數，使用模組來自訂您的環境。</span><span class="sxs-lookup"><span data-stu-id="d1dad-121">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="d1dad-122">已編譯的程式碼開發和散發</span><span class="sxs-lookup"><span data-stu-id="d1dad-122">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="d1dad-123">Cmdlet 和提供者開發人員可以使用模組來測試和散發其已編譯的程式碼，而不需要建立嵌入式管理單元。他們可以將包含已編譯器代碼的元件匯入 (二進位模組) 的模組，而不需要建立及註冊嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="d1dad-123">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1dad-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1dad-124">See Also</span></span>

[<span data-ttu-id="d1dad-125">了解 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="d1dad-125">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="d1dad-126">如何撰寫 PowerShell 指令碼模組</span><span class="sxs-lookup"><span data-stu-id="d1dad-126">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="d1dad-127">如何撰寫 PowerShell 二進位模組</span><span class="sxs-lookup"><span data-stu-id="d1dad-127">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="d1dad-128">如何撰寫 PowerShell 模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="d1dad-128">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="d1dad-129">修改 PSModulePath 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="d1dad-129">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="d1dad-130">匯入 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="d1dad-130">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="d1dad-131">安裝 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="d1dad-131">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
