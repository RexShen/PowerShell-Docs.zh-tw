---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203524"
---
# <span data-ttu-id="a6d84-103">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="a6d84-103">Restore-Computer</span></span>

## <span data-ttu-id="a6d84-104">概要</span><span class="sxs-lookup"><span data-stu-id="a6d84-104">SYNOPSIS</span></span>
<span data-ttu-id="a6d84-105">在本機電腦上啟動系統還原。</span><span class="sxs-lookup"><span data-stu-id="a6d84-105">Starts a system restore on the local computer.</span></span>

## <span data-ttu-id="a6d84-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a6d84-106">SYNTAX</span></span>

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a6d84-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a6d84-107">DESCRIPTION</span></span>
<span data-ttu-id="a6d84-108">**Restore-Computer** Cmdlet 會將本機電腦還原到指定的系統還原點。</span><span class="sxs-lookup"><span data-stu-id="a6d84-108">The **Restore-Computer** cmdlet restores the local computer to the specified system restore point.</span></span>

<span data-ttu-id="a6d84-109">**Restore-Computer** 會重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="a6d84-109">**Restore-Computer** restarts the computer.</span></span>
<span data-ttu-id="a6d84-110">還原會在重新啟動操作期間完成。</span><span class="sxs-lookup"><span data-stu-id="a6d84-110">The restore is completed during the restart operation.</span></span>

<span data-ttu-id="a6d84-111">只有用戶端作業系統 (如 Windows 7、Windows Vista 和 Windows XP) 才支援系統還原點和 **Restore-Computer** 。</span><span class="sxs-lookup"><span data-stu-id="a6d84-111">System restore points and **Restore-Computer** are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="a6d84-112">範例</span><span class="sxs-lookup"><span data-stu-id="a6d84-112">EXAMPLES</span></span>

### <span data-ttu-id="a6d84-113">範例 1︰還原本機電腦</span><span class="sxs-lookup"><span data-stu-id="a6d84-113">Example 1: Restore the local computer</span></span>

```
PS C:\> Restore-Computer -RestorePoint 253
```

<span data-ttu-id="a6d84-114">此命令將本機電腦還原到序號為 253 的還原點。</span><span class="sxs-lookup"><span data-stu-id="a6d84-114">This command restores the local computer to the restore point that has sequence number 253.</span></span>

### <span data-ttu-id="a6d84-115">範例 2︰透過確認還原本機電腦</span><span class="sxs-lookup"><span data-stu-id="a6d84-115">Example 2: Restore the local computer with confirmation</span></span>

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="a6d84-116">此命令將本機電腦還原到序號為 255 的還原點。</span><span class="sxs-lookup"><span data-stu-id="a6d84-116">This command restores the local computer to the restore point that has sequence number 255.</span></span>
<span data-ttu-id="a6d84-117">它使用 *Confirm* 參數以在實際執行操作之前先提示使用者。</span><span class="sxs-lookup"><span data-stu-id="a6d84-117">It uses the *Confirm* parameter to prompt the user before actually performing the operation.</span></span>

### <span data-ttu-id="a6d84-118">範例 3︰ 還原電腦並檢查狀態</span><span class="sxs-lookup"><span data-stu-id="a6d84-118">Example 3: Restore a computer and check the status</span></span>

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

<span data-ttu-id="a6d84-119">這些命令執行系統還原，然後檢查其狀態。</span><span class="sxs-lookup"><span data-stu-id="a6d84-119">These commands run a system restore and then check its status.</span></span>

<span data-ttu-id="a6d84-120">第一個命令使用 **Get-ComputerRestorePoint** 取得本機電腦上的還原點。</span><span class="sxs-lookup"><span data-stu-id="a6d84-120">The first command uses **Get-ComputerRestorePoint** to get the restore points on the local computer.</span></span>

<span data-ttu-id="a6d84-121">第二個命令將電腦還原到序號為 255 的還原點。</span><span class="sxs-lookup"><span data-stu-id="a6d84-121">The second command restores the computer to the restore point with sequence number 255.</span></span>

<span data-ttu-id="a6d84-122">第三個命令使用 *Get-ComputerRestorePoint* Cmdlet 的 *LastStatus* 參數檢查還原操作的狀態。</span><span class="sxs-lookup"><span data-stu-id="a6d84-122">The third command uses the *LastStatus* parameter of *Get-ComputerRestorePoint* cmdlet to check the status of the restore operation.</span></span>
<span data-ttu-id="a6d84-123">由於 **Restore-Computer** 會強制重新啟動，因此在電腦重新啟動後會輸入這個命令。</span><span class="sxs-lookup"><span data-stu-id="a6d84-123">Because **Restore-Computer** forces a restart, this command would be entered after the computer restarts.</span></span>

## <span data-ttu-id="a6d84-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a6d84-124">PARAMETERS</span></span>

### <span data-ttu-id="a6d84-125">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="a6d84-125">-RestorePoint</span></span>
<span data-ttu-id="a6d84-126">指定還原點的序號。</span><span class="sxs-lookup"><span data-stu-id="a6d84-126">Specifies the sequence number of the restore point.</span></span>
<span data-ttu-id="a6d84-127">若要尋找序號，請使用 Get-ComputerRestorePoint Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a6d84-127">To find the sequence number, use the Get-ComputerRestorePoint cmdlet.</span></span>
<span data-ttu-id="a6d84-128">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="a6d84-128">This parameter is required.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6d84-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a6d84-129">-Confirm</span></span>
<span data-ttu-id="a6d84-130">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a6d84-130">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6d84-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a6d84-131">-WhatIf</span></span>
<span data-ttu-id="a6d84-132">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a6d84-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a6d84-133">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a6d84-133">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6d84-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6d84-134">CommonParameters</span></span>
<span data-ttu-id="a6d84-135">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a6d84-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a6d84-136">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a6d84-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a6d84-137">輸入</span><span class="sxs-lookup"><span data-stu-id="a6d84-137">INPUTS</span></span>

### <span data-ttu-id="a6d84-138">無</span><span class="sxs-lookup"><span data-stu-id="a6d84-138">None</span></span>
<span data-ttu-id="a6d84-139">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a6d84-139">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a6d84-140">輸出</span><span class="sxs-lookup"><span data-stu-id="a6d84-140">OUTPUTS</span></span>

### <span data-ttu-id="a6d84-141">無</span><span class="sxs-lookup"><span data-stu-id="a6d84-141">None</span></span>
<span data-ttu-id="a6d84-142">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a6d84-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a6d84-143">注意</span><span class="sxs-lookup"><span data-stu-id="a6d84-143">NOTES</span></span>

* <span data-ttu-id="a6d84-144">若要在 Windows Vista 和更新版本的 Windows 作業系統上執行 Restore-Computer 命令，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a6d84-144">To run a Restore-Computer command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="a6d84-145">此 Cmdlet 會使用 Windows Management Instrumentation (WMI) **SystemRestore** 類別。</span><span class="sxs-lookup"><span data-stu-id="a6d84-145">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

## <span data-ttu-id="a6d84-146">相關連結</span><span class="sxs-lookup"><span data-stu-id="a6d84-146">RELATED LINKS</span></span>

[<span data-ttu-id="a6d84-147">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="a6d84-147">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="a6d84-148">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="a6d84-148">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="a6d84-149">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="a6d84-149">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="a6d84-150">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="a6d84-150">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="a6d84-151">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="a6d84-151">Restart-Computer</span></span>](Restart-Computer.md)
