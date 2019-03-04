---
title: Windows PowerShell API 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860774"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="a6f9c-102">Windows PowerShell API 範例</span><span class="sxs-lookup"><span data-stu-id="a6f9c-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="a6f9c-103">本節包含示範如何建立 runspace，以限制功能，以及如何以非同步方式執行命令，使用提供的 runspace 的 runspace 集區的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6f9c-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="a6f9c-104">您可以使用 Microsoft Visual Studio 來建立主控台應用程式，然後將從這一節的主題的程式碼複製到主應用程式。</span><span class="sxs-lookup"><span data-stu-id="a6f9c-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a6f9c-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="a6f9c-105">In This Section</span></span>

<span data-ttu-id="a6f9c-106">[範例 PowerShell01](./windows-powershell01-sample.md)這個範例示範如何使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件來限制的 runspace 的功能。</span><span class="sxs-lookup"><span data-stu-id="a6f9c-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="a6f9c-107">此範例的輸出會示範如何限制的 runspace、 如何將標示為私用的 cmdlet、 如何新增和移除 cmdlet 和提供者，將語言模式如何新增 proxy 命令，以及其他等等。</span><span class="sxs-lookup"><span data-stu-id="a6f9c-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="a6f9c-108">[PowerShell02 範例](./windows-powershell02-sample.md)這個範例示範如何使用 runspace 的 runspace 集區，以非同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="a6f9c-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="a6f9c-109">此範例會產生一份命令，並再執行這些命令，而 Windows PowerShell 引擎便會開啟 runspace 從集區會在需要時。</span><span class="sxs-lookup"><span data-stu-id="a6f9c-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>