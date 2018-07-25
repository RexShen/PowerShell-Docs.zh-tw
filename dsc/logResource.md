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
# <a name="dsc-log-resource"></a><span data-ttu-id="5a28c-103">DSC 記錄檔資源</span><span class="sxs-lookup"><span data-stu-id="5a28c-103">DSC Log Resource</span></span>

> <span data-ttu-id="5a28c-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5a28c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5a28c-105">Windows PowerShell 預期狀態設定 (DSC) 的 __Log__ 資源會提供一個機制，將訊息寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5a28c-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="5a28c-106">根據預設只會啟用 DSC 的作業記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5a28c-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="5a28c-107">必須先啟用分析記錄檔，才可加以使用或顯示。</span><span class="sxs-lookup"><span data-stu-id="5a28c-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="5a28c-108">如需詳細資訊，請參閱 [DSC 事件記錄檔在哪裡？](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)。</span><span class="sxs-lookup"><span data-stu-id="5a28c-108">For more information, see [Where are DSC Event Logs?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="5a28c-109">Properties</span><span class="sxs-lookup"><span data-stu-id="5a28c-109">Properties</span></span>

|  <span data-ttu-id="5a28c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5a28c-110">Property</span></span>  |  <span data-ttu-id="5a28c-111">描述</span><span class="sxs-lookup"><span data-stu-id="5a28c-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="5a28c-112">訊息</span><span class="sxs-lookup"><span data-stu-id="5a28c-112">Message</span></span>| <span data-ttu-id="5a28c-113">表示要寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔的訊息。</span><span class="sxs-lookup"><span data-stu-id="5a28c-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="5a28c-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5a28c-114">DependsOn</span></span> | <span data-ttu-id="5a28c-115">表示必須先執行另一個資源的設定，再寫入這個登入訊息。</span><span class="sxs-lookup"><span data-stu-id="5a28c-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="5a28c-116">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = '[ResourceType]ResourceName'`。</span><span class="sxs-lookup"><span data-stu-id="5a28c-116">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="5a28c-117">範例</span><span class="sxs-lookup"><span data-stu-id="5a28c-117">Example</span></span>

<span data-ttu-id="5a28c-118">下列範例示範如何將訊息加入 Microsoft Windows 預期狀態設定/分析事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="5a28c-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="5a28c-119">如果您在設定此資源的情況下執行 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)，則一律會傳回 **$false**。</span><span class="sxs-lookup"><span data-stu-id="5a28c-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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