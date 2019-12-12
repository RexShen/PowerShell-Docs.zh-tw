---
title: 正在建立空間 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367577"
---
# <a name="creating-runspaces"></a><span data-ttu-id="712ce-102">建立 Runspace</span><span class="sxs-lookup"><span data-stu-id="712ce-102">Creating Runspaces</span></span>

<span data-ttu-id="712ce-103">「運行時」是主機應用程式所叫用之命令的作業環境。</span><span class="sxs-lookup"><span data-stu-id="712ce-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="712ce-104">此環境包含目前存在的命令和資料，以及目前適用的任何語言限制。</span><span class="sxs-lookup"><span data-stu-id="712ce-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="712ce-105">主應用程式可以使用 Windows PowerShell 所提供的預設執行時間（包括所有可用的核心命令），或建立僅包含可用命令子集的自訂執行時間。</span><span class="sxs-lookup"><span data-stu-id="712ce-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="712ce-106">若要建立自訂的運行時，請建立[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，並將它指派給您的運行空間。</span><span class="sxs-lookup"><span data-stu-id="712ce-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="712ce-107">運行空間工作</span><span class="sxs-lookup"><span data-stu-id="712ce-107">Runspace tasks</span></span>

1. [<span data-ttu-id="712ce-108">建立 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="712ce-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="712ce-109">建立受條件約束的運行空間</span><span class="sxs-lookup"><span data-stu-id="712ce-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="712ce-110">建立多個空間</span><span class="sxs-lookup"><span data-stu-id="712ce-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="712ce-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="712ce-111">See Also</span></span>
