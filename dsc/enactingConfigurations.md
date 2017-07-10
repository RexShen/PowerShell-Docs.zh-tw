---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "施行設定"
ms.openlocfilehash: db82788650186eb82f67b30b24cd45b719bbe314
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="enacting-configurations" class="xliff"></a>
# 施行設定

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

PowerShell 預期狀態設定 (DSC) 設定有兩種施行方式：Push 模式和 Pull 模式。

<a id="push-mode" class="xliff"></a>
## Push 模式

![Push 模式](images/Push.png "Push 模式的運作方式")

Push 模式指的是使用者呼叫 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet，將設定積極套用至目標節點。

建立及編譯設定後，您可以呼叫 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet，設定 MOF 所在路徑之 Cmdlet 的 -Path 參數，以 Push 模式施行設定。 例如，如果設定 MOF 位於 `C:\DSC\Configurations\localhost.mof`，您可以使用下列命令將其套用到本機電腦：`Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __注意__：DSC 預設將設定當做背景工作執行。 若要以互動方式執行設定，請呼叫 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) 配以 __-Wait__ 參數。


<a id="pull-mode" class="xliff"></a>
## Pull 模式

![Pull 模式](images/Pull.png "Pull 模式的運作方式")

在 Pull 模式中，提取用戶端會設定成從遠端的提取伺服器取得其所需的狀態設定。 同樣地，提取伺服器已設為 DSC 服務主機，佈建了提取用戶端所需要的設定和資源。 每個提取用戶端都有排定的工作，對節點設定執行定期的相容性檢查。 當第一次觸發事件時，提取用戶端上的本機設定管理員 (LCM) 會向提取伺服器提出要求，以取得 LCM 中指定的設定。 如果提取伺服器上有這個設定，而且它通過了初始驗證檢查，設定就會傳輸到提取用戶端，LCM 會在這裡執行它。

LCM 會依照 LCM 的 **ConfigurationModeFrequencyMins** 屬性所指定的固定間隔，檢查用戶端是否符合設定。 LCM 會依照 LCM 的 **RefreshModeFrequency** 屬性所指定的固定間隔，檢查提取伺服器上的更新設定。 如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](metaConfig.md)。

如需設定 DSC 提取伺服器的詳細資訊，請參閱[設定 DSC Web 提取伺服器](pullServer.md)。

如果想要利用線上服務裝載提取伺服器功能，請參閱 [Azure 自動化 DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) 服務。

下列主題說明如何設定提取伺服器和用戶端：

- [設定 Web 提取伺服器](pullServer.md)
- [設定 SMB 提取伺服器](pullServerSMB.md)
- [設定提取用戶端](pullClientConfigID.md)

