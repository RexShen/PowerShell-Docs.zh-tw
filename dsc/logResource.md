---
title: "DSC 記錄檔資源"
ms.date: 2016-05-16
keywords: "PowerShell，DSC"
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: fe905237f5f0672f6e5e0cd399e1b71058417d9c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-log-resource"></a>DSC 記錄檔資源 

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的 __Log__ 資源會提供一個機制，將訊息寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔。

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

注意︰根據預設只會啟用 DSC 的作業記錄檔。
必須先啟用分析記錄檔，才可加以使用或顯示。
請參閱以下文章。

[DSC 事件記錄檔在哪裡？](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>[內容]
|  屬性  |  描述   | 
|---|---| 
| 訊息| 表示要寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔的訊息。| 
| DependsOn | 表示必須先執行另一個資源的設定，再寫入這個登入訊息。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## <a name="example"></a>範例

下列範例示範如何將訊息加入 Microsoft Windows 預期狀態設定/分析事件記錄檔中。

> **注意**：如果您在設定此資源的情況下執行 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)，它一律會傳回 **$false**。

```powershell 
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```

