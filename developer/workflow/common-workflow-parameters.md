---
title: 常見的工作流程參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054793"
---
# <a name="common-workflow-parameters"></a>常見工作流程參數

從 Windows PowerShell cmdlet 產生的工作流程活動的所有活動中都定義幾個常見的參數。 在撰寫期間，讓工作流程作者可以自訂活動，您可以指定這些參數的子集。 使用者可以指定這些參數的另一個子集，呼叫活動時。

常見的工作流程參數分為數個類別，如下所示。

## <a name="connectivity-parameters"></a>連線參數

|名稱|類型|描述|您可指定在執行階段的使用者嗎？|您可指定在撰寫期間的工作流程作者嗎？|您可指定在具現化的工作流程作者嗎？|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|要啟動作業的電腦名稱的清單。|是|是|是|
|PSCredential|[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|要使用的驗證認證來登入 PSComputerName 參數所指定的電腦。 此參數會指定 PSComputerName 時才有效。|是|是|是|
|PSPort|UInt32|要用來執行工作流程的連接埠。|是|是|是|
|PSUseSSL|布林值|若要建立安全連線到遠端電腦執行工作流程中使用安全通訊端層 (SSL) 通訊協定。|是|是|是|
|PSConfigurationName|String|用來執行工作流程工作階段設定。|是|是|是|
|PSApplicationName|String|工作流程執行的連線 URI 的應用程式名稱部分。 只有在您不使用 ConnectionURI 參數時，請使用此參數。|是|是|是|
|PSThrottleLimit|UInt32|可執行工作流程建立的並行連線數目上限。|是|TBD|是|
|PSConnectionURI|String[]|針對用來執行工作流程的互動式工作階段指定端點的完整 Uri 的陣列。|是|是|是|
|PSAllowRedirection|布林值|指定是否允許這個連接來執行工作流程的替代 URI 的重新導向。|是|是|是|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|用來執行工作流程工作階段的進階的選項。|是|是|是|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|值為[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)列舉，指定用來驗證使用者的認證的驗證機制。|是|是|是|
|PSCertificateThumbprint|String|數位公開金鑰憑證 (X509) 的可執行工作流程的權限的使用者帳戶。|是|是|是|

### <a name="behavior-parameters"></a>行為的參數