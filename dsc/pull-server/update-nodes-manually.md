---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 從提取伺服器更新節點
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400614"
---
# <a name="update-nodes-from-a-pull-server"></a>從提取伺服器更新節點

下列各節假設您有已設定提取伺服器。 如果您還沒有設定提取伺服器，您可以使用下列指南：

- [設定 DSC SMB 提取伺服器](pullServerSmb.md)
- [設定 DSC HTTP 提取伺服器](pullServer.md)

若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。 本文將說明如何上傳資源，讓它們可被下載，並設定用戶端會自動下載的資源。 當節點會收到指派的組態，透過**提取**或是**推送**(v5)，便會自動下載從 LCM 中指定的位置組態所需的任何資源。

## <a name="using-the-update-dscconfiguration-cmdlet"></a>使用 Update-dscconfiguration cmdlet

從 PowerShell 5.0 [Update-dscconfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet，此 cmdlet 會強制更新從提取伺服器設定 LCM 中其組態的節點。

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>使用叫用 CIMMethod

在 PowerShell 4.0 中，您可以手動強制提取用戶端更新其組態中使用[Invoke-cimmethod](/powershell/module/cimcmdlets/invoke-cimmethod)。 下列範例會使用指定的認證建立 CIM 工作階段、 叫用適當的 CIM 方法，並移除工作階段。

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>另請參閱

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
