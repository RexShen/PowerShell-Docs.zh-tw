---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: 9c1edd90757017c679516553d376d4cd4e552875
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202056"
---
# <span data-ttu-id="0e80a-103">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="0e80a-103">Remove-PSDrive</span></span>

## <span data-ttu-id="0e80a-104">概要</span><span class="sxs-lookup"><span data-stu-id="0e80a-104">SYNOPSIS</span></span>
<span data-ttu-id="0e80a-105">刪除暫存的 PowerShell 磁片磁碟機，並中斷對應網路磁碟機機的連線。</span><span class="sxs-lookup"><span data-stu-id="0e80a-105">Deletes temporary PowerShell drives and disconnects mapped network drives.</span></span>

## <span data-ttu-id="0e80a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0e80a-106">SYNTAX</span></span>

### <span data-ttu-id="0e80a-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="0e80a-107">Name (Default)</span></span>

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0e80a-108">LiteralName</span><span class="sxs-lookup"><span data-stu-id="0e80a-108">LiteralName</span></span>

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0e80a-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0e80a-109">DESCRIPTION</span></span>

<span data-ttu-id="0e80a-110">此 `Remove-PSDrive` Cmdlet 會刪除使用 Cmdlet 所建立的暫存 PowerShell 磁片磁碟機 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="0e80a-110">The `Remove-PSDrive` cmdlet deletes temporary PowerShell drives that were created by using the `New-PSDrive` cmdlet.</span></span>

<span data-ttu-id="0e80a-111">從 Windows PowerShell 3.0 開始， `Remove-PSDrive` 也會中斷對應網路磁碟機機的連接，包括（但不限於）使用的參數建立的磁片磁碟機 `Persist` `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="0e80a-111">Beginning in Windows PowerShell 3.0, `Remove-PSDrive` also disconnects mapped network drives, including, but not limited to, drives created by using the `Persist` parameter of `New-PSDrive`.</span></span>

<span data-ttu-id="0e80a-112">`Remove-PSDrive` 無法刪除 Windows 實體或邏輯磁碟機。</span><span class="sxs-lookup"><span data-stu-id="0e80a-112">`Remove-PSDrive` cannot delete Windows physical or logical drives.</span></span>

<span data-ttu-id="0e80a-113">從 Windows PowerShell 3.0 開始，當外部磁片磁碟機連接到電腦時，PowerShell 會自動將 New-psdrive 新增至代表新磁片磁碟機的檔案系統。</span><span class="sxs-lookup"><span data-stu-id="0e80a-113">Beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="0e80a-114">您不需要重新開機 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0e80a-114">You do not need to restart PowerShell.</span></span>
<span data-ttu-id="0e80a-115">同樣地，當外部磁片磁碟機與電腦中斷連線時，PowerShell 會自動刪除代表已移除之磁片磁碟機的 New-psdrive。</span><span class="sxs-lookup"><span data-stu-id="0e80a-115">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="0e80a-116">範例</span><span class="sxs-lookup"><span data-stu-id="0e80a-116">EXAMPLES</span></span>

### <span data-ttu-id="0e80a-117">範例 1︰移除檔案系統磁碟機</span><span class="sxs-lookup"><span data-stu-id="0e80a-117">Example 1: Remove a file system drive</span></span>

<span data-ttu-id="0e80a-118">此命令會移除名為"smp" 的暫時檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="0e80a-118">This command removes a temporary file system drive named "smp".</span></span>

```powershell
Remove-PSDrive -Name smp
```

### <span data-ttu-id="0e80a-119">範例 2：移除對應的網路磁碟機</span><span class="sxs-lookup"><span data-stu-id="0e80a-119">Example 2: Remove mapped network drives</span></span>

<span data-ttu-id="0e80a-120">此命令會使用 `Remove-PSDrive` 來中斷連接 X：和 S：對應的網路磁碟機機。</span><span class="sxs-lookup"><span data-stu-id="0e80a-120">This command uses `Remove-PSDrive` to disconnect the X: and S: mapped network drives.</span></span>

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## <span data-ttu-id="0e80a-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0e80a-121">PARAMETERS</span></span>

### <span data-ttu-id="0e80a-122">-Force</span><span class="sxs-lookup"><span data-stu-id="0e80a-122">-Force</span></span>

<span data-ttu-id="0e80a-123">移除目前的 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="0e80a-123">Removes the current PowerShell drive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e80a-124">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="0e80a-124">-LiteralName</span></span>

<span data-ttu-id="0e80a-125">指定磁碟機的名稱。</span><span class="sxs-lookup"><span data-stu-id="0e80a-125">Specifies the name of the drive.</span></span>

<span data-ttu-id="0e80a-126">**LiteralName** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="0e80a-126">The value of **LiteralName** is used exactly as typed.</span></span>
<span data-ttu-id="0e80a-127">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="0e80a-127">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="0e80a-128">如果名稱包含逸出字元，請將它括在單引號中 (')。</span><span class="sxs-lookup"><span data-stu-id="0e80a-128">If the name includes escape characters, enclose it in single quotation marks (').</span></span>
<span data-ttu-id="0e80a-129">單引號指示 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="0e80a-129">Single quotation marks instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0e80a-130">-Name</span><span class="sxs-lookup"><span data-stu-id="0e80a-130">-Name</span></span>

<span data-ttu-id="0e80a-131">指定要移除之磁碟機的名稱。</span><span class="sxs-lookup"><span data-stu-id="0e80a-131">Specifies the names of the drives to remove.</span></span>
<span data-ttu-id="0e80a-132">不要在磁碟機名稱後面輸入冒號 (:)。</span><span class="sxs-lookup"><span data-stu-id="0e80a-132">Do not type a colon (:) after the drive name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="0e80a-133">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="0e80a-133">-PSProvider</span></span>

<span data-ttu-id="0e80a-134">指定 **PSProvider** 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="0e80a-134">Specifies an array of **PSProvider** objects.</span></span>
<span data-ttu-id="0e80a-135">此 Cmdlet 會移除並中斷連接與指定 PowerShell 提供者相關聯的所有磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="0e80a-135">This cmdlet removes and disconnects all of the drives associated with the specified PowerShell provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0e80a-136">-Scope</span><span class="sxs-lookup"><span data-stu-id="0e80a-136">-Scope</span></span>

<span data-ttu-id="0e80a-137">指定磁碟機的範圍。</span><span class="sxs-lookup"><span data-stu-id="0e80a-137">Specifies a scope for the drive.</span></span>
<span data-ttu-id="0e80a-138">此參數可接受的值為： Global、Local 和 Script，或相對於目前範圍的數位。</span><span class="sxs-lookup"><span data-stu-id="0e80a-138">The acceptable values for this parameter are: Global, Local, and Script, or a number relative to the current scope.</span></span> <span data-ttu-id="0e80a-139">範圍編號0至範圍數目。</span><span class="sxs-lookup"><span data-stu-id="0e80a-139">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="0e80a-140">目前的範圍號碼為0，而其父系為1。</span><span class="sxs-lookup"><span data-stu-id="0e80a-140">The current scope number is 0 and its parent is 1.</span></span>
<span data-ttu-id="0e80a-141">如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="0e80a-141">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0e80a-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0e80a-142">-Confirm</span></span>

<span data-ttu-id="0e80a-143">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="0e80a-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0e80a-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0e80a-144">-WhatIf</span></span>

<span data-ttu-id="0e80a-145">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="0e80a-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0e80a-146">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="0e80a-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0e80a-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0e80a-147">CommonParameters</span></span>

<span data-ttu-id="0e80a-148">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0e80a-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0e80a-149">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0e80a-149">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0e80a-150">輸入</span><span class="sxs-lookup"><span data-stu-id="0e80a-150">INPUTS</span></span>

### <span data-ttu-id="0e80a-151">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="0e80a-151">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="0e80a-152">您可以使用管線將磁片磁碟機物件（例如 `Get-PSDrive` Cmdlet）傳送至 `Remove-PSDrive` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0e80a-152">You can pipe a drive object, such as one from the `Get-PSDrive` cmdlet, to the `Remove-PSDrive` cmdlet.</span></span>

## <span data-ttu-id="0e80a-153">輸出</span><span class="sxs-lookup"><span data-stu-id="0e80a-153">OUTPUTS</span></span>

### <span data-ttu-id="0e80a-154">無</span><span class="sxs-lookup"><span data-stu-id="0e80a-154">None</span></span>

<span data-ttu-id="0e80a-155">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="0e80a-155">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="0e80a-156">注意</span><span class="sxs-lookup"><span data-stu-id="0e80a-156">NOTES</span></span>

- <span data-ttu-id="0e80a-157">此 `Remove-PSDrive` Cmdlet 是針對與任何 PowerShell 提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="0e80a-157">The `Remove-PSDrive` cmdlet is designed to work with the data exposed by any PowerShell provider.</span></span> <span data-ttu-id="0e80a-158">若要列出會話中的提供者，請使用 `Get-PSProvider` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0e80a-158">To list the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="0e80a-159">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="0e80a-159">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="0e80a-160">相關連結</span><span class="sxs-lookup"><span data-stu-id="0e80a-160">RELATED LINKS</span></span>

[<span data-ttu-id="0e80a-161">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="0e80a-161">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="0e80a-162">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="0e80a-162">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="0e80a-163">about_Providers</span><span class="sxs-lookup"><span data-stu-id="0e80a-163">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

