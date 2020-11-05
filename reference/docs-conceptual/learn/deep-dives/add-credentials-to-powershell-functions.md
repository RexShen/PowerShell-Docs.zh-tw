---
title: 新增認證支援到 PowerShell 函式
description: 如何將認證參數新增至您的 PowerShell 指令碼、函式與 Cmdlet。
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: fb85d47121dc106ae04742254f418e2c727f6157
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143145"
---
# <a name="add-credential-support-to-powershell-functions"></a><span data-ttu-id="d8035-103">新增認證支援到 PowerShell 函式</span><span class="sxs-lookup"><span data-stu-id="d8035-103">Add Credential support to PowerShell functions</span></span>

> [!NOTE]
> <span data-ttu-id="d8035-104">本文的[原始版本][]出現在 [@joshduffney][] 所撰寫的部落格中。</span><span class="sxs-lookup"><span data-stu-id="d8035-104">The [original version][] of this article appeared on the blog written by [@joshduffney][].</span></span> <span data-ttu-id="d8035-105">此文章已經過編輯並刊登於此網站上。</span><span class="sxs-lookup"><span data-stu-id="d8035-105">This article has been edited for inclusion on this site.</span></span> <span data-ttu-id="d8035-106">PowerShell 小組感謝 Josh 分享此內容。</span><span class="sxs-lookup"><span data-stu-id="d8035-106">The PowerShell team thanks Josh for sharing this content with us.</span></span> <span data-ttu-id="d8035-107">請查看他在 [duffney.io][] 上的部落格。</span><span class="sxs-lookup"><span data-stu-id="d8035-107">Please check out his blog at [duffney.io][].</span></span>

<span data-ttu-id="d8035-108">此文章說明如何將認證參數新增至 PowerShell 函式，以及您想要這樣做的原因。</span><span class="sxs-lookup"><span data-stu-id="d8035-108">This article shows you how to add credential parameters to PowerShell functions and why you'd want to.</span></span> <span data-ttu-id="d8035-109">認證參數可讓您以不同的使用者身分執行函式或 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8035-109">A credential parameter is to allow you to run the function or cmdlet as a different user.</span></span> <span data-ttu-id="d8035-110">最常見的用法是以提高權限的使用者帳戶執行函式或 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8035-110">The most common use is to run the function or cmdlet as an elevated user account.</span></span>

<span data-ttu-id="d8035-111">例如，Cmdlet `New-ADUser` 具有 **Credential** 參數，您可以提供網域系統管理員認證來建立網域中的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d8035-111">For example, the cmdlet `New-ADUser` has a **Credential** parameter, which you could provide domain admin credentials to create an account in a domain.</span></span> <span data-ttu-id="d8035-112">假設您執行 PowerShell 工作階段的一般帳戶尚未擁有該存取權。</span><span class="sxs-lookup"><span data-stu-id="d8035-112">Assuming your normal account running the PowerShell session doesn't have that access already.</span></span>

## <a name="creating-credential-object"></a><span data-ttu-id="d8035-113">建立認證物件</span><span class="sxs-lookup"><span data-stu-id="d8035-113">Creating credential object</span></span>

<span data-ttu-id="d8035-114">[PSCredential][] 物件代表一組安全性認證，例如，使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="d8035-114">The [PSCredential][] object represents a set of security credentials such as a user name and password.</span></span> <span data-ttu-id="d8035-115">此物件可以當作參數傳遞到函式，該函式會以該認證物件中的使用者帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="d8035-115">The object can be passed as a parameter to a function that runs as the user account in that credential object.</span></span> <span data-ttu-id="d8035-116">有幾種方式可讓您建立認證物件。</span><span class="sxs-lookup"><span data-stu-id="d8035-116">There are a few ways that you can create a credential object.</span></span> <span data-ttu-id="d8035-117">建立認證物件的第一種方式是使用 PowerShell Cmdlet `Get-Credential`。</span><span class="sxs-lookup"><span data-stu-id="d8035-117">The first way to create a credential object is to use the PowerShell cmdlet `Get-Credential`.</span></span> <span data-ttu-id="d8035-118">當您在沒有參數的情況下執行時，其會提示您輸入使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="d8035-118">When you run without parameters, it prompts you for a username and password.</span></span> <span data-ttu-id="d8035-119">或者，您可以使用一些選擇性參數來呼叫 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8035-119">Or you can call the cmdlet with some optional parameters.</span></span>

<span data-ttu-id="d8035-120">若要提前指定網域名稱與使用者名稱，您可以使用 **Credential** 或 **UserName** 參數。</span><span class="sxs-lookup"><span data-stu-id="d8035-120">To specify the domain name and username ahead of time you can use either the **Credential** or **UserName** parameters.</span></span> <span data-ttu-id="d8035-121">當您使用 **UserName** 參數時，也必須提供 **Message** 值。</span><span class="sxs-lookup"><span data-stu-id="d8035-121">When you use the **UserName** parameter, you're also required to provide a **Message** value.</span></span> <span data-ttu-id="d8035-122">下列程式碼示範如何使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8035-122">The code below demonstrates using the cmdlet.</span></span> <span data-ttu-id="d8035-123">您也可以將認證物件儲存在變數中，如此便可多次使用該認證。</span><span class="sxs-lookup"><span data-stu-id="d8035-123">You can also store the credential object in a variable so that you can use the credential multiple times.</span></span> <span data-ttu-id="d8035-124">在下面的範例中，認證物件會儲存於 `$Cred` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d8035-124">In the example below, the credential object is stored in the variable `$Cred`.</span></span>

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

<span data-ttu-id="d8035-125">有時，您無法使用互動式方法來建立先前範例所示的認證物件。</span><span class="sxs-lookup"><span data-stu-id="d8035-125">Sometimes, you can't use the interactive method of creating credential objects shown in the previous example.</span></span> <span data-ttu-id="d8035-126">大部分的自動化工具都需要非互動式方法。</span><span class="sxs-lookup"><span data-stu-id="d8035-126">Most automation tools require a non-interactive method.</span></span> <span data-ttu-id="d8035-127">若要在沒有使用者互動的情況下建立認證，請建立包含密碼的安全字串。</span><span class="sxs-lookup"><span data-stu-id="d8035-127">To create a credential without user interaction, create a secure string containing the password.</span></span> <span data-ttu-id="d8035-128">接著，將安全字串與使用者名稱傳遞到 `System.Management.Automation.PSCredential()` 方法。</span><span class="sxs-lookup"><span data-stu-id="d8035-128">Then pass the secure string and user name to the `System.Management.Automation.PSCredential()` method.</span></span>

<span data-ttu-id="d8035-129">使用下列命令來建立包含密碼的安全字串：</span><span class="sxs-lookup"><span data-stu-id="d8035-129">Use the following command to create a secure string containing the password:</span></span>

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

<span data-ttu-id="d8035-130">**AsPlainText** 與 **Force** 參數都是必要參數。</span><span class="sxs-lookup"><span data-stu-id="d8035-130">Both the **AsPlainText** and **Force** parameters are required.</span></span> <span data-ttu-id="d8035-131">如果沒有那些參數，您就會收到一則訊息，警告您不應將純文字傳遞到安全字串。</span><span class="sxs-lookup"><span data-stu-id="d8035-131">Without those parameters, you receive a message warning that you shouldn't pass plain text into a secure string.</span></span> <span data-ttu-id="d8035-132">PowerShell 會傳回此警告，因為純文字密碼會記錄於各種記錄中。</span><span class="sxs-lookup"><span data-stu-id="d8035-132">PowerShell returns this warning because the plain text password gets recorded in various logs.</span></span> <span data-ttu-id="d8035-133">建立安全字串之後，您必須將其傳遞到 `PSCredential()` 方法以建立認證物件。</span><span class="sxs-lookup"><span data-stu-id="d8035-133">Once you have a secure string created, you need to pass it to the `PSCredential()` method to create the credential object.</span></span> <span data-ttu-id="d8035-134">在下面的範例中，`$password` 變數包含安全字串，而 `$Cred` 包含認證物件。</span><span class="sxs-lookup"><span data-stu-id="d8035-134">In the following example, the variable `$password` contains the secure string `$Cred` contains the credential object.</span></span>

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

<span data-ttu-id="d8035-135">既然您已了解如何建立認證物件，現在，您可以將認證參數新增到 PowerShell 函式。</span><span class="sxs-lookup"><span data-stu-id="d8035-135">Now that you know how to create credential objects, you can add credential parameters to your PowerShell functions.</span></span>

## <a name="adding-a-credential-parameter"></a><span data-ttu-id="d8035-136">新增認證參數</span><span class="sxs-lookup"><span data-stu-id="d8035-136">Adding a Credential Parameter</span></span>

<span data-ttu-id="d8035-137">就像任何其他參數一樣，您可以透過在函式的 `param` 區塊中新增此參數來開始。</span><span class="sxs-lookup"><span data-stu-id="d8035-137">Just like any other parameter, you start off by adding it in the `param` block of your function.</span></span>
<span data-ttu-id="d8035-138">建議您將參數命名為 `$Credential`，因為那是現有 PowerShell Cmdlet 所使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8035-138">It's recommended that you name the parameter `$Credential` because that's what existing PowerShell cmdlets use.</span></span> <span data-ttu-id="d8035-139">參數的類型應該是 `[System.Management.Automation.PSCredential]`。</span><span class="sxs-lookup"><span data-stu-id="d8035-139">The type of the parameter should be `[System.Management.Automation.PSCredential]`.</span></span>

<span data-ttu-id="d8035-140">下列範例顯示名為 `Get-Something` 之函式的參數區塊。</span><span class="sxs-lookup"><span data-stu-id="d8035-140">The following example shows the parameter block for a function called `Get-Something`.</span></span> <span data-ttu-id="d8035-141">其具有兩個參數：`$Name` 與 `$Credential`。</span><span class="sxs-lookup"><span data-stu-id="d8035-141">It has two parameters: `$Name` and `$Credential`.</span></span>

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

<span data-ttu-id="d8035-142">此範例中的程式碼就足以擁有運作中的認證參數，不過，您可以新增一些內容，以使其更為強固。</span><span class="sxs-lookup"><span data-stu-id="d8035-142">The code in this example is enough to have a working credential parameter, however there are a few things you can add to make it more robust.</span></span>

- <span data-ttu-id="d8035-143">新增 `[ValidateNotNull()]` 驗證屬性，以檢查要傳遞到 **Credential** 的值。</span><span class="sxs-lookup"><span data-stu-id="d8035-143">Add the `[ValidateNotNull()]` validation attribute to check that the value being passed to **Credential**.</span></span> <span data-ttu-id="d8035-144">如果參數值為 Null，此屬性就會防止函式以無效的認證執行。</span><span class="sxs-lookup"><span data-stu-id="d8035-144">If the parameter value is null, this attribute prevents the function from executing with invalid credentials.</span></span>

- <span data-ttu-id="d8035-145">加入 `[System.Management.Automation.Credential()]`。</span><span class="sxs-lookup"><span data-stu-id="d8035-145">Add `[System.Management.Automation.Credential()]`.</span></span> <span data-ttu-id="d8035-146">這可讓您以字串形式傳入使用者名稱，並以互動式提示輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="d8035-146">This allows you to pass in a username as a string and have an interactive prompt for the password.</span></span>

- <span data-ttu-id="d8035-147">將 `$Credential` 參數的預設值設定為 `[System.Management.Automation.PSCredential]::Empty`。</span><span class="sxs-lookup"><span data-stu-id="d8035-147">Set a default value for the `$Credential` parameter to `[System.Management.Automation.PSCredential]::Empty`.</span></span> <span data-ttu-id="d8035-148">您的函式可能會將此 `$Credential` 物件傳遞到現有的 PowerShell Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8035-148">Your function you might be passing this `$Credential` object to existing PowerShell cmdlets.</span></span> <span data-ttu-id="d8035-149">為函式內呼叫的 Cmdlet 提供 Null 值會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8035-149">Providing a null value to the cmdlet called inside your function causes an error.</span></span> <span data-ttu-id="d8035-150">提供空白的認證物件可避免這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8035-150">Providing an empty credential object avoids this error.</span></span>

> [!TIP]
> <span data-ttu-id="d8035-151">某些接受認證參數的 Cmdlet 不應支援 `[System.Management.Automation.PSCredential]::Empty`。</span><span class="sxs-lookup"><span data-stu-id="d8035-151">Some cmdlets that accept a credential parameter do not support `[System.Management.Automation.PSCredential]::Empty` as they should.</span></span> <span data-ttu-id="d8035-152">如需因應措施，請參閱[處理舊版 Cmdlet](#dealing-with-legacy-cmdlets) 一節。</span><span class="sxs-lookup"><span data-stu-id="d8035-152">See the [Dealing with Legacy Cmdlets](#dealing-with-legacy-cmdlets) section for a workaround.</span></span>

## <a name="using-credential-parameters"></a><span data-ttu-id="d8035-153">使用認證參數</span><span class="sxs-lookup"><span data-stu-id="d8035-153">Using credential parameters</span></span>

<span data-ttu-id="d8035-154">下列範例示範如何使用認證參數。</span><span class="sxs-lookup"><span data-stu-id="d8035-154">The following example demonstrates how to use credential parameters.</span></span> <span data-ttu-id="d8035-155">此範例顯示名為 `Set-RemoteRegistryValue` 的函式，而其不在 [The Pester Book][] 中。</span><span class="sxs-lookup"><span data-stu-id="d8035-155">This example shows a function called `Set-RemoteRegistryValue`, which is out of [The Pester Book][].</span></span> <span data-ttu-id="d8035-156">此函式會使用上一節所述的技術來定義認證參數。</span><span class="sxs-lookup"><span data-stu-id="d8035-156">This function defines the credential parameter using the techniques describe in the previous section.</span></span> <span data-ttu-id="d8035-157">此函式會使用函式所建立的 `$Credential` 變數來呼叫 `Invoke-Command`。</span><span class="sxs-lookup"><span data-stu-id="d8035-157">The function calls `Invoke-Command` using the `$Credential` variable created by the function.</span></span> <span data-ttu-id="d8035-158">這可讓您變更正在執行 `Invoke-Command` 的使用者。</span><span class="sxs-lookup"><span data-stu-id="d8035-158">This allows you to change the user who's running `Invoke-Command`.</span></span> <span data-ttu-id="d8035-159">由於 `$Credential` 的預設值是空白認證，因此，函式可以在未提供認證的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="d8035-159">Because the default value of `$Credential` is an empty credential, the function can run without providing credentials.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

<span data-ttu-id="d8035-160">下列各節說明提供認證給 `Set-RemoteRegistryValue` 的不同方法。</span><span class="sxs-lookup"><span data-stu-id="d8035-160">The following sections show different methods of providing credentials to `Set-RemoteRegistryValue`.</span></span>

### <a name="prompting-for-credentials"></a><span data-ttu-id="d8035-161">提示輸入認證</span><span class="sxs-lookup"><span data-stu-id="d8035-161">Prompting for credentials</span></span>

<span data-ttu-id="d8035-162">在執行階段使用以括弧 `()` 括起來的 `Get-Credential`，會導致先執行 `Get-credential`。</span><span class="sxs-lookup"><span data-stu-id="d8035-162">Using `Get-Credential` in parentheses `()` at run time causes the `Get-credential` to run first.</span></span> <span data-ttu-id="d8035-163">系統會提示您輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="d8035-163">You are prompted for a username and password.</span></span> <span data-ttu-id="d8035-164">您可以使用 `Get-credential` 的 **Credential** 或 **UserName** 參數，預先填入使用者名稱與網域。</span><span class="sxs-lookup"><span data-stu-id="d8035-164">You could use the **Credential** or **UserName** parameters of `Get-credential` to pre-populate the username and domain.</span></span> <span data-ttu-id="d8035-165">下列範例使用稱為展開的技術，將參數傳遞到 `Set-RemoteRegistryValue` 函式。</span><span class="sxs-lookup"><span data-stu-id="d8035-165">The following example uses a technique called splatting to pass parameters to the `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="d8035-166">如需有關展開的詳細資訊，請參閱 [about_Splatting][] 文章。</span><span class="sxs-lookup"><span data-stu-id="d8035-166">For more information about splatting, check out the [about_Splatting][] article.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![在執行階段取得認證](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

<span data-ttu-id="d8035-168">使用 `(Get-Credential)` 似乎很繁瑣。</span><span class="sxs-lookup"><span data-stu-id="d8035-168">Using `(Get-Credential)` seems cumbersome.</span></span> <span data-ttu-id="d8035-169">一般來說，當您只搭配使用者名稱使用 **Credential** 參數時，此 Cmdlet 會自動提示輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="d8035-169">Normally, when you use the **Credential** parameter with only a username, the cmdlet automatically prompts for the password.</span></span> <span data-ttu-id="d8035-170">`[System.Management.Automation.Credential()]` 屬性會啟用此行為。</span><span class="sxs-lookup"><span data-stu-id="d8035-170">The `[System.Management.Automation.Credential()]` attribute enables this behavior.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![提示輸入認證](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> <span data-ttu-id="d8035-172">為了設定顯示的登錄值，這些範例假設您已安裝 Windows 的 **Web 伺服器** 功能。</span><span class="sxs-lookup"><span data-stu-id="d8035-172">To set the registry value shown, these examples assume you have the **Web Server** features of Windows installed.</span></span> <span data-ttu-id="d8035-173">在必要時執行 `Install-WindowsFeature Web-Server` 與 `Install-WindowsFeature web-mgmt-tools`。</span><span class="sxs-lookup"><span data-stu-id="d8035-173">Run `Install-WindowsFeature Web-Server` and `Install-WindowsFeature web-mgmt-tools` if required.</span></span>

### <a name="provide-credentials-in-a-variable"></a><span data-ttu-id="d8035-174">在變數中提供認證。</span><span class="sxs-lookup"><span data-stu-id="d8035-174">Provide credentials in a variable</span></span>

<span data-ttu-id="d8035-175">您也可以提前填入認證變數，並將其傳遞到 `Set-RemoteRegistryValue` 函式的 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="d8035-175">You can also populate a credential variable ahead of time and pass it to the **Credential** parameter of `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="d8035-176">使用此方法搭配持續整合/持續部署 (CI/CD) 工具，例如 Jenkins、TeamCity 與 Octopus Deploy。</span><span class="sxs-lookup"><span data-stu-id="d8035-176">Use this method with Continuous Integration / Continuous Deployment (CI/CD) tools such as Jenkins, TeamCity, and Octopus Deploy.</span></span> <span data-ttu-id="d8035-177">如需使用 Jenkins 的範例，請參閱 Hodge 的部落格文章：[在 Windows 上使用 Jenkins 和 PowerShell 進行自動化 - 第 2 部分][]。</span><span class="sxs-lookup"><span data-stu-id="d8035-177">For an example using Jenkins, check out Hodge's blog post [Automating with Jenkins and PowerShell on Windows - Part 2][].</span></span>

<span data-ttu-id="d8035-178">此範例會使用 .NET 方法，來建立認證物件與要傳入密碼的安全字串。</span><span class="sxs-lookup"><span data-stu-id="d8035-178">This example uses the .NET method to create the credential object and a secure string to pass in the password.</span></span>

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

<span data-ttu-id="d8035-179">在此範例中，安全字串會使用純文字密碼來建立。</span><span class="sxs-lookup"><span data-stu-id="d8035-179">For this example, the secure string is created using a clear text password.</span></span> <span data-ttu-id="d8035-180">先前提到的所有 CI/CD 都有一個安全方法，可在執行階段提供該密碼。</span><span class="sxs-lookup"><span data-stu-id="d8035-180">All of the previously mentioned CI/CD have a secure method of providing that password at run time.</span></span> <span data-ttu-id="d8035-181">使用那些工具時，請以您使用之 CI/CD 工具內定義的變數取代純文字密碼。</span><span class="sxs-lookup"><span data-stu-id="d8035-181">When using those tools, replace the plain text password with the variable defined within the CI/CD tool you use.</span></span>

### <a name="run-without-credentials"></a><span data-ttu-id="d8035-182">在沒有認證的情況下執行</span><span class="sxs-lookup"><span data-stu-id="d8035-182">Run without credentials</span></span>

<span data-ttu-id="d8035-183">由於 `$Credential` 預設為空白的認證物件，因此，您可以在沒有認證的情況下執行命令，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d8035-183">Since `$Credential` defaults to an empty credential object, you can run the command without credentials, as shown in this example:</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a><span data-ttu-id="d8035-184">處理舊版 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d8035-184">Dealing with legacy cmdlets</span></span>

<span data-ttu-id="d8035-185">並非所有 Cmdlet 都支援認證物件或允許空白認證。</span><span class="sxs-lookup"><span data-stu-id="d8035-185">Not all cmdlets support credential objects or allow empty credentials.</span></span> <span data-ttu-id="d8035-186">相反地，此 Cmdlet 需要使用者名稱與密碼參數作為字串。</span><span class="sxs-lookup"><span data-stu-id="d8035-186">Instead, the cmdlet wants username and password parameters as strings.</span></span> <span data-ttu-id="d8035-187">有幾種方法可以解決此限制。</span><span class="sxs-lookup"><span data-stu-id="d8035-187">There are a few ways to work around this limitation.</span></span>

### <a name="using-if-else-to-handle-empty-credentials"></a><span data-ttu-id="d8035-188">使用 if-else 來處理空白認證</span><span class="sxs-lookup"><span data-stu-id="d8035-188">Using if-else to handle empty credentials</span></span>

<span data-ttu-id="d8035-189">在此案例中，您想要執行的 Cmdlet 不接受空白的認證物件。</span><span class="sxs-lookup"><span data-stu-id="d8035-189">In this scenario, the cmdlet you want to run doesn't accept an empty credential object.</span></span> <span data-ttu-id="d8035-190">此範例只會在其不是空白時，將 **Credential** 參數新增至 `Invoke-Command`。</span><span class="sxs-lookup"><span data-stu-id="d8035-190">This example adds the **Credential** parameter to `Invoke-Command` only if it's not empty.</span></span> <span data-ttu-id="d8035-191">否則，其會在沒有 **Credential** 參數情況下執行 `Invoke-Command`。</span><span class="sxs-lookup"><span data-stu-id="d8035-191">Otherwise, it runs the `Invoke-Command` without the **Credential** parameter.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a><span data-ttu-id="d8035-192">使用展開來處理空白認證</span><span class="sxs-lookup"><span data-stu-id="d8035-192">Using splatting to handle empty credentials</span></span>

<span data-ttu-id="d8035-193">此範例會使用參數展開來呼叫舊版 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8035-193">This example uses parameter splatting to call the legacy cmdlet.</span></span> <span data-ttu-id="d8035-194">`$Credential` 物件已有條件地新增至雜湊表以進行展開，並避免重複執行 `Invoke-Command` 指令碼區塊的需求。</span><span class="sxs-lookup"><span data-stu-id="d8035-194">The `$Credential` object is conditionally added to the hash table for splatting and avoids the need to repeat the `Invoke-Command` script block.</span></span> <span data-ttu-id="d8035-195">若要深入了解如何在函式內部展開，請參閱[展開進階函式中的參數][]部落格文章。</span><span class="sxs-lookup"><span data-stu-id="d8035-195">To learn more about splatting inside functions, see the [Splatting Parameters Inside Advanced Functions][] blog post.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a><span data-ttu-id="d8035-196">使用字串密碼</span><span class="sxs-lookup"><span data-stu-id="d8035-196">Working with string passwords</span></span>

<span data-ttu-id="d8035-197">`Invoke-Sqlcmd` Cmdlet 是接受字串作為密碼的 Cmdlet 範例。</span><span class="sxs-lookup"><span data-stu-id="d8035-197">The `Invoke-Sqlcmd` cmdlet is an example of a cmdlet that accepts a string as a password.</span></span>
<span data-ttu-id="d8035-198">`Invoke-Sqlcmd` 可讓您執行簡單的 SQL 插入、更新及刪除陳述式。</span><span class="sxs-lookup"><span data-stu-id="d8035-198">`Invoke-Sqlcmd` allows you to run simple SQL insert, update, and delete statements.</span></span> <span data-ttu-id="d8035-199">`Invoke-Sqlcmd` 需要純文字的使用者名稱與密碼，而不是更安全的認證物件。</span><span class="sxs-lookup"><span data-stu-id="d8035-199">`Invoke-Sqlcmd` requires a clear-text username and password rather than a more secure credential object.</span></span> <span data-ttu-id="d8035-200">此範例示範如何從認證物件擷取使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="d8035-200">This example shows how to extract the username and password from a credential object.</span></span>

<span data-ttu-id="d8035-201">此範例中的 `Get-AllSQLDatabases` 函式會呼叫 `Invoke-Sqlcmd` Cmdlet，來查詢 SQL 伺服器中的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="d8035-201">The `Get-AllSQLDatabases` function in this example calls the `Invoke-Sqlcmd` cmdlet to query a SQL server for all its databases.</span></span> <span data-ttu-id="d8035-202">此函式會使用先前範例中所使用的相同屬性，來定義 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="d8035-202">The function defines a **Credential** parameter with the same attribute used in the previous examples.</span></span> <span data-ttu-id="d8035-203">由於使用者名稱與密碼存在於 `$Credential` 變數中，因此，您可以擷取那些值來與 `Invoke-Sqlcmd` 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d8035-203">Since the username and password exist within the `$Credential` variable, you can extract those values for use with `Invoke-Sqlcmd`.</span></span>

<span data-ttu-id="d8035-204">使用者名稱可以從 `$Credential` 變數的 **UserName** 屬性中取得。</span><span class="sxs-lookup"><span data-stu-id="d8035-204">The user name is available from the **UserName** property of the `$Credential` variable.</span></span> <span data-ttu-id="d8035-205">若要取得密碼，您必須使用 `$Credential` 物件的 `GetNetworkCredential()` 方法。</span><span class="sxs-lookup"><span data-stu-id="d8035-205">To obtain the password, you have to use the `GetNetworkCredential()` method of the `$Credential` object.</span></span> <span data-ttu-id="d8035-206">值均會擷取到變數中，而變數會新增到可用來將參數展開到 `Invoke-Sqlcmd` 的雜湊表中。</span><span class="sxs-lookup"><span data-stu-id="d8035-206">The values are extracted into variables that are added to a hash table used for splatting parameters to `Invoke-Sqlcmd`.</span></span>

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a><span data-ttu-id="d8035-207">持續了解認證管理</span><span class="sxs-lookup"><span data-stu-id="d8035-207">Continued learning credential management</span></span>

<span data-ttu-id="d8035-208">安全地建立及儲存認證物件可能很難。</span><span class="sxs-lookup"><span data-stu-id="d8035-208">Creating and storing credential objects securely can be difficult.</span></span> <span data-ttu-id="d8035-209">下列資源可協助您維護 PowerShell 認證。</span><span class="sxs-lookup"><span data-stu-id="d8035-209">The following resources can help you maintain PowerShell credentials.</span></span>

- <span data-ttu-id="d8035-210">[BetterCredentials][]</span><span class="sxs-lookup"><span data-stu-id="d8035-210">[BetterCredentials][]</span></span>
- <span data-ttu-id="d8035-211">[Azure Key Vault][]</span><span class="sxs-lookup"><span data-stu-id="d8035-211">[Azure Key Vault][]</span></span>
- <span data-ttu-id="d8035-212">[Vault 專案][]</span><span class="sxs-lookup"><span data-stu-id="d8035-212">[Vault Project][]</span></span>
- <span data-ttu-id="d8035-213">[SecretManagement 模組][]</span><span class="sxs-lookup"><span data-stu-id="d8035-213">[SecretManagement module][]</span></span>

<!-- link references -->
[原始版本]: https://duffney.io/addcredentialstopowershellfunctions/
[original version]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Vault 專案]: https://www.vaultproject.io/
[Vault Project]: https://www.vaultproject.io/
[展開進階函式中的參數]: http://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Splatting Parameters Inside Advanced Functions]: http://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[在 Windows 上使用 Jenkins 和 PowerShell 進行自動化 - 第 2 部分]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2 \(英文\)
[Automating with Jenkins and PowerShell on Windows - Part 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[The Pester Book]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[SecretManagement 模組]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
[SecretManagement module]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
