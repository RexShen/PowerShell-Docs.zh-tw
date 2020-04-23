---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 從提取伺服器更新節點
ms.openlocfilehash: fa59a2f6574db2dbc96621be4326f1d5a55e5de9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500667"
---
# <a name="update-nodes-from-a-pull-server"></a>從提取伺服器更新節點

下列各節假設您已經設定提取伺服器。 如果尚未設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

每個目標節點都設定為下載設定、資源，甚至是報告其狀態。 本文將示範如何上傳資源，讓它們可供下載，並設定用戶端以自動下載資源。 當節點收到指派的設定時，透過**提取**或**推送** (v5)，它就會自動從 LCM 中指定的位置下載設定所需的任何資源。

## <a name="using-the-update-dscconfiguration-cmdlet"></a>使用 Update-DSCConfiguration Cmdlet

從 PowerShell 5.0 開始，[Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) Cmdlet 會強制節點從 LCM 中設定的提取伺服器更新其設定。

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>使用 Invoke-CIMMethod

在 PowerShell 4.0 中，您仍然可以使用 [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod)，手動強制提取用戶端更新其設定。 下列範例會使用指定的認證建立 CIM 工作階段、叫用適當的 CIM 方法，並移除工作階段。

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>另請參閱

[PerformRequiredConfigurationChecks](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
