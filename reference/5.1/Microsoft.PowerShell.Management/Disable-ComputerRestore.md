---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/disable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ComputerRestore
ms.openlocfilehash: 941829c3caa0f6bb2f5712dda9eb7d8c36908062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204035"
---
# <span data-ttu-id="bb463-103">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="bb463-103">Disable-ComputerRestore</span></span>

## <span data-ttu-id="bb463-104">概要</span><span class="sxs-lookup"><span data-stu-id="bb463-104">SYNOPSIS</span></span>
<span data-ttu-id="bb463-105">在指定的檔案系統磁碟機上停用系統還原功能。</span><span class="sxs-lookup"><span data-stu-id="bb463-105">Disables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="bb463-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb463-106">SYNTAX</span></span>

```
Disable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bb463-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bb463-107">DESCRIPTION</span></span>
<span data-ttu-id="bb463-108">**Enable-computerrestore** Cmdlet 會關閉一或多個檔案系統磁片磁碟機上的系統還原功能。</span><span class="sxs-lookup"><span data-stu-id="bb463-108">The **Disable-ComputerRestore** cmdlet turns off the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="bb463-109">因此，嘗試還原電腦不會影響指定的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="bb463-109">As a result, attempts to restore the computer do not affect the specified drive.</span></span>

<span data-ttu-id="bb463-110">如果要在任一磁碟機上停用系統還原，則必須優先或同時在系統磁碟機上將它停用。</span><span class="sxs-lookup"><span data-stu-id="bb463-110">To disable System Restore on any drive, it must be disabled on the system drive, either first or concurrently.</span></span>

<span data-ttu-id="bb463-111">如果要重新啟用系統還原，請使用 Enable-ComputerRestore Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb463-111">To re-enable System Restore, use the Enable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="bb463-112">如果要尋找每個磁碟機的系統還原狀態，請使用 Rstrui.exe。</span><span class="sxs-lookup"><span data-stu-id="bb463-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="bb463-113">只有用戶端作業系統 (如 Windows 7、Windows Vista 和 Windows XP) 才支援系統還原點和 ComputerRestore Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb463-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="bb463-114">範例</span><span class="sxs-lookup"><span data-stu-id="bb463-114">EXAMPLES</span></span>

### <span data-ttu-id="bb463-115">範例1：停用指定磁片磁碟機上的系統還原</span><span class="sxs-lookup"><span data-stu-id="bb463-115">Example 1: Disable System Restore on the specified drive</span></span>

```
PS C:\> Disable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="bb463-116">此命令會停用 C: 磁碟機上的系統還原 。</span><span class="sxs-lookup"><span data-stu-id="bb463-116">This command disables System Restore on the C: drive.</span></span>

### <span data-ttu-id="bb463-117">範例2：停用多個磁片磁碟機上的系統還原</span><span class="sxs-lookup"><span data-stu-id="bb463-117">Example 2: Disable System Restore on multiple drives</span></span>

```
PS C:\> Disable-ComputerRestore "C:\", "D:\"
```

<span data-ttu-id="bb463-118">此命令會停用 C: 和 D: 磁碟機上的系統還原 。</span><span class="sxs-lookup"><span data-stu-id="bb463-118">This command disables System Restore on the C: and D: drives.</span></span>
<span data-ttu-id="bb463-119">此命令會使用 *drive* 參數，但會省略磁片磁碟機參數名稱。</span><span class="sxs-lookup"><span data-stu-id="bb463-119">The command uses the *Drive* parameter, but it omits the Drive parameter name.</span></span>

## <span data-ttu-id="bb463-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb463-120">PARAMETERS</span></span>

### <span data-ttu-id="bb463-121">-Drive</span><span class="sxs-lookup"><span data-stu-id="bb463-121">-Drive</span></span>
<span data-ttu-id="bb463-122">指定檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="bb463-122">Specifies the file system drives.</span></span>
<span data-ttu-id="bb463-123">輸入一或多個檔系統磁碟機號，並在後面加上冒號和反斜線，並以引號括住，例如 C：\或 D:\。</span><span class="sxs-lookup"><span data-stu-id="bb463-123">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="bb463-124">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="bb463-124">This parameter is required.</span></span>

<span data-ttu-id="bb463-125">您無法使用這個 Cmdlet 來停用遠端網路磁碟機上的系統還原，即使該磁碟機對應本機電腦也一樣，也無法在不適合系統還原的磁碟機 (例如外接式磁碟機) 上停用系統還原。</span><span class="sxs-lookup"><span data-stu-id="bb463-125">You cannot use this cmdlet to disable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot disable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="bb463-126">如果要在任一磁碟機上停用系統還原，必須優先或同時在系統磁碟機上將它停用。</span><span class="sxs-lookup"><span data-stu-id="bb463-126">To disable System Restore on any drive, System Restore must be disabled on the system drive, either before or concurrently.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb463-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bb463-127">-Confirm</span></span>
<span data-ttu-id="bb463-128">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="bb463-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bb463-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb463-129">-WhatIf</span></span>
<span data-ttu-id="bb463-130">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="bb463-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bb463-131">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="bb463-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bb463-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb463-132">CommonParameters</span></span>
<span data-ttu-id="bb463-133">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bb463-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb463-134">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bb463-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb463-135">輸入</span><span class="sxs-lookup"><span data-stu-id="bb463-135">INPUTS</span></span>

### <span data-ttu-id="bb463-136">無</span><span class="sxs-lookup"><span data-stu-id="bb463-136">None</span></span>
<span data-ttu-id="bb463-137">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb463-137">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="bb463-138">輸出</span><span class="sxs-lookup"><span data-stu-id="bb463-138">OUTPUTS</span></span>

### <span data-ttu-id="bb463-139">無</span><span class="sxs-lookup"><span data-stu-id="bb463-139">None</span></span>
<span data-ttu-id="bb463-140">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="bb463-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bb463-141">注意</span><span class="sxs-lookup"><span data-stu-id="bb463-141">NOTES</span></span>

* <span data-ttu-id="bb463-142">若要在 Windows Vista 和更新版本的 Windows 上執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bb463-142">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="bb463-143">若要尋找適合系統還原的檔案系統磁片磁碟機，請在 [系統] 的 [主控台] 中，查看 [系統保護] 索引標籤。若要在 Windows PowerShell 中開啟此索引標籤，請輸入 `SystemPropertiesProtection` 。</span><span class="sxs-lookup"><span data-stu-id="bb463-143">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="bb463-144">此 Cmdlet 會使用 Windows Management Instrumentation (WMI) **SystemRestore** 類別。</span><span class="sxs-lookup"><span data-stu-id="bb463-144">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="bb463-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="bb463-145">RELATED LINKS</span></span>

[<span data-ttu-id="bb463-146">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="bb463-146">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="bb463-147">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="bb463-147">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="bb463-148">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="bb463-148">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="bb463-149">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="bb463-149">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="bb463-150">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="bb463-150">Restore-Computer</span></span>](Restore-Computer.md)
