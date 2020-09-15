---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC 記錄檔資源
ms.openlocfilehash: bc59bb2670561306a039d024fcff5e0746a659f2
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464021"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="da2c9-103">DSC 記錄檔資源</span><span class="sxs-lookup"><span data-stu-id="da2c9-103">DSC Log Resource</span></span>

> <span data-ttu-id="da2c9-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="da2c9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="da2c9-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Log** 資源會提供一個機制，將訊息寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="da2c9-105">The **Log** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

## <a name="syntax"></a><span data-ttu-id="da2c9-106">語法</span><span class="sxs-lookup"><span data-stu-id="da2c9-106">Syntax</span></span>

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="da2c9-107">根據預設只會啟用 DSC 的作業記錄檔。</span><span class="sxs-lookup"><span data-stu-id="da2c9-107">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="da2c9-108">必須先啟用分析記錄檔，才可加以使用或顯示。</span><span class="sxs-lookup"><span data-stu-id="da2c9-108">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="da2c9-109">如需詳細資訊，請參閱 [DSC 事件記錄檔在哪裡？](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs)。</span><span class="sxs-lookup"><span data-stu-id="da2c9-109">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="da2c9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="da2c9-110">Properties</span></span>

| <span data-ttu-id="da2c9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="da2c9-111">Property</span></span> |                                                   <span data-ttu-id="da2c9-112">描述</span><span class="sxs-lookup"><span data-stu-id="da2c9-112">Description</span></span>                                                    |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="da2c9-113">訊息</span><span class="sxs-lookup"><span data-stu-id="da2c9-113">Message</span></span>  | <span data-ttu-id="da2c9-114">表示要寫入 Microsoft Windows 預期狀態設定/分析事件記錄檔的訊息。</span><span class="sxs-lookup"><span data-stu-id="da2c9-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="da2c9-115">通用屬性</span><span class="sxs-lookup"><span data-stu-id="da2c9-115">Common properties</span></span>

|       <span data-ttu-id="da2c9-116">屬性</span><span class="sxs-lookup"><span data-stu-id="da2c9-116">Property</span></span>       |                                                                                                                                                          <span data-ttu-id="da2c9-117">描述</span><span class="sxs-lookup"><span data-stu-id="da2c9-117">Description</span></span>                                                                                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="da2c9-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="da2c9-118">DependsOn</span></span>            | <span data-ttu-id="da2c9-119">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="da2c9-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="da2c9-120">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="da2c9-120">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
| <span data-ttu-id="da2c9-121">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="da2c9-121">PsDscRunAsCredential</span></span> | <span data-ttu-id="da2c9-122">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="da2c9-122">Sets the credential for running the entire resource as.</span></span>                                                                                                                                                                                                                                                                        |

> [!NOTE]
> <span data-ttu-id="da2c9-123">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="da2c9-123">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="da2c9-124">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="da2c9-124">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="da2c9-125">範例</span><span class="sxs-lookup"><span data-stu-id="da2c9-125">Example</span></span>

<span data-ttu-id="da2c9-126">下列範例示範如何將訊息加入 Microsoft Windows 預期狀態設定/分析事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="da2c9-126">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="da2c9-127">如果您在設定此資源的情況下執行 [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration?view=powershell-5.1)，則一律會傳回 **$false**。</span><span class="sxs-lookup"><span data-stu-id="da2c9-127">If you run [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration?view=powershell-5.1) with this resource configured, it will always return **$false**.</span></span>

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
