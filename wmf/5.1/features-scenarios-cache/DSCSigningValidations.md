---
title: "DSC 模組和設定簽署驗證"
author: jaimeo
contributor: berheabra
translationtype: Human Translation
ms.sourcegitcommit: 5c97ca6e93d31aaffc7e2207facc7658ee36dfb4
ms.openlocfilehash: 817fadb79716e41ce8cc8f4245dedc66347ac413

---

##DSC 模組和設定簽署驗證
在 DSC 中，設定文件和模組會從提取伺服器散發到受管理電腦 (在 Azure 自動化提取服務的情況下)。 如果提取伺服器/服務遭到入侵，攻擊者可以修改提取伺服器上的設定和模組，將其散發到所有受管理電腦，甚至因而會危害客戶的更多電腦。 

 此威脅在 WMF 5.1 中已解決。 DSC 支援驗證模組和設定 (.MOF) 檔案上的數位簽章。 這項功能會防止節點執行未經受信任簽署者簽署的設定或模組檔案，或經受信任簽署者簽署後遭竄改的模組檔案。 



###如何簽署設定和模組 
***
1. 設定檔 (.MOFS)：現有的 PowerShell Cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) 已擴充，可支援簽署 MOF 檔案。  
2. 模組：已透過簽署對應的模組類別目錄完成模組簽署，使用步驟如下： 
    * 建立類別目錄檔案︰類別目錄檔案包含密碼編譯雜湊或指紋的集合。 每個指紋都會對應至模組所包含的檔案。  已加入新的 [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) Cmdlet，讓使用者為其模組建立類別目錄檔案。 請參閱類別目錄 Cmdlet [相對連結](catalog-cmdlets.md)來建立類別目錄檔案。 
    * 簽署類別目錄檔案︰使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) 簽署類別目錄檔案。
    * 將類別目錄檔案放在模組資料夾內。
依照慣例，模組類別目錄檔案應該位於與模組同名的模組資料夾內。

###啟用簽署驗證的 LocalConfigurationManager 設定。

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
* 驗證設定檔 (.MOF) 的簽章是否有效。 它會使用 5.1 中已擴充的 PowerShell Cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx)，以支援 MOF 簽章驗證。
* 驗證授權簽署者的憑證授權單位是否受信任。
* 將設定的模組/資源相依性下載至暫存位置。
* 驗證模組內是否包含類別目錄簽章。
    * 尋找 <moduleName>.cat 檔案，並使用 [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) Cmdlet 驗證其簽章。
    * 驗證授權簽署者的憑證授權單位是否受信任。
    * 使用新的 [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) Cmdlet 來驗證模組內容是否未經竄改。
* 將模組安裝到 $env:ProgramFiles\WindowsPowerShell\Modules\
* 處理設定。

注意︰只有第一次在系統上套用設定時，或下載並安裝模組時，才會執行模組類別目錄和設定上的簽章驗證。 一致性執行不會驗證 Current.mof 或其模組相依性的簽章。
如果驗證在任何階段失敗，例如從提取伺服器提取的設定未經簽署，則會終止處理設定並顯示下列錯誤，以及刪除所有暫存檔案。

![錯誤輸出設定範例](../../images/PullUnsignedConfigFail.PNG)

同樣地，提取未簽署類別目錄的模組會產生下列錯誤：

![錯誤輸出模組範例](../../images/PullUnisgnedCatalog.PNG)

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
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.PNG)

* 使用程式碼簽署憑證簽署設定檔。

![SignMofFile](../../images/SignMofFile.PNG)

* 嘗試推入簽署的 MOF 檔案。

![SignMofFile](../../images/PushSignedMof.PNG)




<!--HONumber=Aug16_HO3-->


