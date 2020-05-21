---
title: 一般工作流程參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: c436ad017be72d97c26552c85d9fd212892ec731
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557511"
---
# <a name="common-workflow-parameters"></a>常見工作流程參數

從 Windows PowerShell Cmdlet 產生的工作流程活動會定義一些通用於所有活動的參數。 在撰寫時可以指定這些參數的子集，讓工作流程作者可以自訂活動。 呼叫活動時，使用者可以指定這些參數的另一個子集。

一般工作流程參數分為數個類別，如下所示。

## <a name="connectivity-parameters"></a>連線性參數

|名稱|類型|描述|使用者可以在執行時間時指定嗎？|在撰寫時可以由工作流程作者指定嗎？|可由工作流程作者在具現化時指定嗎？|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|要啟動作業的電腦名稱稱清單。|是|是|是|
|PSCredential|[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|用來登入 PSComputerName 參數所指定之電腦的驗證認證。 只有在指定 PSComputerName 時，此參數才有效。|是|是|是|
|PSPort|UInt32|要用來執行工作流程的埠。|是|是|是|
|PSUseSSL|Boolean|使用安全通訊端層（SSL）通訊協定來建立遠端電腦的安全連線，以執行工作流程。|是|是|是|
|PSConfigurationName|String|用來執行工作流程的會話設定。|是|是|是|
|PSApplicationName|String|工作流程執行之連接 URI 的應用程式名稱部分。 只有當您不使用 ConnectionURI 參數時，才使用此參數。|是|是|是|
|PSThrottleLimit|UInt32|可建立來執行工作流程的最大並行連接數目。|是|TBD|是|
|PSConnectionURI|String[]|完整 Uri 陣列，指定用來執行工作流程之互動式會話的端點。|是|是|是|
|PSAllowRedirection|Boolean|指定是否允許將這個連接重新導向至替代 URI，以執行工作流程。|是|是|是|
|PSSessionOption|[System.web. Pssessionoption （自動化）](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|用於執行工作流程之會話的 Advanced 選項。|是|是|是|
|PSAuthentication|[System.management.automation.runspaces.authenticationmechanism （系統管理）](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|[System.management.automation.runspaces.authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)列舉的值，指定用來驗證使用者認證的驗證機制（authentication）。|是|是|是|
|PSCertificateThumbprint|String|具有執行工作流程許可權之使用者帳戶的數位公開金鑰憑證（X509）。|是|是|是|

### <a name="behavior-parameters"></a>行為參數
