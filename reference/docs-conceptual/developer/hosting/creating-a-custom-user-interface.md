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
# <a name="creating-a-custom-user-interface"></a>建立自訂使用者介面

Windows PowerShell 提供抽象的類別和介面，可讓您建立裝載 Windows PowerShell 引擎的自訂互動式 UI。 若要建立自訂 UI，您必須執行[PSHost](/dotnet/api/System.Management.Automation.Host.PSHost)類別。 （選擇性）您也可以執行[Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)和 Pshostuserinterface 類別，以及 Ihostsupportsinteractivesession 和 System.web. [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession)和[System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface)類別，並將其命名為和......[管理介面。](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection)
