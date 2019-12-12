---
title: 模組和嵌入式管理單元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365367"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="645a6-102">模組與嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="645a6-102">Modules and Snap-ins</span></span>

<span data-ttu-id="645a6-103">您可以使用模組（由 Windows PowerShell 2.0 引進）或嵌入式管理單元，將 Cmdlet 新增至會話。一旦將 Cmdlet 新增至會話，它就可以由主應用程式以程式設計方式執行，或在命令列以互動方式執行。</span><span class="sxs-lookup"><span data-stu-id="645a6-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="645a6-104">基於下列原因，建議您使用模組做為將 Cmdlet 新增至會話的傳遞方法：</span><span class="sxs-lookup"><span data-stu-id="645a6-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="645a6-105">模組可讓您藉由載入定義 Cmdlet 的元件來新增 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="645a6-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="645a6-106">不需要執行嵌入式管理單元類別。</span><span class="sxs-lookup"><span data-stu-id="645a6-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="645a6-107">模組可讓您新增其他資源，例如變數、函式、腳本、類型和格式檔案等等。</span><span class="sxs-lookup"><span data-stu-id="645a6-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="645a6-108">嵌入式管理單元只能用來將 Cmdlet 和提供者新增至會話。</span><span class="sxs-lookup"><span data-stu-id="645a6-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="645a6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="645a6-109">See Also</span></span>

[<span data-ttu-id="645a6-110">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="645a6-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="645a6-111">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="645a6-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
