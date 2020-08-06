---
title: 模組和嵌入式管理單元 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07cdc55fd6d1462130f1a81deb30056623a525e6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787303"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="1fe21-102">模組與嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="1fe21-102">Modules and Snap-ins</span></span>

<span data-ttu-id="1fe21-103">您可以使用 Windows PowerShell 2.0) 或嵌入式管理單元 (引進的模組，將 Cmdlet 新增至會話。一旦將 Cmdlet 新增至會話，它就可以由主應用程式以程式設計方式執行，或在命令列以互動方式執行。</span><span class="sxs-lookup"><span data-stu-id="1fe21-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="1fe21-104">基於下列原因，建議您使用模組做為將 Cmdlet 新增至會話的傳遞方法：</span><span class="sxs-lookup"><span data-stu-id="1fe21-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="1fe21-105">模組可讓您藉由載入定義 Cmdlet 的元件來新增 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1fe21-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="1fe21-106">不需要執行嵌入式管理單元類別。</span><span class="sxs-lookup"><span data-stu-id="1fe21-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="1fe21-107">模組可讓您新增其他資源，例如變數、函式、腳本、類型和格式檔案等等。</span><span class="sxs-lookup"><span data-stu-id="1fe21-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="1fe21-108">嵌入式管理單元只能用來將 Cmdlet 和提供者新增至會話。</span><span class="sxs-lookup"><span data-stu-id="1fe21-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fe21-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fe21-109">See Also</span></span>

[<span data-ttu-id="1fe21-110">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="1fe21-110">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="1fe21-111">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1fe21-111">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
