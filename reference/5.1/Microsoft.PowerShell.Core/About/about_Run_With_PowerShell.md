---
description: 說明如何使用「使用 PowerShell 執行」功能，從檔案系統磁片磁碟機執行腳本。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 28eb4b6d7419ffa52ce205cfea8521bf51e9021f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207563"
---
# <a name="about-run-with-powershell"></a><span data-ttu-id="e1e63-104">關於使用 PowerShell 執行</span><span class="sxs-lookup"><span data-stu-id="e1e63-104">About Run With PowerShell</span></span>

## <a name="short-description"></a><span data-ttu-id="e1e63-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="e1e63-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="e1e63-106">說明如何使用「使用 PowerShell 執行」功能，從檔案系統磁片磁碟機執行腳本。</span><span class="sxs-lookup"><span data-stu-id="e1e63-106">Explains how to use the "Run with PowerShell" feature to run a script from a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="e1e63-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="e1e63-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e1e63-108">從 Windows PowerShell 3.0 開始，您可以使用「使用 PowerShell 執行」功能，從 Windows 8 和 Windows Server 2012 中的檔案總管，以及舊版 Windows 中的 Windows 檔案總管執行腳本。</span><span class="sxs-lookup"><span data-stu-id="e1e63-108">Beginning in Windows PowerShell 3.0, you can use the "Run with PowerShell" feature to run scripts from File Explorer in Windows 8 and Windows Server 2012 and from Windows Explorer in earlier versions of Windows.</span></span>

<span data-ttu-id="e1e63-109">「使用 PowerShell 執行」功能的設計目的是要執行沒有必要參數的腳本，而不會將輸出傳回命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e1e63-109">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="e1e63-110">當您使用「使用 PowerShell 執行」功能時，只會短暫顯示 Windows PowerShell 主控台視窗（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="e1e63-110">When you use the "Run with PowerShell" feature, the Windows PowerShell console window appears only briefly, if at all.</span></span> <span data-ttu-id="e1e63-111">您無法與其互動。</span><span class="sxs-lookup"><span data-stu-id="e1e63-111">You cannot interact with it.</span></span>

<span data-ttu-id="e1e63-112">若要使用「使用 PowerShell 執行」功能：</span><span class="sxs-lookup"><span data-stu-id="e1e63-112">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="e1e63-113">在檔案總管 (或 Windows 檔案總管) 的指令檔名上按一下滑鼠右鍵，然後選取 [使用 PowerShell 執行]。</span><span class="sxs-lookup"><span data-stu-id="e1e63-113">In File Explorer (or Windows Explorer), right-click the script file name and then select "Run with PowerShell".</span></span>

<span data-ttu-id="e1e63-114">[以 PowerShell 執行] 功能會啟動具有 [略過] 執行原則的 Windows PowerShell 會話，並執行腳本，並關閉會話。</span><span class="sxs-lookup"><span data-stu-id="e1e63-114">The "Run with PowerShell" feature starts a Windows PowerShell session that has an execution policy of Bypass, runs the script, and closes the session.</span></span>

<span data-ttu-id="e1e63-115">它會執行具有下列格式的命令：</span><span class="sxs-lookup"><span data-stu-id="e1e63-115">It runs a command that has the following format:</span></span>

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

<span data-ttu-id="e1e63-116">「使用 PowerShell 執行」會針對會話 (設定腳本執行) 的目前 PowerShell 進程實例的略過執行原則。</span><span class="sxs-lookup"><span data-stu-id="e1e63-116">"Run with PowerShell" sets the Bypass execution policy only for the session (the current instance of the PowerShell process) in which the script runs.</span></span>
<span data-ttu-id="e1e63-117">這項功能不會變更電腦或使用者的執行原則。</span><span class="sxs-lookup"><span data-stu-id="e1e63-117">This feature does not change the execution policy for the computer or the user.</span></span>

<span data-ttu-id="e1e63-118">只有 AllSigned 執行原則會影響「使用 PowerShell 執行」功能。</span><span class="sxs-lookup"><span data-stu-id="e1e63-118">The "Run with PowerShell" feature is affected only by the AllSigned execution policy.</span></span> <span data-ttu-id="e1e63-119">如果電腦或使用者的 AllSigned 執行原則是有效的，「使用 PowerShell 執行」就只會執行已簽署的腳本。</span><span class="sxs-lookup"><span data-stu-id="e1e63-119">If the AllSigned execution policy is effective for the computer or the user, "Run with PowerShell" runs only signed scripts.</span></span> <span data-ttu-id="e1e63-120">「使用 PowerShell 執行」不會受到任何其他執行原則的影響。</span><span class="sxs-lookup"><span data-stu-id="e1e63-120">"Run with PowerShell" is not affected by any other execution policy.</span></span> <span data-ttu-id="e1e63-121">如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="e1e63-121">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="e1e63-122">疑難排解注意事項：以 PowerShell 執行命令可能會提示您確認執行原則變更。</span><span class="sxs-lookup"><span data-stu-id="e1e63-122">Troubleshooting Note: Run with PowerShell command might prompt you to confirm the execution policy change.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1e63-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1e63-123">SEE ALSO</span></span>

[<span data-ttu-id="e1e63-124">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="e1e63-124">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="e1e63-125">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="e1e63-125">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="e1e63-126">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="e1e63-126">about_Scripts</span></span>](about_Scripts.md)
