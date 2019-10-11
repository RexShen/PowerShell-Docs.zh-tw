---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC 記錄檔資源
ms.openlocfilehash: a1b7bf44fbaf36a3adaf0666e9f0a754fa3f6ee1
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954665"
---
# <a name="dsc-log-resource"></a>DSC 記錄檔資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **Log** 資源會提供一個機制，將訊息寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔。

## <a name="syntax"></a>語法

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> 根據預設只會啟用 DSC 的作業記錄檔。 必須先啟用分析記錄檔，才可加以使用或顯示。 如需詳細資訊，請參閱 [DSC 事件記錄檔在哪裡？](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs)。

## <a name="properties"></a>Properties

|屬性 |描述 |
|---|---|
|訊息 |表示要寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔的訊息。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

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