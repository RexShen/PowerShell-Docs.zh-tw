---
title: "DSC WindowsFeature 資源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 522dbea958a60f76e98abe32e11e6491ea6d457c

---

# DSC WindowsFeature 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsFeature** 資源提供一個機制，確保可在目標節點上新增或移除角色和功能。

## 語法

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## [內容]

|  屬性  |  描述   | 
|---|---| 
| 名稱| 表示您想要確保新增或移除的角色或功能名稱。 這與來自 [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) Cmdlet 的 __Name__ 屬性相同，不是角色或功能的顯示名稱。| 
| 認證| 表示要用以新增或移除角色或功能的認證。| 
| Ensure| 表示角色或功能是否新增。 若要確保新增角色或功能，這個屬性請設為 "Present"。若要確保移除角色或功能，請將屬性設定為 "Absent"。| 
| IncludeAllSubFeature| 這個屬性設為 __$true__ 可讓您使用以 __Name__ 屬性指定的功能狀態來確保所有必要子功能的狀態。| 
| LogPath| 表示要讓資源提供者記錄作業的記錄檔路徑。| 
| DependsOn| 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 
| 來源| 如有必要，表示用於安裝的來源檔案位置。| 

## 範例
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```




<!--HONumber=Jun16_HO4-->


