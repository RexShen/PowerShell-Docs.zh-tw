---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 1f56dce193cc3c7c8b6af3a7854021b420107255
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203108"
---
# <span data-ttu-id="b70f9-103">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="b70f9-103">Unblock-File</span></span>

## <span data-ttu-id="b70f9-104">概要</span><span class="sxs-lookup"><span data-stu-id="b70f9-104">SYNOPSIS</span></span>
<span data-ttu-id="b70f9-105">將從網際網路下載的檔案解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="b70f9-105">Unblocks files that were downloaded from the Internet.</span></span>

## <span data-ttu-id="b70f9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b70f9-106">SYNTAX</span></span>

### <span data-ttu-id="b70f9-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="b70f9-107">ByPath (Default)</span></span>

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b70f9-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b70f9-108">ByLiteralPath</span></span>

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b70f9-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b70f9-109">DESCRIPTION</span></span>

<span data-ttu-id="b70f9-110">**Unblock-File** Cmdlet 可讓您開啟從網際網路下載的檔案。</span><span class="sxs-lookup"><span data-stu-id="b70f9-110">The **Unblock-File** cmdlet lets you open files that were downloaded from the Internet.</span></span>
<span data-ttu-id="b70f9-111">它會將從網際網路下載的 PowerShell 指令檔解除封鎖，讓您可以執行它們，即使是在 **RemoteSigned** powershell 執行原則時也一樣。</span><span class="sxs-lookup"><span data-stu-id="b70f9-111">It unblocks PowerShell script files that were downloaded from the Internet so you can run them, even when the PowerShell execution policy is **RemoteSigned** .</span></span>
<span data-ttu-id="b70f9-112">這些檔案預設會被封鎖，以保護電腦免於不受信任檔案的損害。</span><span class="sxs-lookup"><span data-stu-id="b70f9-112">By default, these files are blocked to protect the computer from untrusted files.</span></span>

<span data-ttu-id="b70f9-113">在使用 **Unblock-File** Cmdlet 之前，請先檢閱檔案及其來源，並確認開啟它是安全的。</span><span class="sxs-lookup"><span data-stu-id="b70f9-113">Before using the **Unblock-File** cmdlet, review the file and its source and verify that it is safe to open.</span></span>

<span data-ttu-id="b70f9-114">就內部而言， **Unblock-File** Cmdlet 會移除 Zone.Identifier 替代資料流，其值為"3"，表示它是下載自網際網路。</span><span class="sxs-lookup"><span data-stu-id="b70f9-114">Internally, the **Unblock-File** cmdlet removes the Zone.Identifier alternate data stream, which has a value of "3" to indicate that it was downloaded from the Internet.</span></span>

<span data-ttu-id="b70f9-115">如需 PowerShell 執行原則的詳細資訊，請參閱 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="b70f9-115">For more information about PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="b70f9-116">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b70f9-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b70f9-117">範例</span><span class="sxs-lookup"><span data-stu-id="b70f9-117">EXAMPLES</span></span>

### <span data-ttu-id="b70f9-118">範例 1：將檔案解除封鎖</span><span class="sxs-lookup"><span data-stu-id="b70f9-118">Example 1: Unblock a file</span></span>

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

<span data-ttu-id="b70f9-119">這個命令會將 PowerShellTips.chm 檔案解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="b70f9-119">This command unblocks the PowerShellTips.chm file.</span></span>

### <span data-ttu-id="b70f9-120">範例 2：將多個檔案解除封鎖</span><span class="sxs-lookup"><span data-stu-id="b70f9-120">Example 2: Unblock multiple files</span></span>

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

<span data-ttu-id="b70f9-121">這個命令會將 C:\Downloads 目錄中名稱包含 "PowerShell" 的所有檔案解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="b70f9-121">This command unblocks all of the files in the C:\Downloads directory whose names include "PowerShell".</span></span>
<span data-ttu-id="b70f9-122">除非您已確認所有檔案都是安全的，否則請勿執行這類命令。</span><span class="sxs-lookup"><span data-stu-id="b70f9-122">Do not run a command like this one until you have verified that all files are safe.</span></span>

### <span data-ttu-id="b70f9-123">範例 3：尋找指令碼並將其解除封鎖</span><span class="sxs-lookup"><span data-stu-id="b70f9-123">Example 3: Find and unblock scripts</span></span>

```
The first command uses the *Stream* parameter of the Get-Item cmdlet get files with the Zone.Identifier stream.Although you could pipe the output directly to the **Unblock-File** cmdlet (Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue | ForEach {Unblock-File $_.FileName}), it is prudent to review the file and confirm that it is safe before unblocking.
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**. The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.
PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

The third command uses the **Unblock-File** cmdlet to unblock the script so it can run in the session.
PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

<span data-ttu-id="b70f9-124">此命令示範如何尋找 PowerShell 腳本，並將其解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="b70f9-124">This command shows how to find and unblock PowerShell scripts.</span></span>

## <span data-ttu-id="b70f9-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b70f9-125">PARAMETERS</span></span>

### <span data-ttu-id="b70f9-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b70f9-126">-LiteralPath</span></span>
<span data-ttu-id="b70f9-127">指定要解除封鎖的檔案。</span><span class="sxs-lookup"><span data-stu-id="b70f9-127">Specifies the files to unblock.</span></span>
<span data-ttu-id="b70f9-128">與 *Path* 不同， *LiteralPath* 參數值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="b70f9-128">Unlike *Path* , the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="b70f9-129">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b70f9-129">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="b70f9-130">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="b70f9-130">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="b70f9-131">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="b70f9-131">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b70f9-132">-Path</span><span class="sxs-lookup"><span data-stu-id="b70f9-132">-Path</span></span>
<span data-ttu-id="b70f9-133">指定要解除封鎖的檔案。</span><span class="sxs-lookup"><span data-stu-id="b70f9-133">Specifies the files to unblock.</span></span>
<span data-ttu-id="b70f9-134">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b70f9-134">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="b70f9-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b70f9-135">-Confirm</span></span>

<span data-ttu-id="b70f9-136">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="b70f9-136">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b70f9-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b70f9-137">-WhatIf</span></span>

<span data-ttu-id="b70f9-138">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="b70f9-138">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b70f9-139">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="b70f9-139">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b70f9-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b70f9-140">CommonParameters</span></span>

<span data-ttu-id="b70f9-141">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b70f9-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b70f9-142">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b70f9-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b70f9-143">輸入</span><span class="sxs-lookup"><span data-stu-id="b70f9-143">INPUTS</span></span>

### <span data-ttu-id="b70f9-144">System.String</span><span class="sxs-lookup"><span data-stu-id="b70f9-144">System.String</span></span>

<span data-ttu-id="b70f9-145">您可以使用管線將檔案路徑傳送至 **Unblock-File** 。</span><span class="sxs-lookup"><span data-stu-id="b70f9-145">You can pipe a file path to **Unblock-File** .</span></span>

## <span data-ttu-id="b70f9-146">輸出</span><span class="sxs-lookup"><span data-stu-id="b70f9-146">OUTPUTS</span></span>

### <span data-ttu-id="b70f9-147">無</span><span class="sxs-lookup"><span data-stu-id="b70f9-147">None</span></span>

<span data-ttu-id="b70f9-148">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="b70f9-148">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b70f9-149">注意</span><span class="sxs-lookup"><span data-stu-id="b70f9-149">NOTES</span></span>

* <span data-ttu-id="b70f9-150">**Unblock-File** Cmdlet 只有在檔案系統磁碟機中才有作用。</span><span class="sxs-lookup"><span data-stu-id="b70f9-150">The **Unblock-File** cmdlet works only in file system drives.</span></span>
* <span data-ttu-id="b70f9-151"> 對話方塊上的 [Unblock]  按鈕相同。</span><span class="sxs-lookup"><span data-stu-id="b70f9-151">**Unblock-File** performs the same operation as the **Unblock** button on the **Properties** dialog box in File Explorer.</span></span>
* <span data-ttu-id="b70f9-152">如果您在未遭封鎖的檔案上使用 **Unblock-File** Cmdlet，則此命令對於該未遭封鎖的檔案並不會有任何作用，而此 Cmdlet 也不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b70f9-152">If you use the **Unblock-File** cmdlet on a file that is not blocked, the command has no effect on the unblocked file and the cmdlet does not generate errors.</span></span>

## <span data-ttu-id="b70f9-153">相關連結</span><span class="sxs-lookup"><span data-stu-id="b70f9-153">RELATED LINKS</span></span>

[<span data-ttu-id="b70f9-154">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="b70f9-154">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="b70f9-155">Get-Item</span><span class="sxs-lookup"><span data-stu-id="b70f9-155">Get-Item</span></span>](../Microsoft.PowerShell.Management/Get-Item.md)

[<span data-ttu-id="b70f9-156">Out-File</span><span class="sxs-lookup"><span data-stu-id="b70f9-156">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="b70f9-157">FileSystem 提供者</span><span class="sxs-lookup"><span data-stu-id="b70f9-157">FileSystem Provider</span></span>](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
