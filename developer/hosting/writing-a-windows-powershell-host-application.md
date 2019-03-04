---
title: 撰寫 Windows PowerShell 主機應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 2039e181becd1b39fc3d6cf0cdbcf0c20e9fc206
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863174"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="44332-102">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="44332-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="44332-103">您可以在您的應用程式中裝載 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="44332-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="44332-104">主應用程式可以定義命令執行、 開啟工作階段的本機或遠端電腦上，並叫用的命令是同步或非同步地根據需求的應用程式所在的 runspace。</span><span class="sxs-lookup"><span data-stu-id="44332-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="44332-105">下列主題說明如何建立應用程式裝載</span><span class="sxs-lookup"><span data-stu-id="44332-105">The following topics explain how to create an application that hosts</span></span>

## <a name="in-this-section"></a><span data-ttu-id="44332-106">在本節中</span><span class="sxs-lookup"><span data-stu-id="44332-106">In This Section</span></span>

<span data-ttu-id="44332-107">[Windows PowerShell 主應用程式快速入門](./windows-powershell-host-quickstart.md)提供指示和程式碼範例，可讓您啟動 建立主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="44332-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="44332-108">[建立 Runspace](./creating-runspaces.md)一組主題會說明如何建立 runspace，主應用程式中執行 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="44332-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="44332-109">[新增和叫用命令](./adding-and-invoking-commands.md)說明如何建立和執行命令管線中主應用程式...</span><span class="sxs-lookup"><span data-stu-id="44332-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="44332-110">[建立遠端 runspace](./creating-remote-runspaces.md) Expains 如何連接到遠端電腦的 runspace。</span><span class="sxs-lookup"><span data-stu-id="44332-110">[Creating remote runspaces](./creating-remote-runspaces.md) Expains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="44332-111">[建立自訂使用者介面](./creating-a-custom-user-interface.md)介紹自訂使用者介面，並提供範例連結。</span><span class="sxs-lookup"><span data-stu-id="44332-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="44332-112">[裝載應用程式範例](./host-application-samples.md)本章節包含的完整主機應用程式範例。</span><span class="sxs-lookup"><span data-stu-id="44332-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="44332-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44332-113">See Also</span></span>

[<span data-ttu-id="44332-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="44332-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)