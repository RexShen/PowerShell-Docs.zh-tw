---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 記錄檔資源
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676602"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="b6e3e-103">DSC 記錄檔資源</span><span class="sxs-lookup"><span data-stu-id="b6e3e-103">DSC Log Resource</span></span>

> <span data-ttu-id="b6e3e-104">_適用於：Windows PowerShell 4.0、Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="b6e3e-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="b6e3e-105">Windows PowerShell 預期狀態設定 (DSC) 的 __Log__ 資源會提供一個機制，將訊息寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b6e3e-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="b6e3e-106">根據預設只會啟用 DSC 的作業記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b6e3e-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="b6e3e-107">必須先啟用分析記錄檔，才可加以使用或顯示。</span><span class="sxs-lookup"><span data-stu-id="b6e3e-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="b6e3e-108">如需詳細資訊，請參閱 [DSC 事件記錄檔在哪裡？](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs)。</span><span class="sxs-lookup"><span data-stu-id="b6e3e-108">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="b6e3e-109">Properties</span><span class="sxs-lookup"><span data-stu-id="b6e3e-109">Properties</span></span>

| <span data-ttu-id="b6e3e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b6e3e-110">Property</span></span> | <span data-ttu-id="b6e3e-111">描述</span><span class="sxs-lookup"><span data-stu-id="b6e3e-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b6e3e-112">訊息</span><span class="sxs-lookup"><span data-stu-id="b6e3e-112">Message</span></span>| <span data-ttu-id="b6e3e-113">表示要寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔的訊息。</span><span class="sxs-lookup"><span data-stu-id="b6e3e-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="b6e3e-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b6e3e-114">DependsOn</span></span> | <span data-ttu-id="b6e3e-115">表示必須先執行另一個資源的設定，再寫入這個登入訊息。</span><span class="sxs-lookup"><span data-stu-id="b6e3e-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="b6e3e-116">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = '[ResourceType]ResourceName'`。</span><span class="sxs-lookup"><span data-stu-id="b6e3e-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="b6e3e-117">範例</span><span class="sxs-lookup"><span data-stu-id="b6e3e-117">Example</span></span>

<span data-ttu-id="b6e3e-118">下列範例示範如何將訊息加入 Microsoft Windows 預期狀態設定/分析事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="b6e3e-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="b6e3e-119">如果您在設定此資源的情況下執行 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)，則一律會傳回 **$false**。</span><span class="sxs-lookup"><span data-stu-id="b6e3e-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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
