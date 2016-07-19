---
title: "DSC WindowsFeatureSet 資源"
ms.date: 2016-05-24
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: df6869cdf1d1f6c823704e4de2882e90cb672ad2

---

# DSC WindowsFeatureSet 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsFeatureSet** 資源提供一個機制，確保可在目標節點上新增或移除角色和功能。
此資源是為 `Name` 屬性中指定的每項功能呼叫 [WindowsFeature 資源](windowsfeatureResource.md)的[複合資源](authoringResourceComposite.md)。

當您想要將多個 Windows 功能設定成相同的狀態，請使用此資源。

## 語法

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]] 
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## [內容]

|  屬性  |  描述   | 
|---|---| 
| 名稱| 您想要確保新增或移除的角色或功能名稱。 這與 [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) Cmdlet 的 **Name** 屬性相同，且不是角色或功能的顯示名稱。| 
| 認證| 用以新增或移除角色或功能的認證。| 
| Ensure| 表示是否已新增角色或功能。 若要確保新增角色或功能，這個屬性請設為 "Present"。若要確保移除角色或功能，請將屬性設定為 "Absent"。| 
| IncludeAllSubFeature| 這個屬性設為 **$true** 可讓您使用以 **Name** 屬性指定的功能包含所有必要的子功能。| 
| LogPath| 要讓資源提供者記錄作業的記錄檔路徑。| 
| DependsOn| 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 
| 來源| 如有必要，表示用於安裝的來源檔案位置。| 

## 範例

下列設定可確保安裝 **Web 伺服器** (IIS) 和 **SMTP 伺服器**功能及其各自的所有子功能。

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        } 
    }
}
```




<!--HONumber=Jul16_HO1-->


