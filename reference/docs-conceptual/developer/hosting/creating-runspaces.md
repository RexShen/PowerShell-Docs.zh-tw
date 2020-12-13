---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 Runspace
description: 建立 Runspace
ms.openlocfilehash: c6b2c577e435ec88364b189a0c3d065f54f02525
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649350"
---
# <a name="creating-runspaces"></a><span data-ttu-id="e7071-103">建立 Runspace</span><span class="sxs-lookup"><span data-stu-id="e7071-103">Creating Runspaces</span></span>

<span data-ttu-id="e7071-104">運行空間是主機應用程式所叫用之命令的作業環境。</span><span class="sxs-lookup"><span data-stu-id="e7071-104">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="e7071-105">此環境包含目前存在的命令和資料，以及目前適用的任何語言限制。</span><span class="sxs-lookup"><span data-stu-id="e7071-105">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="e7071-106">主機應用程式可以使用 Windows PowerShell 所提供的預設運行空間（其中包含所有可用的核心命令），或建立只包含可用命令子集的自訂執行空間。</span><span class="sxs-lookup"><span data-stu-id="e7071-106">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="e7071-107">若要建立自訂的運行時，請建立 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 物件，並將它指派給您的運行空間。</span><span class="sxs-lookup"><span data-stu-id="e7071-107">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="e7071-108">作業空間工作</span><span class="sxs-lookup"><span data-stu-id="e7071-108">Runspace tasks</span></span>

1. [<span data-ttu-id="e7071-109">建立 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="e7071-109">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="e7071-110">建立受限 Runspace</span><span class="sxs-lookup"><span data-stu-id="e7071-110">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="e7071-111">建立多個 Runspace</span><span class="sxs-lookup"><span data-stu-id="e7071-111">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="e7071-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7071-112">See Also</span></span>
