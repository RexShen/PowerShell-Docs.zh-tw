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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860494"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="98632-102">模組與嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="98632-102">Modules and Snap-ins</span></span>

<span data-ttu-id="98632-103">Cmdlet 可以加入使用 （Windows PowerShell 2.0 所引進） 的模組或嵌入式管理單元的工作階段。一旦此 cmdlet 會新增至工作階段，它可以執行以程式設計方式在命令列的主應用程式或以互動方式。</span><span class="sxs-lookup"><span data-stu-id="98632-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="98632-104">我們建議您將模組使用做為傳遞方法，將 cmdlet 新增至工作階段，原因如下：</span><span class="sxs-lookup"><span data-stu-id="98632-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="98632-105">模組可讓您將 cmdlet 新增載入組件定義此指令程式的位置。</span><span class="sxs-lookup"><span data-stu-id="98632-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="98632-106">沒有需要實作的嵌入式管理單元類別。</span><span class="sxs-lookup"><span data-stu-id="98632-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="98632-107">模組可讓您新增其他資源，例如變數、 函式、 指令碼、 類型和格式檔案，以及更多。</span><span class="sxs-lookup"><span data-stu-id="98632-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="98632-108">嵌入式管理單元可用於只新增到工作階段的 cmdlet 與提供者。</span><span class="sxs-lookup"><span data-stu-id="98632-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="98632-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98632-109">See Also</span></span>

[<span data-ttu-id="98632-110">撰寫 Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="98632-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="98632-111">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="98632-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
