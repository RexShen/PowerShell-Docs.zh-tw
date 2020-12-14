---
ms.date: 09/13/2016
ms.topic: reference
title: 建立自訂使用者介面
description: 建立自訂使用者介面
ms.openlocfilehash: 411165f868cd524c0cef0ba9cce3188c60a7dbdf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645397"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="5bff2-103">建立自訂使用者介面</span><span class="sxs-lookup"><span data-stu-id="5bff2-103">Creating a custom user interface</span></span>

<span data-ttu-id="5bff2-104">Windows PowerShell 提供抽象類別和介面，可讓您建立裝載 Windows PowerShell 引擎的自訂互動式 UI。</span><span class="sxs-lookup"><span data-stu-id="5bff2-104">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="5bff2-105">若要建立自訂 UI，您必須執行 [PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) 類別。</span><span class="sxs-lookup"><span data-stu-id="5bff2-105">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="5bff2-106">（選擇性）您也可以執行 [Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)和 [Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) 類別，以及 [Ihostsupportsinteractivesession 和和和和和和和和和和](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) 和 [Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) 介面。</span><span class="sxs-lookup"><span data-stu-id="5bff2-106">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
