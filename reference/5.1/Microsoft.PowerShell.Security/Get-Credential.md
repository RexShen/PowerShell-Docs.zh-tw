---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 26c4f8c8dcc1fbd56e29f55a6a8c2e6aa37a2842
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "93208888"
---
# <span data-ttu-id="4077a-103">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="4077a-103">Get-Credential</span></span>

## <span data-ttu-id="4077a-104">概要</span><span class="sxs-lookup"><span data-stu-id="4077a-104">SYNOPSIS</span></span>
<span data-ttu-id="4077a-105">依據使用者名稱與密碼取得認證物件。</span><span class="sxs-lookup"><span data-stu-id="4077a-105">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="4077a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4077a-106">SYNTAX</span></span>

### <span data-ttu-id="4077a-107">CredentialSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="4077a-107">CredentialSet (Default)</span></span>

```
Get-Credential [-Credential] <PSCredential> [<CommonParameters>]
```

### <span data-ttu-id="4077a-108">MessageSet</span><span class="sxs-lookup"><span data-stu-id="4077a-108">MessageSet</span></span>

```
Get-Credential -Message <String> [[-UserName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="4077a-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4077a-109">DESCRIPTION</span></span>

<span data-ttu-id="4077a-110">`Get-Credential`Cmdlet 會為指定的使用者名稱和密碼建立認證物件。</span><span class="sxs-lookup"><span data-stu-id="4077a-110">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="4077a-111">您可以在安全性作業中使用認證物件。</span><span class="sxs-lookup"><span data-stu-id="4077a-111">You can use the credential object in security operations.</span></span>

<span data-ttu-id="4077a-112">從 PowerShell 3.0 開始，您可以使用 **Message** 參數，在提示使用者輸入其名稱和密碼的對話方塊上指定自訂的訊息。</span><span class="sxs-lookup"><span data-stu-id="4077a-112">Beginning in PowerShell 3.0, you can use the **Message** parameter to specify a customized message on the dialog box that prompts the user for their name and password.</span></span>

<span data-ttu-id="4077a-113">此 `Get-Credential` Cmdlet 會提示使用者輸入密碼或使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4077a-113">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="4077a-114">根據預設，會出現驗證對話方塊提示使用者。</span><span class="sxs-lookup"><span data-stu-id="4077a-114">By default, an authentication dialog box appears to prompt the user.</span></span> <span data-ttu-id="4077a-115">不過，在某些主機程式中，例如 PowerShell 主控台，您可以藉由變更登錄專案在命令列提示使用者。</span><span class="sxs-lookup"><span data-stu-id="4077a-115">However, in some host programs, such as the PowerShell console, you can prompt the user at the command line by changing a registry entry.</span></span> <span data-ttu-id="4077a-116">如需有關此登錄項目的詳細資訊，請參閱附註和範例。</span><span class="sxs-lookup"><span data-stu-id="4077a-116">For more information about this registry entry, see the notes and examples.</span></span>

## <span data-ttu-id="4077a-117">範例</span><span class="sxs-lookup"><span data-stu-id="4077a-117">EXAMPLES</span></span>

### <span data-ttu-id="4077a-118">範例 1</span><span class="sxs-lookup"><span data-stu-id="4077a-118">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="4077a-119">此命令會取得認證物件，並將它儲存在 `$c` 變數中。</span><span class="sxs-lookup"><span data-stu-id="4077a-119">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="4077a-120">當您輸入命令時，會出現對話方塊要求使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4077a-120">When you enter the command, a dialog box appears requesting a user name and password.</span></span> <span data-ttu-id="4077a-121">當您輸入要求的資訊時，Cmdlet 會建立代表使用者認證的 **PSCredential** 物件，並將其儲存在 `$c` 變數中。</span><span class="sxs-lookup"><span data-stu-id="4077a-121">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="4077a-122">您可以使用該物件做為要求使用者驗證的 Cmdlet 輸入，例如那些包含 **Credential** 參數的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4077a-122">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="4077a-123">不過，某些隨 PowerShell 安裝的提供者不支援 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="4077a-123">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="4077a-124">範例 2</span><span class="sxs-lookup"><span data-stu-id="4077a-124">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="4077a-125">這些命令會使用 Cmdlet 傳回的認證物件， `Get-Credential` 來驗證遠端電腦上的使用者，讓他們可以使用 Windows Management Instrumentation (WMI) 來管理電腦。</span><span class="sxs-lookup"><span data-stu-id="4077a-125">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="4077a-126">第一個命令會取得認證物件，並將它儲存在 `$c` 變數中。</span><span class="sxs-lookup"><span data-stu-id="4077a-126">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="4077a-127">第二個命令會在命令中使用 credential 物件 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="4077a-127">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="4077a-128">此命令取得 Server01 電腦上磁碟機的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4077a-128">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="4077a-129">範例 3</span><span class="sxs-lookup"><span data-stu-id="4077a-129">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="4077a-130">此命令顯示如何 `Get-Credential` 在命令中包含命令  `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="4077a-130">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="4077a-131">此命令會使用 `Get-CimInstance` Cmdlet 來取得 Server01 電腦上 BIOS 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4077a-131">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="4077a-132">它會使用 **credential** 參數來驗證使用者、Domain01\User01 和 `Get-Credential` 命令，作為 **Credential** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="4077a-132">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="4077a-133">範例 4</span><span class="sxs-lookup"><span data-stu-id="4077a-133">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="4077a-134">此範例建立的認證包含沒有網域名稱的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4077a-134">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="4077a-135">第一個命令取得具有使用者名稱 User01 的認證，並將它儲存在 `$c` 變數中。</span><span class="sxs-lookup"><span data-stu-id="4077a-135">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="4077a-136">第二個命令顯示產生之認證物件的 **Username** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="4077a-136">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="4077a-137">範例 5</span><span class="sxs-lookup"><span data-stu-id="4077a-137">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="4077a-138">此命令使用 **PromptForCredential** 方法提示使用者輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4077a-138">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="4077a-139">此命令會將產生的認證儲存在 `$Credential` 變數中。</span><span class="sxs-lookup"><span data-stu-id="4077a-139">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="4077a-140">**PromptForCredential** 方法是使用 Cmdlet 的替代方法 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="4077a-140">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="4077a-141">當您使用 **PromptForCredential** 時可以指定標題、訊息和訊息方塊中顯示的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4077a-141">When you use **PromptForCredential** , you can specify the caption, messages, and user name that appear in the message box.</span></span>

<span data-ttu-id="4077a-142">如需詳細資訊，請參閱 SDK 中的 [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) 檔。</span><span class="sxs-lookup"><span data-stu-id="4077a-142">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="4077a-143">範例 6</span><span class="sxs-lookup"><span data-stu-id="4077a-143">Example 6</span></span>

```powershell
Set-ItemProperty "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds" -Name ConsolePrompting -Value $true
```

<span data-ttu-id="4077a-144">此範例示範如何修改登錄，以在命令列提示使用者，而不是使用對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4077a-144">This example shows how to modify the registry so that the user is prompted at the command line, instead of by using a dialog box.</span></span>

<span data-ttu-id="4077a-145">該命令會建立 **ConsolePrompting** 登錄項目，並將它的值設為 True。</span><span class="sxs-lookup"><span data-stu-id="4077a-145">The command creates the **ConsolePrompting** registry entry and sets its value to True.</span></span> <span data-ttu-id="4077a-146">若要執行此命令，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4077a-146">To run this command, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="4077a-147">若要使用對話方塊來提示，請將 ConsolePrompting 的值設定為 false ($false) 或使用 `Remove-ItemProperty` Cmdlet 來刪除它。</span><span class="sxs-lookup"><span data-stu-id="4077a-147">To use a dialog box for prompting, set the value of the ConsolePrompting to false ($false) or use the `Remove-ItemProperty` cmdlet to delete it.</span></span>

<span data-ttu-id="4077a-148">ConsolePrompting 登錄專案適用于某些主機程式，例如 PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="4077a-148">The ConsolePrompting registry entry works in some host programs, such as the PowerShell console.</span></span> <span data-ttu-id="4077a-149">它可能不適用於所有的主機程式。</span><span class="sxs-lookup"><span data-stu-id="4077a-149">It might not work in all host programs.</span></span>

### <span data-ttu-id="4077a-150">範例 7</span><span class="sxs-lookup"><span data-stu-id="4077a-150">Example 7</span></span>

<span data-ttu-id="4077a-151">這個範例示範如何建立認證物件，此物件與傳回的物件完全相同， `Get-Credential` 而不會提示使用者。</span><span class="sxs-lookup"><span data-stu-id="4077a-151">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="4077a-152">此方法需要純文字密碼，這可能會違反某些企業的安全性標準。</span><span class="sxs-lookup"><span data-stu-id="4077a-152">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="4077a-153">第一個命令會將使用者帳戶名稱儲存在 `$User` 參數中。</span><span class="sxs-lookup"><span data-stu-id="4077a-153">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="4077a-154">該值必須具有 "Domain\User" 或 "ComputerName\User" 格式。</span><span class="sxs-lookup"><span data-stu-id="4077a-154">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="4077a-155">第二個命令會使用 `ConvertTo-SecureString` Cmdlet，從純文字密碼建立安全字串。</span><span class="sxs-lookup"><span data-stu-id="4077a-155">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="4077a-156">命令使用 **AsPlainText** 參數指示字串為純文字，並使用 **Force** 參數確認您了解使用純文字的風險。</span><span class="sxs-lookup"><span data-stu-id="4077a-156">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="4077a-157">第三個命令會使用 `New-Object` Cmdlet，從和變數中的值建立 **PSCredential** 物件 `$User` `$PWord` 。</span><span class="sxs-lookup"><span data-stu-id="4077a-157">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="4077a-158">範例 8</span><span class="sxs-lookup"><span data-stu-id="4077a-158">Example 8</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="4077a-159">此命令會使用 Cmdlet 的 **Message** 和 **UserName** 參數 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="4077a-159">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="4077a-160">此命令的格式是為共用的指令碼和函式而設計。</span><span class="sxs-lookup"><span data-stu-id="4077a-160">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="4077a-161">在本例中，訊息會告知使用者為什麼需要認證，並讓使用者相信此為合法要求。</span><span class="sxs-lookup"><span data-stu-id="4077a-161">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="4077a-162">範例 9</span><span class="sxs-lookup"><span data-stu-id="4077a-162">Example 9</span></span>

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

<span data-ttu-id="4077a-163">此命令會從 Server01 遠端電腦取得認證。</span><span class="sxs-lookup"><span data-stu-id="4077a-163">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="4077a-164">此命令會使用 `Invoke-Command` Cmdlet `Get-Credential` 在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="4077a-164">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="4077a-165">輸出會顯示 `Get-Credential` 驗證提示中包含的遠端安全性訊息。</span><span class="sxs-lookup"><span data-stu-id="4077a-165">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="4077a-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4077a-166">PARAMETERS</span></span>

### <span data-ttu-id="4077a-167">-Credential</span><span class="sxs-lookup"><span data-stu-id="4077a-167">-Credential</span></span>

<span data-ttu-id="4077a-168">指定認證的使用者名稱，例如 **User01** 或 **Domain01\User01** 。</span><span class="sxs-lookup"><span data-stu-id="4077a-168">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="4077a-169">參數名稱 `-Credential` 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4077a-169">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="4077a-170">當您提交命令並指定使用者名稱時，系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="4077a-170">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="4077a-171">如果您省略此參數，系統就會提示您輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4077a-171">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="4077a-172">從 PowerShell 3.0 開始，如果您輸入不含網域的使用者名稱，則 `Get-Credential` 不會再于名稱之前插入反斜線。</span><span class="sxs-lookup"><span data-stu-id="4077a-172">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="4077a-173">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="4077a-173">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="4077a-174">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="4077a-174">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4077a-175">-Message</span><span class="sxs-lookup"><span data-stu-id="4077a-175">-Message</span></span>

<span data-ttu-id="4077a-176">指定顯示在驗證提示中的訊息。</span><span class="sxs-lookup"><span data-stu-id="4077a-176">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="4077a-177">此參數是針對在函式或指令碼中使用而設計。</span><span class="sxs-lookup"><span data-stu-id="4077a-177">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="4077a-178">您可以使用該訊息向使用者說明為何要求認證，以及認證的用途。</span><span class="sxs-lookup"><span data-stu-id="4077a-178">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="4077a-179">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4077a-179">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4077a-180">-UserName</span><span class="sxs-lookup"><span data-stu-id="4077a-180">-UserName</span></span>

<span data-ttu-id="4077a-181">指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4077a-181">Specifies a user name.</span></span> <span data-ttu-id="4077a-182">驗證提示要求使用者名稱的密碼。</span><span class="sxs-lookup"><span data-stu-id="4077a-182">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="4077a-183">根據預設，使用者名稱是空白的，且驗證提示會要求使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4077a-183">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="4077a-184">當驗證提示出現在對話方塊時，使用者可以編輯指定的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4077a-184">When the authentication prompt appears in a dialog box, the user can edit the specified user name.</span></span>
<span data-ttu-id="4077a-185">不過，當提示出現在命令列時，使用者無法變更使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4077a-185">However, the user cannot change the user name when the prompt appears at the command line.</span></span> <span data-ttu-id="4077a-186">當您在共用的函式或指令碼中使用此參數時，請考慮所有可能的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="4077a-186">When using this parameter in a shared function or script, consider all possible presentations.</span></span>

<span data-ttu-id="4077a-187">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4077a-187">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="4077a-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4077a-188">CommonParameters</span></span>

<span data-ttu-id="4077a-189">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4077a-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4077a-190">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4077a-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4077a-191">輸入</span><span class="sxs-lookup"><span data-stu-id="4077a-191">INPUTS</span></span>

### <span data-ttu-id="4077a-192">無</span><span class="sxs-lookup"><span data-stu-id="4077a-192">None</span></span>

<span data-ttu-id="4077a-193">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4077a-193">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="4077a-194">輸出</span><span class="sxs-lookup"><span data-stu-id="4077a-194">OUTPUTS</span></span>

### <span data-ttu-id="4077a-195">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="4077a-195">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="4077a-196">`Get-Credential` 傳回 credential 物件。</span><span class="sxs-lookup"><span data-stu-id="4077a-196">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="4077a-197">注意</span><span class="sxs-lookup"><span data-stu-id="4077a-197">NOTES</span></span>

<span data-ttu-id="4077a-198">您可以使用 **PSCredential** `Get-Credential` 在 Cmdlet 中建立並要求使用者驗證的 PSCredential 物件，例如具有 **Credential** 參數的使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="4077a-198">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="4077a-199">根據預設，驗證提示會出現在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="4077a-199">By default, the authentication prompt appears in a dialog box.</span></span> <span data-ttu-id="4077a-200">若要在命令列顯示驗證提示，請將 **ConsolePrompting** 登錄專案新增 (`HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting`) ，並將其值設定為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="4077a-200">To display the authentication prompt at the command line, add the **ConsolePrompting** registry entry (`HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting`) and set its value to **True**.</span></span>
<span data-ttu-id="4077a-201">如果 **ConsolePrompting** 登錄項目不存在，或其值為 False，驗證提示會出現在對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4077a-201">If the **ConsolePrompting** registry entry does not exist or if its value is False, the authentication prompt appears in a dialog box.</span></span> <span data-ttu-id="4077a-202">如需指示，請參閱範例。</span><span class="sxs-lookup"><span data-stu-id="4077a-202">For instructions, see the examples.</span></span>

<span data-ttu-id="4077a-203">**ConsolePrompting** 登錄專案適用于 PowerShell 主控台，但無法在所有主機程式中運作。</span><span class="sxs-lookup"><span data-stu-id="4077a-203">The **ConsolePrompting** registry entry works in the PowerShell console, but it does not work in all host programs.</span></span>

<span data-ttu-id="4077a-204">例如，在 (ISE) 的 PowerShell 整合式腳本環境中，它不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="4077a-204">For example, it has no effect in the PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="4077a-205">如需 **ConsolePrompting** 登錄項目效果的相關資訊，請參閱主機程式的說明主題。</span><span class="sxs-lookup"><span data-stu-id="4077a-205">For information about the effect of the **ConsolePrompting** registry entry, see the help topics for the host program.</span></span>

<span data-ttu-id="4077a-206">使用 PowerShell 安裝的所有提供者都不支援 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="4077a-206">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="4077a-207">從 PowerShell 3.0 開始，選取的 Cmdlet （例如和 Cmdlet）支援此 `Get-Content` 功能 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="4077a-207">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="4077a-208">相關連結</span><span class="sxs-lookup"><span data-stu-id="4077a-208">RELATED LINKS</span></span>

[<span data-ttu-id="4077a-209">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="4077a-209">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
