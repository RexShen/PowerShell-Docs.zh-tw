---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: df7025999945b7fcf93001d992b3c067a6e508c7
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "93208892"
---
# <span data-ttu-id="c91d8-103">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="c91d8-103">Get-Credential</span></span>

## <span data-ttu-id="c91d8-104">概要</span><span class="sxs-lookup"><span data-stu-id="c91d8-104">SYNOPSIS</span></span>
<span data-ttu-id="c91d8-105">依據使用者名稱與密碼取得認證物件。</span><span class="sxs-lookup"><span data-stu-id="c91d8-105">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="c91d8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c91d8-106">SYNTAX</span></span>

### <span data-ttu-id="c91d8-107">CredentialSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="c91d8-107">CredentialSet (Default)</span></span>

```
Get-Credential [[-Credential] <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="c91d8-108">MessageSet</span><span class="sxs-lookup"><span data-stu-id="c91d8-108">MessageSet</span></span>

```
Get-Credential [-Message <String>] [[-UserName] <String>] [-Title <String>] [<CommonParameters>]
```

## <span data-ttu-id="c91d8-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c91d8-109">DESCRIPTION</span></span>

<span data-ttu-id="c91d8-110">`Get-Credential`Cmdlet 會為指定的使用者名稱和密碼建立認證物件。</span><span class="sxs-lookup"><span data-stu-id="c91d8-110">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="c91d8-111">您可以在安全性作業中使用認證物件。</span><span class="sxs-lookup"><span data-stu-id="c91d8-111">You can use the credential object in security operations.</span></span>

<span data-ttu-id="c91d8-112">此 `Get-Credential` Cmdlet 會提示使用者輸入密碼或使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c91d8-112">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="c91d8-113">您可以使用 **Message** 參數，在命令列提示字元中指定自訂的訊息。</span><span class="sxs-lookup"><span data-stu-id="c91d8-113">You can use the **Message** parameter to specify a customized message in the command line prompt.</span></span>

## <span data-ttu-id="c91d8-114">範例</span><span class="sxs-lookup"><span data-stu-id="c91d8-114">EXAMPLES</span></span>

### <span data-ttu-id="c91d8-115">範例 1</span><span class="sxs-lookup"><span data-stu-id="c91d8-115">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="c91d8-116">此命令會取得認證物件，並將它儲存在 `$c` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c91d8-116">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="c91d8-117">當您輸入命令時，系統會提示您輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c91d8-117">When you enter the command, you are prompted for a user name and password.</span></span> <span data-ttu-id="c91d8-118">當您輸入要求的資訊時，Cmdlet 會建立代表使用者認證的 **PSCredential** 物件，並將其儲存在 `$c` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c91d8-118">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="c91d8-119">您可以使用該物件做為要求使用者驗證的 Cmdlet 輸入，例如那些包含 **Credential** 參數的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c91d8-119">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="c91d8-120">不過，某些隨 PowerShell 安裝的提供者不支援 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="c91d8-120">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="c91d8-121">範例 2</span><span class="sxs-lookup"><span data-stu-id="c91d8-121">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="c91d8-122">這些命令會使用 Cmdlet 傳回的認證物件， `Get-Credential` 來驗證遠端電腦上的使用者，讓他們可以使用 Windows Management Instrumentation (WMI) 來管理電腦。</span><span class="sxs-lookup"><span data-stu-id="c91d8-122">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="c91d8-123">第一個命令會取得認證物件，並將它儲存在 `$c` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c91d8-123">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="c91d8-124">第二個命令會在命令中使用 credential 物件 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="c91d8-124">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="c91d8-125">此命令取得 Server01 電腦上磁碟機的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c91d8-125">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="c91d8-126">範例 3</span><span class="sxs-lookup"><span data-stu-id="c91d8-126">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="c91d8-127">此命令顯示如何 `Get-Credential` 在命令中包含命令  `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="c91d8-127">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="c91d8-128">此命令會使用 `Get-CimInstance` Cmdlet 來取得 Server01 電腦上 BIOS 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c91d8-128">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="c91d8-129">它會使用 **credential** 參數來驗證使用者、Domain01\User01 和 `Get-Credential` 命令，作為 **Credential** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="c91d8-129">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="c91d8-130">範例 4</span><span class="sxs-lookup"><span data-stu-id="c91d8-130">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="c91d8-131">此範例建立的認證包含沒有網域名稱的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="c91d8-131">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="c91d8-132">第一個命令取得具有使用者名稱 User01 的認證，並將它儲存在 `$c` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c91d8-132">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="c91d8-133">第二個命令顯示產生之認證物件的 **Username** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="c91d8-133">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="c91d8-134">範例 5</span><span class="sxs-lookup"><span data-stu-id="c91d8-134">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="c91d8-135">此命令使用 **PromptForCredential** 方法提示使用者輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c91d8-135">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="c91d8-136">此命令會將產生的認證儲存在 `$Credential` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c91d8-136">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="c91d8-137">**PromptForCredential** 方法是使用 Cmdlet 的替代方法 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="c91d8-137">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c91d8-138">當您使用 **PromptForCredential** 時，可以指定出現在提示字元中的標題、訊息和使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="c91d8-138">When you use **PromptForCredential** , you can specify the caption, messages, and user name that appear in the prompt.</span></span>

<span data-ttu-id="c91d8-139">如需詳細資訊，請參閱 SDK 中的 [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) 檔。</span><span class="sxs-lookup"><span data-stu-id="c91d8-139">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="c91d8-140">範例 6</span><span class="sxs-lookup"><span data-stu-id="c91d8-140">Example 6</span></span>

<span data-ttu-id="c91d8-141">這個範例示範如何建立認證物件，此物件與傳回的物件完全相同， `Get-Credential` 而不會提示使用者。</span><span class="sxs-lookup"><span data-stu-id="c91d8-141">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="c91d8-142">此方法需要純文字密碼，這可能會違反某些企業的安全性標準。</span><span class="sxs-lookup"><span data-stu-id="c91d8-142">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="c91d8-143">第一個命令會將使用者帳戶名稱儲存在 `$User` 參數中。</span><span class="sxs-lookup"><span data-stu-id="c91d8-143">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="c91d8-144">該值必須具有 "Domain\User" 或 "ComputerName\User" 格式。</span><span class="sxs-lookup"><span data-stu-id="c91d8-144">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="c91d8-145">第二個命令會使用 `ConvertTo-SecureString` Cmdlet，從純文字密碼建立安全字串。</span><span class="sxs-lookup"><span data-stu-id="c91d8-145">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="c91d8-146">命令使用 **AsPlainText** 參數指示字串為純文字，並使用 **Force** 參數確認您了解使用純文字的風險。</span><span class="sxs-lookup"><span data-stu-id="c91d8-146">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="c91d8-147">第三個命令會使用 `New-Object` Cmdlet，從和變數中的值建立 **PSCredential** 物件 `$User` `$PWord` 。</span><span class="sxs-lookup"><span data-stu-id="c91d8-147">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="c91d8-148">範例 7</span><span class="sxs-lookup"><span data-stu-id="c91d8-148">Example 7</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="c91d8-149">此命令會使用 Cmdlet 的 **Message** 和 **UserName** 參數 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="c91d8-149">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c91d8-150">此命令的格式是為共用的指令碼和函式而設計。</span><span class="sxs-lookup"><span data-stu-id="c91d8-150">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="c91d8-151">在本例中，訊息會告知使用者為什麼需要認證，並讓使用者相信此為合法要求。</span><span class="sxs-lookup"><span data-stu-id="c91d8-151">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="c91d8-152">範例 8</span><span class="sxs-lookup"><span data-stu-id="c91d8-152">Example 8</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

<span data-ttu-id="c91d8-153">此命令會從 Server01 遠端電腦取得認證。</span><span class="sxs-lookup"><span data-stu-id="c91d8-153">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="c91d8-154">此命令會使用 `Invoke-Command` Cmdlet `Get-Credential` 在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="c91d8-154">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="c91d8-155">輸出會顯示 `Get-Credential` 驗證提示中包含的遠端安全性訊息。</span><span class="sxs-lookup"><span data-stu-id="c91d8-155">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="c91d8-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c91d8-156">PARAMETERS</span></span>

### <span data-ttu-id="c91d8-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="c91d8-157">-Credential</span></span>

<span data-ttu-id="c91d8-158">指定認證的使用者名稱，例如 **User01** 或 **Domain01\User01** 。</span><span class="sxs-lookup"><span data-stu-id="c91d8-158">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="c91d8-159">參數名稱 `-Credential` 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c91d8-159">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="c91d8-160">當您提交命令並指定使用者名稱時，系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="c91d8-160">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="c91d8-161">如果您省略此參數，系統就會提示您輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c91d8-161">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="c91d8-162">從 PowerShell 3.0 開始，如果您輸入不含網域的使用者名稱，則 `Get-Credential` 不會再于名稱之前插入反斜線。</span><span class="sxs-lookup"><span data-stu-id="c91d8-162">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="c91d8-163">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="c91d8-163">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="c91d8-164">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="c91d8-164">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c91d8-165">-Message</span><span class="sxs-lookup"><span data-stu-id="c91d8-165">-Message</span></span>

<span data-ttu-id="c91d8-166">指定顯示在驗證提示中的訊息。</span><span class="sxs-lookup"><span data-stu-id="c91d8-166">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="c91d8-167">此參數是針對在函式或指令碼中使用而設計。</span><span class="sxs-lookup"><span data-stu-id="c91d8-167">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="c91d8-168">您可以使用該訊息向使用者說明為何要求認證，以及認證的用途。</span><span class="sxs-lookup"><span data-stu-id="c91d8-168">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="c91d8-169">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c91d8-169">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c91d8-170">-Title</span><span class="sxs-lookup"><span data-stu-id="c91d8-170">-Title</span></span>

<span data-ttu-id="c91d8-171">在主控台中設定驗證提示的標題列文字。</span><span class="sxs-lookup"><span data-stu-id="c91d8-171">Sets the text of the title line for the authentication prompt in the console.</span></span>

<span data-ttu-id="c91d8-172">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c91d8-172">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c91d8-173">-UserName</span><span class="sxs-lookup"><span data-stu-id="c91d8-173">-UserName</span></span>

<span data-ttu-id="c91d8-174">指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="c91d8-174">Specifies a user name.</span></span> <span data-ttu-id="c91d8-175">驗證提示要求使用者名稱的密碼。</span><span class="sxs-lookup"><span data-stu-id="c91d8-175">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="c91d8-176">根據預設，使用者名稱是空白的，且驗證提示會要求使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c91d8-176">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="c91d8-177">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c91d8-177">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c91d8-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c91d8-178">CommonParameters</span></span>

<span data-ttu-id="c91d8-179">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c91d8-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c91d8-180">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c91d8-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c91d8-181">輸入</span><span class="sxs-lookup"><span data-stu-id="c91d8-181">INPUTS</span></span>

### <span data-ttu-id="c91d8-182">無</span><span class="sxs-lookup"><span data-stu-id="c91d8-182">None</span></span>

<span data-ttu-id="c91d8-183">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c91d8-183">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c91d8-184">輸出</span><span class="sxs-lookup"><span data-stu-id="c91d8-184">OUTPUTS</span></span>

### <span data-ttu-id="c91d8-185">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="c91d8-185">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="c91d8-186">`Get-Credential` 傳回 credential 物件。</span><span class="sxs-lookup"><span data-stu-id="c91d8-186">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="c91d8-187">注意</span><span class="sxs-lookup"><span data-stu-id="c91d8-187">NOTES</span></span>

<span data-ttu-id="c91d8-188">您可以使用 **PSCredential** `Get-Credential` 在 Cmdlet 中建立並要求使用者驗證的 PSCredential 物件，例如具有 **Credential** 參數的使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="c91d8-188">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="c91d8-189">使用 PowerShell 安裝的所有提供者都不支援 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="c91d8-189">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="c91d8-190">從 PowerShell 3.0 開始，選取的 Cmdlet （例如和 Cmdlet）支援此 `Get-Content` 功能 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="c91d8-190">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="c91d8-191">相關連結</span><span class="sxs-lookup"><span data-stu-id="c91d8-191">RELATED LINKS</span></span>

[<span data-ttu-id="c91d8-192">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="c91d8-192">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
