---
ms.date: 09/13/2016
ms.topic: reference
title: 模組與嵌入式管理單元
description: 模組與嵌入式管理單元
ms.openlocfilehash: de4ff1de9a29b78d7783fe7ed0265f5516db1fb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658676"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="4a517-103">模組與嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="4a517-103">Modules and Snap-ins</span></span>

<span data-ttu-id="4a517-104">您可以使用 Windows PowerShell 2.0) 或嵌入式管理單元 (引進的模組，將 Cmdlet 新增至會話。一旦將指令程式新增至會話，它就可以由主應用程式以程式設計方式執行，或在命令列以互動方式執行。</span><span class="sxs-lookup"><span data-stu-id="4a517-104">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="4a517-105">基於下列原因，建議您使用模組作為將 Cmdlet 新增至會話的傳遞方法：</span><span class="sxs-lookup"><span data-stu-id="4a517-105">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="4a517-106">模組可讓您藉由載入已定義 Cmdlet 的元件來新增 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a517-106">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="4a517-107">不需要執行嵌入式管理單元類別。</span><span class="sxs-lookup"><span data-stu-id="4a517-107">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="4a517-108">模組可讓您新增其他資源，例如變數、函式、腳本、類型和格式化檔案等等。</span><span class="sxs-lookup"><span data-stu-id="4a517-108">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="4a517-109">嵌入式管理單元只能用來將 Cmdlet 和提供者新增至會話。</span><span class="sxs-lookup"><span data-stu-id="4a517-109">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a517-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a517-110">See Also</span></span>

[<span data-ttu-id="4a517-111">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="4a517-111">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="4a517-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4a517-112">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
