---
title: 建立 Runspace |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082935"
---
# <a name="creating-runspaces"></a><span data-ttu-id="a8408-102">建立 Runspace</span><span class="sxs-lookup"><span data-stu-id="a8408-102">Creating Runspaces</span></span>

<span data-ttu-id="a8408-103">Runspace 都由主應用程式叫用命令的作業環境。</span><span class="sxs-lookup"><span data-stu-id="a8408-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="a8408-104">此環境包含命令和資料目前存在於，以及目前適用於任何語言限制。</span><span class="sxs-lookup"><span data-stu-id="a8408-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="a8408-105">裝載應用程式可以使用預設 runspace 所提供的 Windows PowerShell 中，其中包含所有可用的核心命令，或建立自訂的 runspace，其中包含可用命令的子集。</span><span class="sxs-lookup"><span data-stu-id="a8408-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="a8408-106">若要建立自訂的 runspace，建立[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，並將它指派給您的 runspace。</span><span class="sxs-lookup"><span data-stu-id="a8408-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="a8408-107">Runspace 工作</span><span class="sxs-lookup"><span data-stu-id="a8408-107">Runspace tasks</span></span>

1. [<span data-ttu-id="a8408-108">建立 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="a8408-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="a8408-109">建立受限的 runspace</span><span class="sxs-lookup"><span data-stu-id="a8408-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="a8408-110">建立多個執行空間</span><span class="sxs-lookup"><span data-stu-id="a8408-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="a8408-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8408-111">See Also</span></span>
