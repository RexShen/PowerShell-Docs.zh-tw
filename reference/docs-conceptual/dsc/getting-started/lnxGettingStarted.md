---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 開始使用 Linux 預期狀態設定 (DSC)
description: 本主題說明如何開始使用 Linux 的 PowerShell 預期狀態設定 (DSC)。
ms.openlocfilehash: 826707654a297306c39d4dfcfd3941f56b7cf91d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651123"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>開始使用 Linux 預期狀態設定 (DSC)

本主題說明如何開始使用 Linux 的 PowerShell 預期狀態設定 (DSC)。
如需 DSC 的一般資訊，請參閱[開始使用 Windows PowerShell 預期狀態設定](../overview/overview.md)。

## <a name="supported-linux-operation-system-versions"></a>支援的 Linux 作業系統版本

DSC for Linux 支援下列 Linux 作業系統版本。

- CentOS 5、6 和 7 (x86/x64)
- Debian GNU/Linux 6、7 及 8 (x86/x64)
- Oracle Linux 5、6 和 7 (x86/x64)
- Red Hat Enterprise Linux Server 5、6 和 7 (x86/x64)
- SUSE Linux Enterprise Server 10、11 和 12 (x86/x64)
- Ubuntu Server 12.04 LTS、14.04 LTS、16.04 LTS (x86/x64)

## <a name="installing-dsc-for-linux"></a>安裝 DSC for Linux

您必須先安裝[開放式管理基礎結構 (OMI)](https://github.com/Microsoft/omi)，才能安裝 DSC for Linux。

### <a name="installing-omi"></a>安裝 OMI

Linux 的 Desired State Configuration 需要開放式管理基礎結構 (OMI) CIM 伺服器版本 1.0.8.1 或更新的版本。 OMI 可以從 The Open Group 下載：[開放式管理基礎結構 (OMI)](https://github.com/Microsoft/omi)。

若要安裝 OMI，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。 RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。 DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。 ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。

> [!NOTE]
> 若要判斷已安裝的 OpenSSL 版本，請執行命令 `openssl version`。

執行下列命令，在 CentOS 7 x64 系統上安裝 OMI。

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>安裝 DSC

適用於 Linux 的 DSC 可從存放庫中的 [PowerShell-DSC-for-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294) \(英文\) 存放庫下載。

若要安裝 DSC，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。 RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。 DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。 ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。

> [!NOTE]
> 若要判斷已安裝的 OpenSSL 版本，請執行命令 openssl version。

執行下列命令，在 CentOS 7 x64 系統上安裝 DSC。

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>使用 DSC for Linux

下列章節說明如何在 Linux 電腦上建立並執行 DSC 設定。

### <a name="creating-a-configuration-mof-document"></a>建立設定 MOF 文件

Windows PowerShell 設定關鍵字可用來建立 Windows 電腦的設定，就像 Linux 電腦一樣。 下列步驟說明如何使用 Windows PowerShell 建立 Linux 電腦的設定文件。

1. 匯入 nx 模組。 Nx Windows PowerShell 模組包含 DSC for Linux 內建資源的結構描述，並且必須安裝到本機電腦，然後匯入設定中。

   - 若要安裝 nx 模組，請將 nx 模組目錄複製到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 或 `$PSHOME\Modules`。 nx 模組包含在 DSC for Linux 安裝套件中。 若要在您的設定中匯入 nx 模組，請使用 `Import-DSCResource` 命令：

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. 定義設定，然後產生設定文件：

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a>將設定推送至 Linux 電腦

設定文件 (MOF 檔案) 可以使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 推送至 Linux 電腦。 若要從遠端針對 Linux 電腦使用此 Cmdlet 及 [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) \(英文\) 或 [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) \(英文\) Cmdlet，您必須使用 CIMSession。 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) Cmdlet 是用來針對 Linux 電腦建立 **CIMSession** 。

下列程式碼示範如何建立 DSC for Linux 的 CIMSession。

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> 針對 [推送] 模式，使用者認證必須是在 Linux 電腦上的根使用者。 DSC for Linux 僅支援 SSL/TLS 連線，必須使用 `New-CimSession` 並將 –UseSSL 參數設為 $true。 OMI (DSC) 所使用的 SSL 憑證在此檔案中指定：`/etc/opt/omi/conf/omiserver.conf`，屬性為：pemfile 和 keyfile。 如果此憑證不受您正在執行 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) Cmdlet 的 Windows 電腦信任，您可以使用 CIMSession 選項 `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true` 選擇忽略憑證驗證

執行下列命令，將 DSC 設定推送至 Linux 節點。

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>以提取伺服器散發設定

可以用提取伺服器來散發設定給 Linux 電腦，就像 Windows 電腦一樣。 如需使用提取伺服器的指引，請參閱 [Windows PowerShell 預期狀態設定提取伺服器](../pull-server/pullServer.md)。 如需使用提取伺服器與 Linux 電腦的其他資訊與限制，請參閱 Linux 的預期狀態設定版本資訊。

### <a name="working-with-configurations-locally"></a>在本機使用設定

DSC for Linux 包含指令碼以使用本機 Linux 電腦的設定。 這些指令碼位於 `/opt/microsoft/dsc/Scripts` 並且包含下列項目：

- GetDscConfiguration.py

  傳回套用到此電腦的目前設定。 類似於 Windows PowerShell Cmdlet 的 `Get-DscConfiguration` Cmdlet。

  `# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

  傳回套用到此電腦的目前中繼設定。 類似於 [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) Cmdlet。

  `# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

  安裝自訂 DSC 資源模組。 需要包含模組共用物件的程式庫和結構描述 MOF 檔案的 .zip 檔案路徑。

 `# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

  移除自訂的 DSC 資源模組。 需要有要移除的模組名稱。

  `# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

  將設定 MOF 檔案套用至電腦。 類似於 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet。 需要有要套用的設定 MOF 路徑。

  `# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

  將中繼設定 MOF 檔案套用至電腦。 類似於 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) Cmdlet。 需要有要套用的中繼設定 MOF 路徑。

  `# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>Linux 記錄檔的 PowerShell 預期狀態設定

會對 DSC for Linux 訊息產生下列記錄檔。

|     記錄檔      |     目錄      |                                               描述                                                |
| ----------------- | ------------------ | -------------------------------------------------------------------------------------------------------- |
| **omiserver.log** | `/var/opt/omi/log` | OMI CIM 伺服器作業相關的訊息。                                                |
| **dsc.log**       | `/var/opt/omi/log` | 與本機設定管理員 (LCM) 和 DSC 資源作業的作業相關的訊息。 |
