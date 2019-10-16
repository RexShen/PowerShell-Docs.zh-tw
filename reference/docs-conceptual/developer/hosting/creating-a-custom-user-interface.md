---
title: 建立自訂使用者介面 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367627"
---
# <a name="creating-a-custom-user-interface"></a>建立自訂使用者介面

Windows PowerShell 提供抽象的類別和介面，可讓您建立裝載 Windows PowerShell 引擎的自訂互動式 UI。 若要建立自訂 UI，您必須執行[PSHost](/dotnet/api/System.Management.Automation.Host.PSHost)類別。 （選擇性）您也可以執行[Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)和[Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface)類別，並進行此[功能，並建立。Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession)和[System.web. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection)介面的的，都不是。
