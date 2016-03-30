# 設定 DSC Web 提取伺服器

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

DSC Web 提取伺服器是一種 Web 服務，在目標節點請求 DSC 設定檔時，可使用 OData 介面將 DSC 設定檔提供給這些目標節點。

使用提取伺服器的需求：

* 伺服器需執行：
  - WMF/PowerShell 4.0 或更新版本
  - IIS 伺服器角色
  - DSC 服務
* 在理想情況下，某些用來保護憑證的憑證產生方式，可傳遞到在目標節點的本機設定管理員 (LCM)。

您可以使用 [伺服器管理員] 中的 [新增角色及功能精靈]，或使用 PowerShell 新增 IIS 伺服器角色與 DSC 服務。 本主題中所包含的範例指令碼也將為您處理這兩個步驟。

## 使用 xWebService 資源
設定 Web 提取伺服器的最簡單方式，是使用包含在 xPSDesiredStateConfiguration 模組的 xWebService 資源。 下列步驟說明如何使用設定 Web 服務之設定中的資源。

1. 呼叫 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) Cmdlet 以安裝 **xPSDesiredStateConfiguration** 模組。 **注意**：**Install-Module** 已納入 **PowerShellGet** 模組，其隨附於 PowerShell 5.0。 您可以在 [PackageManagement PowerShell 模組預覽](https://www.microsoft.com/en-us/download/details.aspx?id=49186)下載 PowerShell 3.0 和 4.0 的 **PowerShellGet** 模組。 
1. 在 `CERT:\LocalMachine\MY\` 存放區建立主體為 `"CN=PSDSCPullServerCert"` 的自我簽署憑證。 您可以使用命令 `New-SelfSignedCertificate  -CertStoreLocation 'CERT:\LocalMachine\MY' -DnsName "PSDSCPullServerCert"` 進行這項作業。
1. 在 PowerShell ISE 中，啟動 (F5) 下列設定指令碼 (包含於 **xPSDesiredStateConfiguration** 模組的 Example 資料夾的 Sample_xDscWebService.ps1)。 此指令碼會設定提取伺服器和更新狀態伺服器。
  
```powershell
configuration Sample_xDscWebService 
6 { 
7     param  
8     ( 
9         [string[]]$NodeName = 'localhost', 
10 
 
11         [ValidateNotNullOrEmpty()] 
12         [string] $certificateThumbPrint 
13     ) 
14 
 
15     Import-DSCResource -ModuleName xPSDesiredStateConfiguration 
16 
 
17     Node $NodeName 
18     { 
19         WindowsFeature DSCServiceFeature 
20         { 
21             Ensure = "Present" 
22             Name   = "DSC-Service"             
23         } 
24 
 
25         xDscWebService PSDSCPullServer 
26         { 
27             Ensure                  = "Present" 
28             EndpointName            = "PSDSCPullServer" 
29             Port                    = 8080 
30             PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer" 
31             CertificateThumbPrint   = $certificateThumbPrint          
32             ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
33             ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"             
34             State                   = "Started" 
35             DependsOn               = "[WindowsFeature]DSCServiceFeature"                         
36         } 
```

1. 執行設定，傳遞您所建立的自我簽署憑證指紋，作為 **certificateThumbPrint** 參數：

```powershell
PS:\>$myCert = Get-ChildItem CERT:\LocalMachine\My | Where-Object {$_.Subject -eq 'CN=PSDSCPullServerCert'}
PS:\>Sample_xDSCService -certificateThumbprint $myCert.Thumbprint 
```

## 註冊金鑰
若要可讓用戶端向伺服器註冊，使其可以使用設定名稱，而非設定識別碼，註冊金鑰 (也就是伺服器和用戶端節點皆已知的 GUID) 必須放在名為 `RegistrationKeys.txt` 的檔案中。 根據預設，此範例所建立的提取伺服器預期該檔案必須位於 `C:\Program Files\WindowsPowerShell\DscService`。 建立文字檔案，其中只有包含註冊金鑰的一行字，然後將此文字檔案儲存在該資料夾中。
> **注意**：PowerShell 4.0 中不支援註冊金鑰。 

## 放置設定和資源
提取伺服器安裝完成之後，在 `$env:PROGRAMFILES\WindowsPowerShell` 底下有一個名為 "DscService" 的新資料夾。 在該資料夾中，有名為 "Modules" 和 "Configuration" 的兩個資料夾。 在 [Modules] 資料夾中，放入節點將從這部伺服器提取之設定所需的任何資源。 在 [Configuration] 資料夾中，放入要由節點提取之任何設定的設定 MOF 檔案。 MOF 檔案的名稱取決於提取用戶端的類型。 下列主題將詳細描述如何設定提取用戶端：

* [使用設定識別碼設定 DSC 提取用戶端](pullClientConfigID.md)
* [使用設定名稱設定 DSC 提取用戶端](pullClientConfigNames.md)
* [部分設定](partialConfigs.md)

## 建立 MOF 總和檢查碼
設定 MOF 檔案需要與總和檢查碼檔案配對，以便目標節點上的 LCM 可驗證設定。 若要建立總和檢查碼，請呼叫 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) Cmdlet。 此 Cmdlet 會使用 **Path** 參數，指定設定 MOF 所在的資料夾。 此 Cmdlet 會建立名為 `ConfigurationMOFName.mof.checksum` 的總和檢查碼檔案，其中 `ConfigurationMOFName` 是設定 MOF 檔案的名稱。 如果在指定的資料夾中有多個設定 MOF 檔案，就會在每個設定資料夾中各建立一個總和檢查碼。

總和檢查碼檔案必須存在於和設定 MOF 檔案相同的目錄中 (預設為 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`)，而且具有相同名稱，附加副檔名為 `.checksum`。

>**注意**：如果您以任何方式變更設定 MOF 檔案，也必須重新建立總和檢查碼檔案。

## 另請參閱
* [Windows PowerShell 預期狀態設定概觀](overview.md)
* [施行設定](enactingConfigurations.md)
* [如何從 DSC 提取伺服器擷取節點資訊](retrieveNodeInfo.md)
<!--HONumber=Mar16_HO1-->
