---
description: 憑證
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 憑證提供者
ms.openlocfilehash: b3ac701f18ba57d9108a76b7c478b8514075b3ee
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207276"
---
# <a name="certificate-provider"></a><span data-ttu-id="8bf58-104">憑證提供者</span><span class="sxs-lookup"><span data-stu-id="8bf58-104">Certificate Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="8bf58-105">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="8bf58-105">Provider name</span></span>

<span data-ttu-id="8bf58-106">憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-106">Certificate</span></span>

## <a name="drives"></a><span data-ttu-id="8bf58-107">磁碟機</span><span class="sxs-lookup"><span data-stu-id="8bf58-107">Drives</span></span>

`Cert:`

## <a name="capabilities"></a><span data-ttu-id="8bf58-108">功能</span><span class="sxs-lookup"><span data-stu-id="8bf58-108">Capabilities</span></span>

<span data-ttu-id="8bf58-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="8bf58-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="8bf58-110">簡短描述</span><span class="sxs-lookup"><span data-stu-id="8bf58-110">Short description</span></span>

<span data-ttu-id="8bf58-111">提供 PowerShell 中 x.509 憑證存放區和憑證的存取權。</span><span class="sxs-lookup"><span data-stu-id="8bf58-111">Provides access to X.509 certificate stores and certificates in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="8bf58-112">詳細描述</span><span class="sxs-lookup"><span data-stu-id="8bf58-112">Detailed description</span></span>

<span data-ttu-id="8bf58-113">PowerShell **憑證** 提供者可讓您在 powershell 中取得、新增、變更、清除和刪除憑證和憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="8bf58-113">The PowerShell **Certificate** provider lets you get, add, change, clear, and delete certificates and certificate stores in PowerShell.</span></span>

<span data-ttu-id="8bf58-114">**憑證** 磁片磁碟機是階層式命名空間，其中包含您電腦上的憑證存放區和憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-114">The **Certificate** drive is a hierarchical namespace containing the certificate stores and certificates on your computer.</span></span>

<span data-ttu-id="8bf58-115">**憑證** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。</span><span class="sxs-lookup"><span data-stu-id="8bf58-115">The **Certificate** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="8bf58-116">Get-Location</span><span class="sxs-lookup"><span data-stu-id="8bf58-116">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="8bf58-117">Set-Location</span><span class="sxs-lookup"><span data-stu-id="8bf58-117">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="8bf58-118">Get-Item</span><span class="sxs-lookup"><span data-stu-id="8bf58-118">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="8bf58-119">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8bf58-119">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="8bf58-120">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="8bf58-120">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="8bf58-121">Move-Item</span><span class="sxs-lookup"><span data-stu-id="8bf58-121">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="8bf58-122">New-Item</span><span class="sxs-lookup"><span data-stu-id="8bf58-122">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="8bf58-123">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="8bf58-123">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="8bf58-124">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8bf58-124">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="8bf58-125">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8bf58-125">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="8bf58-126">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="8bf58-126">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="8bf58-127">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="8bf58-127">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="8bf58-128">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="8bf58-128">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="8bf58-129">此提供者公開的類型</span><span class="sxs-lookup"><span data-stu-id="8bf58-129">Types exposed by this provider</span></span>

<span data-ttu-id="8bf58-130">憑證磁片磁碟機會公開下列類型。</span><span class="sxs-lookup"><span data-stu-id="8bf58-130">The Certificate drive exposes the following types.</span></span>

- <span data-ttu-id="8bf58-131"> (Microsoft.powershell.commands.x509storelocation) 的商店位置，也就是高階容器，可將目前使用者和所有使用者的憑證組成群組。</span><span class="sxs-lookup"><span data-stu-id="8bf58-131">Store locations (Microsoft.PowerShell.Commands.X509StoreLocation), which are high-level containers that group the certificates for the current user and for all users.</span></span> <span data-ttu-id="8bf58-132">每個系統都有 CurrentUser 和 LocalMachine (所有使用者) 存放區位置。</span><span class="sxs-lookup"><span data-stu-id="8bf58-132">Each system has a CurrentUser and LocalMachine (all users) store location.</span></span>

- <span data-ttu-id="8bf58-133">憑證會儲存 (System.security.cryptography.x509certificates.x509certificate2. System.security.cryptography.x509certificates.x509store) ，也就是儲存和管理憑證的實體存放區。</span><span class="sxs-lookup"><span data-stu-id="8bf58-133">Certificates stores (System.Security.Cryptography.X509Certificates.X509Store), which are physical stores in which certificates are saved and managed.</span></span>

- <span data-ttu-id="8bf58-134">X.509 **system.security.cryptography.x509certificates.x509certificate2. X509Certificate2** 憑證，每個憑證都代表電腦上的一個 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-134">X.509 **System.Security.Cryptography.X509Certificates.X509Certificate2** certificates, each of which represent an X.509 certificate on the computer.</span></span>
  <span data-ttu-id="8bf58-135">憑證是由其指紋來識別。</span><span class="sxs-lookup"><span data-stu-id="8bf58-135">Certificates are identified by their thumbprints.</span></span>

## <a name="navigating-the-certificate-drive"></a><span data-ttu-id="8bf58-136">流覽憑證磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="8bf58-136">Navigating the Certificate drive</span></span>

<span data-ttu-id="8bf58-137">**憑證** 提供者會將憑證命名空間公開為 `Cert:` PowerShell 中的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8bf58-137">The **Certificate** provider exposes the certificate namespace as the `Cert:` drive in PowerShell.</span></span> <span data-ttu-id="8bf58-138">此命令會使用 `Set-Location` 命令將目前的位置變更為 LocalMachine 存放區位置中的根憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="8bf58-138">This command uses the `Set-Location` command to change the current location to the Root certificate store in the LocalMachine store location.</span></span> <span data-ttu-id="8bf58-139">使用反斜線 (\\) 或正斜線 (/) 來指出磁片磁碟機的層級 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="8bf58-139">Use a backslash (\\) or a forward slash (/) to indicate a level of the `Cert:` drive.</span></span>

```powershell
Set-Location Cert:
```

<span data-ttu-id="8bf58-140">您也可以使用其他任何 PowerShell 磁片磁碟機中的憑證提供者。</span><span class="sxs-lookup"><span data-stu-id="8bf58-140">You can also work with the certificate provider from any other PowerShell drive.</span></span> <span data-ttu-id="8bf58-141">若要從其他位置參照別名，請 `Cert:` 在路徑中使用磁片磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="8bf58-141">To reference an alias from another location, use the `Cert:` drive name in the path.</span></span>

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

<span data-ttu-id="8bf58-142">若要返回檔案系統磁碟機，請輸入磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="8bf58-142">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="8bf58-143">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="8bf58-143">For example, type:</span></span>

```powershell
Set-Location C:
```

> [!NOTE]
> <span data-ttu-id="8bf58-144">PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="8bf58-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="8bf58-145">和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="8bf58-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span>
> <span data-ttu-id="8bf58-146">和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="8bf58-146">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-contents-of-the-cert-drive"></a><span data-ttu-id="8bf58-147">顯示 Cert：磁片磁碟機的內容</span><span class="sxs-lookup"><span data-stu-id="8bf58-147">Displaying the Contents of the Cert: drive</span></span>

<span data-ttu-id="8bf58-148">此命令會使用 `Get-ChildItem` Cmdlet 來顯示 CurrentUser 憑證存放區位置中的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="8bf58-148">This command uses the `Get-ChildItem` cmdlet to display the certificate stores in the CurrentUser certificate store location.</span></span>

<span data-ttu-id="8bf58-149">如果您不在 `Cert:` 磁片磁碟機中，請使用絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="8bf58-149">If you are not in the `Cert:` drive, use an absolute path.</span></span>

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a><span data-ttu-id="8bf58-150">顯示 Cert：磁片磁碟機內的憑證屬性</span><span class="sxs-lookup"><span data-stu-id="8bf58-150">Displaying certificate properties within the Cert: drive</span></span>

<span data-ttu-id="8bf58-151">這個範例會取得具有的憑證 `Get-Item` ，並將它儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="8bf58-151">This example gets a certificate with `Get-Item` and stores it in a variable.</span></span>
<span data-ttu-id="8bf58-152">此範例會使用 ( **DnsNameList** 、 **EnhancedKeyUsageList** 、 **SendAsTrustedIssuer** ) 來顯示新的憑證腳本屬性 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="8bf58-152">The example shows the new certificate script properties ( **DnsNameList** , **EnhancedKeyUsageList** , **SendAsTrustedIssuer** ) using `Select-Object`.</span></span>

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a><span data-ttu-id="8bf58-153">尋找所有 CodeSigning 的憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-153">Find all CodeSigning certificates</span></span>

<span data-ttu-id="8bf58-154">此命令會使用 Cmdlet 的 **CodeSigningCert** 和 **遞迴** 參數 `Get-ChildItem` 來取得電腦上具有程式碼簽署授權單位的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-154">This command uses the **CodeSigningCert** and **Recurse** parameters of the `Get-ChildItem` cmdlet to get all of the certificates on the computer that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a><span data-ttu-id="8bf58-155">尋找過期的憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-155">Find expired certificates</span></span>

<span data-ttu-id="8bf58-156">此命令會使用 Cmdlet 的 **ExpiringInDays** 參數 `Get-ChildItem` 來取得將在接下來的30天內到期的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-156">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet to get certificates that will expire within the next 30 days.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a><span data-ttu-id="8bf58-157">尋找伺服器 SSL 憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-157">Find Server SSL Certificates</span></span>

<span data-ttu-id="8bf58-158">此命令會使用 Cmdlet 的 **SSLServerAuthentication** 參數 `Get-ChildItem` 來取得 My 和 WebHosting 存放區中的所有伺服器 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-158">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get all Server SSL Certificates in the My and WebHosting stores.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a><span data-ttu-id="8bf58-159">在遠端電腦上尋找過期的憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-159">Find expired certificates on remote computers</span></span>

<span data-ttu-id="8bf58-160">此命令會使用 `Invoke-Command` Cmdlet `Get-ChildItem` 在 Srv01 和 Srv02 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="8bf58-160">This command uses the `Invoke-Command` cmdlet to run a `Get-ChildItem` command on the Srv01 and Srv02 computers.</span></span> <span data-ttu-id="8bf58-161">**ExpiringInDays** 參數中零 (0) 的值會取得已過期之 Srv01 和 Srv02 電腦上的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-161">A value of zero (0) in the **ExpiringInDays** parameter gets certificates on the Srv01 and Srv02 computers that have expired.</span></span>

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a><span data-ttu-id="8bf58-162">結合篩選器來尋找一組特定的憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-162">Combining filters to find a specific set of certificates</span></span>

<span data-ttu-id="8bf58-163">此命令會取得 LocalMachine 存放區位置中具有下列屬性的所有憑證：</span><span class="sxs-lookup"><span data-stu-id="8bf58-163">This command gets all certificates in the LocalMachine store location that have the following attributes:</span></span>

- <span data-ttu-id="8bf58-164">其 DNS 名稱中的 "fabrikam"</span><span class="sxs-lookup"><span data-stu-id="8bf58-164">"fabrikam" in their DNS name</span></span>
- <span data-ttu-id="8bf58-165">EKU 中的「用戶端驗證」</span><span class="sxs-lookup"><span data-stu-id="8bf58-165">"Client Authentication" in their EKU</span></span>
- <span data-ttu-id="8bf58-166">`$true` **SendAsTrustedIssuer** 屬性的值</span><span class="sxs-lookup"><span data-stu-id="8bf58-166">a value of `$true` for the **SendAsTrustedIssuer** property</span></span>
- <span data-ttu-id="8bf58-167">在接下來的30天內不會過期。</span><span class="sxs-lookup"><span data-stu-id="8bf58-167">do not expire within the next 30 days.</span></span>

<span data-ttu-id="8bf58-168">**NotAfter** 屬性會儲存憑證到期日。</span><span class="sxs-lookup"><span data-stu-id="8bf58-168">The **NotAfter** property stores the certificate expiration date.</span></span>

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a><span data-ttu-id="8bf58-169">開啟憑證 MMC 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="8bf58-169">Opening the Certificates MMC Snap-in</span></span>

<span data-ttu-id="8bf58-170">此 `Invoke-Item` Cmdlet 會使用預設的應用程式來開啟您指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="8bf58-170">The `Invoke-Item` cmdlet will use the default application to open a path you specify.</span></span> <span data-ttu-id="8bf58-171">若為憑證，則預設應用程式是 [憑證] MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="8bf58-171">For certificates, the default application is the Certificates MMC snap-in.</span></span>

<span data-ttu-id="8bf58-172">此命令會開啟 [憑證] MMC 嵌入式管理單元來管理指定的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-172">This command opens the Certificates MMC snap-in to manage the specified certificate.</span></span>

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a><span data-ttu-id="8bf58-173">複製憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-173">Copying Certificates</span></span>

<span data-ttu-id="8bf58-174">**憑證** 提供者不支援複製憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-174">Copying certificates is not supported by the **Certificate** provider.</span></span> <span data-ttu-id="8bf58-175">當您嘗試複製憑證時，您會看到此錯誤。</span><span class="sxs-lookup"><span data-stu-id="8bf58-175">When you attempt to copy a certificate, you see this error.</span></span>

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a><span data-ttu-id="8bf58-176">移動憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-176">Moving Certificates</span></span>

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a><span data-ttu-id="8bf58-177">將所有 SSL 伺服器驗證憑證移至 WebHosting 存放區</span><span class="sxs-lookup"><span data-stu-id="8bf58-177">Move all SSL Server authentication certs to the WebHosting store</span></span>

<span data-ttu-id="8bf58-178">此命令會使用 `Move-Item` Cmdlet，將憑證從「我的存放區」移至 WebHosting 存放區。</span><span class="sxs-lookup"><span data-stu-id="8bf58-178">This command uses the `Move-Item` cmdlet to move a certificate from the My store to the WebHosting store.</span></span>

<span data-ttu-id="8bf58-179">`Move-Item` 將不會移動憑證存放區，而且不會將憑證移動至不同的存放區位置，例如，將憑證從 LocalMachine 移至 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="8bf58-179">`Move-Item` will not move certificate stores and it will not move certificates to a different store location, such as moving a certificate from LocalMachine to CurrentUser.</span></span> <span data-ttu-id="8bf58-180">`Move-Item`Cmdlet 會移動憑證，但不會移動私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="8bf58-180">The `Move-Item` cmdlet moves certificates, but it does not move private keys.</span></span>

<span data-ttu-id="8bf58-181">此命令會使用 Cmdlet 的 **SSLServerAuthentication** 參數 `Get-ChildItem` 來取得「我的」憑證存放區中的 SSL 伺服器驗證憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-181">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get SSL server authentication certificates in the MY certificate store.</span></span>

<span data-ttu-id="8bf58-182">傳回的憑證會透過管道傳送至 `Move-Item` Cmdlet，此 Cmdlet 會將憑證移至 WebHosting 存放區。</span><span class="sxs-lookup"><span data-stu-id="8bf58-182">The returned certificates are piped to the `Move-Item` cmdlet, which moves the certificates to the WebHosting store.</span></span>

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a><span data-ttu-id="8bf58-183">刪除憑證和私密金鑰</span><span class="sxs-lookup"><span data-stu-id="8bf58-183">Deleting Certificates and Private Keys</span></span>

<span data-ttu-id="8bf58-184">此 `Remove-Item` Cmdlet 會移除您指定的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-184">The `Remove-Item` cmdlet will remove certificates that you specify.</span></span> <span data-ttu-id="8bf58-185">`-DeleteKey`動態參數會刪除私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="8bf58-185">The `-DeleteKey` dynamic parameter deletes the private key.</span></span>

### <a name="delete-a-certificate-from-the-ca-store"></a><span data-ttu-id="8bf58-186">從 CA 存放區刪除憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-186">Delete a Certificate from the CA store</span></span>

<span data-ttu-id="8bf58-187">此命令會從 CA 憑證存放區刪除憑證，但會原封不動地保留相關聯的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="8bf58-187">This command deletes a certificate from the CA certificate store, but leaves the associated private key intact.</span></span>

<span data-ttu-id="8bf58-188">在 `Cert:` 磁片磁碟機中，此 `Remove-Item` Cmdlet 只支援 **DeleteKey** 、 **Path** 、 **WhatIf** 和 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="8bf58-188">In the `Cert:` drive, the `Remove-Item` cmdlet supports only the **DeleteKey** , **Path** , **WhatIf** , and **Confirm** parameters.</span></span> <span data-ttu-id="8bf58-189">會忽略所有其他參數。</span><span class="sxs-lookup"><span data-stu-id="8bf58-189">All other parameters are ignored.</span></span>

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a><span data-ttu-id="8bf58-190">使用 DNS 名稱中的萬用字元刪除憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-190">Delete a Certificate using a wildcards in the DNS name</span></span>

<span data-ttu-id="8bf58-191">此命令會刪除 DNS 名稱包含 "Fabrikam" 的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-191">This command deletes all certificates that have a DNS name that contains "Fabrikam".</span></span> <span data-ttu-id="8bf58-192">它會使用 Cmdlet 的 **DNSName** 參數 `Get-ChildItem` 來取得憑證，並使用 `Remove-Item` Cmdlet 來刪除它們。</span><span class="sxs-lookup"><span data-stu-id="8bf58-192">It uses the **DNSName** parameter of the `Get-ChildItem` cmdlet to get the certificates and the `Remove-Item` cmdlet to delete them.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a><span data-ttu-id="8bf58-193">從遠端電腦刪除私密金鑰</span><span class="sxs-lookup"><span data-stu-id="8bf58-193">Delete private keys from a remote computer</span></span>

<span data-ttu-id="8bf58-194">這一系列的命令會啟用委派，然後刪除遠端電腦上的憑證和相關聯的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="8bf58-194">This series of commands enables delegation and then deletes the certificate and associated private key on a remote computer.</span></span> <span data-ttu-id="8bf58-195">若要刪除遠端電腦上的私密金鑰，您必須使用委派的認證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-195">To delete a private key on a remote computer, you must use delegated credentials.</span></span>

<span data-ttu-id="8bf58-196">使用 `Enable-WSManCredSSP` Cmdlet 在 S1 遠端電腦上的用戶端上，啟用 (CredSSP) 驗證的認證安全性服務提供者。</span><span class="sxs-lookup"><span data-stu-id="8bf58-196">Use the `Enable-WSManCredSSP` cmdlet to enable Credential Security Service Provider (CredSSP) authentication on a client on the S1 remote computer.</span></span>
<span data-ttu-id="8bf58-197">CredSSP 允許委派的驗證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-197">CredSSP permits delegated authentication.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

<span data-ttu-id="8bf58-198">使用 `Connect-WSMan` Cmdlet 將 S1 電腦連接到本機電腦上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="8bf58-198">Use the `Connect-WSMan` cmdlet to connect the S1 computer to the WinRM service on the local computer.</span></span> <span data-ttu-id="8bf58-199">當此命令完成時，S1 電腦會出現在 PowerShell 的本機 `WSMan:` 磁片磁碟機中。</span><span class="sxs-lookup"><span data-stu-id="8bf58-199">When this command completes, the S1 computer appears in the local `WSMan:` drive in PowerShell.</span></span>

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

<span data-ttu-id="8bf58-200">現在，您可以使用 WSMan：磁片磁碟機中的 Set-Item Cmdlet，來啟用 WinRM 服務的 CredSSP 屬性。</span><span class="sxs-lookup"><span data-stu-id="8bf58-200">Now, you can use the Set-Item cmdlet in the WSMan: drive to enable the CredSSP attribute for the WinRM service.</span></span>

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

<span data-ttu-id="8bf58-201">使用 Cmdlet 在 s1 電腦上啟動遠端會話 `New-PSSession` ，並指定 CredSSP 驗證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-201">Start a remote session on the s1 computer using the `New-PSSession` cmdlet, and specify CredSSP authentication.</span></span> <span data-ttu-id="8bf58-202">將會話儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="8bf58-202">Saves the session in the `$s` variable.</span></span>

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

<span data-ttu-id="8bf58-203">最後，使用 `Invoke-Command` Cmdlet 在 `Remove-Item` 變數的會話中執行命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="8bf58-203">Finally, use the `Invoke-Command` cmdlet to run a `Remove-Item` command in the session in the `$s` variable.</span></span> <span data-ttu-id="8bf58-204">此 `Remove-Item` 命令會使用 **DeleteKey** 參數來移除私密金鑰以及指定的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-204">The `Remove-Item` command uses the **DeleteKey** parameter to remove the private key along with the specified certificate.</span></span>

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a><span data-ttu-id="8bf58-205">刪除過期的憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-205">Delete expired Certificates</span></span>

<span data-ttu-id="8bf58-206">此命令會使用 Cmdlet 的 **ExpiringInDays** 參數 `Get-ChildItem` ，其值為0，以取得已過期 WebHosting 存放區中的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-206">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet with a value of 0 to get certificates in the WebHosting store that have expired.</span></span>

<span data-ttu-id="8bf58-207">包含所傳回憑證的變數會透過管道傳送至 `Remove-Item` Cmdlet，以將其刪除。</span><span class="sxs-lookup"><span data-stu-id="8bf58-207">The variable containing the returned certificates is piped to the `Remove-Item` cmdlet, which deletes them.</span></span> <span data-ttu-id="8bf58-208">此命令會使用 **DeleteKey** 參數來刪除私密金鑰以及憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-208">The command uses the **DeleteKey** parameter to delete the private key along with the certificate.</span></span>

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a><span data-ttu-id="8bf58-209">建立憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-209">Creating Certificates</span></span>

<span data-ttu-id="8bf58-210">`New-Item`Cmdlet 不會在 **憑證** 提供者中建立新的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-210">The `New-Item` cmdlet does not create new certificates in the **Certificate** provider.</span></span> <span data-ttu-id="8bf58-211">使用 [new-selfsignedcertificate 指令程式](/powershell/module/pkiclient/new-selfsignedcertificate) 來建立憑證以供測試之用。</span><span class="sxs-lookup"><span data-stu-id="8bf58-211">Use the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet to create a certificate for testing purposes.</span></span>

## <a name="creating-certificate-stores"></a><span data-ttu-id="8bf58-212">建立憑證存放區</span><span class="sxs-lookup"><span data-stu-id="8bf58-212">Creating Certificate Stores</span></span>

<span data-ttu-id="8bf58-213">在 Cert：磁片磁碟機中，此 `New-Item` Cmdlet 會在 LocalMachine 存放區位置中建立憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="8bf58-213">In the Cert: drive, the `New-Item` cmdlet creates certificate stores in the LocalMachine store location.</span></span> <span data-ttu-id="8bf58-214">它支援 **Name** 、 **Path** 、 **WhatIf** 和 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="8bf58-214">It supports the **Name** , **Path** , **WhatIf** , and **Confirm** parameters.</span></span> <span data-ttu-id="8bf58-215">會忽略所有其他參數。</span><span class="sxs-lookup"><span data-stu-id="8bf58-215">All other parameters are ignored.</span></span> <span data-ttu-id="8bf58-216">此命令會傳回代表新憑證存放區的 **system.security.cryptography.x509certificates.x509certificate2. system.security.cryptography.x509certificates.x509store** 。</span><span class="sxs-lookup"><span data-stu-id="8bf58-216">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

<span data-ttu-id="8bf58-217">此命令會在LocalMachine 存放區位置中建立名為 "CustomStore" 的新憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="8bf58-217">This command creates a new certificate store named "CustomStore" in the LocalMachine store location.</span></span>

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a><span data-ttu-id="8bf58-218">在遠端電腦上建立新的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="8bf58-218">Create a new certificate store on a remote computer</span></span>

<span data-ttu-id="8bf58-219">此命令會在 Server01 電腦上的 LocalMachine 存放區位置中建立名為 "HostingStore" 的新憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="8bf58-219">This command creates a new certificate store named "HostingStore" in the LocalMachine store location on the Server01 computer.</span></span>

<span data-ttu-id="8bf58-220">此命令會使用 `Invoke-Command` Cmdlet `New-Item` 在 Server01 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="8bf58-220">The command uses the `Invoke-Command` cmdlet to run a `New-Item` command on the Server01 computer.</span></span> <span data-ttu-id="8bf58-221">此命令會傳回代表新憑證存放區的 **system.security.cryptography.x509certificates.x509certificate2. system.security.cryptography.x509certificates.x509store** 。</span><span class="sxs-lookup"><span data-stu-id="8bf58-221">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a><span data-ttu-id="8bf58-222">建立 WS-Man 的用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-222">Creating Client Certificates for WS-Man</span></span>

<span data-ttu-id="8bf58-223">此命令會建立 **ws-management** 用戶端可以使用的 **ClientCertificate** 專案。</span><span class="sxs-lookup"><span data-stu-id="8bf58-223">This command creates **ClientCertificate** entry that can be used by the **WS-Management** client.</span></span> <span data-ttu-id="8bf58-224">新的 **ClientCertificate** 會在 **ClientCertificate** 目錄下顯示為 "ClientCertificate_1234567890"。</span><span class="sxs-lookup"><span data-stu-id="8bf58-224">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="8bf58-225">所有的參數都是必要項。</span><span class="sxs-lookup"><span data-stu-id="8bf58-225">All of the parameters are mandatory.</span></span> <span data-ttu-id="8bf58-226">**簽發者必須是簽發者** 憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="8bf58-226">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a><span data-ttu-id="8bf58-227">刪除憑證存放區</span><span class="sxs-lookup"><span data-stu-id="8bf58-227">Deleting Certificate Stores</span></span>

### <a name="delete-a-certificate-store-from-a-remote-computer"></a><span data-ttu-id="8bf58-228">從遠端電腦刪除憑證存放區</span><span class="sxs-lookup"><span data-stu-id="8bf58-228">Delete a certificate store from a remote computer</span></span>

<span data-ttu-id="8bf58-229">此命令會使用 `Invoke-Command` Cmdlet `Remove-Item` 在 S1 和 S2 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="8bf58-229">This command uses the `Invoke-Command` cmdlet to run a `Remove-Item` command on the S1 and S2 computers.</span></span> <span data-ttu-id="8bf58-230">此 `Remove-Item` 命令包含 **遞迴** 參數，它會在刪除存放區之前先刪除存放區中的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-230">The `Remove-Item` command includes the **Recurse** parameter, which deletes the certificates in the store before it deletes the store.</span></span>

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a><span data-ttu-id="8bf58-231">動態參數</span><span class="sxs-lookup"><span data-stu-id="8bf58-231">Dynamic parameters</span></span>

<span data-ttu-id="8bf58-232">動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。</span><span class="sxs-lookup"><span data-stu-id="8bf58-232">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span> <span data-ttu-id="8bf58-233">這些參數在憑證提供者的所有子目錄中都是有效的，但只對憑證有效。</span><span class="sxs-lookup"><span data-stu-id="8bf58-233">These parameters are valid in all subdirectories of the Certificate provider, but are effective only on certificates.</span></span>

> [!NOTE]
> <span data-ttu-id="8bf58-234">針對屬性進行篩選的參數 `EnhancedKeyUsageList` 也會傳回具有空白 `EnhancedKeyUsageList` 屬性值的專案。</span><span class="sxs-lookup"><span data-stu-id="8bf58-234">Parameters that perform filtering against the `EnhancedKeyUsageList` property also return items with an empty `EnhancedKeyUsageList` property value.</span></span>
> <span data-ttu-id="8bf58-235">具有空白 **EnhancedKeyUsageList** 的憑證可用於所有用途。</span><span class="sxs-lookup"><span data-stu-id="8bf58-235">Certificates that have an empty **EnhancedKeyUsageList** can be used for all purposes.</span></span>

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="8bf58-236">CodeSigningCert <System.Management.Automation.SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="8bf58-236">CodeSigningCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="8bf58-237">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bf58-237">Cmdlets supported</span></span>

- [<span data-ttu-id="8bf58-238">Get-Item</span><span class="sxs-lookup"><span data-stu-id="8bf58-238">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="8bf58-239">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8bf58-239">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="8bf58-240">此參數會取得其 **EnhancedKeyUsageList** 屬性值中具有「程式碼簽署」的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-240">This parameter gets certificates that have "Code Signing" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="deletekey-systemmanagementautomationswitchparameter"></a><span data-ttu-id="8bf58-241">DeleteKey <System.Management.Automation.SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="8bf58-241">DeleteKey <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="8bf58-242">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bf58-242">Cmdlets supported</span></span>

- [<span data-ttu-id="8bf58-243">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="8bf58-243">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

<span data-ttu-id="8bf58-244">此參數刪除憑證時，會刪除相關聯的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="8bf58-244">This parameter deletes the associated private key when it deletes the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bf58-245">若要刪除遠端電腦上存放區中與使用者憑證相關聯的私密金鑰 `Cert:\CurrentUser` ，您必須使用委派的認證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-245">To delete a private key that is associated with a user certificate in the `Cert:\CurrentUser` store on a remote computer, you must use delegated credentials.</span></span> <span data-ttu-id="8bf58-246">此 `Invoke-Command` Cmdlet 支援使用 **CredSSP** 參數的認證委派。</span><span class="sxs-lookup"><span data-stu-id="8bf58-246">The `Invoke-Command` cmdlet supports credential delegation using the **CredSSP** parameter.</span></span> <span data-ttu-id="8bf58-247">使用搭配 `Remove-Item` 和認證委派之前，您應該考慮任何安全性風險 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="8bf58-247">You should consider any security risks before using `Remove-Item` with `Invoke-Command` and credential delegation.</span></span>

<span data-ttu-id="8bf58-248">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="8bf58-248">This parameter was introduced in PowerShell 3.0.</span></span>

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a><span data-ttu-id="8bf58-249">DnsName <Microsoft.PowerShell.Commands.DnsNameRepresentation></span><span class="sxs-lookup"><span data-stu-id="8bf58-249">DnsName <Microsoft.PowerShell.Commands.DnsNameRepresentation></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="8bf58-250">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bf58-250">Cmdlets supported</span></span>

- [<span data-ttu-id="8bf58-251">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8bf58-251">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="8bf58-252">此參數會取得憑證的 **DNSNameList** 屬性中具有指定功能變數名稱或名稱模式的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-252">This parameter gets certificates that have the specified domain name or name pattern in the **DNSNameList** property of the certificate.</span></span> <span data-ttu-id="8bf58-253">此參數的值可以是「Unicode」或「ASCII」。</span><span class="sxs-lookup"><span data-stu-id="8bf58-253">The value of this parameter can either be "Unicode" or "ASCII".</span></span> <span data-ttu-id="8bf58-254">Punycode 值會轉換為 Unicode。</span><span class="sxs-lookup"><span data-stu-id="8bf58-254">Punycode values are converted to Unicode.</span></span> <span data-ttu-id="8bf58-255">`*`允許 () 的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8bf58-255">Wildcard characters (`*`) are permitted.</span></span>

<span data-ttu-id="8bf58-256">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="8bf58-256">This parameter was introduced in PowerShell 3.0.</span></span>

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="8bf58-257">>documentencryptioncert <SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="8bf58-257">DocumentEncryptionCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="8bf58-258">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bf58-258">Cmdlets supported</span></span>

- [<span data-ttu-id="8bf58-259">Get-Item</span><span class="sxs-lookup"><span data-stu-id="8bf58-259">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="8bf58-260">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8bf58-260">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="8bf58-261">此參數會取得其 **EnhancedKeyUsageList** 屬性值中具有「檔加密」的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-261">This parameter gets certificates that have "Document Encryption" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="eku-systemstring"></a><span data-ttu-id="8bf58-262">EKU <System.String></span><span class="sxs-lookup"><span data-stu-id="8bf58-262">EKU <System.String></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="8bf58-263">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bf58-263">Cmdlets supported</span></span>

- [<span data-ttu-id="8bf58-264">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8bf58-264">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="8bf58-265">此參數會取得憑證屬性中具有指定文字或文字模式的憑證 `EnhancedKeyUsageList` 。</span><span class="sxs-lookup"><span data-stu-id="8bf58-265">This parameter gets certificates that have the specified text or text pattern in the `EnhancedKeyUsageList` property of the certificate.</span></span> <span data-ttu-id="8bf58-266">`*`允許 () 的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8bf58-266">Wildcard characters (`*`) are permitted.</span></span> <span data-ttu-id="8bf58-267">`EnhancedKeyUsageList`屬性包含 EKU 的易記名稱和 OID 欄位。</span><span class="sxs-lookup"><span data-stu-id="8bf58-267">The `EnhancedKeyUsageList` property contains the friendly name and the OID fields of the EKU.</span></span>

<span data-ttu-id="8bf58-268">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="8bf58-268">This parameter was introduced in PowerShell 3.0.</span></span>

### <a name="expiringindays-systemint32"></a><span data-ttu-id="8bf58-269">ExpiringInDays <System.Int32></span><span class="sxs-lookup"><span data-stu-id="8bf58-269">ExpiringInDays <System.Int32></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="8bf58-270">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bf58-270">Cmdlets supported</span></span>

- [<span data-ttu-id="8bf58-271">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8bf58-271">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="8bf58-272">此參數會取得在指定天數內或之前到期的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-272">This parameter gets certificates that are expiring in or before the specified number of days.</span></span> <span data-ttu-id="8bf58-273">值為 0 (零) 可取得已過期的憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-273">A value of 0 (zero) gets certificates that have expired.</span></span>

<span data-ttu-id="8bf58-274">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="8bf58-274">This parameter was introduced in PowerShell 3.0.</span></span>

### <a name="itemtype-string"></a><span data-ttu-id="8bf58-275">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="8bf58-275">ItemType \<String\></span></span>

<span data-ttu-id="8bf58-276">這個參數可讓您指定所建立的專案類型 `New-Item` 。</span><span class="sxs-lookup"><span data-stu-id="8bf58-276">This parameter allows you to specify the type of item created by `New-Item`.</span></span>

<span data-ttu-id="8bf58-277">在 `Certificate` 磁片磁碟機中，允許下列值：</span><span class="sxs-lookup"><span data-stu-id="8bf58-277">In a `Certificate` drive, the following values are allowed:</span></span>

- <span data-ttu-id="8bf58-278">憑證提供者</span><span class="sxs-lookup"><span data-stu-id="8bf58-278">Certificate Provider</span></span>
- <span data-ttu-id="8bf58-279">憑證</span><span class="sxs-lookup"><span data-stu-id="8bf58-279">Certificate</span></span>
- <span data-ttu-id="8bf58-280">市集</span><span class="sxs-lookup"><span data-stu-id="8bf58-280">Store</span></span>
- <span data-ttu-id="8bf58-281">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="8bf58-281">StoreLocation</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="8bf58-282">支援的指令程式</span><span class="sxs-lookup"><span data-stu-id="8bf58-282">Cmdlets Supported</span></span>

- [<span data-ttu-id="8bf58-283">New-Item</span><span class="sxs-lookup"><span data-stu-id="8bf58-283">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a><span data-ttu-id="8bf58-284">SSLServerAuthentication <System.Management.Automation.SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="8bf58-284">SSLServerAuthentication <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="8bf58-285">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8bf58-285">Cmdlets supported</span></span>

- [<span data-ttu-id="8bf58-286">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8bf58-286">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="8bf58-287">只取得適用於 SSL 虛擬主機的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-287">Gets only server certificates for SSL web hosting.</span></span> <span data-ttu-id="8bf58-288">此參數會取得其屬性值中具有「伺服器驗證」的憑證 `EnhancedKeyUsageList` 。</span><span class="sxs-lookup"><span data-stu-id="8bf58-288">This parameter gets certificates that have "Server Authentication" in their `EnhancedKeyUsageList` property value.</span></span>

<span data-ttu-id="8bf58-289">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="8bf58-289">This parameter was introduced in PowerShell 3.0.</span></span>

## <a name="script-properties"></a><span data-ttu-id="8bf58-290">腳本屬性</span><span class="sxs-lookup"><span data-stu-id="8bf58-290">Script properties</span></span>

<span data-ttu-id="8bf58-291">新的腳本屬性已新增至代表憑證的 **x509Certificate2** 物件，可讓您輕鬆地搜尋及管理憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-291">New script properties have been added to the **x509Certificate2** object that represents the certificates to make it easy to search and manage the certificates.</span></span>

- <span data-ttu-id="8bf58-292">`DnsNameList`：若要填入 `DnsNameList` 屬性，憑證提供者會從 SubjectAlternativeName (SAN) 延伸模組的 DNSName 專案中複製內容。</span><span class="sxs-lookup"><span data-stu-id="8bf58-292">`DnsNameList`: To populate the `DnsNameList` property, the Certificate provider copies the content from the DNSName entry in the SubjectAlternativeName (SAN) extension.</span></span> <span data-ttu-id="8bf58-293">如果 SAN 延伸模組是空的，就會將憑證的 [主體] 欄位內容填入到屬性中。</span><span class="sxs-lookup"><span data-stu-id="8bf58-293">If the SAN extension is empty, the property is populated with content from the Subject field of the certificate.</span></span>

- <span data-ttu-id="8bf58-294">`EnhancedKeyUsageList`：若要填入 `EnhancedKeyUsageList` 屬性，憑證提供者會複製憑證中 EnhancedKeyUsage (EKU) 欄位的 OID 屬性，並為它建立易記名稱。</span><span class="sxs-lookup"><span data-stu-id="8bf58-294">`EnhancedKeyUsageList`: To populate the `EnhancedKeyUsageList` property, the Certificate provider copies the OID properties of the EnhancedKeyUsage (EKU) field in the certificate and creates a friendly name for it.</span></span>

- <span data-ttu-id="8bf58-295">`SendAsTrustedIssuer`：若要填入 `SendAsTrustedIssuer` 屬性，憑證提供者會複製 `SendAsTrustedIssuer` 憑證中的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bf58-295">`SendAsTrustedIssuer`: To populate the `SendAsTrustedIssuer` property, the Certificate provider copies the `SendAsTrustedIssuer` property from the certificate.</span></span>  <span data-ttu-id="8bf58-296">如需詳細資訊，請參閱 [管理用戶端驗證的受信任](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers)簽發者。</span><span class="sxs-lookup"><span data-stu-id="8bf58-296">For more information see [Management of trusted issuers for client authentication](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span></span>

<span data-ttu-id="8bf58-297">這些新功能可讓您根據憑證的 DNS 名稱和到期日來搜尋它們，並透過它們的增強金鑰使用方法 (EKU) 屬性值來區分用戶端和伺服器驗證憑證。</span><span class="sxs-lookup"><span data-stu-id="8bf58-297">These new features let you search for certificates based on their DNS names and expiration dates, and distinguish client and server authentication certificates by the value of their Enhanced Key Usage (EKU) properties.</span></span>

## <a name="using-the-pipeline"></a><span data-ttu-id="8bf58-298">使用管線</span><span class="sxs-lookup"><span data-stu-id="8bf58-298">Using the pipeline</span></span>

<span data-ttu-id="8bf58-299">提供者 Cmdlet 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="8bf58-299">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="8bf58-300">您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。</span><span class="sxs-lookup"><span data-stu-id="8bf58-300">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="8bf58-301">若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="8bf58-301">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="8bf58-302">取得說明</span><span class="sxs-lookup"><span data-stu-id="8bf58-302">Getting help</span></span>

<span data-ttu-id="8bf58-303">從 PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁片磁碟機中的行為。</span><span class="sxs-lookup"><span data-stu-id="8bf58-303">Beginning in PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="8bf58-304">若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用的 `-Path` 參數 `Get-Help` 來指定檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8bf58-304">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of `Get-Help` to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a><span data-ttu-id="8bf58-305">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bf58-305">See also</span></span>

[<span data-ttu-id="8bf58-306">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8bf58-306">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="8bf58-307">about_Signing</span><span class="sxs-lookup"><span data-stu-id="8bf58-307">about_Signing</span></span>](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[<span data-ttu-id="8bf58-308">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="8bf58-308">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[<span data-ttu-id="8bf58-309">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="8bf58-309">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[<span data-ttu-id="8bf58-310">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="8bf58-310">Get-PfxCertificate</span></span>](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
