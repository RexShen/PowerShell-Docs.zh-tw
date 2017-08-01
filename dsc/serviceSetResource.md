---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC ServiceSet 資源"
ms.openlocfilehash: 92fa4a442eb42e89195162b7831f1a96d40b84f5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0


Windows PowerShell 預期狀態設定 (DSC) 的 **ServiceSet** 資源提供了管理目標節點服務的機制。 此資源是為 `Name` 屬性中指定的每項服務呼叫 [Service 資源](serviceResource.md)的[複合資源](authoringResourceComposite.md)。

當您想要將多項服務設定成相同的狀態，請使用此資源。

## <a name="syntax"></a>語法

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>[內容]

|  屬性  |  描述   | 
|---|---| 
| 名稱| 表示服務名稱。 請注意，有時候和顯示名稱不同。 您可以使用 [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) Cmdlet 取得服務清單及其目前狀態。|
| StartupType| 表示服務的啟動類型。 這個屬性所允許的值為：**Automatic**、**Disabled** 和 **Manual**|  
| BuiltInAccount| 表示用於服務的登入帳戶。 這個屬性所允許的值為：**LocalService**、**LocalSystem** 和 **NetworkService**。| 
| State| 表示您要確保的服務狀態：**已停止**或**正在執行**。| 
| Ensure| 表示系統上是否有服務。 請將此屬性設為 **Absent** 以確保服務不存在。 屬性設定為 **Present** (預設值)，可確保目標服務存在。|
| 認證| 表示執行服務資源的帳戶認證。 這個屬性與 **BuiltinAccount** 屬性不能同時使用。| 
| DependsOn| 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 *ResourceName*，而它的類型是 *ResourceType*，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 



## <a name="example"></a>範例

下列設定會啟動「Windows 音訊」和「遠端桌面服務」服務。

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

