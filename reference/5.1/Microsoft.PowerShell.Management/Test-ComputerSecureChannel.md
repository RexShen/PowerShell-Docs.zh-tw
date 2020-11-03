---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203459"
---
# <span data-ttu-id="c7c6b-103">Test-ComputerSecureChannel</span><span class="sxs-lookup"><span data-stu-id="c7c6b-103">Test-ComputerSecureChannel</span></span>

## <span data-ttu-id="c7c6b-104">概要</span><span class="sxs-lookup"><span data-stu-id="c7c6b-104">SYNOPSIS</span></span>
<span data-ttu-id="c7c6b-105">測試和修復本機電腦和其網域之間的安全通道。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-105">Tests and repairs the secure channel between the local computer and its domain.</span></span>

## <span data-ttu-id="c7c6b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c7c6b-106">SYNTAX</span></span>

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="c7c6b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c7c6b-107">DESCRIPTION</span></span>
<span data-ttu-id="c7c6b-108">**Test-computersecurechannel** 指令程式會檢查其信任關係的狀態，以確認本機電腦與其網域之間的通道是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-108">The **Test-ComputerSecureChannel** cmdlet verifies that the channel between the local computer and its domain is working correctly by checking the status of its trust relationships.</span></span>
<span data-ttu-id="c7c6b-109">如果連線失敗，您可以使用 *Repair* 參數嘗試還原它。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-109">If a connection fails, you can use the *Repair* parameter to try to restore it.</span></span>

<span data-ttu-id="c7c6b-110">如果通道正常運作， **test-computersecurechannel** 會傳回 $True，並 $False。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-110">**Test-ComputerSecureChannel** returns $True if the channel is working correctly and $False if it is not.</span></span>
<span data-ttu-id="c7c6b-111">此結果可讓您在函式和指令碼中的條件陳述式使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-111">This result lets you use the cmdlet in conditional statements in functions and scripts.</span></span>
<span data-ttu-id="c7c6b-112">若要取得更詳細的測試結果，請使用 *Verbose* 參數。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-112">To get more detailed test results, use the *Verbose* parameter.</span></span>

<span data-ttu-id="c7c6b-113">此 Cmdlet 的運作方式與 NetDom.exe 非常類似。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-113">This cmdlet works much like NetDom.exe.</span></span>
<span data-ttu-id="c7c6b-114">NetDom 和 **測試 test-computersecurechannel** 都使用 **NetLogon** 服務來執行動作。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-114">Both NetDom and **Test-ComputerSecureChannel** use the **NetLogon** service to perform the actions.</span></span>

## <span data-ttu-id="c7c6b-115">範例</span><span class="sxs-lookup"><span data-stu-id="c7c6b-115">EXAMPLES</span></span>

### <span data-ttu-id="c7c6b-116">範例1：測試本機電腦與其網域之間的通道</span><span class="sxs-lookup"><span data-stu-id="c7c6b-116">Example 1: Test a channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel
True
```

<span data-ttu-id="c7c6b-117">此命令會測試本機電腦與其聯結網域之間的通道。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-117">This command tests the channel between the local computer and the domain to which it is joined.</span></span>

### <span data-ttu-id="c7c6b-118">範例2：在本機電腦和網域控制站之間測試通道</span><span class="sxs-lookup"><span data-stu-id="c7c6b-118">Example 2: Test a channel between the local computer and a domain controller</span></span>

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

<span data-ttu-id="c7c6b-119">此命令會指定測試的慣用網域控制站。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-119">This command specifies a preferred domain controller for the test.</span></span>

### <span data-ttu-id="c7c6b-120">範例3：重設本機電腦和其網域之間的通道</span><span class="sxs-lookup"><span data-stu-id="c7c6b-120">Example 3: Reset the channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

<span data-ttu-id="c7c6b-121">此命令會重設本機電腦和其網域之間的通道。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-121">This command resets the channel between the local computer and its domain.</span></span>

### <span data-ttu-id="c7c6b-122">範例4：顯示測試的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="c7c6b-122">Example 4: Display detailed information about the test</span></span>

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

<span data-ttu-id="c7c6b-123">此命令會使用 *Verbose* 一般參數來要求有關作業的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-123">This command uses the *Verbose* common parameter to request detailed messages about the operation.</span></span>
<span data-ttu-id="c7c6b-124">如需 *詳細* 資訊的詳細資訊，請參閱 about_CommonParameters。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-124">For more information about *Verbose* , see about_CommonParameters.</span></span>

### <span data-ttu-id="c7c6b-125">範例5：執行腳本之前先測試連接</span><span class="sxs-lookup"><span data-stu-id="c7c6b-125">Example 5: Test a connection before you run a script</span></span>

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

<span data-ttu-id="c7c6b-126">這個範例示範如何在執行需要連線的腳本之前，先使用 **測試 test-computersecurechannel** 來測試連接。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-126">This example shows how to use **Test-ComputerSecureChannel** to test a connection before you run a script that requires the connection.</span></span>

<span data-ttu-id="c7c6b-127">第一個命令會使用 Set-Alias Cmdlet 建立 Cmdlet 名稱的別名。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-127">The first command uses the Set-Alias cmdlet to create an alias for the cmdlet name.</span></span>
<span data-ttu-id="c7c6b-128">如此可節省空間和避免輸入錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-128">This saves space and prevents typing errors.</span></span>

<span data-ttu-id="c7c6b-129">**If** 語句會在執行腳本之前檢查 **test-computersecurechannel** 傳回的值。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-129">The **If** statement checks the value that **Test-ComputerSecureChannel** returns before it runs a script.</span></span>

## <span data-ttu-id="c7c6b-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c7c6b-130">PARAMETERS</span></span>

### <span data-ttu-id="c7c6b-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="c7c6b-131">-Credential</span></span>
<span data-ttu-id="c7c6b-132">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-132">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="c7c6b-133">輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-133">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one that the Get-Credential cmdlet returns.</span></span>
<span data-ttu-id="c7c6b-134">根據預設，Cmdlet 會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-134">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="c7c6b-135">*Credential* 參數是設計用於使用 *repair* 參數修復電腦與網域之間通道的命令。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-135">The *Credential* parameter is designed for use in commands that use the *Repair* parameter to repair the channel between the computer and the domain.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7c6b-136">-Repair</span><span class="sxs-lookup"><span data-stu-id="c7c6b-136">-Repair</span></span>
<span data-ttu-id="c7c6b-137">指出此 Cmdlet 會移除並重建 NetLogon 服務所建立的通道。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-137">Indicates that this cmdlet removes and then rebuilds the channel established by the NetLogon service.</span></span>
<span data-ttu-id="c7c6b-138">使用這個參數來嘗試還原測試失敗的連接。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-138">Use this parameter to try to restore a connection that has failed the test.</span></span>

<span data-ttu-id="c7c6b-139">如果要使用這個參數，目前使用者必須是本機電腦上之 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-139">To use this parameter, the current user must be a member of the Administrators group on the local computer.</span></span>

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

### <span data-ttu-id="c7c6b-140">-Server</span><span class="sxs-lookup"><span data-stu-id="c7c6b-140">-Server</span></span>
<span data-ttu-id="c7c6b-141">指定要執行命令的網域控制站。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-141">Specifies the domain controller to run the command.</span></span>
<span data-ttu-id="c7c6b-142">如果未指定這個參數，此 Cmdlet 會為作業選取預設網域控制站。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-142">If this parameter is not specified, this cmdlet selects a default domain controller for the operation.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7c6b-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c7c6b-143">-Confirm</span></span>
<span data-ttu-id="c7c6b-144">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c7c6b-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c7c6b-145">-WhatIf</span></span>
<span data-ttu-id="c7c6b-146">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-146">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c7c6b-147">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c7c6b-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c7c6b-148">CommonParameters</span></span>
<span data-ttu-id="c7c6b-149">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c7c6b-150">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c7c6b-151">輸入</span><span class="sxs-lookup"><span data-stu-id="c7c6b-151">INPUTS</span></span>

### <span data-ttu-id="c7c6b-152">無</span><span class="sxs-lookup"><span data-stu-id="c7c6b-152">None</span></span>
<span data-ttu-id="c7c6b-153">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c7c6b-154">輸出</span><span class="sxs-lookup"><span data-stu-id="c7c6b-154">OUTPUTS</span></span>

### <span data-ttu-id="c7c6b-155">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="c7c6b-155">System.Boolean</span></span>
<span data-ttu-id="c7c6b-156">如果連線正常運作，此 Cmdlet 會傳回 $True，如果沒有，則會 $False。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-156">This cmdlet returns $True if the connection is working correctly and $False if it is not.</span></span>

## <span data-ttu-id="c7c6b-157">注意</span><span class="sxs-lookup"><span data-stu-id="c7c6b-157">NOTES</span></span>

* <span data-ttu-id="c7c6b-158">若要在 Windows Vista 和更新版本的 Windows 作業系統上執行 **test-computersecurechannel** 命令，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-158">To run a **Test-ComputerSecureChannel** command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="c7c6b-159">**測試 test-computersecurechannel** 是使用 **I_NetLogonControl2** 函式來執行，此函式會控制 Netlogon 服務的各個層面。</span><span class="sxs-lookup"><span data-stu-id="c7c6b-159">**Test-ComputerSecureChannel** is implemented by using the **I_NetLogonControl2** function, which controls various aspects of the Netlogon service.</span></span>

## <span data-ttu-id="c7c6b-160">相關連結</span><span class="sxs-lookup"><span data-stu-id="c7c6b-160">RELATED LINKS</span></span>

[<span data-ttu-id="c7c6b-161">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="c7c6b-161">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="c7c6b-162">Reset-ComputerMachinePassword</span><span class="sxs-lookup"><span data-stu-id="c7c6b-162">Reset-ComputerMachinePassword</span></span>](Reset-ComputerMachinePassword.md)

[<span data-ttu-id="c7c6b-163">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="c7c6b-163">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="c7c6b-164">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="c7c6b-164">Stop-Computer</span></span>](Stop-Computer.md)
