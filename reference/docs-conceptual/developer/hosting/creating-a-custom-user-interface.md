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
# <a name="creating-a-custom-user-interface"></a>建立自訂使用者介面

Windows PowerShell 提供抽象類別和介面，可讓您建立裝載 Windows PowerShell 引擎的自訂互動式 UI。 若要建立自訂 UI，您必須執行 [PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) 類別。 （選擇性）您也可以執行 [Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)和 [Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) 類別，以及 [Ihostsupportsinteractivesession 和和和和和和和和和和](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) 和 [Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) 介面。
