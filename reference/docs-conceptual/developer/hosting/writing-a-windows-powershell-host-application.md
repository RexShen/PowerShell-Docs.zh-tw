---
title: 撰寫 Windows PowerShell 主應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: b44708b3bbcb974a6178323dff2302b7da121af6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367277"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="62f68-102">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="62f68-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="62f68-103">您可以在應用程式中裝載 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="62f68-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="62f68-104">主應用程式可以定義命令執行所在的執行時間、在本機或遠端電腦上開啟會話，並根據應用程式的需求以同步或非同步方式叫用命令。</span><span class="sxs-lookup"><span data-stu-id="62f68-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="62f68-105">下列主題說明如何建立裝載 Windows PowerShell 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="62f68-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="62f68-106">在本節中</span><span class="sxs-lookup"><span data-stu-id="62f68-106">In This Section</span></span>

<span data-ttu-id="62f68-107">[Windows PowerShell 主機快速入門](./windows-powershell-host-quickstart.md)提供指示和程式碼範例，讓您開始建立主應用程式。</span><span class="sxs-lookup"><span data-stu-id="62f68-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="62f68-108">[建立空間](./creating-runspaces.md)一組主題，說明如何建立執行空間以在主應用程式中執行 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="62f68-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="62f68-109">[新增和](./adding-and-invoking-commands.md)叫用命令說明如何在您的主應用程式中建立及執行命令管線。</span><span class="sxs-lookup"><span data-stu-id="62f68-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="62f68-110">[建立遠端的空間](./creating-remote-runspaces.md)說明如何將執行時間連接至遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="62f68-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="62f68-111">[建立自訂使用者介面](./creating-a-custom-user-interface.md)介紹自訂的使用者介面，並提供範例的連結。</span><span class="sxs-lookup"><span data-stu-id="62f68-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="62f68-112">[主應用程式範例](./host-application-samples.md)本節包含完整主機應用程式的範例。</span><span class="sxs-lookup"><span data-stu-id="62f68-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="62f68-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62f68-113">See Also</span></span>

[<span data-ttu-id="62f68-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="62f68-114">Windows PowerShell</span></span>](https://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
