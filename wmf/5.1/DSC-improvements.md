---
title: "WMF 5.1 (Preview) 的 DSC 改善"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 1f00f2706f3c3ece783590f3a2b0bdb6734402b0

---

#WMF 5.1 的預期狀態設定 (DSC) 改善

## DSC 類別資源改善

WMF 5.1 中已修正下列已知問題︰
* 如果類別型 DSC 資源的 Get() 函式傳回複雜/雜湊表類型，Get-DscConfiguration 可能會傳回空值 (null) 或錯誤。
* 當 DSC 設定使用 RunAs 認證時，Get-DscConfiguration 就會傳回錯誤。
* 類別型資源無法用於複合設定中。
* 如果類別型資源有其本身類型的屬性，Start-DscConfiguration 會停止回應。
* 類別型資源不能用為獨佔資源。


## DSC 資源偵錯改善

在 WMF 5.0 中，PowerShell 偵錯工具並未直接停在類別資源方法 (Get/Set/Test)。
在 WMF 5.1 中，偵錯工具會停在類別資源方法，方式一如 MOF 資源方法。

## DSC 提取用戶端支援 TLS1.1 和 TLS1.2 
DSC 提取用戶端過去只支援 HTTPS 連線的 SSL3.0 和 TLS1.0。 強制使用更安全的通訊協定時，提取用戶端就會停止運作。 在 WMF 5.1 中，DSC 提取用戶端不再支援 SSL 3.0，卻加入了更安全的 TLS 1.1 和 TLS 1.2 通訊協定支援。  

## 改善的提取伺服器登錄 ##

在舊版的 WMF 中，在使用 ESENT 資料庫時，同時登錄/報告 DSC 提取伺服器的要求，會導致 LCM 無法登錄及/或報告。 在這種情況下，提取伺服器的事件記錄檔就會出現「執行個體名稱已在使用中」的錯誤。
這是因為在多執行緒案例中使用不正確的模式存取 ESENT 資料庫。 WMF 5.1 已修正此問題。 WMF 5.1 中可以正常同時登錄或報告 (包含 ESENT 資料庫)。 只有 ESENT 資料庫會發生這個問題，OLEDB 資料庫無此問題。 

##提取命名慣例的部分設定
在舊版中，提取伺服器/服務的部分設定命名慣例 MOF 檔案名稱，應該符合本機設定管理員設定中指定的部分設定名稱，該本機設定管理員設定必須依次比對 MOF 檔案中內嵌的設定名稱。 

請參閱下列快照集：•   本機組態設定，定義允許接收節點的部分設定。

![中繼設定範例](../../images/MetaConfigPartialOne.png)

•   部分設定定義範例 

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

•   內嵌在產生之 MOF 檔案中的 'ConfigurationName'。

![產生的 MOF 檔案範例](../../images/PartialGeneratedMof.png)

•   提取設定存放庫中的檔案名稱 

![設定存放庫中的檔案名稱](../../images/PartialInConfigRepository.png)

Azure 自動化服務名稱以前產生的 MOF 檔案為 <ConfigurationName>.<NodeName>.mof。 所以下面的設定會編譯為 PartialOne.Localhost.mof。

如此即不可能從 Azure 自動化服務提取您其中一項部分設定。

```Powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

在 WMF 5.1 中，提取伺服器/服務中的部分設定可以命名為 <ConfigurationName>.<NodeName>.mof。 但若電腦從提取伺服器/服務中提取了單一設定，則提取伺服器存放庫上的設定檔可以有任意的檔案名稱。 命名彈性可讓您管理 Azure 自動化服務部分管理的節點，其中節點的某些設定來自 Azure 自動化 DSC，且某項部分設定是您曾想在本機管理的。

下面的中繼設定會設定由本機及 Azure 自動化服務來管理節點。

```Powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30;
            RefreshMode = "PULL";            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation Service.
        PartialConfiguration PartialCOnfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   slcm -Path .\RegistrationMetaConfig -Verbose
 ```

# 使用 PsDscRunAsCredential 和 DSC 複合資源   

我們新增了支援以使用 [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) 和 DSC [複合](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite)資源。    

在設定內使用複合資源時，使用者現在可以指定一個 PsDscRunAsCredential 值。 指定後，複合資源內的所有資源都會以 RunAs 使用者身分執行。 如果複合資源呼叫另一項複合資源，也會以 RunAs 使用者身分執行其所有資源。  RunAs 認證會傳播至複合資源階層的所有層級。 如果複合資源內的任何資源指定自己的 PsDscRunAsCredential 值，則設定編譯期間就會發生合併錯誤。

本範例示範如何使用包含在 PSDesiredStateConfiguration 模組內的 [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) 複合資源。 



```powershell

Configuration InstallWindowsFeature     
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features 
        {  
            Name = @("Telnet-Client","SNMP-Service")  
            Ensure = "Present"  
            IncludeAllSubFeature = $true  
            PsDscRunAsCredential = Get-Credential   
        }  
    }

}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}


InstallWindowsFeature -ConfigurationData $configData 

```

##DSC 模組和設定簽署驗證
在 DSC 中，設定和模組會從提取伺服器散發到受管理的電腦。 如果提取伺服器遭到入侵，攻擊者可以修改提取伺服器上的設定和模組，將其散發到所有受管理的節點以危害所有節點。 

 在 WMF 5.1 中，DSC 支援驗證類別目錄和設定 (.MOF) 檔案的數位簽章。 這項功能會防止執行未經受信任簽署者簽署的設定或模組檔案，或經受信任簽署者簽署後遭竄改的檔案。 



###如何簽署設定和模組 
***
* 設定檔 (.MOFS)：現有的 PowerShell Cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) 已擴充，可支援簽署 MOF 檔案。  
* 模組：已透過簽署對應的模組類別目錄完成模組簽署，使用步驟如下： 
    1. 建立類別目錄檔案︰類別目錄檔案包含密碼編譯雜湊或指紋的集合。 每個指紋都會對應至模組所包含的檔案。 已加入新的 [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) Cmdlet，讓使用者為其模組建立類別目錄檔案。
    2. 簽署類別目錄檔案︰使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) 簽署類別目錄檔案。
    3. 將類別目錄檔案放在模組資料夾內。
依照慣例，模組類別目錄檔案應該位於與模組同名的模組資料夾內。

###啟用簽署驗證的 LocalConfigurationManager 設定

####提取
節點的 LocalConfigurationManager 會根據其目前的設定，執行模組和設定的簽署驗證。 預設停用簽章驗證。 將 'SignatureValidation' 區塊加入節點的中繼設定定義可啟用簽章驗證，如下所示：

```PowerShell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'        
    } 
    
    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default,LCM will use default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM will use this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType =  'Configuration','Module'         # Those are list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

在節點上設定上述中繼設定，可在下載的設定和模組上啟用簽章驗證。 本機設定管理員會執行下列步驟來驗證數位簽章。
1. 驗證設定檔 (.MOF) 的簽章是否有效。 它會使用 5.1 中已擴充的 PowerShell Cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx)，以支援 MOF 簽章驗證。
2. 驗證授權簽署者的憑證授權單位是否受信任。
3. 將設定的模組/資源相依性下載至暫存位置。
4. 驗證模組內是否包含類別目錄簽章。
    * 尋找 <moduleName>.cat 檔案，並使用 [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) Cmdlet 驗證其簽章。
    * 驗證授權簽署者的憑證授權單位是否受信任。
    * 驗證是否已使用新的 [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) Cmdlet 來刪減模組內容。
5. 將模組安裝到 $env:ProgramFiles\WindowsPowerShell\Modules\
6. 處理設定

> 注意︰只有第一次在系統上套用設定時，或下載並安裝模組時，才會執行模組類別目錄和設定上的簽章驗證。 一致性執行不會驗證 Current.mof 或其模組相依性的簽章。
如果驗證在任何階段失敗，例如從提取伺服器提取的設定未經簽署，則會終止處理設定並顯示下列錯誤，以及刪除所有暫存檔案。

![錯誤輸出設定範例](../../images/PullUnsignedConfigFail.png)

同樣地，提取未簽署類別目錄的模組會產生下列錯誤：

![錯誤輸出模組範例](../../images/PullUnisgnedCatalog.png)

####推入
透過推入傳遞的設定，可能在傳送到節點之前即已在來源遭到竄改。 本機設定管理員會對已推入或發行的設定，執行類似的簽章驗證步驟。
以下是推入簽章驗證的完整範例。

* 在節點上啟用簽章驗證。

```Powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'        
    } 
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'   
        SignedItemType =  'Configuration','Module'             
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
``` 
* 建立設定檔範例。

```Powershell
# Sample configuration
Configuration Test{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* 嘗試將未經簽署的設定檔推入至節點。 

```Powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.png)

* 使用程式碼簽署憑證簽署設定檔。

![SignMofFile](../../images/SignMofFile.png)

* 嘗試推入簽署的 MOF 檔案。

![SignMofFile](../../images/PushSignedMof.png)




<!--HONumber=Jul16_HO3-->


