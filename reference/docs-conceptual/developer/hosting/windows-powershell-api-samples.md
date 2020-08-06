---
title: Windows PowerShell API 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d7232bb16851f1d568cbdfc4374e287d0875adc8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780163"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="bba27-102">Windows PowerShell API 範例</span><span class="sxs-lookup"><span data-stu-id="bba27-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="bba27-103">本節包含範例程式碼，示範如何建立可限制功能的執行空間，以及如何使用執行時間集區以非同步方式執行命令，以提供執行空間。</span><span class="sxs-lookup"><span data-stu-id="bba27-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="bba27-104">您可以使用 Microsoft Visual Studio 建立主控台應用程式，然後將此區段中的主題中的程式碼複製到您的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="bba27-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bba27-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="bba27-105">In This Section</span></span>

<span data-ttu-id="bba27-106">[PowerShell01 範例](./windows-powershell01-sample.md)這個範例示範如何使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件來限制執行時間的功能。</span><span class="sxs-lookup"><span data-stu-id="bba27-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="bba27-107">這個範例的輸出示範如何限制執行時間的語言模式、如何將 Cmdlet 標示為私用、如何新增和移除 Cmdlet 和提供者、如何新增 proxy 命令等。</span><span class="sxs-lookup"><span data-stu-id="bba27-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="bba27-108">[PowerShell02 範例](./windows-powershell02-sample.md)這個範例會示範如何使用執行時間集區的執行程式，以非同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="bba27-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="bba27-109">此範例會產生命令的清單，然後在 Windows PowerShell 引擎視需要從集區開啟執行時間時，執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="bba27-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>
