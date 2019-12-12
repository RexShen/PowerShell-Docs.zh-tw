---
title: 撰寫 Windows PowerShell 模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360617"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="17938-102">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="17938-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="17938-103">本檔是針對需要封裝和散佈其 Windows PowerShell Cmdlet 的系統管理員、腳本開發人員和 Cmdlet 開發人員所撰寫。</span><span class="sxs-lookup"><span data-stu-id="17938-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="17938-104">藉由使用 Windows PowerShell 模組，您可以封裝和散發您的 Windows PowerShell 解決方案，而不需要使用已編譯的語言。</span><span class="sxs-lookup"><span data-stu-id="17938-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="17938-105">Windows PowerShell 模組可讓您將 Windows PowerShell 程式碼分割、組織及抽象化成獨立、可重複使用的單位。</span><span class="sxs-lookup"><span data-stu-id="17938-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="17938-106">有了這些可重複使用的單位，您就可以輕鬆地直接與其他人共用您的模組。</span><span class="sxs-lookup"><span data-stu-id="17938-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="17938-107">如果您是腳本開發人員，也可以重新封裝協力廠商模組，以建立自訂的腳本架構應用程式。</span><span class="sxs-lookup"><span data-stu-id="17938-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="17938-108">模組與其他指令碼語言（例如 Perl 和 Python）中的模組類似，可讓生產環境準備好使用可轉散發元件的腳本解決方案，還有額外的優點可讓您將多個元件重新封裝並抽象化至建立自訂解決方案。</span><span class="sxs-lookup"><span data-stu-id="17938-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="17938-109">在最基本的情況下，Windows PowerShell 會將儲存在 .psm1 檔案中的任何有效 Windows PowerShell 腳本程式碼視為模組。</span><span class="sxs-lookup"><span data-stu-id="17938-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="17938-110">PowerShell 也會自動將任何二元 Cmdlet 元件視為模組。</span><span class="sxs-lookup"><span data-stu-id="17938-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="17938-111">不過，您也可以使用模組（或更明確地說，模組資訊清單）將整個解決方案組合在一起。</span><span class="sxs-lookup"><span data-stu-id="17938-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="17938-112">下列案例說明 Windows PowerShell 模組的一般用法。</span><span class="sxs-lookup"><span data-stu-id="17938-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="17938-113">媒體櫃</span><span class="sxs-lookup"><span data-stu-id="17938-113">Libraries</span></span>

<span data-ttu-id="17938-114">模組可以用來封裝和散發執行一般工作的功能緊密程式庫。</span><span class="sxs-lookup"><span data-stu-id="17938-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="17938-115">一般而言，這些函式的名稱會共用一或多個名詞，以反映它們所用的一般工作。</span><span class="sxs-lookup"><span data-stu-id="17938-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="17938-116">這些函式也可以與 .NET Framework 類別類似，因為它們可以有公用和私用成員。</span><span class="sxs-lookup"><span data-stu-id="17938-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="17938-117">例如，程式庫可以包含一組用於檔案傳輸的函數。</span><span class="sxs-lookup"><span data-stu-id="17938-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="17938-118">在此情況下，反映一般工作的名詞可能是 "file"。</span><span class="sxs-lookup"><span data-stu-id="17938-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="17938-119">設定</span><span class="sxs-lookup"><span data-stu-id="17938-119">Configuration</span></span>

<span data-ttu-id="17938-120">您可以藉由新增特定的 Cmdlet、提供者、函式和變數，使用模組來自訂您的環境。</span><span class="sxs-lookup"><span data-stu-id="17938-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="17938-121">已編譯的程式碼開發和散發</span><span class="sxs-lookup"><span data-stu-id="17938-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="17938-122">Cmdlet 和提供者開發人員可以使用模組來測試和散佈其已編譯的程式碼，而不需要建立嵌入式管理單元。他們可以將包含已編譯器代碼的元件匯入為模組（二進位模組），而不需要建立及註冊嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="17938-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="17938-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17938-123">See Also</span></span>

[<span data-ttu-id="17938-124">瞭解 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="17938-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="17938-125">如何撰寫 PowerShell 腳本模組</span><span class="sxs-lookup"><span data-stu-id="17938-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="17938-126">如何撰寫 PowerShell 二進位模組</span><span class="sxs-lookup"><span data-stu-id="17938-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="17938-127">如何撰寫 PowerShell 模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="17938-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="17938-128">修改 PSModulePath 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="17938-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="17938-129">匯入 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="17938-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="17938-130">安裝 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="17938-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
