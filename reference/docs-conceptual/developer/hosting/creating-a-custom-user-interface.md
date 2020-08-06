---
title: 建立自訂使用者介面 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebbaba4231b54d42cdcdef07a3ff665bd207d696
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779772"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="41c46-102">建立自訂使用者介面</span><span class="sxs-lookup"><span data-stu-id="41c46-102">Creating a custom user interface</span></span>

<span data-ttu-id="41c46-103">Windows PowerShell 提供抽象的類別和介面，可讓您建立裝載 Windows PowerShell 引擎的自訂互動式 UI。</span><span class="sxs-lookup"><span data-stu-id="41c46-103">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="41c46-104">若要建立自訂 UI，您必須執行[PSHost](/dotnet/api/System.Management.Automation.Host.PSHost)類別。</span><span class="sxs-lookup"><span data-stu-id="41c46-104">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="41c46-105">（選擇性）您也可以執行[Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)和 Pshostuserinterface 類別，以及 Ihostsupportsinteractivesession 和 System.web. [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession)和[System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface)類別，並將其命名為和......[管理介面。](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection)</span><span class="sxs-lookup"><span data-stu-id="41c46-105">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
