---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: 指令碼追蹤和記錄
ms.openlocfilehash: dd18453c041428d5a6537c413c3ebe324a62dfee
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809864"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="a3e43-103">指令碼追蹤和記錄</span><span class="sxs-lookup"><span data-stu-id="a3e43-103">Script Tracing and Logging</span></span>

<span data-ttu-id="a3e43-104">雖然 PowerShell 已有 **LogPipelineExecutionDetails** 群組原則設定會記錄 Cmdlet 的引動過程，但 PowerShell 的指令碼語言仍具備數個您可能想要記錄和稽核的功能。</span><span class="sxs-lookup"><span data-stu-id="a3e43-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="a3e43-105">新的詳細指令碼追蹤功能會在系統上提供 PowerShell 指令碼活動的詳細追蹤和分析。</span><span class="sxs-lookup"><span data-stu-id="a3e43-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="a3e43-106">啟用詳細指令碼追蹤之後，PowerShell 會將所有指令碼區塊記錄於 ETW 事件記錄檔中：**Microsoft-Windows-PowerShell/Operational**。</span><span class="sxs-lookup"><span data-stu-id="a3e43-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="a3e43-107">例如，若指令碼區塊會建立另一個指令碼區塊，則透過呼叫 `Invoke-Expression`，也會記錄叫用的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="a3e43-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="a3e43-108">您可以透過 [打開 PowerShell 指令碼區塊記錄]  群組原則設定 (位於 [系統管理範本]   -> [Windows 元件]   ->  [Windows PowerShell]  ) 來啟用記錄。</span><span class="sxs-lookup"><span data-stu-id="a3e43-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="a3e43-109">這些事件為︰</span><span class="sxs-lookup"><span data-stu-id="a3e43-109">The events are:</span></span>

| <span data-ttu-id="a3e43-110">通路</span><span class="sxs-lookup"><span data-stu-id="a3e43-110">Channel</span></span> |                               <span data-ttu-id="a3e43-111">運作</span><span class="sxs-lookup"><span data-stu-id="a3e43-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="a3e43-112">層級</span><span class="sxs-lookup"><span data-stu-id="a3e43-112">Level</span></span>   | <span data-ttu-id="a3e43-113">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="a3e43-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="a3e43-114">OpCode</span><span class="sxs-lookup"><span data-stu-id="a3e43-114">Opcode</span></span>  | <span data-ttu-id="a3e43-115">建立</span><span class="sxs-lookup"><span data-stu-id="a3e43-115">Create</span></span>                                                                  |
| <span data-ttu-id="a3e43-116">Task</span><span class="sxs-lookup"><span data-stu-id="a3e43-116">Task</span></span>    | <span data-ttu-id="a3e43-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="a3e43-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="a3e43-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a3e43-118">Keyword</span></span> | <span data-ttu-id="a3e43-119">Runspace</span><span class="sxs-lookup"><span data-stu-id="a3e43-119">Runspace</span></span>                                                                |
| <span data-ttu-id="a3e43-120">EventId</span><span class="sxs-lookup"><span data-stu-id="a3e43-120">EventId</span></span> | <span data-ttu-id="a3e43-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="a3e43-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="a3e43-122">訊息</span><span class="sxs-lookup"><span data-stu-id="a3e43-122">Message</span></span> | <span data-ttu-id="a3e43-123">建立指令碼區塊文字 (%2 之 %1)：</span><span class="sxs-lookup"><span data-stu-id="a3e43-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="a3e43-124">%3</span><span class="sxs-lookup"><span data-stu-id="a3e43-124">%3</span></span> </br> <span data-ttu-id="a3e43-125">ScriptBlock 識別碼：%4</span><span class="sxs-lookup"><span data-stu-id="a3e43-125">ScriptBlock ID: %4</span></span> |

<span data-ttu-id="a3e43-126">訊息中的內嵌文字是編譯的指令碼區塊範圍。</span><span class="sxs-lookup"><span data-stu-id="a3e43-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="a3e43-127">識別碼是保留給指令碼區塊存留期的 GUID。</span><span class="sxs-lookup"><span data-stu-id="a3e43-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="a3e43-128">當您啟用詳細資訊記錄時，此功能會寫入開始和結束標記︰</span><span class="sxs-lookup"><span data-stu-id="a3e43-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="a3e43-129">通路</span><span class="sxs-lookup"><span data-stu-id="a3e43-129">Channel</span></span> |                                 <span data-ttu-id="a3e43-130">運作</span><span class="sxs-lookup"><span data-stu-id="a3e43-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="a3e43-131">層級</span><span class="sxs-lookup"><span data-stu-id="a3e43-131">Level</span></span>   | <span data-ttu-id="a3e43-132">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="a3e43-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="a3e43-133">OpCode</span><span class="sxs-lookup"><span data-stu-id="a3e43-133">Opcode</span></span>  | <span data-ttu-id="a3e43-134">Open / Close</span><span class="sxs-lookup"><span data-stu-id="a3e43-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="a3e43-135">Task</span><span class="sxs-lookup"><span data-stu-id="a3e43-135">Task</span></span>    | <span data-ttu-id="a3e43-136">CommandStart / CommandStop</span><span class="sxs-lookup"><span data-stu-id="a3e43-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="a3e43-137">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a3e43-137">Keyword</span></span> | <span data-ttu-id="a3e43-138">Runspace</span><span class="sxs-lookup"><span data-stu-id="a3e43-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="a3e43-139">EventId</span><span class="sxs-lookup"><span data-stu-id="a3e43-139">EventId</span></span> | <span data-ttu-id="a3e43-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="a3e43-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="a3e43-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="a3e43-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="a3e43-142">訊息</span><span class="sxs-lookup"><span data-stu-id="a3e43-142">Message</span></span> | <span data-ttu-id="a3e43-143">已啟動 / 已完成 ScriptBlock 識別碼的引動過程：%1</span><span class="sxs-lookup"><span data-stu-id="a3e43-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="a3e43-144">Runspace 識別碼：%2</span><span class="sxs-lookup"><span data-stu-id="a3e43-144">Runspace ID: %2</span></span> |

<span data-ttu-id="a3e43-145">識別碼是代表指令碼區塊的 GUID (可與事件識別碼 0x1008 相互關聯)，Runspace 識別碼則代表之前執行這個指令碼區塊的 Runspace。</span><span class="sxs-lookup"><span data-stu-id="a3e43-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="a3e43-146">引動過程訊息中的百分比符號代表結構化的 ETW 屬性。</span><span class="sxs-lookup"><span data-stu-id="a3e43-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="a3e43-147">雖以訊息文字中的實際值取代了它們，但更健全的存取方式是以 Get-WinEvent Cmdlet 擷取訊息，然後使用訊息的**屬性**陣列。</span><span class="sxs-lookup"><span data-stu-id="a3e43-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="a3e43-148">下例說明這項功能如何協助解除包裝加密和模糊化指令碼的惡意嘗試：</span><span class="sxs-lookup"><span data-stu-id="a3e43-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="a3e43-149">執行這項功能會產生下列記錄項目︰</span><span class="sxs-lookup"><span data-stu-id="a3e43-149">Running this generates the following log entries:</span></span>

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

如果指令碼區塊長度超過單一事件的容量，PowerShell 就會將指令碼分成多個部分。 <span data-ttu-id="a3e43-151">以下是從其記錄檔訊息重新合併指令碼的範例程式碼：</span><span class="sxs-lookup"><span data-stu-id="a3e43-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="a3e43-152">如同具備有限保留緩衝區的所有記錄系統，攻擊此基礎結構的方式之一是使用假性事件來填滿記錄，以隱藏較早的辨識項。</span><span class="sxs-lookup"><span data-stu-id="a3e43-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="a3e43-153">若要防範這類攻擊，請確定您具有某種形式的事件記錄檔集合，可設定 Windows 事件轉送。</span><span class="sxs-lookup"><span data-stu-id="a3e43-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="a3e43-154">如需詳細資訊，請參閱[使用 Windows 事件記錄檔監視來發掘敵人](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="a3e43-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>
