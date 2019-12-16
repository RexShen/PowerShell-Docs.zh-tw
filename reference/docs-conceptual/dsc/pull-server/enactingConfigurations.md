---
ms.date: 10/16/2017
keywords: dsc,powershell,設定,安裝
title: 施行設定
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953645"
---
# <a name="enacting-configurations"></a>施行設定

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

PowerShell 預期狀態設定 (DSC) 設定有兩種施行方式：Push 模式和 Pull 模式。

## <a name="push-mode"></a>Push 模式

![Push 模式](../images/pushModel.png "Push 模式的運作方式")

Push 模式指的是使用者呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet，將設定積極套用至目標節點。

建立及編譯設定後，您可以呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet，設定 MOF 所在路徑之 Cmdlet 的 -Path 參數，以 Push 模式施行設定。
例如，如果設定 MOF 位於 `C:\DSC\Configurations\localhost.mof`，您可以使用下列命令將其套用到本機電腦：`Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __注意__：DSC 預設會將設定當做背景作業執行。 若要以互動方式執行設定，請呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) 配以 __-Wait__ 參數。

## <a name="pull-mode"></a>Pull 模式

![Pull 模式](../images/pullModel.png "Pull 模式的運作方式")

在 Pull 模式中，提取用戶端會設定成從遠端提取服務取得其所需的狀態設定。
同樣地，提取服務已設為 DSC 服務主機，並已佈建提取用戶端所需要的設定和資源。
每個提取用戶端都有排定的事件，會針對節點的設定執行定期的合規性檢查。
事件初次觸發時，提取用戶端上的本機設定管理員 (LCM) 會向提取服務提出要求，以取得於 LCM 中指定的設定。
如果提取服務上有該設定，且它通過初始驗證檢查，設定就會被下載至提取用戶端，而 LCM 將會在那裡執行它。

LCM 會依照 LCM 的 **ConfigurationModeFrequencyMins** 屬性所指定的固定間隔，檢查用戶端是否符合設定。
LCM 會依照 LCM 的 **RefreshModeFrequency** 屬性所指定的固定間隔，檢查提取服務上的更新設定。
如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)。

託管提取服務的建議解決方案為 DSC 雲端服務：[Azure 自動化](https://azure.microsoft.com/services/automation/)。
此託管解決方案能提供圖形化管理、報告，以及集中化的系統管理。

如需在 Windows Server 上設定提取服務的詳細資訊，請參閱[設定 DSC Web 提取伺服器](pullServer.md)。
不過，請了解此實作僅具備有限的功能，且需要您自行完成部分的整合。

下列主題會說明提取服務和用戶端：

- [Azure 自動化 DSC 概觀](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [設定 SMB 提取伺服器](pullServerSMB.md)
- [設定提取用戶端](pullClientConfigID.md)
