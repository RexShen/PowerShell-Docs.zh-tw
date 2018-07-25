---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 記錄檔資源
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093471"
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

> [!NOTE]
> 根據預設只會啟用 DSC 的作業記錄檔。 必須先啟用分析記錄檔，才可加以使用或顯示。 如需詳細資訊，請參閱 [DSC 事件記錄檔在哪裡？](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)。

## <a name="properties"></a>Properties

|  屬性  |  描述   |
|---|---|
| 訊息| 表示要寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔的訊息。|
| DependsOn | 表示必須先執行另一個資源的設定，再寫入這個登入訊息。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = '[ResourceType]ResourceName'`。|

## <a name="example"></a>範例

下列範例示範如何將訊息加入 Microsoft Windows 預期狀態設定/分析事件記錄檔中。

> [!NOTE]
> 如果您在設定此資源的情況下執行 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)，則一律會傳回 **$false**。

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```