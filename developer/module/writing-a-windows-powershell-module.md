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
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857934"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="3a3e0-102">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="3a3e0-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="3a3e0-103">這份文件會寫入系統管理員、 指令碼的開發人員，和指令程式的開發人員必須封裝並散發其 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="3a3e0-104">您可以藉由使用 Windows PowerShell 模組，來封裝及散發您的 Windows PowerShell 解決方案，而不使用已編譯的語言。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="3a3e0-105">Windows PowerShell 模組可讓您將資料分割、 組織和擷取成獨立、 可重複使用單位的 Windows PowerShell 程式碼。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="3a3e0-106">使用這些可重複使用的單位，您可以輕鬆地共用您的模組，直接與其他人。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="3a3e0-107">如果您是指令碼開發人員，您也可以重新封裝來建立自訂指令碼為基礎的應用程式的第三方模組。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="3a3e0-108">模組，類似於在其他指令碼的語言，例如 Perl 及 Python，模組可讓備妥可重複使用、 可轉散發套件的元件，使用額外的好處是讓您重新封裝並擷取多個元件的指令碼解決方案建立自訂解決方案。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="3a3e0-109">在其最基本功能，Windows PowerShell 會將儲存為模組為.psm1 檔案中任何有效 Windows PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="3a3e0-110">PowerShell 也會自動將視為二進位 cmdlet 中的任何組件的模組。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="3a3e0-111">不過，您也可以使用模組 （或更具體來說，模組資訊清單） 組合在一起的整個解決方案。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="3a3e0-112">下列案例描述 Windows PowerShell 模組的一般用法。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="3a3e0-113">媒體櫃</span><span class="sxs-lookup"><span data-stu-id="3a3e0-113">Libraries</span></span>

<span data-ttu-id="3a3e0-114">模組可以用來封裝及散發一致的程式庫執行常見工作的函式。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="3a3e0-115">一般而言，這些函式的名稱會共用反映使用中的常見工作的一或多個名詞。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="3a3e0-116">這些函式也可以與.NET Framework 類別類似，因為它們可以有公用和私用成員。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="3a3e0-117">比方說，程式庫可以包含一組函式檔案傳輸。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="3a3e0-118">在此情況下，名詞反映常見的工作可能是"file"。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="3a3e0-119">設定</span><span class="sxs-lookup"><span data-stu-id="3a3e0-119">Configuration</span></span>

<span data-ttu-id="3a3e0-120">模組可用來新增特定 cmdlet、 提供者、 函數和變數來自訂您的環境。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="3a3e0-121">已編譯程式碼開發和散佈</span><span class="sxs-lookup"><span data-stu-id="3a3e0-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="3a3e0-122">Cmdlet 和提供者的開發人員可以使用模組來測試和發佈其已編譯的程式碼，而不需要建立的嵌入式管理單元。他們可以匯入包含已編譯的程式碼為 （二進位模組） 模組的組件，而不需要建立並註冊的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="3a3e0-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a3e0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a3e0-123">See Also</span></span>

[<span data-ttu-id="3a3e0-124">了解 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="3a3e0-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="3a3e0-125">如何撰寫 PowerShell 指令碼模組</span><span class="sxs-lookup"><span data-stu-id="3a3e0-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="3a3e0-126">如何撰寫 PowerShell 二進位模組</span><span class="sxs-lookup"><span data-stu-id="3a3e0-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="3a3e0-127">如何撰寫 PowerShell 模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="3a3e0-127">How to Write a PowerShell Module Manifest</span></span>](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[<span data-ttu-id="3a3e0-128">修改 PSModulePath 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="3a3e0-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="3a3e0-129">匯入 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="3a3e0-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="3a3e0-130">安裝 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="3a3e0-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
