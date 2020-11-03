---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: a48f2c5f62990258f14195eda934bbf4bbe589a1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203528"
---
# <span data-ttu-id="87006-103">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="87006-103">Resolve-Path</span></span>

## <span data-ttu-id="87006-104">概要</span><span class="sxs-lookup"><span data-stu-id="87006-104">SYNOPSIS</span></span>
<span data-ttu-id="87006-105">解析路徑中的萬用字元，並顯示路徑內容。</span><span class="sxs-lookup"><span data-stu-id="87006-105">Resolves the wildcard characters in a path, and displays the path contents.</span></span>

## <span data-ttu-id="87006-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="87006-106">SYNTAX</span></span>

### <span data-ttu-id="87006-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="87006-107">Path (Default)</span></span>

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="87006-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="87006-108">LiteralPath</span></span>

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="87006-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="87006-109">DESCRIPTION</span></span>

<span data-ttu-id="87006-110">`Resolve-Path`Cmdlet 會在指定的位置顯示符合萬用字元模式的專案和容器。</span><span class="sxs-lookup"><span data-stu-id="87006-110">The `Resolve-Path` cmdlet displays the items and containers that match the wildcard pattern at the location specified.</span></span> <span data-ttu-id="87006-111">相符可包含檔案、資料夾、登錄機碼，或可從 New-psdrive 提供者存取的任何其他物件。</span><span class="sxs-lookup"><span data-stu-id="87006-111">The match can include files, folders, registry keys, or any other object accessible from a PSDrive provider.</span></span>

## <span data-ttu-id="87006-112">範例</span><span class="sxs-lookup"><span data-stu-id="87006-112">EXAMPLES</span></span>

### <span data-ttu-id="87006-113">範例1：解析主資料夾路徑</span><span class="sxs-lookup"><span data-stu-id="87006-113">Example 1: Resolve the home folder path</span></span>

<span data-ttu-id="87006-114"> (~) 的波狀符號字元是目前使用者的主資料夾的縮寫標記法。</span><span class="sxs-lookup"><span data-stu-id="87006-114">The tilde character (~) is shorthand notation for the current user's home folder.</span></span> <span data-ttu-id="87006-115">此範例顯示傳回 `Resolve-Path` 完整路徑值。</span><span class="sxs-lookup"><span data-stu-id="87006-115">This example shows `Resolve-Path` returning the fully qualified path value.</span></span>

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### <span data-ttu-id="87006-116">範例2：解析 Windows 資料夾的路徑</span><span class="sxs-lookup"><span data-stu-id="87006-116">Example 2: Resolve the path of the Windows folder</span></span>

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="87006-117">從 C：磁片磁碟機的根目錄執行時，此命令會傳回 C：磁片磁碟機中 Windows 資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="87006-117">When run from the root of the C: drive, this command returns the path of the Windows folder in the C: drive.</span></span>

### <span data-ttu-id="87006-118">範例3：取得 Windows 資料夾中的所有路徑</span><span class="sxs-lookup"><span data-stu-id="87006-118">Example 3: Get all paths in the Windows folder</span></span>

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

<span data-ttu-id="87006-119">此命令會傳回 C：\Windows 資料夾中的所有資料夾。</span><span class="sxs-lookup"><span data-stu-id="87006-119">This command returns all of the folders in the C:\Windows folder.</span></span> <span data-ttu-id="87006-120">命令使用管線運算子 (|) 傳送路徑字串至 `Resolve-Path` 。</span><span class="sxs-lookup"><span data-stu-id="87006-120">The command uses a pipeline operator (|) to send a path string to `Resolve-Path`.</span></span>

### <span data-ttu-id="87006-121">範例4：解析 UNC 路徑</span><span class="sxs-lookup"><span data-stu-id="87006-121">Example 4: Resolve a UNC path</span></span>

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

<span data-ttu-id="87006-122">此命令解析通用命名慣例 (UNC) 路徑，並傳回路徑中的共用。</span><span class="sxs-lookup"><span data-stu-id="87006-122">This command resolves a Universal Naming Convention (UNC) path and returns the shares in the path.</span></span>

### <span data-ttu-id="87006-123">範例5：取得相對路徑</span><span class="sxs-lookup"><span data-stu-id="87006-123">Example 5: Get relative paths</span></span>

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

<span data-ttu-id="87006-124">此命令傳回位於 C: 磁碟機根目錄之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="87006-124">This command returns relative paths for the directories at the root of the C: drive.</span></span>

### <span data-ttu-id="87006-125">範例6：解析包含括弧的路徑</span><span class="sxs-lookup"><span data-stu-id="87006-125">Example 6: Resolve a path containing brackets</span></span>

<span data-ttu-id="87006-126">此範例使用 **LiteralPath** 參數來解析測試 \[ xml \] 子資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="87006-126">This example uses the **LiteralPath** parameter to resolve the path of the Test\[xml\] subfolder.</span></span>
<span data-ttu-id="87006-127">使用 **LiteralPath** 會讓括弧被視為一般字元，而不是正則運算式。</span><span class="sxs-lookup"><span data-stu-id="87006-127">Using **LiteralPath** causes the brackets to be treated as normal characters rather than a regular expression.</span></span>

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## <span data-ttu-id="87006-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="87006-128">PARAMETERS</span></span>

### <span data-ttu-id="87006-129">-Credential</span><span class="sxs-lookup"><span data-stu-id="87006-129">-Credential</span></span>

<span data-ttu-id="87006-130">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="87006-130">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="87006-131">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="87006-131">The default is the current user.</span></span>

<span data-ttu-id="87006-132">輸入使用者名稱（例如 User01 或 Domain01\User01），或傳遞 **PSCredential** 物件。</span><span class="sxs-lookup"><span data-stu-id="87006-132">Type a user name, such as User01 or Domain01\User01, or pass a **PSCredential** object.</span></span> <span data-ttu-id="87006-133">您可以使用 Cmdlet 來建立 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="87006-133">You can create a **PSCredential** object using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="87006-134">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="87006-134">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="87006-135">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="87006-135">This parameter is not supported by any providers installed with PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="87006-136">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="87006-136">-LiteralPath</span></span>

<span data-ttu-id="87006-137">指定要解析的路徑。</span><span class="sxs-lookup"><span data-stu-id="87006-137">Specifies the path to be resolved.</span></span> <span data-ttu-id="87006-138">**LiteralPath** 參數的值會完全依照輸入的方式使用。</span><span class="sxs-lookup"><span data-stu-id="87006-138">The value of the **LiteralPath** parameter is used exactly as typed.</span></span> <span data-ttu-id="87006-139">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="87006-139">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="87006-140">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="87006-140">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="87006-141">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="87006-141">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="87006-142">-Path</span><span class="sxs-lookup"><span data-stu-id="87006-142">-Path</span></span>

<span data-ttu-id="87006-143">指定要解析的 PowerShell 路徑。</span><span class="sxs-lookup"><span data-stu-id="87006-143">Specifies the PowerShell path to resolve.</span></span> <span data-ttu-id="87006-144">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="87006-144">This parameter is required.</span></span> <span data-ttu-id="87006-145">您也可以使用管線將路徑字串傳送至 `Resolve-Path` 。</span><span class="sxs-lookup"><span data-stu-id="87006-145">You can also pipe a path string to `Resolve-Path`.</span></span> <span data-ttu-id="87006-146">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="87006-146">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="87006-147">-Relative</span><span class="sxs-lookup"><span data-stu-id="87006-147">-Relative</span></span>

<span data-ttu-id="87006-148">指出此 Cmdlet 會傳回相對路徑。</span><span class="sxs-lookup"><span data-stu-id="87006-148">Indicates that this cmdlet returns a relative path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87006-149">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="87006-149">-UseTransaction</span></span>
<span data-ttu-id="87006-150">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="87006-150">Includes the command in the active transaction.</span></span>
<span data-ttu-id="87006-151">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="87006-151">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="87006-152">如需詳細資訊，請參閱 about_transactions。</span><span class="sxs-lookup"><span data-stu-id="87006-152">For more information, see about_transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="87006-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="87006-153">CommonParameters</span></span>

<span data-ttu-id="87006-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="87006-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="87006-155">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="87006-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="87006-156">輸入</span><span class="sxs-lookup"><span data-stu-id="87006-156">INPUTS</span></span>

### <span data-ttu-id="87006-157">System.String</span><span class="sxs-lookup"><span data-stu-id="87006-157">System.String</span></span>

<span data-ttu-id="87006-158">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="87006-158">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="87006-159">輸出</span><span class="sxs-lookup"><span data-stu-id="87006-159">OUTPUTS</span></span>

### <span data-ttu-id="87006-160">System.management.automation.pathinfo，System.string. String</span><span class="sxs-lookup"><span data-stu-id="87006-160">System.Management.Automation.PathInfo, System.String</span></span>

<span data-ttu-id="87006-161">傳回 **system.management.automation.pathinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="87006-161">Returns a **PathInfo** object.</span></span> <span data-ttu-id="87006-162">如果您指定了 **相對** 參數，則會傳回已解析路徑的字串值。</span><span class="sxs-lookup"><span data-stu-id="87006-162">Returns a string value for the resolved path if you specify the **Relative** parameter.</span></span>

## <span data-ttu-id="87006-163">注意</span><span class="sxs-lookup"><span data-stu-id="87006-163">NOTES</span></span>

<span data-ttu-id="87006-164">這些 `*-Path` Cmdlet 可與 FileSystem、登錄和憑證提供者搭配運作。</span><span class="sxs-lookup"><span data-stu-id="87006-164">The `*-Path` cmdlets work with the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="87006-165">`Resolve-Path` 是設計來搭配任何提供者使用。</span><span class="sxs-lookup"><span data-stu-id="87006-165">`Resolve-Path` is designed to work with any provider.</span></span> <span data-ttu-id="87006-166">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="87006-166">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="87006-167">如需詳細資訊，請參閱 [about_providers](../microsoft.powershell.core/about/about_providers.md)。</span><span class="sxs-lookup"><span data-stu-id="87006-167">For more information, see [about_providers](../microsoft.powershell.core/about/about_providers.md).</span></span>

<span data-ttu-id="87006-168">`Resolve-Path` 只解析現有的路徑。</span><span class="sxs-lookup"><span data-stu-id="87006-168">`Resolve-Path` only resolves existing paths.</span></span> <span data-ttu-id="87006-169">它無法用來解析尚未存在的位置。</span><span class="sxs-lookup"><span data-stu-id="87006-169">It cannot be used to resolve a location that does not exist yet.</span></span>

## <span data-ttu-id="87006-170">相關連結</span><span class="sxs-lookup"><span data-stu-id="87006-170">RELATED LINKS</span></span>

[<span data-ttu-id="87006-171">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="87006-171">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="87006-172">Join-Path</span><span class="sxs-lookup"><span data-stu-id="87006-172">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="87006-173">Split-Path</span><span class="sxs-lookup"><span data-stu-id="87006-173">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="87006-174">Test-Path</span><span class="sxs-lookup"><span data-stu-id="87006-174">Test-Path</span></span>](Test-Path.md)
