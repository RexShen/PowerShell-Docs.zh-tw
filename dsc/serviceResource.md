---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC Service 資源"
ms.openlocfilehash: 611729e5d971ebaf15ac947454cffadc6797927b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a id="dsc-service-resource" class="xliff"></a>
# DSC Service 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0


Windows PowerShell 預期狀態設定 (DSC) 的 **Service** 資源提供了管理目標節點服務的機制。

<a id="syntax" class="xliff"></a>
## 語法

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

<a id="properties" class="xliff"></a>
## [內容]

|  屬性  |  描述   | 
|---|---| 
| 名稱| 表示服務名稱。 請注意，有時候和顯示名稱不同。 您可以使用 Get-Service Cmdlet 取得服務清單及其目前狀態。| 
| BuiltInAccount| 表示用於服務的登入帳戶。 這個屬性所允許的值為：**LocalService**、**LocalSystem** 和 **NetworkService**。| 
| 認證| 表示執行服務的帳戶認證。 這個屬性與 __BuiltinAccount__ 屬性不能同時使用。| 
| DependsOn| 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 
| StartupType| 表示服務的啟動類型。 這個屬性所允許的值為：**Automatic**、**Disabled** 和 **Manual**| 
| State| 表示您要確保的服務狀態。| 
| 描述 | 表示目標服務的描述。| 
| DisplayName | 表示目標服務的顯示名稱。| 
| Ensure | 表示系統上是否有目標服務。 請將此屬性設定為**Absent** 以確保目標服務不存在。 屬性設定為 **Present** (預設值)，可確保目標服務存在。|
| 路徑 | 表示新服務的二進位檔路徑。| 

<a id="example" class="xliff"></a>
## 範例

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

