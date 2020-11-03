---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/enable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ComputerRestore
ms.openlocfilehash: f9616a7f9af4dd2fa45e150bb64eef65427b4947
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204032"
---
# <span data-ttu-id="a8c13-103">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="a8c13-103">Enable-ComputerRestore</span></span>

## <span data-ttu-id="a8c13-104">概要</span><span class="sxs-lookup"><span data-stu-id="a8c13-104">SYNOPSIS</span></span>
<span data-ttu-id="a8c13-105">在指定的檔案系統磁碟機上啟用系統還原功能。</span><span class="sxs-lookup"><span data-stu-id="a8c13-105">Enables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="a8c13-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a8c13-106">SYNTAX</span></span>

```
Enable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a8c13-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a8c13-107">DESCRIPTION</span></span>
<span data-ttu-id="a8c13-108">**Enable-ComputerRestore** Cmdlet 會開啟一或多個檔案系統磁碟機上的系統還原功能。</span><span class="sxs-lookup"><span data-stu-id="a8c13-108">The **Enable-ComputerRestore** cmdlet turns on the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="a8c13-109">如此一來，您可以使用工具 (例如 Restore-Computer Cmdlet) 將電腦還原成先前的狀態。</span><span class="sxs-lookup"><span data-stu-id="a8c13-109">As a result, you can use tools, such as the Restore-Computer cmdlet, to restore the computer to a previous state.</span></span>

<span data-ttu-id="a8c13-110">依預設，所有適合的磁碟機上都已啟用系統還原，但是您可以停用它，像是使用 Disable-ComputerRestore Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a8c13-110">By default, System Restore is enabled on all eligible drives, but you can disable it, such as by using the Disable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="a8c13-111">如果要在任一磁碟機上啟用 (或重新啟用) 系統還原，則必須優先或同時在系統磁碟機上將它啟用。</span><span class="sxs-lookup"><span data-stu-id="a8c13-111">To enable (or re-enable) System Restore on any drive, it must be enabled on the system drive, either first or concurrently.</span></span>
<span data-ttu-id="a8c13-112">如果要尋找每個磁碟機的系統還原狀態，請使用 Rstrui.exe。</span><span class="sxs-lookup"><span data-stu-id="a8c13-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="a8c13-113">只有用戶端作業系統 (如 Windows 7、Windows Vista 和 Windows XP) 才支援系統還原點和 ComputerRestore Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a8c13-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="a8c13-114">範例</span><span class="sxs-lookup"><span data-stu-id="a8c13-114">EXAMPLES</span></span>

### <span data-ttu-id="a8c13-115">範例 1︰啟用指定磁碟機的系統還原</span><span class="sxs-lookup"><span data-stu-id="a8c13-115">Example 1: Enable System Restore on the specified drive</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="a8c13-116">此命令會啟用本機電腦 Ｃ: 磁碟機上的系統還原。</span><span class="sxs-lookup"><span data-stu-id="a8c13-116">This command enables System Restore on the C: drive of the local computer.</span></span>

### <span data-ttu-id="a8c13-117">範例 2︰啟用多個磁碟機的系統還原</span><span class="sxs-lookup"><span data-stu-id="a8c13-117">Example 2: Enable System Restore on multiple drives</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\", "D:\"
```

<span data-ttu-id="a8c13-118">此命令會啟用本機電腦 Ｃ: 與 D: 磁碟機上的系統還原。</span><span class="sxs-lookup"><span data-stu-id="a8c13-118">This command enables System Restore on the C: and D: drives of the local computer.</span></span>

## <span data-ttu-id="a8c13-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a8c13-119">PARAMETERS</span></span>

### <span data-ttu-id="a8c13-120">-Drive</span><span class="sxs-lookup"><span data-stu-id="a8c13-120">-Drive</span></span>
<span data-ttu-id="a8c13-121">指定檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="a8c13-121">Specifies the file system drives.</span></span>
<span data-ttu-id="a8c13-122">輸入一或多個檔系統磁碟機號，並在後面加上冒號和反斜線，並以引號括住，例如 C：\或 D:\。</span><span class="sxs-lookup"><span data-stu-id="a8c13-122">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="a8c13-123">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="a8c13-123">This parameter is required.</span></span>

<span data-ttu-id="a8c13-124">您無法使用這個 Cmdlet 來啟用遠端網路磁碟機上的系統還原，即使該磁碟機對應本機電腦也一樣，也無法在不適合系統還原的磁碟機 (例如外接式磁碟機) 上啟用系統還原。</span><span class="sxs-lookup"><span data-stu-id="a8c13-124">You cannot use this cmdlet to enable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot enable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="a8c13-125">如果要在任一磁碟機上啟用系統還原，必須優先或同時在系統磁碟機上將它啟用。</span><span class="sxs-lookup"><span data-stu-id="a8c13-125">To enable System Restore on any drive, System Restore must be enabled on the system drive, either before or concurrently.</span></span>

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

### <span data-ttu-id="a8c13-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a8c13-126">-Confirm</span></span>
<span data-ttu-id="a8c13-127">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a8c13-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a8c13-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a8c13-128">-WhatIf</span></span>
<span data-ttu-id="a8c13-129">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a8c13-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a8c13-130">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a8c13-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a8c13-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a8c13-131">CommonParameters</span></span>
<span data-ttu-id="a8c13-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a8c13-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a8c13-133">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a8c13-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a8c13-134">輸入</span><span class="sxs-lookup"><span data-stu-id="a8c13-134">INPUTS</span></span>

### <span data-ttu-id="a8c13-135">無</span><span class="sxs-lookup"><span data-stu-id="a8c13-135">None</span></span>
<span data-ttu-id="a8c13-136">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a8c13-136">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="a8c13-137">輸出</span><span class="sxs-lookup"><span data-stu-id="a8c13-137">OUTPUTS</span></span>

### <span data-ttu-id="a8c13-138">無</span><span class="sxs-lookup"><span data-stu-id="a8c13-138">None</span></span>
<span data-ttu-id="a8c13-139">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a8c13-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a8c13-140">注意</span><span class="sxs-lookup"><span data-stu-id="a8c13-140">NOTES</span></span>

* <span data-ttu-id="a8c13-141">若要在 Windows Vista 和更新版本的 Windows 上執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a8c13-141">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="a8c13-142">若要尋找適合系統還原的檔案系統磁片磁碟機，請在 [系統] 的 [主控台] 中，查看 [系統保護] 索引標籤。若要在 Windows PowerShell 中開啟此索引標籤，請輸入 `SystemPropertiesProtection` 。</span><span class="sxs-lookup"><span data-stu-id="a8c13-142">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="a8c13-143">此 Cmdlet 會使用 Windows Management Instrumentation (WMI) **SystemRestore** 類別。</span><span class="sxs-lookup"><span data-stu-id="a8c13-143">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="a8c13-144">相關連結</span><span class="sxs-lookup"><span data-stu-id="a8c13-144">RELATED LINKS</span></span>

[<span data-ttu-id="a8c13-145">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="a8c13-145">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="a8c13-146">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="a8c13-146">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="a8c13-147">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="a8c13-147">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="a8c13-148">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="a8c13-148">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="a8c13-149">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="a8c13-149">Restore-Computer</span></span>](Restore-Computer.md)
