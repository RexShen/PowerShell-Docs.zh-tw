---
title: "DSC for Linux nxPackage 資源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 31867cc7af96a3d8d527f5906d77bed5206940b4

---

# DSC for Linux nxPackage 資源

PowerShell 預期狀態設定 (DSC) 的 **nxPackage** 資源會提供一個機制，在 Linux 節點管理套件。

## 語法

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]
    
}
```

## [內容]

|  屬性 |  描述 | 
|---|---|
| 名稱| 您要確保其特定狀態的套件名稱。| 
| Ensure| 決定是否要檢查套件存在。 將此屬性設定為 "Present" 以確保套件存在。 設為 "Absent" 以確保此套件不存在。 預設值為 "Present"。|  
| PackageManager| 支援的值為 "yum"、"apt" 和 "zypper"。 指定安裝套件時所使用的套件管理員。 如果 **FilePath** 已指定，則使用提供的路徑，以安裝套件。 否則，套件管理員將用於從預先設定的儲存機制安裝套件。 如果沒有提供 **PackageManager** 或 **FilePath**，則會使用系統的預設套件管理員。| 
| FilePath| 套件所在的檔案路徑| 
| PackageGroup| 若為 **$true**，則 **Name** 預計會是套件群組的名稱，以搭配 **PackageManager** 群組使用。 **PackageGroup** 在提供 **FilePath** 時無效。| 
| 引數| 將傳遞至套件的引數字串，與所提供者完全相同。| 
| ReturnCode| 預期的傳回碼。 如果實際的傳回碼不符這裡提供的預期值，此設定就會傳回錯誤。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## 範例

下列範例會確保名為 "httpd" 的套件已使用 "Yum" 套件管理員安裝在 Linux 電腦上。

```
Import-DSCResource -Module nx 

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```




<!--HONumber=Jun16_HO4-->


