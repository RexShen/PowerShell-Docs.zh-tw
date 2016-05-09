# 開始使用 Linux 預期狀態設定 (DSC)

本主題說明如何開始使用 Linux 的 PowerShell 預期狀態設定 (DSC)。 如需 DSC 的一般資訊，請參閱[開始使用 Windows PowerShell 預期狀態設定](overview.md)。

## 支援的 Linux 作業系統版本

DSC for Linux 支援下列 Linux 作業系統版本。
- CentOS 5、6 和 7 (x86/x64)
- Debian GNU/Linux 6 和 7 (x86/x64)
- Oracle Linux 5、6 和 7 (x86/x64)
- Red Hat Enterprise Linux Server 5、6 和 7 (x86/x64)
- SUSE Linux Enterprise Server 10、11 和 12 (x86/x64)
- Ubuntu Server 12.04 LTS 和 14.04 LTS (x86/x64)

下表描述 DSC for Linux 必要的套件相依性。

|  必要的套件 |  描述 |  最低版本 | 
|---|---|---|
| glibc| GNU 程式庫| 2…4 – 31.30| 
| python| Python| 2.4 – 3.4| 
| omiserver| 開放式管理基礎結構| 1.0.8.1| 
| openssl| OpenSSL 程式庫| 0.9.8 或 1.0| 
| ctypes| Python CTypes 程式庫| 必須符合 Python 版本| 
| libcurl| cURL http 用戶端程式庫| 7.15.1| 

## 安裝 DSC for Linux

您必須先安裝[開放式管理基礎結構 (OMI)](https://collaboration.opengroup.org/omi/)，才能安裝 DSC for Linux。

### 安裝 OMI

Linux 的預期狀態設定需要開放式管理基礎結構 (OMI) CIM 伺服器版本 1.0.8.1。 OMI 可以從開放式群組下載：[開放式管理基礎結構 (OMI)](https://collaboration.opengroup.org/omi/)。

若要安裝 OMI，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。 RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。 DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。 ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。

> **注意**：若要判斷已安裝的 OpenSSL 版本，請執行命令 `openssl version`。

執行下列命令，在 CentOS 7 x64 系統上安裝 OMI。

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### 安裝 DSC

您可以從[這裡](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest)下載 Linux 的 DSC。 

若要安裝 DSC，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。 RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。 DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。 ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。

> **注意**：若要判斷已安裝的 OpenSSL 版本，請執行命令 openssl version。
 
執行下列命令，在 CentOS 7 x64 系統上安裝 DSC。

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## 使用 DSC for Linux

下列章節說明如何在 Linux 電腦上建立並執行 DSC 設定。

### 建立設定 MOF 文件

Windows PowerShell 設定關鍵字可用來建立 Windows 電腦的設定，就像 Linux 電腦一樣。 下列步驟說明如何使用 Windows PowerShell 建立 Linux 電腦的設定文件。

1. 匯入 nx 模組。 Nx Windows PowerShell 模組包含 DSC for Linux 內建資源的結構描述，並且必須安裝到本機電腦，然後匯入設定中。

    若要安裝 nx 模組，請將 nx 模組目錄複製到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 或 `$PSHOME\Modules`。 nx 模組包含在 DSC for Linux 安裝套件 (MSI) 中。 若要在您的設定中匯入 nx 模組，請使用 __Import-DSCResource__ 命令：
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. 定義設定，然後產生設定文件：

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### 將設定推送至 Linux 電腦

設定文件 (MOF 檔案) 可以使用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 推送至 Linux 電腦。 為了從遠端對 Linux 電腦使用這個 Cmdlet，以及 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379).aspx, 或 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) Cmdlet，您必須使用 CIMSession。 [New-CimSession](https://technet.microsoft.com/en-us/library/jj590760.aspx) Cmdlet 用來建立 Linux 電腦的 CIMSession。

下列程式碼示範如何建立 DSC for Linux 的 CIMSession。

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> **注意**：
* 在「推送」模式中，使用者認證必須是在 Linux 電腦上的根使用者。
* DSC for Linux 僅支援 SSL/TLS 連線，必須使用 New-CimSession 且將 –UseSSL 參數設為 $true。
* OMI (DSC) 所使用的 SSL 憑證在此檔案中指定：`/opt/omi/etc/omiserver.conf`，屬性為：pemfile 和 keyfile。
如果此憑證不受您正在執行 [New-CimSession](https://technet.microsoft.com/en-us/library/jj590760.aspx) Cmdlet 的 Windows 電腦信任，您可以使用 CIMSession 選項：`-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true` 選擇忽略憑證驗證

執行下列命令，將 DSC 設定推送至 Linux 節點。

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### 以提取伺服器散發設定

可以用提取伺服器來散發設定給 Linux 電腦，就像 Windows 電腦一樣。 如需使用提取伺服器的指引，請參閱 [Windows PowerShell 預期狀態設定提取伺服器](pullServer.md)。 如需使用提取伺服器與 Linux 電腦的其他資訊與限制，請參閱 Linux 的預期狀態設定版本資訊。

### 在本機使用設定

DSC for Linux 包含指令碼以使用本機 Linux 電腦的設定。 這些指令碼位於 `/opt/microsoft/dsc/Scripts` 並且包含下列項目：
* GetDscConfiguration.py

 傳回套用到此電腦的目前設定。 類似於 Windows PowerShell Cmdlet 的 Get-DscConfiguration Cmdlet。

`# sudo ./GetDscConfiguration.py`

* GetDscLocalConfigurationManager.py

 傳回套用到此電腦的目前中繼設定。 類似於 [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) Cmdlet。

`# sudo ./GetDscLocalConfigurationManager.py`

* InstallModule.py

 安裝自訂 DSC 資源模組。 需要包含模組共用物件的程式庫和結構描述 MOF 檔案的 .zip 檔案路徑。

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 移除自訂的 DSC 資源模組。 需要有要移除的模組名稱。

`# sudo ./RemoveModule.py cnx_Resource`

* StartDscLocalConfigurationManager.py 

 將設定 MOF 檔案套用至電腦。 類似於 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet。 需要有要套用的設定 MOF 路徑。

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* SetDscLocalConfigurationManager.py

 將中繼設定 MOF 檔案套用至電腦。 類似於 [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) Cmdlet。 需要有要套用的中繼設定 MOF 路徑。

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## Linux 記錄檔的 PowerShell 預期狀態設定

會對 DSC for Linux 訊息產生下列記錄檔。

|記錄檔|Directory|描述|
|---|---|---|
|omiserver.log|/opt/omi/var/log/|OMI CIM 伺服器作業相關的訊息。|
|dsc.log|/opt/omi/var/log/|與本機設定管理員 (LCM) 和 DSC 資源作業的作業相關的訊息。|


<!--HONumber=Apr16_HO2-->


