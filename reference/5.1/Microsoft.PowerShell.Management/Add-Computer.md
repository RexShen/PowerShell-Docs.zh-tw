---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: c1527c04d795206b8de968daf62456837627a098
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204096"
---
# <span data-ttu-id="15f11-103">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="15f11-103">Add-Computer</span></span>

## <span data-ttu-id="15f11-104">概要</span><span class="sxs-lookup"><span data-stu-id="15f11-104">SYNOPSIS</span></span>
<span data-ttu-id="15f11-105">將本機電腦新增到網域或工作群組。</span><span class="sxs-lookup"><span data-stu-id="15f11-105">Add the local computer to a domain or workgroup.</span></span>

## <span data-ttu-id="15f11-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="15f11-106">SYNTAX</span></span>

### <span data-ttu-id="15f11-107">網域 (預設) </span><span class="sxs-lookup"><span data-stu-id="15f11-107">Domain (Default)</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="15f11-108">工作群組</span><span class="sxs-lookup"><span data-stu-id="15f11-108">Workgroup</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="15f11-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="15f11-109">DESCRIPTION</span></span>

<span data-ttu-id="15f11-110">`Add-Computer`Cmdlet 會將本機電腦或遠端電腦新增到網域或工作組，或將它們從一個網域移到另一個網域。</span><span class="sxs-lookup"><span data-stu-id="15f11-110">The `Add-Computer` cmdlet adds the local computer or remote computers to a domain or workgroup, or moves them from one domain to another.</span></span>
<span data-ttu-id="15f11-111">如果將電腦新增到網域時沒有帳戶，它也會一併建立網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-111">It also creates a domain account if the computer is added to the domain without an account.</span></span>

<span data-ttu-id="15f11-112">您可以使用這個 Cmdlet 的參數來指定組織單位 (OU) 和網域控制站，或是執行非安全性加入。</span><span class="sxs-lookup"><span data-stu-id="15f11-112">You can use the parameters of this cmdlet to specify an organizational unit (OU) and domain controller or to perform an unsecure join.</span></span>

<span data-ttu-id="15f11-113">若要取得此命令的結果，請使用 **Verbose** 和 **PassThru** 參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-113">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span>

## <span data-ttu-id="15f11-114">範例</span><span class="sxs-lookup"><span data-stu-id="15f11-114">EXAMPLES</span></span>

### <span data-ttu-id="15f11-115">範例1：將本機電腦新增至網域，然後重新開機電腦</span><span class="sxs-lookup"><span data-stu-id="15f11-115">Example 1: Add a local computer to a domain then restart the computer</span></span>

```powershell
Add-Computer -DomainName Domain01 -Restart
```

<span data-ttu-id="15f11-116">這個命令會將本機電腦新增到 Domain01 網域，然後重新啟動電腦以使變更生效。</span><span class="sxs-lookup"><span data-stu-id="15f11-116">This command adds the local computer to the Domain01 domain and then restarts the computer to make the change effective.</span></span>

### <span data-ttu-id="15f11-117">範例2：將本機電腦新增至工作組</span><span class="sxs-lookup"><span data-stu-id="15f11-117">Example 2: Add a local computer to a workgroup</span></span>

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

<span data-ttu-id="15f11-118">這個命令會將本機電腦新增到 Workgroup-A 工作群組。</span><span class="sxs-lookup"><span data-stu-id="15f11-118">This command adds the local computer to the Workgroup-A workgroup.</span></span>

### <span data-ttu-id="15f11-119">範例3：將本機電腦新增至網域</span><span class="sxs-lookup"><span data-stu-id="15f11-119">Example 3: Add a local computer to a domain</span></span>

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

<span data-ttu-id="15f11-120">這個命令使用 Domain01\DC01 網域控制站將本機電腦新增到 Domain01 網域。</span><span class="sxs-lookup"><span data-stu-id="15f11-120">This command adds the local computer to the Domain01 domain by using the Domain01\DC01 domain controller.</span></span>

<span data-ttu-id="15f11-121">此命令使用 **PassThru** 和 **Verbose** 參數來取得有關命令結果的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="15f11-121">The command uses the **PassThru** and **Verbose** parameters to get detailed information about the results of the command.</span></span>

### <span data-ttu-id="15f11-122">範例4：使用 OUPath 參數將本機電腦新增至網域</span><span class="sxs-lookup"><span data-stu-id="15f11-122">Example 4: Add a local computer to a domain using the OUPath parameter</span></span>

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

<span data-ttu-id="15f11-123">這個命令會將本機電腦新增到 Domain02 網域。</span><span class="sxs-lookup"><span data-stu-id="15f11-123">This command adds the local computer to the Domain02 domain.</span></span>
<span data-ttu-id="15f11-124">它使用 OUPath 參數來指定新帳戶的組織單位。</span><span class="sxs-lookup"><span data-stu-id="15f11-124">It uses the OUPath parameter to specify the organizational unit for the new accounts.</span></span>

### <span data-ttu-id="15f11-125">範例5：使用認證將本機電腦新增至網域</span><span class="sxs-lookup"><span data-stu-id="15f11-125">Example 5: Add a local computer to a domain using credentials</span></span>

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

<span data-ttu-id="15f11-126">這個命令會將 Server01 電腦新增到 Domain02 網域。</span><span class="sxs-lookup"><span data-stu-id="15f11-126">This command adds the Server01 computer to the Domain02 domain.</span></span>
<span data-ttu-id="15f11-127">它使用 **LocalCredential** 參數來指定具有連線到 Server01 電腦之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-127">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the Server01 computer.</span></span>
<span data-ttu-id="15f11-128">它使用 **Credential** 參數來指定具有將電腦加入網域之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-128">It uses the **Credential** parameter to specify a user account that has permission to join computers to the domain.</span></span>
<span data-ttu-id="15f11-129">它使用 **Restart** 參數，以在加入操作完成後重新啟動電腦，並且使用 **Force** 參數，以抑制使用者確認訊息。</span><span class="sxs-lookup"><span data-stu-id="15f11-129">It uses the **Restart** parameter to restart the computer after the join operation completes and the **Force** parameter to suppress user confirmation messages.</span></span>

### <span data-ttu-id="15f11-130">範例6：將電腦群組移至新網域</span><span class="sxs-lookup"><span data-stu-id="15f11-130">Example 6: Move a group of computers to a new domain</span></span>

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="15f11-131">這個命令會將 Server01 和 Server02 電腦以及本機電腦從 Domain01 移到 Domain02。</span><span class="sxs-lookup"><span data-stu-id="15f11-131">This command moves the Server01 and Server02 computers, and the local computer, from Domain01 to Domain02.</span></span>

<span data-ttu-id="15f11-132">它使用 **LocalCredential** 參數來指定具有連線到這三部受影響電腦之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-132">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the three affected computers.</span></span>
<span data-ttu-id="15f11-133">它使用 **UnjoinDomainCredential** 參數來指定具有將電腦從 Domain01 網域退出之權限的使用者帳戶，並且使用 **Credential** 參數來指定具有將電腦加入 Domain02 網域之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-133">It uses the **UnjoinDomainCredential** parameter to specify a user account that has permission to unjoin the computers from the Domain01 domain and the **Credential** parameter to specify a user account that has permission to join the computers to the Domain02 domain.</span></span>
<span data-ttu-id="15f11-134">它使用 **Restart** 參數，以在完成移動後重新啟動這三部電腦。</span><span class="sxs-lookup"><span data-stu-id="15f11-134">It uses the **Restart** parameter to restart all three computers after the move is complete.</span></span>

### <span data-ttu-id="15f11-135">範例7：將電腦移至新網域，並變更電腦的名稱</span><span class="sxs-lookup"><span data-stu-id="15f11-135">Example 7: Move a computer to a new domain and change the name of the computer</span></span>

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="15f11-136">這個命令會將 Server01 電腦移到 Domain02，並將電腦名稱變更為 Server044。</span><span class="sxs-lookup"><span data-stu-id="15f11-136">This command moves the Server01 computer to the Domain02 and changes the machine name to Server044.</span></span>

<span data-ttu-id="15f11-137">此命令使用目前使用者的認證來連線到 Server01 電腦，以及將它從其目前的網域退出。</span><span class="sxs-lookup"><span data-stu-id="15f11-137">The command uses the credential of the current user to connect to the Server01 computer and unjoin it from its current domain.</span></span>
<span data-ttu-id="15f11-138">它使用 **Credential** 參數來指定具有將電腦加入 Domain02 網域之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-138">It uses the **Credential** parameter to specify  a user account that has permission to join the computer to the Domain02 domain.</span></span>

### <span data-ttu-id="15f11-139">範例8：將檔案中列出的電腦新增至新的網域</span><span class="sxs-lookup"><span data-stu-id="15f11-139">Example 8: Add computers listed in a file to a new domain</span></span>

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

<span data-ttu-id="15f11-140">這個命令會將 Servers.txt 檔案中所列的電腦新增到 Domain02 網域。</span><span class="sxs-lookup"><span data-stu-id="15f11-140">This command adds the computers that are listed in the Servers.txt file to the Domain02 domain.</span></span>
<span data-ttu-id="15f11-141">它使用 **Options** 參數來指定 **Win9xUpgrade** 選項。</span><span class="sxs-lookup"><span data-stu-id="15f11-141">It uses the **Options** parameter to specify the **Win9xUpgrade** option.</span></span>
<span data-ttu-id="15f11-142">**Restart** 參數會在加入操作完成後，重新啟動所有新加入的電腦。</span><span class="sxs-lookup"><span data-stu-id="15f11-142">The **Restart** parameter restarts all of the newly added computers after the join operation completes.</span></span>

### <span data-ttu-id="15f11-143">範例9：使用預先定義的電腦認證將電腦新增至網域</span><span class="sxs-lookup"><span data-stu-id="15f11-143">Example 9: Add a computer to a domain using predefined computer credentials</span></span>

<span data-ttu-id="15f11-144">第一個命令應該由系統管理員從已加入網域的電腦執行 `Domain03` ：</span><span class="sxs-lookup"><span data-stu-id="15f11-144">This first command should be run by an administrator from a computer that is already joined to domain `Domain03`:</span></span>

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

<span data-ttu-id="15f11-145">這項命令組合會使用已加入網域的現有電腦，在網域中建立具有預先定義名稱和暫時聯結密碼的新電腦帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-145">This combination of commands creates a new computer account with a predefined name and temporary join password in a domain using an existing domain-joined computer.</span></span>
<span data-ttu-id="15f11-146">接著，如果電腦具有預先定義的名稱，則只會使用電腦名稱稱和暫時聯結密碼來加入網域。</span><span class="sxs-lookup"><span data-stu-id="15f11-146">Then separately, a computer with the predefined name joins the domain using only the computer name and the temporary join password.</span></span>
<span data-ttu-id="15f11-147">預先定義的密碼只是用來支援聯結作業，而且會在電腦完成聯結之後，被取代為一般電腦帳戶程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="15f11-147">The predefined password is only used to support the join operation and is replaced as part of normal computer account procedures after the computer completes the join.</span></span>

## <span data-ttu-id="15f11-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="15f11-148">PARAMETERS</span></span>

### <span data-ttu-id="15f11-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="15f11-149">-ComputerName</span></span>

<span data-ttu-id="15f11-150">指定要新增到網域或工作群組的電腦。</span><span class="sxs-lookup"><span data-stu-id="15f11-150">Specifies the computers to add to a domain or workgroup.</span></span>
<span data-ttu-id="15f11-151">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="15f11-151">The default is the local computer.</span></span>

<span data-ttu-id="15f11-152">輸入每部遠端電腦的 NetBIOS 名稱、網際網路通訊協定 (IP) 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="15f11-152">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of each of the  remote computers.</span></span>
<span data-ttu-id="15f11-153">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="15f11-153">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="15f11-154">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="15f11-154">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="15f11-155">**ComputerName** `Add-Computer` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-155">You can use the **ComputerName** parameter of `Add-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="15f11-156">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="15f11-156">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="15f11-157">-Credential</span></span>

<span data-ttu-id="15f11-158">指定具有將電腦加入新網域之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-158">Specifies a user account that has permission to join the computers to a new domain.</span></span>
<span data-ttu-id="15f11-159">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="15f11-159">The default is the current user.</span></span>

<span data-ttu-id="15f11-160">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="15f11-160">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="15f11-161">若您輸入使用者名稱，將會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="15f11-161">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="15f11-162">若要指定具有將電腦從其目前網域中移除之權限的使用者帳戶，請使用 **UnjoinDomainCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-162">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span>
<span data-ttu-id="15f11-163">若要指定具有連線到遠端電腦之權限的使用者帳戶，請使用 **LocalCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-163">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-164">-DomainName</span><span class="sxs-lookup"><span data-stu-id="15f11-164">-DomainName</span></span>

<span data-ttu-id="15f11-165">指定要將電腦新增到其中的網域。</span><span class="sxs-lookup"><span data-stu-id="15f11-165">Specifies the domain to which the computers are added.</span></span>
<span data-ttu-id="15f11-166">將電腦新增到網域時，必須使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-166">This parameter is required when adding the computers to a domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-167">-Force</span><span class="sxs-lookup"><span data-stu-id="15f11-167">-Force</span></span>

<span data-ttu-id="15f11-168">抑制使用者確認提示。</span><span class="sxs-lookup"><span data-stu-id="15f11-168">Suppresses the user confirmation prompt.</span></span>
<span data-ttu-id="15f11-169">如果沒有這個參數， `Add-Computer` 則會要求您確認新增每部電腦。</span><span class="sxs-lookup"><span data-stu-id="15f11-169">Without this parameter, `Add-Computer` requires you to confirm the addition of each computer.</span></span>

<span data-ttu-id="15f11-170">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="15f11-170">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="15f11-171">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="15f11-171">-LocalCredential</span></span>

<span data-ttu-id="15f11-172">指定具有連線到 **ComputerName** 參數所指定電腦之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-172">Specifies a user account that has permission to connect to the computers that are specified by the **ComputerName** parameter.</span></span>
<span data-ttu-id="15f11-173">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="15f11-173">The default is the current user.</span></span>

<span data-ttu-id="15f11-174">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="15f11-174">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="15f11-175">若您輸入使用者名稱，將會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="15f11-175">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="15f11-176">若要指定具有將電腦新增到新網域之權限的使用者帳戶，請使用 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-176">To specify a user account that has permission to add the computers to a new domain, use the **Credential** parameter.</span></span>
<span data-ttu-id="15f11-177">若要指定具有將電腦從其目前網域中移除之權限的使用者帳戶，請使用 **UnjoinDomainCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-177">To specify a user account that has permission to remove the computers from their current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="15f11-178">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="15f11-178">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-179">-NewName</span><span class="sxs-lookup"><span data-stu-id="15f11-179">-NewName</span></span>

<span data-ttu-id="15f11-180">指定新網域中電腦的新名稱。</span><span class="sxs-lookup"><span data-stu-id="15f11-180">Specifies a new name for the computer in the new domain.</span></span>
<span data-ttu-id="15f11-181">這個參數只有在新增或移除電腦時才有效。</span><span class="sxs-lookup"><span data-stu-id="15f11-181">This parameter is valid only when one computer is being added or moved.</span></span>

<span data-ttu-id="15f11-182">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="15f11-182">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-183">-選項</span><span class="sxs-lookup"><span data-stu-id="15f11-183">-Options</span></span>

<span data-ttu-id="15f11-184">指定 **載入電腦** 聯結作業的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="15f11-184">Specifies advanced options for the **Add-Computer** join operation.</span></span>
<span data-ttu-id="15f11-185">請以逗號分隔的字串方式輸入一個或多個值。</span><span class="sxs-lookup"><span data-stu-id="15f11-185">Enter one or more values in a comma-separated string.</span></span>

<span data-ttu-id="15f11-186">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="15f11-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="15f11-187">**帳戶** ：建立網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-187">**AccountCreate** : Creates a domain account.</span></span> <span data-ttu-id="15f11-188">**新增** 電腦指令 Cmdlet 會在將電腦新增到網域時自動建立網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-188">The **Add-Computer** cmdlet automatically creates a domain account when it adds a computer to a domain.</span></span> <span data-ttu-id="15f11-189">包含這個選項是為了完整性。</span><span class="sxs-lookup"><span data-stu-id="15f11-189">This option is included for completeness.</span></span>

- <span data-ttu-id="15f11-190">**Win9XUpgrade** ：表示聯結作業是 Windows 作業系統升級的一部分。</span><span class="sxs-lookup"><span data-stu-id="15f11-190">**Win9XUpgrade** : Indicates that the join operation is part of a Windows operating system upgrade.</span></span>

- <span data-ttu-id="15f11-191">**UnsecuredJoin** ：執行不安全的聯結。</span><span class="sxs-lookup"><span data-stu-id="15f11-191">**UnsecuredJoin** : Performs an unsecured join.</span></span> <span data-ttu-id="15f11-192">若要要求不安全的聯結，請使用不 *安全* 的參數或這個選項。</span><span class="sxs-lookup"><span data-stu-id="15f11-192">To request an unsecured join, use the *Unsecure* parameter or this option.</span></span> <span data-ttu-id="15f11-193">如果您想要傳遞電腦密碼，則必須將此選項與選項搭配使用 `PasswordPass` 。</span><span class="sxs-lookup"><span data-stu-id="15f11-193">If you want to pass a machine password, then you must use this option in combination with `PasswordPass` option.</span></span>

- <span data-ttu-id="15f11-194">**PasswordPass** ：在執行不安全的聯結之後，將電腦密碼設定為 *Credential* (DomainCredential) 參數的值。</span><span class="sxs-lookup"><span data-stu-id="15f11-194">**PasswordPass** : Sets the machine password to the value of the *Credential* (DomainCredential) parameter after performing an unsecured join.</span></span> <span data-ttu-id="15f11-195">這個選項也會指出 *Credential* (DomainCredential) 參數的值是電腦密碼，而不是使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="15f11-195">This option also indicates that the value of the *Credential* (DomainCredential) parameter is a machine password, not a user password.</span></span> <span data-ttu-id="15f11-196">只有在指定選項時，這個選項才有效 `UnsecuredJoin` 。</span><span class="sxs-lookup"><span data-stu-id="15f11-196">This option is valid only when the `UnsecuredJoin` option is specified.</span></span> <span data-ttu-id="15f11-197">使用此選項時，提供給參數的認證 `-Credential` *必須* 有 null 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="15f11-197">When using this option, the credential provided to the `-Credential` parameter *must* have a null username.</span></span>

- <span data-ttu-id="15f11-198">**JoinWithNewName** ：將新網域中的電腦名稱稱重新命名為 *NewName* 參數所指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="15f11-198">**JoinWithNewName** : Renames the computer name in the new domain to the name specified by the *NewName* parameter.</span></span> <span data-ttu-id="15f11-199">使用 *NewName* 參數時，會自動設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="15f11-199">When you use the *NewName* parameter, this option is set automatically.</span></span> <span data-ttu-id="15f11-200">此選項的設計目的是要搭配 Rename-Computer Cmdlet 使用。</span><span class="sxs-lookup"><span data-stu-id="15f11-200">This option is designed to be used with the Rename-Computer cmdlet.</span></span> <span data-ttu-id="15f11-201">如果您使用「 **重新命名電腦** 」 Cmdlet 來重新命名電腦，但並未重新開機電腦以使變更生效，您可以使用此參數將電腦加入具有新名稱的網域。</span><span class="sxs-lookup"><span data-stu-id="15f11-201">If you use the **Rename-Computer** cmdlet to rename the computer, but do not restart the computer to make the change effective, you can use this parameter to join the computer to a domain with its new name.</span></span>

- <span data-ttu-id="15f11-202">**JoinReadOnly** ：使用現有的電腦帳戶將電腦加入唯讀網域控制站。</span><span class="sxs-lookup"><span data-stu-id="15f11-202">**JoinReadOnly** : Uses an existing machine account to join the computer to a read-only domain controller.</span></span> <span data-ttu-id="15f11-203">您必須將電腦帳戶新增到密碼複寫原則的允許清單中，而且必須先將帳戶密碼複寫到唯讀網域控制站，才能進行聯結操作。</span><span class="sxs-lookup"><span data-stu-id="15f11-203">The machine account must be added to the allowed list for password replication policy and the account password must be replicated to the read-only domain controller prior to the join operation.</span></span>

- <span data-ttu-id="15f11-204">**InstallInvoke** ：設定 **JoinDomainOrWorkgroup** 方法之 **joindomainorworkgroup** 參數的 create (0x2) 和 delete (0x4) 旗標。</span><span class="sxs-lookup"><span data-stu-id="15f11-204">**InstallInvoke** : Sets the create (0x2) and delete (0x4) flags of the **FJoinOptions** parameter of the **JoinDomainOrWorkgroup** method.</span></span> <span data-ttu-id="15f11-205">如需 **JoinDomainOrWorkgroup** 方法的詳細資訊，請參閱 MSDN library 中 [的 Win32_ComputerSystem 類別的 JoinDomainOrWorkgroup 方法](https://msdn.microsoft.com/library/aa392154) 。</span><span class="sxs-lookup"><span data-stu-id="15f11-205">For more information about the **JoinDomainOrWorkgroup** method, see [JoinDomainOrWorkgroup method of the Win32_ComputerSystem class](https://msdn.microsoft.com/library/aa392154) in the MSDN library.</span></span> <span data-ttu-id="15f11-206">如需這些選項的詳細資訊，請參閱 MSDN library 中的 [NetJoinDomain 函數](https://msdn.microsoft.com/library/aa370433) 。</span><span class="sxs-lookup"><span data-stu-id="15f11-206">For more information about these options, see [NetJoinDomain function](https://msdn.microsoft.com/library/aa370433) in the MSDN library.</span></span>

<span data-ttu-id="15f11-207">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="15f11-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-208">-OUPath</span><span class="sxs-lookup"><span data-stu-id="15f11-208">-OUPath</span></span>

<span data-ttu-id="15f11-209">指定網域帳戶的組織單位 (OU)。</span><span class="sxs-lookup"><span data-stu-id="15f11-209">Specifies an organizational unit (OU) for the domain account.</span></span>
<span data-ttu-id="15f11-210">請以引號括住的方式輸入 OU 的完整辨別名稱。</span><span class="sxs-lookup"><span data-stu-id="15f11-210">Enter the full distinguished name of the OU in quotation marks.</span></span>
<span data-ttu-id="15f11-211">預設值是網域中電腦物件的預設 OU。</span><span class="sxs-lookup"><span data-stu-id="15f11-211">The default value is the default OU for machine objects in the domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-212">-PassThru</span><span class="sxs-lookup"><span data-stu-id="15f11-212">-PassThru</span></span>

<span data-ttu-id="15f11-213">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="15f11-213">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="15f11-214">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="15f11-214">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="15f11-215">-Restart</span><span class="sxs-lookup"><span data-stu-id="15f11-215">-Restart</span></span>

<span data-ttu-id="15f11-216">重新啟動已新增到網域或工作群組的電腦。</span><span class="sxs-lookup"><span data-stu-id="15f11-216">Restarts the computers that were added to the domain or workgroup.</span></span>
<span data-ttu-id="15f11-217">通常必須重新啟動才能使變更生效。</span><span class="sxs-lookup"><span data-stu-id="15f11-217">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="15f11-218">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="15f11-218">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="15f11-219">-Server</span><span class="sxs-lookup"><span data-stu-id="15f11-219">-Server</span></span>

<span data-ttu-id="15f11-220">指定將電腦新增到網域的網域控制站名稱。</span><span class="sxs-lookup"><span data-stu-id="15f11-220">Specifies the name of a domain controller that adds the computer to the domain.</span></span>
<span data-ttu-id="15f11-221">請以 DomainName\ComputerName 格式輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="15f11-221">Enter the name in DomainName\ComputerName format.</span></span>
<span data-ttu-id="15f11-222">預設不會指定任何網域控制站。</span><span class="sxs-lookup"><span data-stu-id="15f11-222">By default, no domain controller is specified.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-223">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="15f11-223">-UnjoinDomainCredential</span></span>

<span data-ttu-id="15f11-224">指定具有將電腦從其目前網域中移除之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="15f11-224">Specifies a user account that has permission to remove the computers from their current domains.</span></span>
<span data-ttu-id="15f11-225">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="15f11-225">The default is the current user.</span></span>

<span data-ttu-id="15f11-226">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="15f11-226">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="15f11-227">若您輸入使用者名稱，將會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="15f11-227">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="15f11-228">當您要將電腦移到不同的網域時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-228">Use this parameter when you are moving computers to a different domain.</span></span>
<span data-ttu-id="15f11-229">若要指定具有將電腦加入新網域之權限的使用者帳戶，請使用 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-229">To specify a user account that has permission to join the new domain, use the **Credential** parameter.</span></span>
<span data-ttu-id="15f11-230">若要指定具有連線到遠端電腦之權限的使用者帳戶，請使用 **LocalCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="15f11-230">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="15f11-231">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="15f11-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-232">-不安全</span><span class="sxs-lookup"><span data-stu-id="15f11-232">-Unsecure</span></span>

<span data-ttu-id="15f11-233">執行對指定之網域的非安全性加入。</span><span class="sxs-lookup"><span data-stu-id="15f11-233">Performs an unsecure join to the specified domain.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-234">-WorkgroupName</span><span class="sxs-lookup"><span data-stu-id="15f11-234">-WorkgroupName</span></span>

<span data-ttu-id="15f11-235">指定要將電腦新增到其中的工作群組名稱。</span><span class="sxs-lookup"><span data-stu-id="15f11-235">Specifies the name of a workgroup to which the computers are added.</span></span>
<span data-ttu-id="15f11-236">預設值為 "WORKGROUP"。</span><span class="sxs-lookup"><span data-stu-id="15f11-236">The default value is "WORKGROUP".</span></span>

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f11-237">-Confirm</span><span class="sxs-lookup"><span data-stu-id="15f11-237">-Confirm</span></span>

<span data-ttu-id="15f11-238">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="15f11-238">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="15f11-239">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="15f11-239">-WhatIf</span></span>

<span data-ttu-id="15f11-240">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="15f11-240">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="15f11-241">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="15f11-241">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="15f11-242">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15f11-242">CommonParameters</span></span>

<span data-ttu-id="15f11-243">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="15f11-243">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15f11-244">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="15f11-244">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="15f11-245">輸入</span><span class="sxs-lookup"><span data-stu-id="15f11-245">INPUTS</span></span>

### <span data-ttu-id="15f11-246">System.String</span><span class="sxs-lookup"><span data-stu-id="15f11-246">System.String</span></span>

<span data-ttu-id="15f11-247">您可以透過管線將電腦名稱稱和新名稱傳送至 `Add-Computer` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="15f11-247">You can pipe computer names and new names to the `Add-Computer` Cmdlet.</span></span>

## <span data-ttu-id="15f11-248">輸出</span><span class="sxs-lookup"><span data-stu-id="15f11-248">OUTPUTS</span></span>

### <span data-ttu-id="15f11-249">Microsoft.PowerShell.Commands.ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="15f11-249">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="15f11-250">當您使用 **PassThru** 參數時，會傳回 `Add-Computer` **ComputerChangeInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="15f11-250">When you use the **PassThru** parameter, `Add-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="15f11-251">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="15f11-251">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="15f11-252">注意</span><span class="sxs-lookup"><span data-stu-id="15f11-252">NOTES</span></span>

- <span data-ttu-id="15f11-253">在 Windows PowerShell 2.0 中，即使伺服器存在， **伺服器** 參數也 `Add-Computer` 會失敗。</span><span class="sxs-lookup"><span data-stu-id="15f11-253">In Windows PowerShell 2.0, the **Server** parameter of `Add-Computer` fails even when the server is present.</span></span> <span data-ttu-id="15f11-254">在 Windows PowerShell 3.0 中， **Server** 參數的實作已變更，使其能夠可靠地運作。</span><span class="sxs-lookup"><span data-stu-id="15f11-254">In Windows PowerShell 3.0, the implementation of the **Server** parameter is changed so that it works reliably.</span></span>

## <span data-ttu-id="15f11-255">相關連結</span><span class="sxs-lookup"><span data-stu-id="15f11-255">RELATED LINKS</span></span>

[<span data-ttu-id="15f11-256">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="15f11-256">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="15f11-257">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="15f11-257">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="15f11-258">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="15f11-258">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="15f11-259">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="15f11-259">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="15f11-260">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="15f11-260">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="15f11-261">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="15f11-261">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="15f11-262">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="15f11-262">Test-Connection</span></span>](Test-Connection.md)
