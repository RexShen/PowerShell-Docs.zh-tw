---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 在 Nano Server 上使用 DSC
description: DSC 是選擇性套件，其可在您針對 Windows Nano Server 建立 VHD 時加以安裝。
ms.openlocfilehash: 18585323359abd85515d4db194dae4adbad7c3d8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647064"
---
# <a name="using-dsc-on-nano-server"></a>在 Nano Server 上使用 DSC

> 適用於：Windows PowerShell 5.0

您可以選用 Windows Server 2016 媒體上 `NanoServer\Packages` 資料夾中的 **Nano Server 上的 DSC** 封裝。 當您建立 Nano Server 的 VHD 時，可以安裝此套件，方法是指定 **Microsoft-NanoServer-DSC-Package** 作為 **New-NanoServerImage** 函數中 **Packages** 參數的值。 例如，如果要建立虛擬機器的 VHD，命令會如下所示︰

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

如需安裝及使用 Nano Server 以及如何透過 PowerShell 遠端來管理 Nano Server 的相關資訊，請參閱 [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server) (開始使用 Nano Server)。

## <a name="dsc-features-available-on-nano-server"></a>Nano Server 提供的 DSC 功能

相較於完整版的 Windows Server，Nano Server 僅支援一組有限的 API，所以目前 Nano Server 上的 DSC 和執行於完整 SKU 上的 DSC 相較，並不具備完整的同位功能。 Nano Server 上的 DSC 正在開發中，功能還不夠完備。

目前於 Nano Server 上提供的 DSC 功能如下︰

推入與提取模式

- 完整版 Windows Server 的所有現有 DSC Cmdlet 包括︰
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](/powershell/module/powershellget/find-dscresource)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- 編譯設定 (請參閱 [DSC 設定](../configurations/configurations.md))。

  **問題︰** 密碼加密 (請參閱 [保護 MOF 檔案](../pull-server/secureMOF.md)) 在設定編譯期間無法運作。

- 編譯中繼設定 (請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md))

- 執行使用者內容下的資源 (請參閱[以使用者認證執行 DSC (RunAs)](../configurations/runAsUser.md))

- 類別型資源 (請參閱[使用 PowerShell 類別撰寫自訂 DSC 資源](/previous-versions//dn948461(v=technet.10)))

- 為 DSC 資源偵錯 (請參閱[為 DSC 資源偵錯](../troubleshooting/debugResource.md))

  **問題︰** 如果資源使用 PsDscRunAsCredential 則無法運作 (請參閱 [以使用者認證執行 DSC](../configurations/runAsUser.md))

- [指定跨節點相依性](../configurations/crossNodeDependencies.md)

- [資源的版本管理](../configurations/sxsResource.md)

- 提取用戶端 (設定與資源) (請參閱[使用設定名稱設定提取用戶端](../pull-server/pullClientConfigNames.md))

- [部分設定 (提取與推送)](../pull-server/partialConfigs.md)

- [回報至提取伺服器](../pull-server/reportServer.md)

- MOF 加密

- 事件記錄

- Azure 自動化 DSC 報告

- 可完全正常運作的資源

  - **封存**
  - **環境**
  - **檔案**
  - **Log**
  - **ProcessSet**
  - **登錄**
  - **指令碼**
  - **WindowsPackageCab**
  - **WindowsProcess**
  - **WaitForAll** (請參閱[指定跨節點相依性](../configurations/crossNodeDependencies.md))
  - **WaitForAny** (請參閱[指定跨節點相依性](../configurations/crossNodeDependencies.md))
  - **WaitForSome** (請參閱[指定跨節點相依性](../configurations/crossNodeDependencies.md))

- 部分運作的資源

  - **群組**
  - **GroupSet**

    **問題︰** 若呼叫特定執行個體兩次 (執行兩次相同的設定)，則上述資源會失敗

  - **服務**
  - **ServiceSet**

    **問題︰** 只適用於開始/停止 (狀態) 服務。 如果嘗試變更啟動類型、認證、描述等其他服務屬性，則會失敗。 擲回的錯誤類似如下︰

    ```
    Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.
    ```

- 無法正常運作的資源

  - **使用者**

## <a name="dsc-features-not-available-on-nano-server"></a>Nano Server 上不提供的 DSC 功能

目前於 Nano Server 上沒有提供下列 DSC 功能︰

- 使用加密密碼將 MOF 文件解密
- 提取伺服器 -- 目前無法在 Nano Server 上設定提取伺服器
- 任何不在功能清單中的項目皆可使用

## <a name="using-custom-dsc-resources-on-nano-server"></a>在 Nano Server 上使用自訂 DSC 資源

因為 Nano Server 上僅提供有限的 Windows API 與 CLR 程式庫，所以在 Windows 完整 CLR 版能執行的 DSC 資源，在 Nano Server 上不一定有效。
請先完成端對端測試，再將任何 DSC 自訂資源部署至生產環境。

## <a name="see-also"></a>另請參閱

- [開始使用 Nano Server](/windows-server/get-started/getting-started-with-nano-server)
