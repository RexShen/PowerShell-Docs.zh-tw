---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 DSC 在初始開機時設定虛擬機器
ms.openlocfilehash: f9634c330832e23fb2c6f08c5b299b55a5505ac9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954605"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>使用 DSC 在初始開機時設定虛擬機器

> [!IMPORTANT]
> 適用於：Windows PowerShell 5.0

## <a name="requirements"></a>需求

> [!NOTE]
> 本主題所述的 **DSCAutomationHostEnabled** 登錄機碼無法在 PowerShell 4.0 中使用。
> 如需如何在 PowerShell 4.0 初始開機時設定新的虛擬機器，請參閱 [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/) (想要使用 DSC 在初始開機時自動設定您的電腦嗎？)

若要執行這些範例，您需要︰

- 可開機使用的 VHD。 您可以從 [TechNet 評估中心](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)下載評估版 Windows Server 2016 的 ISO。
  您可以在 [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)) (建立可開機的虛擬硬碟) 中尋找如何從 ISO 建立 VHD 的指示。
- 已啟用 HYPER-V 的主機電腦。 如需資訊，請參閱 [HYPER-V 概觀](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))。

  藉由使用 DSC，您可以在初始開機時自動安裝軟體及設定電腦。
  您可以將設定 MOF 文件或 metaconfiguration 插入可開機的媒體 (例如 VHD)，於初始開機程序期間加以執行。
  此行為是由 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` 下方的 [DSCAutomationHostEnabled 登錄機碼](DSCAutomationHostEnabled.md) 登錄機碼所設定的。
  此機碼的值預設為 2，表示允許 DSC 在開機時執行。

  若您不想在開機時執行 DSC，請將 [DSCAutomationHostEnabled 登錄機碼](DSCAutomationHostEnabled.md) 登錄機碼設為 0。

- 將設定 MOF 文件插入 VHD
- 將 DSC metaconfiguration 插入 VHD
- 開機時停用 DSC

> [!NOTE]
> 您可以同時將 `Pending.mof` 和 `MetaConfig.mof` 插入到同一部電腦。
> 當這兩個檔案同時存在時，`MetaConfig.mof` 中所指定的設定會優先執行。

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>將設定 MOF 文件插入 VHD

若要制定初始開機時的組態，可以將預先編譯的設定 MOF 文件用為 `Pending.mof` 檔案插入 VHD。
若 **DSCAutomationHostEnabled** 登錄機碼設定為 2 (預設值)，當電腦第一次開機時，DSC 會套用 `Pending.mof` 所定義的組態。

此範例中，我們會使用下列組態在新的電腦上安裝 IIS：

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>將設定 MOF 文件插入 VHD

1. 呼叫 [掛接 VHD](/powershell/module/hyper-v/mount-vhd) Cmdlet，以掛接組態所要插入的 VHD。 例如：

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. 在執行 PowerShell 5.0 或更新版本的電腦上，將上述組態 (**SampleIISInstall**) 另存為 PowerShell 指令碼 (.ps1) 檔案。

3. 在 PowerShell 主控台中，瀏覽至用以儲存.ps1 檔案的資料夾。

4. 執行下列 PowerShell 命令編譯 MOF 文件 (如需如何編譯 DSC 組態的資訊，請參閱 [DSC 組態](../configurations/configurations.md)：

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. 這會在名為 `SampleIISInstall` 的新資料夾中建立 `localhost.mof` 檔案。
   使用 `Pending.mof`Move-Item[ Cmdlet 將該檔案重新命名為 ](/powershell/module/microsoft.powershell.management/move-item)，再將其移至 VHD 上正確的位置。 例如：

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. 呼叫 [DISMOUNT-VHD](/powershell/module/hyper-v/dismount-vhd) Cmdlet 可卸載 VHD。 例如：

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. 使用安裝有 DSC MOF 文件的 VHD 建立 VM。

在初始開機和安裝作業系統之後，便會安裝 IIS。
您可以呼叫 [Get-windowsfeature](/powershell/module/servermanager/get-windowsfeature) Cmdlet 加以驗證。

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>將 DSC metaconfiguration 插入 VHD

您也可以將中繼設定作為 VHD 的 `MetaConfig.mof` 檔案插入 VHD，將電腦設定成在初始開機時提取設定 (請參閱[設定本機設定管理員 (LCM)](../managing-nodes/metaConfig.md))。
若 **DSCAutomationHostEnabled** 登錄機碼設為 2 (預設值)，則電腦第一次開機時，DSC 將會套用 `MetaConfig.mof` 所定義的中繼設定。
若中繼設定指定 LCM 應從提取伺服器提取設定，電腦就會嘗試在初始開機時從該提取伺服器提取設定。
如需設定 DSC 提取伺服器的資訊，請參閱[設定 DSC Web 提取伺服器](../pull-server/pullServer.md)。

在此範例中，我們將會同時使用上一節所述的組態 (**SampleIISInstall**) 及下列中繼設定：

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>將中繼設定 MOF 文件插入 VHD

1. 呼叫 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) Cmdlet，掛接您要插入中繼設定的 VHD。 例如：

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [設定 DSC Web 提取伺服器](../pull-server/pullServer.md)，並將 **SampleIISInistall** 設定儲存到適當的資料夾。

3. 在執行 PowerShell 5.0 或更新版本的電腦上，將上述繼設定 (**PullClientBootstrap**) 另存為 PowerShell 指令碼 (.ps1) 檔案。

4. 在 PowerShell 主控台中，瀏覽至用以儲存.ps1 檔案的資料夾。

5. 執行下列 PowerShell 命令編譯中繼設定 MOF 文件 (如需如何編譯 DSC 組態的資訊，請參閱 [DSC 組態](../configurations/configurations.md)：

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. 這會在名為 `PullClientBootstrap` 的新資料夾中建立 `localhost.meta.mof` 檔案。
   使用 `MetaConfig.mof`Move-Item[ Cmdlet 將該檔案重新命名為 ](/powershell/module/microsoft.powershell.management/move-item)，再將其移至 VHD 上正確的位置。

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. 呼叫 [DISMOUNT-VHD](/powershell/module/hyper-v/dismount-vhd) Cmdlet 可卸載 VHD。 例如：

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. 使用安裝有 DSC MOF 文件的 VHD 建立 VM。

初始開機並安裝作業系統之後，DSC 會從提取伺服器提取設定，然後安裝 IIS。
您可以呼叫 [Get-windowsfeature](/powershell/module/servermanager/get-windowsfeature) Cmdlet 加以驗證。

## <a name="disable-dsc-at-boot-time"></a>開機時停用 DSC

預設會將 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` 機碼的值設為 2，讓 DSC 設定可以在電腦處於擱置或目前狀態時執行。 對於不想在初始開機時執行的組態，您必須將此機碼值設為 0：

1. 呼叫 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) Cmdlet，以掛接 VHD。 例如：

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. 呼叫 `reg load`，以從 VHD 載入登錄 `HKLM\Software` 子機碼。

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. 使用 PowerShell 登錄提供者瀏覽至 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`。

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. 將 `DSCAutomationHostEnabled` 的值變更為 0。

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. 執行下列命令，以卸載此機碼︰

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>另請參閱

[DSC 設定](../configurations/configurations.md)

[DSCAutomationHostEnabled 登錄機碼](DSCAutomationHostEnabled.md)

[設定本機設定管理員 (LCM)](../managing-nodes/metaConfig.md)

[設定 DSC Web 提取伺服器](../pull-server/pullServer.md)
