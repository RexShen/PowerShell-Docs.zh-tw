---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Reset-ComputerMachinePassword
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203531"
---
# <span data-ttu-id="5be07-103">Reset-ComputerMachinePassword</span><span class="sxs-lookup"><span data-stu-id="5be07-103">Reset-ComputerMachinePassword</span></span>

## <span data-ttu-id="5be07-104">概要</span><span class="sxs-lookup"><span data-stu-id="5be07-104">SYNOPSIS</span></span>
<span data-ttu-id="5be07-105">重設電腦的電腦帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="5be07-105">Resets the machine account password for the computer.</span></span>

## <span data-ttu-id="5be07-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5be07-106">SYNTAX</span></span>

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="5be07-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5be07-107">DESCRIPTION</span></span>
<span data-ttu-id="5be07-108">**Reset-computermachinepassword** 指令程式會將電腦用來向網域中的網域控制站進行驗證的電腦帳戶密碼變更。</span><span class="sxs-lookup"><span data-stu-id="5be07-108">The **Reset-ComputerMachinePassword** cmdlet changes the computer account password that the computers use to authenticate to the domain controllers in the domain.</span></span>
<span data-ttu-id="5be07-109">您可以使用它來重設本機電腦的密碼。</span><span class="sxs-lookup"><span data-stu-id="5be07-109">You can use it to reset the password of the local computer.</span></span>

## <span data-ttu-id="5be07-110">範例</span><span class="sxs-lookup"><span data-stu-id="5be07-110">EXAMPLES</span></span>

### <span data-ttu-id="5be07-111">範例1：重設本機電腦的密碼</span><span class="sxs-lookup"><span data-stu-id="5be07-111">Example 1: Reset the password for the local computer</span></span>

```
PS C:\> Reset-ComputerMachinePassword
```

<span data-ttu-id="5be07-112">此命令會重設本機電腦的電腦密碼。</span><span class="sxs-lookup"><span data-stu-id="5be07-112">This command resets the computer password for the local computer.</span></span>
<span data-ttu-id="5be07-113">此命令會使用目前使用者的認證執行。</span><span class="sxs-lookup"><span data-stu-id="5be07-113">The command runs with the credentials of the current user.</span></span>

### <span data-ttu-id="5be07-114">範例2：使用指定的網域控制站重設本機電腦的密碼</span><span class="sxs-lookup"><span data-stu-id="5be07-114">Example 2: Reset the password for the local computer by using a specified domain controller</span></span>

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

<span data-ttu-id="5be07-115">此命令會使用 DC01 網域控制站重設本機電腦的電腦密碼。</span><span class="sxs-lookup"><span data-stu-id="5be07-115">This command resets the computer password of the local computer by using the DC01 domain controller.</span></span>
<span data-ttu-id="5be07-116">它會使用 *Credential* 參數來指定有權在網域中重設電腦密碼的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5be07-116">It uses the *Credential* parameter to specify a user account that has permission to reset a computer password in the domain.</span></span>

### <span data-ttu-id="5be07-117">範例3：在遠端電腦上重設密碼</span><span class="sxs-lookup"><span data-stu-id="5be07-117">Example 3: Reset the password on a remote computer</span></span>

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

<span data-ttu-id="5be07-118">此命令會使用 Invoke-Command Cmdlet，在 Server01 遠端電腦上執行 **reset-computermachinepassword** 命令。</span><span class="sxs-lookup"><span data-stu-id="5be07-118">This command uses the Invoke-Command cmdlet to run a **Reset-ComputerMachinePassword** command on the Server01 remote computer.</span></span>

<span data-ttu-id="5be07-119">如需 Windows PowerShell 中之遠端命令的詳細資訊，請參閱 about_Remote 和 **Invoke-Command** 。</span><span class="sxs-lookup"><span data-stu-id="5be07-119">For more information about remote commands in Windows PowerShell, see about_Remote and **Invoke-Command** .</span></span>

## <span data-ttu-id="5be07-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5be07-120">PARAMETERS</span></span>

### <span data-ttu-id="5be07-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="5be07-121">-Credential</span></span>
<span data-ttu-id="5be07-122">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5be07-122">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="5be07-123">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="5be07-123">The default is the current user.</span></span>

<span data-ttu-id="5be07-124">輸入使用者名稱，例如 User01 或 Domain01\User01，或輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 產生的物件。</span><span class="sxs-lookup"><span data-stu-id="5be07-124">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="5be07-125">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="5be07-125">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="5be07-126">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="5be07-126">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5be07-127">-Server</span><span class="sxs-lookup"><span data-stu-id="5be07-127">-Server</span></span>
<span data-ttu-id="5be07-128">指定此 Cmdlet 設定電腦帳戶密碼時要使用的網域控制站名稱。</span><span class="sxs-lookup"><span data-stu-id="5be07-128">Specifies the name of a domain controller to use when this cmdlet sets the computer account password.</span></span>

<span data-ttu-id="5be07-129">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="5be07-129">This parameter is optional.</span></span>
<span data-ttu-id="5be07-130">如果您省略此參數，會選擇一個網域控制站來為命令提供服務。</span><span class="sxs-lookup"><span data-stu-id="5be07-130">If you omit this parameter, a domain controller is chosen to service the command.</span></span>

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

### <span data-ttu-id="5be07-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5be07-131">-Confirm</span></span>
<span data-ttu-id="5be07-132">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="5be07-132">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5be07-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5be07-133">-WhatIf</span></span>
<span data-ttu-id="5be07-134">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="5be07-134">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5be07-135">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="5be07-135">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5be07-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5be07-136">CommonParameters</span></span>
<span data-ttu-id="5be07-137">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5be07-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5be07-138">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5be07-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5be07-139">輸入</span><span class="sxs-lookup"><span data-stu-id="5be07-139">INPUTS</span></span>

### <span data-ttu-id="5be07-140">無</span><span class="sxs-lookup"><span data-stu-id="5be07-140">None</span></span>
<span data-ttu-id="5be07-141">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5be07-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="5be07-142">輸出</span><span class="sxs-lookup"><span data-stu-id="5be07-142">OUTPUTS</span></span>

### <span data-ttu-id="5be07-143">無</span><span class="sxs-lookup"><span data-stu-id="5be07-143">None</span></span>
<span data-ttu-id="5be07-144">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="5be07-144">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5be07-145">注意</span><span class="sxs-lookup"><span data-stu-id="5be07-145">NOTES</span></span>

## <span data-ttu-id="5be07-146">相關連結</span><span class="sxs-lookup"><span data-stu-id="5be07-146">RELATED LINKS</span></span>

## <span data-ttu-id="5be07-147">相關連結</span><span class="sxs-lookup"><span data-stu-id="5be07-147">RELATED LINKS</span></span>
