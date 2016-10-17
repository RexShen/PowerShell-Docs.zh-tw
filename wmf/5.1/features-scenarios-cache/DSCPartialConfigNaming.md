---
title: "提取命名慣例的部分設定"
author: jaimeo
contributor: berheabrha
translationtype: Human Translation
ms.sourcegitcommit: dfa487a11528e26faf5b0e8637b75983abe0b1c8
ms.openlocfilehash: 368c26766961e760fd2de8c99057121bea076158

---

##提取命名慣例的部分設定
在舊版中，提取伺服器/服務的部分設定命名慣例 mof 檔案名稱，應該符合本機設定管理員設定中指定的部分設定名稱，該本機設定管理員設定必須依次比對 MOF 檔案中內嵌的設定名稱。 請參閱下列快照集：•   本機組態設定，定義允許接收節點的部分設定。

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

Azure 自動化服務名稱以前產生的 mof 檔案為 ``<ConfigurationName>.<NodeName>.mof``。 所以下面的設定會編譯為 PartialOne.Localhost.mof。  
如此即不可能從 Azure 自動化服務提取部分設定。

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

在 WMF 5.1 中，提取伺服器/服務中的部分設定可以命名為 ``<ConfigurationName>.<NodeName>.mof``。 但若電腦從提取伺服器/服務中提取單一設定，則提取伺服器設定存放庫上的設定文件可以有任意名稱。 這項命名彈性會使用 onprem 和 Azure 自動化提取服務來管理節點的部分設定。 例如，您可以有在本機提取的「基本」部分設定，以及另一個從 Azure 自動化服務提取的部分設定。

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





<!--HONumber=Aug16_HO3-->


