---
description: WSMan
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan 提供者
ms.openlocfilehash: 52a36a9246c3d98650eaeed352aa46fb67ed9bc0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206764"
---
# <a name="wsman-provider"></a><span data-ttu-id="cd86d-104">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="cd86d-104">WSMan Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="cd86d-105">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="cd86d-105">Provider name</span></span>

<span data-ttu-id="cd86d-106">WSMan</span><span class="sxs-lookup"><span data-stu-id="cd86d-106">WSMan</span></span>

## <a name="drives"></a><span data-ttu-id="cd86d-107">磁碟機</span><span class="sxs-lookup"><span data-stu-id="cd86d-107">Drives</span></span>

`WSMan:`

## <a name="short-description"></a><span data-ttu-id="cd86d-108">簡短描述</span><span class="sxs-lookup"><span data-stu-id="cd86d-108">Short description</span></span>

<span data-ttu-id="cd86d-109">提供存取適用於管理的 Web 服務 (WS-Management) 設定資訊。</span><span class="sxs-lookup"><span data-stu-id="cd86d-109">Provides access to Web Services for Management (WS-Management) configuration information.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="cd86d-110">詳細描述</span><span class="sxs-lookup"><span data-stu-id="cd86d-110">Detailed description</span></span>

<span data-ttu-id="cd86d-111">適用于 PowerShell 的 **WSMan** 提供者可讓您在本機或遠端電腦上新增、變更、清除和刪除 WS-Management 設定資料。</span><span class="sxs-lookup"><span data-stu-id="cd86d-111">The **WSMan** provider for PowerShell lets you add, change, clear, and delete WS-Management configuration data on local or remote computers.</span></span>

<span data-ttu-id="cd86d-112">**WSMan** 提供者會公開 PowerShell 磁片磁碟機，其目錄結構對應于 WS-Management 設定的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="cd86d-112">The **WSMan** provider exposes a PowerShell drive with a directory structure that corresponds to a logical grouping of WS-Management configuration settings.</span></span> <span data-ttu-id="cd86d-113">這些群組稱為容器。</span><span class="sxs-lookup"><span data-stu-id="cd86d-113">These groupings are known as containers.</span></span>

<span data-ttu-id="cd86d-114">從 Windows PowerShell 3.0 開始， **WSMan** 提供者已更新，可支援會話設定的新屬性，例如 **OutputBufferingMode** 。</span><span class="sxs-lookup"><span data-stu-id="cd86d-114">Beginning in Windows PowerShell 3.0, the **WSMan** provider has been updated to support new properties for session configurations, such as **OutputBufferingMode** .</span></span> <span data-ttu-id="cd86d-115">會話設定會顯示為磁片磁碟機外掛程式目錄中的專案 `WSMan:` ，而這些屬性會在每個會話設定中顯示為專案。</span><span class="sxs-lookup"><span data-stu-id="cd86d-115">The session configurations appear as items in the Plugin directory of the `WSMan:` drive and the properties appear as items in each session configuration.</span></span>

<span data-ttu-id="cd86d-116">**WSMan** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。</span><span class="sxs-lookup"><span data-stu-id="cd86d-116">The **WSMan** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="cd86d-117">Get-Location</span><span class="sxs-lookup"><span data-stu-id="cd86d-117">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="cd86d-118">Set-Location</span><span class="sxs-lookup"><span data-stu-id="cd86d-118">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="cd86d-119">Get-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-119">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="cd86d-120">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="cd86d-120">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="cd86d-121">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="cd86d-122">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> <span data-ttu-id="cd86d-123">您可以使用磁片磁碟機中的命令 `WSMan:` 來變更新屬性的值。</span><span class="sxs-lookup"><span data-stu-id="cd86d-123">You can use commands in the `WSMan:` drive to change the values of the new properties.</span></span> <span data-ttu-id="cd86d-124">不過，您無法使用 `WSMan:` PowerShell 2.0 中的磁片磁碟機來變更 Windows PowerShell 3.0 中引進的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd86d-124">However, you cannot use the `WSMan:` drive in PowerShell 2.0 to change properties that are introduced in Windows PowerShell 3.0.</span></span>
> <span data-ttu-id="cd86d-125">雖然不會產生任何錯誤，但命令對於變更這些設定並不有效，請使用 Windows PowerShell 3.0 中的 **WSMan** 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="cd86d-125">Although no error is generated, the commands are not effective To change these settings, use the **WSMan** drive in Windows PowerShell 3.0.</span></span>

### <a name="organization-of-the-wsman-drive"></a><span data-ttu-id="cd86d-126">WSMan：磁片磁碟機的組織</span><span class="sxs-lookup"><span data-stu-id="cd86d-126">Organization of the WSMan: Drive</span></span>

- <span data-ttu-id="cd86d-127">**用戶端** ：您可以設定 WS-Management 用戶端的各種層面。</span><span class="sxs-lookup"><span data-stu-id="cd86d-127">**Client** : You can configure various aspects of the WS-Management client.</span></span> <span data-ttu-id="cd86d-128">設定資訊是儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="cd86d-128">The configuration information is stored in the registry.</span></span>

- <span data-ttu-id="cd86d-129">**服務** ：您可以設定 WS-Management 服務的各種層面。</span><span class="sxs-lookup"><span data-stu-id="cd86d-129">**Service** : You can configure various aspects of the WS-Management service.</span></span>
  <span data-ttu-id="cd86d-130">設定資訊是儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="cd86d-130">The configuration information is stored in the registry.</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-131">服務設定有時稱為「伺服器設定」。</span><span class="sxs-lookup"><span data-stu-id="cd86d-131">Service configuration is sometimes referred to as Server configuration.</span></span>

- <span data-ttu-id="cd86d-132">**Shell** ：您可以設定 WS-Management Shell 的各個層面，例如允許遠端 Shell 存取的設定 ( **AllowRemoteShellAccess** ) 以及 ( **MaxConcurrentUsers** ) 允許的並行使用者數目上限。</span><span class="sxs-lookup"><span data-stu-id="cd86d-132">**Shell** : You can configure various aspects of the WS-Management shell, such as the setting to allow remote shell access ( **AllowRemoteShellAccess** ) and the maximum number of concurrent users allowed ( **MaxConcurrentUsers** ).</span></span>

- <span data-ttu-id="cd86d-133">接聽 **程式：您** 可以建立及設定接聽程式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-133">**Listener** : You can create and configure a listener.</span></span> <span data-ttu-id="cd86d-134">接聽程式是一種管理服務，可實作 WS-Management 通訊協定來傳送及接收訊息。</span><span class="sxs-lookup"><span data-stu-id="cd86d-134">A listener is a management service that implements the WS-Management protocol to send and to receive messages.</span></span>

- <span data-ttu-id="cd86d-135">**外掛程式** ： WS-Management 服務載入和使用外掛程式，以提供各種功能。</span><span class="sxs-lookup"><span data-stu-id="cd86d-135">**Plugin** : Plug-ins are loaded and used by the WS-Management service to provide various functions.</span></span> <span data-ttu-id="cd86d-136">PowerShell 預設會提供三個外掛程式：</span><span class="sxs-lookup"><span data-stu-id="cd86d-136">By default, PowerShell provides three plug-ins:</span></span>
  - <span data-ttu-id="cd86d-137">事件轉送外掛程式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-137">The Event Forwarding plug-in.</span></span>
  - <span data-ttu-id="cd86d-138">Microsoft PowerShell 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-138">The Microsoft.PowerShell plug-in.</span></span>
  - <span data-ttu-id="cd86d-139">Windows Management Instrumentation (WMI) 提供者外掛程式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-139">The Windows Management Instrumentation (WMI) Provider plug-in.</span></span>
  <span data-ttu-id="cd86d-140">這三個外掛程式支援事件轉送、設定和 WMI 存取。</span><span class="sxs-lookup"><span data-stu-id="cd86d-140">These three plug-ins support event forwarding, configuration, and WMI access.</span></span>

- <span data-ttu-id="cd86d-141">**ClientCertificate** ：您可以建立並設定用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="cd86d-141">**ClientCertificate** : You can create and configure a client certificate.</span></span>
  <span data-ttu-id="cd86d-142">將 WS-Management 用戶端設定為使用憑證驗證時，會使用用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="cd86d-142">A client certificate is used when the WS-Management client is configured to use certificate authentication.</span></span>

### <a name="directory-hierarchy-of-the-wsman-provider"></a><span data-ttu-id="cd86d-143">WSMan 提供者的目錄階層</span><span class="sxs-lookup"><span data-stu-id="cd86d-143">Directory Hierarchy of the WSMan Provider</span></span>

<span data-ttu-id="cd86d-144">本機電腦的 WSMan 提供者目錄階層如下所示。</span><span class="sxs-lookup"><span data-stu-id="cd86d-144">The directory hierarchy of the WSMan provider for the local computer is as follows.</span></span>

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

<span data-ttu-id="cd86d-145">遠端電腦的 WSMan 提供者目錄階層和本機電腦的目錄階層相同。</span><span class="sxs-lookup"><span data-stu-id="cd86d-145">The directory hierarchy of the WSMan provider for a remote computer is the same as a local computer.</span></span> <span data-ttu-id="cd86d-146">不過，若要存取遠端電腦的組態設定，您需要使用 [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan) 連線到遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="cd86d-146">However, in order to access the configuration settings of a remote computer, you need to make a connection to the remote computer using [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span> <span data-ttu-id="cd86d-147">一旦連線到遠端電腦之後，遠端電腦的名稱就會顯示於提供者中。</span><span class="sxs-lookup"><span data-stu-id="cd86d-147">Once a connection is made to a remote computer, the name of the remote computer shows up in the provider.</span></span>

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a><span data-ttu-id="cd86d-148">流覽 WSMan：磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="cd86d-148">Navigating the WSMan: Drive</span></span>

<span data-ttu-id="cd86d-149">此命令會使用 `Set-Location` Cmdlet 將目前的位置變更為 `WSMan:` 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="cd86d-149">This command uses the `Set-Location` cmdlet to change the current location to the `WSMan:` drive.</span></span>

```powershell
Set-Location WSMan:
```

<span data-ttu-id="cd86d-150">若要返回檔案系統磁碟機，請輸入磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="cd86d-150">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="cd86d-151">例如，輸入。</span><span class="sxs-lookup"><span data-stu-id="cd86d-151">For example, type.</span></span>

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a><span data-ttu-id="cd86d-152">流覽至遠端系統存放區位置</span><span class="sxs-lookup"><span data-stu-id="cd86d-152">Navigating to a remote system store location</span></span>

<span data-ttu-id="cd86d-153">此命令會使用 `Set-Location` 命令將目前的位置變更為遠端系統存放區位置中的根位置。</span><span class="sxs-lookup"><span data-stu-id="cd86d-153">This command uses the `Set-Location` command to change the current location to the root location in the remote system store location.</span></span> <span data-ttu-id="cd86d-154">使用反斜線 `\` 或正斜線 `/` 來指出磁片磁碟機的層級 `WSMan:` 。</span><span class="sxs-lookup"><span data-stu-id="cd86d-154">Use a backslash `\` or forward slash `/` to indicate a level of the `WSMan:` drive.</span></span>

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="cd86d-155">上述命令假設遠端系統的連線已經存在。</span><span class="sxs-lookup"><span data-stu-id="cd86d-155">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="displaying-the-contents-of-the-wsman-drive"></a><span data-ttu-id="cd86d-156">顯示 WSMan：磁片磁碟機的內容</span><span class="sxs-lookup"><span data-stu-id="cd86d-156">Displaying the Contents of the WSMan: Drive</span></span>

<span data-ttu-id="cd86d-157">此命令會使用 `Get-Childitem` Cmdlet 來顯示 Localhost 存放區位置中的 WS-Management 存放區。</span><span class="sxs-lookup"><span data-stu-id="cd86d-157">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the Localhost store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\Localhost
```

<span data-ttu-id="cd86d-158">如果您是在 `WSMan:` 磁片磁碟機中，您可以省略磁片磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="cd86d-158">If you are in the `WSMan:` drive, you can omit the drive name.</span></span>

<span data-ttu-id="cd86d-159">此命令會使用 `Get-Childitem` Cmdlet 來顯示遠端電腦 "SERVER01" 存放區位置中的 WS-Management 存放區。</span><span class="sxs-lookup"><span data-stu-id="cd86d-159">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the remote computer "SERVER01" store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="cd86d-160">上述命令假設遠端系統的連線已經存在。</span><span class="sxs-lookup"><span data-stu-id="cd86d-160">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a><span data-ttu-id="cd86d-161">設定 WSMAN：磁片磁碟機中的專案值</span><span class="sxs-lookup"><span data-stu-id="cd86d-161">Setting the value of items in the  WSMAN: drive</span></span>

<span data-ttu-id="cd86d-162">您可以使用 `Set-Item` Cmdlet 來變更磁片磁碟機中的設定 `WSMAN` 。</span><span class="sxs-lookup"><span data-stu-id="cd86d-162">You can use the `Set-Item` cmdlet to change configuration settings in the `WSMAN` drive.</span></span> <span data-ttu-id="cd86d-163">下列範例會將 **TrustedHosts** 值設定為接受尾碼為 "contoso.com" 的所有主機。</span><span class="sxs-lookup"><span data-stu-id="cd86d-163">The following example sets the **TrustedHosts** value to accept all hosts with the suffix "contoso.com".</span></span>

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

<span data-ttu-id="cd86d-164">此 `Set-Item` Cmdlet 支援附加值的額外參數 `-Concatenate` ，而不是變更它。</span><span class="sxs-lookup"><span data-stu-id="cd86d-164">The `Set-Item` cmdlet supports an additional parameter `-Concatenate` that appends a value instead of changing it.</span></span> <span data-ttu-id="cd86d-165">下列範例會將新值 "\*. domain2.com" 附加至儲存在中的舊值 `TrustedHost:`</span><span class="sxs-lookup"><span data-stu-id="cd86d-165">The following example will append a new value "\*.domain2.com" to the old value stored in `TrustedHost:`</span></span>

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a><span data-ttu-id="cd86d-166">在 WSMAN：磁片磁碟機中建立專案</span><span class="sxs-lookup"><span data-stu-id="cd86d-166">Creating items in the WSMAN: drive</span></span>

### <a name="creating-a-new-listener"></a><span data-ttu-id="cd86d-167">建立新的接聽程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-167">Creating a new listener</span></span>

<span data-ttu-id="cd86d-168">`New-Item`Cmdlet 會在提供者磁片磁碟機中建立專案。</span><span class="sxs-lookup"><span data-stu-id="cd86d-168">The `New-Item` cmdlet creates items within a provider drive.</span></span> <span data-ttu-id="cd86d-169">每個提供者都有您可以建立的不同專案類型。</span><span class="sxs-lookup"><span data-stu-id="cd86d-169">Each provider has different item types that you can create.</span></span> <span data-ttu-id="cd86d-170">在 `WSMAN:` 磁片磁碟機中，您可以建立接聽程式，並設定接聽 *程式以* 接收和回應遠端要求。</span><span class="sxs-lookup"><span data-stu-id="cd86d-170">In the `WSMAN:` drive, you can create *Listeners* which you configure to receive and respond to remote requests.</span></span> <span data-ttu-id="cd86d-171">下列命令會使用 Cmdlet 建立新的 HTTP 接聽程式 `New-Item` 。</span><span class="sxs-lookup"><span data-stu-id="cd86d-171">The following command creates a new HTTP listener using the `New-Item` cmdlet.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a><span data-ttu-id="cd86d-172">建立新外掛程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-172">Creating a new plug-in</span></span>

<span data-ttu-id="cd86d-173">此命令會建立適用於 WS-Management 服務的 (暫存器) 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-173">This command creates (registers) a plug-in for the WS-Management service.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a><span data-ttu-id="cd86d-174">建立新的資源專案</span><span class="sxs-lookup"><span data-stu-id="cd86d-174">Creating a new resource entry</span></span>

<span data-ttu-id="cd86d-175">此命令會在 TestPlugin 的 Resources 目錄中建立資源專案。</span><span class="sxs-lookup"><span data-stu-id="cd86d-175">This command creates a resource entry in the Resources directory of a TestPlugin.</span></span> <span data-ttu-id="cd86d-176">此命令假設已使用個別命令建立 TestPlugin。</span><span class="sxs-lookup"><span data-stu-id="cd86d-176">This command assumes that a TestPlugin has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a><span data-ttu-id="cd86d-177">建立資源的新安全性專案</span><span class="sxs-lookup"><span data-stu-id="cd86d-177">Creating a new security entry for a resource</span></span>

<span data-ttu-id="cd86d-178">此命令會在 Resource_5967683 (特定資源) 的 [安全性] 目錄中建立安全性項目。</span><span class="sxs-lookup"><span data-stu-id="cd86d-178">This command creates a security entry in the Security directory of Resource_5967683 (a specific resource).</span></span> <span data-ttu-id="cd86d-179">此命令假設已使用個別命令建立資源專案。</span><span class="sxs-lookup"><span data-stu-id="cd86d-179">This command assumes that the resource entry has been created using a separate command.</span></span>

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a><span data-ttu-id="cd86d-180">建立新的用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="cd86d-180">Creating a new Client Certificate</span></span>

<span data-ttu-id="cd86d-181">此命令會建立 WS-Management 用戶端可以使用的 **ClientCertificate** 專案。</span><span class="sxs-lookup"><span data-stu-id="cd86d-181">This command creates **ClientCertificate** entry that can be used by the WS-Management client.</span></span> <span data-ttu-id="cd86d-182">新的 **ClientCertificate** 會在 **ClientCertificate** 目錄下顯示為 "ClientCertificate_1234567890"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-182">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="cd86d-183">所有的參數都是必要項。</span><span class="sxs-lookup"><span data-stu-id="cd86d-183">All of the parameters are mandatory.</span></span> <span data-ttu-id="cd86d-184">**簽發者必須是簽發者** 憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="cd86d-184">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a><span data-ttu-id="cd86d-185">建立新的初始化參數</span><span class="sxs-lookup"><span data-stu-id="cd86d-185">Creating a new Initialization Parameter</span></span>

<span data-ttu-id="cd86d-186">此命令會在 "InitializationParameters" 目錄中建立名為 "testparametername" 的初始化參數。</span><span class="sxs-lookup"><span data-stu-id="cd86d-186">This command creates an Initialization parameter named "testparametername" in the "InitializationParameters" directory.</span></span> <span data-ttu-id="cd86d-187">此命令假設已使用個別的命令來建立 "TestPlugin"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-187">This command assumes that the "TestPlugin" has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a><span data-ttu-id="cd86d-188">動態參數</span><span class="sxs-lookup"><span data-stu-id="cd86d-188">Dynamic parameters</span></span>

<span data-ttu-id="cd86d-189">動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。</span><span class="sxs-lookup"><span data-stu-id="cd86d-189">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="address-string"></a><span data-ttu-id="cd86d-190">Address \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-190">Address \<String\></span></span>

<span data-ttu-id="cd86d-191">指定為其建立此接聽程式的位址。</span><span class="sxs-lookup"><span data-stu-id="cd86d-191">Specifies the address for which this listener was created.</span></span> <span data-ttu-id="cd86d-192">這個值可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="cd86d-192">The value can be one of the following:</span></span>

- <span data-ttu-id="cd86d-193">常值字串 "\*"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-193">The literal string "\*".</span></span> <span data-ttu-id="cd86d-194"> (萬用字元字元 (`*`) 讓命令系結所有網路介面卡上的所有 IP 位址。 ) </span><span class="sxs-lookup"><span data-stu-id="cd86d-194">(The wildcard character (`*`) makes the command bind all the IP addresses on all the network adapters.)</span></span>
- <span data-ttu-id="cd86d-195">常值字串 "IP："，後面接著 IPv4 以點分隔的十進位格式或 IPv6 複製的十六進位格式的有效 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="cd86d-195">The literal string "IP:" followed by a valid IP address in either IPv4 dotted-decimal format or in IPv6 cloned-hexadecimal format.</span></span>
- <span data-ttu-id="cd86d-196">常值字串 "MAC："，後面接著介面卡的 MAC 位址。</span><span class="sxs-lookup"><span data-stu-id="cd86d-196">The literal string "MAC:" followed by the MAC address of an adapter.</span></span>
  <span data-ttu-id="cd86d-197">例如： MAC： 32-a3-58-90-cc。</span><span class="sxs-lookup"><span data-stu-id="cd86d-197">For example: MAC:32-a3-58-90-be-cc.</span></span>

> [!NOTE]
> <span data-ttu-id="cd86d-198">Address 值是在建立接聽程式時建立的。</span><span class="sxs-lookup"><span data-stu-id="cd86d-198">The Address value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-199">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cd86d-199">Cmdlets supported</span></span>

- [<span data-ttu-id="cd86d-200">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-200">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a><span data-ttu-id="cd86d-201">Capability \<Enumeration\></span><span class="sxs-lookup"><span data-stu-id="cd86d-201">Capability \<Enumeration\></span></span>

<span data-ttu-id="cd86d-202">使用 *外掛程式* 時，此參數會指定此統一資源識別項 (URI) 所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="cd86d-202">When working with *Plug-ins* this parameter specifies an operation that is supported on this Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="cd86d-203">您必須針對 URI 支援的每個操作類型建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="cd86d-203">You have to create one entry for each type of operation that the URI supports.</span></span> <span data-ttu-id="cd86d-204">如果作業支援指定的作業，您可以指定任何有效的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd86d-204">You can specify any valid attributes for a given operation, if the operation supports it.</span></span>

<span data-ttu-id="cd86d-205">這些屬性包含 **SupportsFiltering** 和 **SupportsFragment** 。</span><span class="sxs-lookup"><span data-stu-id="cd86d-205">These attributes include **SupportsFiltering** and **SupportsFragment** .</span></span>

- <span data-ttu-id="cd86d-206">**Create** ： URI 上支援建立作業。</span><span class="sxs-lookup"><span data-stu-id="cd86d-206">**Create** : Create operations are supported on the URI.</span></span>
  - <span data-ttu-id="cd86d-207">如果建立作業支援這個概念，就會使用 **SupportFragment**  屬性。</span><span class="sxs-lookup"><span data-stu-id="cd86d-207">The **SupportFragment**  attribute is used if the Create operation supports the concept.</span></span>
  - <span data-ttu-id="cd86d-208">**SupportFiltering** 屬性對 Create 作業無效，應設定為 "False"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-208">The **SupportFiltering** attribute is NOT valid for Create operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-209">如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。</span><span class="sxs-lookup"><span data-stu-id="cd86d-209">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="cd86d-210">**Delete** ： URI 支援刪除作業。</span><span class="sxs-lookup"><span data-stu-id="cd86d-210">**Delete** : Delete operations are supported on the URI.</span></span>
  - <span data-ttu-id="cd86d-211">如果刪除作業支援這個概念，就會使用 **SupportFragment** 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd86d-211">The **SupportFragment** attribute is used if the Delete operation supports the concept.</span></span>
  - <span data-ttu-id="cd86d-212">**SupportFiltering** 屬性對刪除作業而言無效，應設定為 "False"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-212">The **SupportFiltering** attribute is NOT valid for Delete operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-213">如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。</span><span class="sxs-lookup"><span data-stu-id="cd86d-213">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="cd86d-214">**列舉** ： URI 支援列舉作業。</span><span class="sxs-lookup"><span data-stu-id="cd86d-214">**Enumerate** : Enumerate operations are supported on the URI.</span></span>
  - <span data-ttu-id="cd86d-215">列舉作業不支援 **SupportFragment** 屬性，應設定為 False。</span><span class="sxs-lookup"><span data-stu-id="cd86d-215">The **SupportFragment** attribute is NOT supported for Enumerate operations and should be set to False.</span></span>
  - <span data-ttu-id="cd86d-216">**SupportFiltering** 屬性是有效的，而且如果外掛程式支援篩選，這個屬性應該設定為 "True"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-216">The **SupportFiltering** attribute is valid, and if the plug-in supports filtering, this attribute should be set to "True".</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-217">如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。</span><span class="sxs-lookup"><span data-stu-id="cd86d-217">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="cd86d-218">**Get** ： URI 支援 get 作業。</span><span class="sxs-lookup"><span data-stu-id="cd86d-218">**Get** : Get operations are supported on the URI.</span></span>
  - <span data-ttu-id="cd86d-219">如果 Get 作業支援這個概念，就會使用 **SupportFragment** 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd86d-219">The **SupportFragment** attribute is used if the Get operation supports the concept.</span></span>
  - <span data-ttu-id="cd86d-220">**SupportFiltering** 屬性對 Get 作業無效，應設定為 "False"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-220">The **SupportFiltering** attribute is NOT valid for Get operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-221">如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。</span><span class="sxs-lookup"><span data-stu-id="cd86d-221">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="cd86d-222">**Invoke** ： URI 支援 invoke 作業。</span><span class="sxs-lookup"><span data-stu-id="cd86d-222">**Invoke** : Invoke operations are supported on the URI.</span></span>
  - <span data-ttu-id="cd86d-223">Invoke 作業不支援 **SupportFragment** 屬性，應設定為 False。</span><span class="sxs-lookup"><span data-stu-id="cd86d-223">The **SupportFragment** attribute is not supported for Invoke operations and should be set to False.</span></span>
  - <span data-ttu-id="cd86d-224">**SupportFiltering** 屬性無效，應設定為 "False"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-224">The **SupportFiltering** attribute is not valid and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-225">如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。</span><span class="sxs-lookup"><span data-stu-id="cd86d-225">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="cd86d-226">**Put** ： URI 支援 put 作業。</span><span class="sxs-lookup"><span data-stu-id="cd86d-226">**Put** : Put operations are supported on the URI.</span></span>
  - <span data-ttu-id="cd86d-227">如果 Put 作業支援這個概念，就會使用 **SupportFragment** 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd86d-227">The **SupportFragment** attribute is used if the Put operation supports the concept.</span></span>
  - <span data-ttu-id="cd86d-228">**SupportFiltering** 屬性對 Put 作業無效，應設定為 "False"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-228">The **SupportFiltering** attribute is not valid for Put operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-229">如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。</span><span class="sxs-lookup"><span data-stu-id="cd86d-229">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="cd86d-230">**訂閱** ： URI 支援訂閱作業。</span><span class="sxs-lookup"><span data-stu-id="cd86d-230">**Subscribe** : Subscribe operations are supported on the URI.</span></span>
  - <span data-ttu-id="cd86d-231">訂閱作業不支援 **SupportFragment** 屬性，應設定為 False。</span><span class="sxs-lookup"><span data-stu-id="cd86d-231">The **SupportFragment** attribute is not supported for Subscribe operations and should be set to False.</span></span>
  - <span data-ttu-id="cd86d-232">**SupportFiltering** 屬性對訂閱作業而言無效，應設定為 "False"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-232">The **SupportFiltering** attribute is not valid for Subscribe operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-233">如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。</span><span class="sxs-lookup"><span data-stu-id="cd86d-233">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="cd86d-234">**Shell** ： URI 支援 shell 作業。</span><span class="sxs-lookup"><span data-stu-id="cd86d-234">**Shell** : Shell operations are supported on the URI.</span></span>
  - <span data-ttu-id="cd86d-235">Shell 作業不支援 **SupportFragment** 屬性，應設定為 "False"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-235">The **SupportFragment** attribute is not supported for Shell operations and should be set to "False".</span></span>
  - <span data-ttu-id="cd86d-236">**SupportFiltering** 屬性對 Shell 作業無效，應設定為 "False"。</span><span class="sxs-lookup"><span data-stu-id="cd86d-236">The **SupportFiltering** attribute is not valid for Shell operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-237">如果也支援任何其他作業，則這項作業對 URI 而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="cd86d-237">This operation is not valid for a URI if ANY other operation is also supported.</span></span>
  > [!NOTE]
  > <span data-ttu-id="cd86d-238">如果已針對 URI 設定 Shell 操作，則會在 WS-Management (WinRM) 服務內部處理 Get、Put、Create、Delete、Invoke 及 Enumerate 操作來管理殼層。</span><span class="sxs-lookup"><span data-stu-id="cd86d-238">If a Shell operation is configured for a URI, Get, Put, Create, Delete, Invoke, and Enumerate operations are processed internally within the WS-Management (WinRM) service to manage shells.</span></span> <span data-ttu-id="cd86d-239">因此，外掛程式無法處理這些操作。</span><span class="sxs-lookup"><span data-stu-id="cd86d-239">As a result, the plug-in cannot handle the operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-240">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cd86d-240">Cmdlets supported</span></span>

- [<span data-ttu-id="cd86d-241">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-241">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a><span data-ttu-id="cd86d-242">CertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-242">CertificateThumbprint \<String\></span></span>

<span data-ttu-id="cd86d-243">指定服務憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="cd86d-243">Specifies the thumbprint of the service certificate.</span></span>

<span data-ttu-id="cd86d-244">這個值表示憑證 [指紋] 欄位中兩位數十六進位值的字串。</span><span class="sxs-lookup"><span data-stu-id="cd86d-244">This value represents the string of two-digit hexadecimal values in the Thumbprint field of the certificate.</span></span> <span data-ttu-id="cd86d-245">它會為有權執行此動作的使用者帳戶指定數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="cd86d-245">It specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="cd86d-246">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="cd86d-246">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="cd86d-247">它們只能對應到本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="cd86d-247">They can be mapped only to local user accounts, and they do not work with domain accounts.</span></span> <span data-ttu-id="cd86d-248">若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell 磁片磁碟機中的或 Cmdlet `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="cd86d-248">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell `Cert:` drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-249">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cd86d-249">Cmdlets supported</span></span>

- [<span data-ttu-id="cd86d-250">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-250">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a><span data-ttu-id="cd86d-251">Enabled \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="cd86d-251">Enabled \<Boolean\></span></span>

<span data-ttu-id="cd86d-252">指定接聽程式已啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="cd86d-252">Specifies whether the listener is enabled or disabled.</span></span> <span data-ttu-id="cd86d-253">預設值為 True。</span><span class="sxs-lookup"><span data-stu-id="cd86d-253">The default is True.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-254">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-254">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-255">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-255">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a><span data-ttu-id="cd86d-256">FileName (Plugin) \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-256">FileName (Plugin) \<String\></span></span>

<span data-ttu-id="cd86d-257">指定作業外掛程式的檔案名。</span><span class="sxs-lookup"><span data-stu-id="cd86d-257">Specifies the file name of the operations plug-in.</span></span> <span data-ttu-id="cd86d-258">當收到要求時，將會在使用者的內容中展開任何放置於此專案中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="cd86d-258">Any environment variables that are put in this entry will be expanded in the users' context when a request is received.</span></span> <span data-ttu-id="cd86d-259">由於每個使用者可能會有不同版本的相同環境變數，因此每個使用者可能會有不同的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-259">Because each user could have a different version of the same environment variable, each user could have a different plug-in.</span></span> <span data-ttu-id="cd86d-260">這個專案不能空白，且必須指向有效的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-260">This entry cannot be blank and must point to a valid plug-in.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-261">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-261">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-262">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-262">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a><span data-ttu-id="cd86d-263">HostName \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-263">HostName \<String\></span></span>

<span data-ttu-id="cd86d-264">指定 WS-Management (WinRM) 服務執行所在之電腦的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="cd86d-264">Specifies the host name of the computer on which the WS-Management (WinRM) service is running.</span></span>

<span data-ttu-id="cd86d-265">值必須是完整網域名稱、IPv4 或 IPv6 常值字串，或是萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cd86d-265">The value must be a fully qualified domain name, an IPv4 or IPv6 literal string, or a wildcard character.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-266">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-266">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-267">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-267">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a><span data-ttu-id="cd86d-268">Issuer \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-268">Issuer \<String\></span></span>

<span data-ttu-id="cd86d-269">指定簽發憑證的憑證授權單位名稱。</span><span class="sxs-lookup"><span data-stu-id="cd86d-269">Specifies the name of the certification authority that issued the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-270">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-270">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-271">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-271">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a><span data-ttu-id="cd86d-272">外掛程式 \<\> WS-Management 外掛程式是 (dll 的原生動態連結程式庫) </span><span class="sxs-lookup"><span data-stu-id="cd86d-272">Plugin \<\> WS-Management plug-ins are native dynamic link libraries (DLLs)</span></span>

<span data-ttu-id="cd86d-273">這會插入並擴充 WS-Management 的功能。</span><span class="sxs-lookup"><span data-stu-id="cd86d-273">that plug in to and extend the functionality of WS-Management .</span></span> <span data-ttu-id="cd86d-274">WSW-Management 外掛程式 API 提供的功能，可讓使用者藉由針對支援的資源 Uri 和作業來執行某些 Api 來寫入外掛程式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-274">The WSW-Management Plug-in API provides functionality that enables a user to write plug-ins by implementing certain APIs for supported resource URIs and operations.</span></span> <span data-ttu-id="cd86d-275">針對 WS-Management (WinRM) 服務或 Internet Information Services (IIS) 設定外掛程式之後，就會分別在 WS-Management 主機或 IIS 主機上載入外掛程式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-275">After the plug-ins are configured for either the WS-Management (WinRM) service or for Internet Information Services (IIS), the plug-ins are loaded in the WS-Management host or in the IIS host, respectively.</span></span> <span data-ttu-id="cd86d-276">系統會將遠端要求路由傳送到這些外掛程式的進入點來執行操作。</span><span class="sxs-lookup"><span data-stu-id="cd86d-276">Remote requests are routed to these plug-in entry points to perform operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-277">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-277">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-278">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-278">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a><span data-ttu-id="cd86d-279">Port \<Unsigned Short Integer\></span><span class="sxs-lookup"><span data-stu-id="cd86d-279">Port \<Unsigned Short Integer\></span></span>

<span data-ttu-id="cd86d-280">指定為其建立此接聽程式的 TCP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="cd86d-280">Specifies the TCP port for which this listener is created.</span></span> <span data-ttu-id="cd86d-281">您可以指定 1 到 65535 之間的任何值。</span><span class="sxs-lookup"><span data-stu-id="cd86d-281">You can specify any value from 1 through 65535.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-282">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-282">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-283">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-283">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="cd86d-284">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-284">Resource \<String\></span></span>

<span data-ttu-id="cd86d-285">指定代表不同類型的管理操作或值的端點。</span><span class="sxs-lookup"><span data-stu-id="cd86d-285">Specifies an endpoint that represents a distinct type of management operation or value.</span></span> <span data-ttu-id="cd86d-286">服務會公開一或多個資源，而有些資源可具有一個以上的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cd86d-286">A service exposes one or more resources, and some resources can have more than one instance.</span></span> <span data-ttu-id="cd86d-287">管理資源類似 WMI 類別或資料庫資料表，而執行個體類似類別的執行個體或資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd86d-287">A management resource is similar to a WMI class or to a database table, and an instance is similar to an instance of the class or to a row in the table.</span></span> <span data-ttu-id="cd86d-288">例如， **Win32_LogicalDisk** 類別代表資源。</span><span class="sxs-lookup"><span data-stu-id="cd86d-288">For example, the **Win32_LogicalDisk** class represents a resource.</span></span> <span data-ttu-id="cd86d-289">`Win32_LogicalDisk="C:\\"` 是資源的特定實例。</span><span class="sxs-lookup"><span data-stu-id="cd86d-289">`Win32_LogicalDisk="C:\\"` is a specific instance of the resource.</span></span>

<span data-ttu-id="cd86d-290">統一資源識別項 (URI) 包含資源的前置詞與路徑。</span><span class="sxs-lookup"><span data-stu-id="cd86d-290">A Uniform Resource Identifier (URI) contains a prefix and a path to a resource.</span></span>
<span data-ttu-id="cd86d-291">例如：</span><span class="sxs-lookup"><span data-stu-id="cd86d-291">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-292">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-292">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-293">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-293">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="cd86d-294">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-294">Resource \<String\></span></span>

<span data-ttu-id="cd86d-295">指定統一資源識別項 (URI) 來識別電腦上特定類型的資源，例如，磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="cd86d-295">Specifies the Uniform Resource Identifier (URI) that identifies a specific type of resource, such as a disk or a process, on a computer.</span></span>

<span data-ttu-id="cd86d-296">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="cd86d-296">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="cd86d-297">例如：</span><span class="sxs-lookup"><span data-stu-id="cd86d-297">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-298">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-298">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-299">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-299">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a><span data-ttu-id="cd86d-300">SDKVersion \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-300">SDKVersion \<String\></span></span>

<span data-ttu-id="cd86d-301">指定 SDK 中 WS-Management 外掛程式的版本。</span><span class="sxs-lookup"><span data-stu-id="cd86d-301">Specifies the version of the WS-Management plug-in SDK.</span></span> <span data-ttu-id="cd86d-302">唯一有效的值是</span><span class="sxs-lookup"><span data-stu-id="cd86d-302">The only valid value is</span></span>
1.

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-303">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-303">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-304">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-304">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a><span data-ttu-id="cd86d-305">Subject \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-305">Subject \<String\></span></span>

<span data-ttu-id="cd86d-306">指定由憑證識別的實體。</span><span class="sxs-lookup"><span data-stu-id="cd86d-306">Specifies the entity that is identified by the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-307">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-307">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-308">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-308">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a><span data-ttu-id="cd86d-309">Transport \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-309">Transport \<String\></span></span>

<span data-ttu-id="cd86d-310">指定要用來傳送和接收 WS-Management 通訊協定的要求和回應的傳輸。</span><span class="sxs-lookup"><span data-stu-id="cd86d-310">Specifies the transport to use to send and receive WS-Management protocol requests and responses.</span></span> <span data-ttu-id="cd86d-311">值必須是 HTTP 或 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="cd86d-311">The value must be either HTTP or HTTPS.</span></span>

<span data-ttu-id="cd86d-312">注意：建立接聽程式時，會設定傳輸值。</span><span class="sxs-lookup"><span data-stu-id="cd86d-312">Note: The Transport value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-313">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-313">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-314">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-314">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a><span data-ttu-id="cd86d-315">URI \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-315">URI \<String\></span></span>

<span data-ttu-id="cd86d-316">識別要根據 Sddl 參數值授權存取的 URI。</span><span class="sxs-lookup"><span data-stu-id="cd86d-316">Identifies the URI for which access is authorized based on the value of the Sddl parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-317">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-317">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-318">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-318">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a><span data-ttu-id="cd86d-319">URLPrefix \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-319">URLPrefix \<String\></span></span>

<span data-ttu-id="cd86d-320">要接受 HTTP 或 HTTPS 要求的 URL 首碼。</span><span class="sxs-lookup"><span data-stu-id="cd86d-320">A URL prefix on which to accept HTTP or HTTPS requests.</span></span> <span data-ttu-id="cd86d-321">這是一個字串，其中只包含字元 `[a-z]` 、 `[A-Z]` 、 `[9-0]` 、底線 (`_`) 和反斜線 (`/`) 。</span><span class="sxs-lookup"><span data-stu-id="cd86d-321">This is a string containing only the characters `[a-z]`, `[A-Z]`, `[9-0]`, underscore (`_`) and backslash (`/`).</span></span> <span data-ttu-id="cd86d-322">字串不能以反斜線開頭或結尾， (`/`) 。</span><span class="sxs-lookup"><span data-stu-id="cd86d-322">The string must not start with or end with a backslash (`/`).</span></span> <span data-ttu-id="cd86d-323">例如，如果電腦名稱稱為 "SampleComputer"，WS-Management 用戶端會 `http://SampleMachine/URLPrefix` 在目的地位址中指定。</span><span class="sxs-lookup"><span data-stu-id="cd86d-323">For example, if the computer name is "SampleComputer", the WS-Management client would specify `http://SampleMachine/URLPrefix` in the destination address.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-324">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-324">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-325">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-325">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a><span data-ttu-id="cd86d-326">Value \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-326">Value \<String\></span></span>

<span data-ttu-id="cd86d-327">指定初始化參數的值，這是用來指定設定選項的外掛程式特定值。</span><span class="sxs-lookup"><span data-stu-id="cd86d-327">Specifies the value of an initialization parameter, which is a plug-in-specific value that is used to specify configuration options.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-328">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-328">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-329">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-329">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a><span data-ttu-id="cd86d-330">XMLRenderingType \<String\></span><span class="sxs-lookup"><span data-stu-id="cd86d-330">XMLRenderingType \<String\></span></span>

<span data-ttu-id="cd86d-331">指定透過 **WSMAN_DATA** 物件將 XML 傳遞至外掛程式的格式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-331">Specifies the format in which XML is passed to plug-ins through the **WSMAN_DATA** object.</span></span> <span data-ttu-id="cd86d-332">以下是有效值：</span><span class="sxs-lookup"><span data-stu-id="cd86d-332">The following are valid values:</span></span>

- <span data-ttu-id="cd86d-333">Text：傳入的 XML 資料會包含在 **WSMAN_DATA_TYPE_TEXT** 結構中，這表示 xml 做為 **PCWSTR** 記憶體緩衝區。</span><span class="sxs-lookup"><span data-stu-id="cd86d-333">Text: Incoming XML data is contained in a **WSMAN_DATA_TYPE_TEXT** structure, which represents the XML as a **PCWSTR** memory buffer.</span></span>
- <span data-ttu-id="cd86d-334">XMLReader：內送 XML 資料包含在 **WSMAN_DATA_TYPE_WS_XML_READER** 結構中，它會將 xml 表示為 **XmlReader** 物件，該物件定義于 "WebServices .h" 標頭檔中。</span><span class="sxs-lookup"><span data-stu-id="cd86d-334">XMLReader: Incoming XML data is contained in a **WSMAN_DATA_TYPE_WS_XML_READER** structure, which represents the XML as an **XmlReader** object, which is defined in the "WebServices.h" header file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="cd86d-335">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="cd86d-335">Cmdlets Supported</span></span>

- [<span data-ttu-id="cd86d-336">New-Item</span><span class="sxs-lookup"><span data-stu-id="cd86d-336">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="cd86d-337">使用管線</span><span class="sxs-lookup"><span data-stu-id="cd86d-337">Using the pipeline</span></span>

<span data-ttu-id="cd86d-338">提供者 Cmdlet 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="cd86d-338">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="cd86d-339">您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。</span><span class="sxs-lookup"><span data-stu-id="cd86d-339">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="cd86d-340">若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="cd86d-340">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="cd86d-341">取得說明</span><span class="sxs-lookup"><span data-stu-id="cd86d-341">Getting help</span></span>

<span data-ttu-id="cd86d-342">從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。</span><span class="sxs-lookup"><span data-stu-id="cd86d-342">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="cd86d-343">若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 的參數來指定檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="cd86d-343">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a><span data-ttu-id="cd86d-344">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd86d-344">See also</span></span>

[<span data-ttu-id="cd86d-345">about_Providers</span><span class="sxs-lookup"><span data-stu-id="cd86d-345">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)
