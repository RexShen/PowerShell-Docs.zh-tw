---
description: 描述 PowerShell 提供者如何提供無法在命令列輕鬆存取之資料和元件的存取權。 資料是以一致的格式呈現，類似于檔案系統磁片磁碟機。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 08ea1679516b58e326eeb3d90fc1aaef4e983a34
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208303"
---
# <a name="about-providers"></a><span data-ttu-id="ae725-105">關於提供者</span><span class="sxs-lookup"><span data-stu-id="ae725-105">About Providers</span></span>

## <a name="short-description"></a><span data-ttu-id="ae725-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="ae725-106">Short description</span></span>
<span data-ttu-id="ae725-107">描述 PowerShell 提供者如何提供無法在命令列輕鬆存取之資料和元件的存取權。</span><span class="sxs-lookup"><span data-stu-id="ae725-107">Describes how PowerShell providers provide access to data and components that wouldn't otherwise be easily accessible at the command line.</span></span>
<span data-ttu-id="ae725-108">資料是以一致的格式呈現，類似于檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ae725-108">The data is presented in a consistent format that resembles a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="ae725-109">完整描述</span><span class="sxs-lookup"><span data-stu-id="ae725-109">Long description</span></span>

<span data-ttu-id="ae725-110">PowerShell 提供者是 .NET 程式，可讓您存取特定的資料存放區，以便更輕鬆地進行流覽和管理。</span><span class="sxs-lookup"><span data-stu-id="ae725-110">PowerShell providers are .NET programs that provide access to specialized data stores for easier viewing and management.</span></span> <span data-ttu-id="ae725-111">資料會出現在磁片磁碟機中，您可以像在硬碟一樣存取路徑中的資料。</span><span class="sxs-lookup"><span data-stu-id="ae725-111">The data appears in a drive, and you access the data in a path like you would on a hard disk drive.</span></span> <span data-ttu-id="ae725-112">您可以使用提供者支援的任何內建 Cmdlet 來管理提供者磁片磁碟機中的資料。</span><span class="sxs-lookup"><span data-stu-id="ae725-112">You can use any of the built-in cmdlets that the provider supports to manage the data in the provider drive.</span></span> <span data-ttu-id="ae725-113">而且，您可以使用特別針對資料設計的自訂 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae725-113">And, you can use custom cmdlets that are designed especially for the data.</span></span>

<span data-ttu-id="ae725-114">提供者也可以將動態參數新增至內建的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae725-114">The providers can also add dynamic parameters to the built-in cmdlets.</span></span> <span data-ttu-id="ae725-115">只有當您搭配提供者資料使用 Cmdlet 時，才能使用這些參數。</span><span class="sxs-lookup"><span data-stu-id="ae725-115">These parameters are only available when you use the cmdlet with the provider data.</span></span>

## <a name="built-in-providers"></a><span data-ttu-id="ae725-116">內建提供者</span><span class="sxs-lookup"><span data-stu-id="ae725-116">Built-in providers</span></span>

<span data-ttu-id="ae725-117">PowerShell 包含一組內建提供者，可讓您用來存取不同類型的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="ae725-117">PowerShell includes a set of built-in providers that you can use to access the different types of data stores.</span></span>

| <span data-ttu-id="ae725-118">提供者</span><span class="sxs-lookup"><span data-stu-id="ae725-118">Provider</span></span>   |   <span data-ttu-id="ae725-119">磁片磁碟機 (s) </span><span class="sxs-lookup"><span data-stu-id="ae725-119">Drive(s)</span></span>  |<span data-ttu-id="ae725-120">OutputType</span><span class="sxs-lookup"><span data-stu-id="ae725-120">OutputType</span></span>                                                    |
|----------- |------------ |--------------------------------------------------------------|
|<span data-ttu-id="ae725-121">Alias</span><span class="sxs-lookup"><span data-stu-id="ae725-121">Alias</span></span>       |<span data-ttu-id="ae725-122">Alias:</span><span class="sxs-lookup"><span data-stu-id="ae725-122">Alias:</span></span>       |<span data-ttu-id="ae725-123">System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="ae725-123">System.Management.Automation.AliasInfo</span></span>                        |
|<span data-ttu-id="ae725-124">憑證</span><span class="sxs-lookup"><span data-stu-id="ae725-124">Certificate</span></span> |<span data-ttu-id="ae725-125">Cert:</span><span class="sxs-lookup"><span data-stu-id="ae725-125">Cert:</span></span>        |<span data-ttu-id="ae725-126">Microsoft.powershell.commands.x509storelocation。</span><span class="sxs-lookup"><span data-stu-id="ae725-126">Microsoft.PowerShell.Commands.X509StoreLocation</span></span>               |
|            |             |<span data-ttu-id="ae725-127">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="ae725-127">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>|
|<span data-ttu-id="ae725-128">環境</span><span class="sxs-lookup"><span data-stu-id="ae725-128">Environment</span></span> |<span data-ttu-id="ae725-129">Env:</span><span class="sxs-lookup"><span data-stu-id="ae725-129">Env:</span></span>         |<span data-ttu-id="ae725-130">DictionaryEntry</span><span class="sxs-lookup"><span data-stu-id="ae725-130">System.Collections.DictionaryEntry</span></span>                            |
|<span data-ttu-id="ae725-131">FileSystem</span><span class="sxs-lookup"><span data-stu-id="ae725-131">FileSystem</span></span>  |<span data-ttu-id="ae725-132">C： ( \* ) </span><span class="sxs-lookup"><span data-stu-id="ae725-132">C: (\*)</span></span>       |<span data-ttu-id="ae725-133">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="ae725-133">System.IO.FileInfo</span></span>                                            |
|            |             |<span data-ttu-id="ae725-134">DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="ae725-134">System.IO.DirectoryInfo</span></span>                                       |
|<span data-ttu-id="ae725-135">函式</span><span class="sxs-lookup"><span data-stu-id="ae725-135">Function</span></span>    |<span data-ttu-id="ae725-136">函式：</span><span class="sxs-lookup"><span data-stu-id="ae725-136">Function:</span></span>    |<span data-ttu-id="ae725-137">System.Management.Automation.FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="ae725-137">System.Management.Automation.FunctionInfo</span></span>                     |
|<span data-ttu-id="ae725-138">登錄</span><span class="sxs-lookup"><span data-stu-id="ae725-138">Registry</span></span>    |<span data-ttu-id="ae725-139">HKLM： HKCU：</span><span class="sxs-lookup"><span data-stu-id="ae725-139">HKLM: HKCU:</span></span>  |<span data-ttu-id="ae725-140">Microsoft. RegistryKey</span><span class="sxs-lookup"><span data-stu-id="ae725-140">Microsoft.Win32.RegistryKey</span></span>                                   |
|<span data-ttu-id="ae725-141">變數</span><span class="sxs-lookup"><span data-stu-id="ae725-141">Variable</span></span>    |<span data-ttu-id="ae725-142">Variable:</span><span class="sxs-lookup"><span data-stu-id="ae725-142">Variable:</span></span>    |<span data-ttu-id="ae725-143">System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="ae725-143">System.Management.Automation.PSVariable</span></span>                       |
|<span data-ttu-id="ae725-144">WSMan</span><span class="sxs-lookup"><span data-stu-id="ae725-144">WSMan</span></span>       |<span data-ttu-id="ae725-145">WSMan:</span><span class="sxs-lookup"><span data-stu-id="ae725-145">WSMan:</span></span>       |<span data-ttu-id="ae725-146">Microsoft.WSMan.Management.WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="ae725-146">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>        |

<span data-ttu-id="ae725-147"> (\ * ) 每個系統上的 FileSystem 磁片磁碟機各不相同。</span><span class="sxs-lookup"><span data-stu-id="ae725-147">(\*) The FileSystem drives vary on each system.</span></span>

<span data-ttu-id="ae725-148">您也可以建立自己的 PowerShell 提供者，而且可以安裝其他人所開發的提供者。</span><span class="sxs-lookup"><span data-stu-id="ae725-148">You can also create your own PowerShell providers, and you can install providers that others develop.</span></span> <span data-ttu-id="ae725-149">若要列出您的會話中可用的提供者，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-149">To list the providers that are available in your session, type:</span></span>

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a><span data-ttu-id="ae725-150">安裝和移除提供者</span><span class="sxs-lookup"><span data-stu-id="ae725-150">Installing and removing providers</span></span>

<span data-ttu-id="ae725-151">提供者通常會透過 PowerShell 模組安裝。</span><span class="sxs-lookup"><span data-stu-id="ae725-151">Providers are typically installed via PowerShell modules.</span></span> <span data-ttu-id="ae725-152">匯入模組會將提供者載入您的會話中。</span><span class="sxs-lookup"><span data-stu-id="ae725-152">Importing the module loads the provider into your session.</span></span> <span data-ttu-id="ae725-153">您無法卸載內建的提供者。</span><span class="sxs-lookup"><span data-stu-id="ae725-153">You can't uninstall the built-in providers.</span></span> <span data-ttu-id="ae725-154">您可以卸載其他模組所載入的提供者。</span><span class="sxs-lookup"><span data-stu-id="ae725-154">You can uninstall providers loaded by other modules.</span></span>

<span data-ttu-id="ae725-155">您可以使用 Cmdlet 從目前的會話中卸載提供者 `Remove-Module` 。</span><span class="sxs-lookup"><span data-stu-id="ae725-155">You can unload a provider from the current session using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="ae725-156">此 Cmdlet 不會卸載提供者，但它會讓提供者無法在會話中使用。</span><span class="sxs-lookup"><span data-stu-id="ae725-156">This cmdlet doesn't uninstall the provider, but it makes the provider unavailable in the session.</span></span>

<span data-ttu-id="ae725-157">您也可以使用 `Remove-PSDrive` Cmdlet 來移除目前會話中的任何磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ae725-157">You can also use the `Remove-PSDrive` cmdlet to remove any drive from the current session.</span></span> <span data-ttu-id="ae725-158">磁片磁碟機上的此資料不會受到影響，但該會話無法再使用該磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ae725-158">This data on the drive isn't affected, but the drive is no longer available in that session.</span></span>

## <a name="viewing-providers"></a><span data-ttu-id="ae725-159">查看提供者</span><span class="sxs-lookup"><span data-stu-id="ae725-159">Viewing providers</span></span>

<span data-ttu-id="ae725-160">若要在您的電腦上查看 PowerShell 提供者，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-160">To view the PowerShell providers on your computer, type:</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="ae725-161">輸出會列出內建提供者，以及您新增至會話的提供者。</span><span class="sxs-lookup"><span data-stu-id="ae725-161">The output lists the built-in providers and the providers that you added to the session.</span></span>

## <a name="the-provider-cmdlets"></a><span data-ttu-id="ae725-162">提供者 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae725-162">The provider cmdlets</span></span>

<span data-ttu-id="ae725-163">下列 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="ae725-163">The following cmdlets are designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ae725-164">您可以用相同的方式使用相同的 Cmdlet 來管理提供者公開的不同資料類型。</span><span class="sxs-lookup"><span data-stu-id="ae725-164">You can use the same cmdlets in the same way to manage the different types of data that providers expose.</span></span> <span data-ttu-id="ae725-165">在您瞭解如何管理某個提供者的資料之後，您可以使用來自任何提供者之資料的相同程式。</span><span class="sxs-lookup"><span data-stu-id="ae725-165">After you learn to manage the data of one provider, you can use the same procedures with the data from any provider.</span></span>

<span data-ttu-id="ae725-166">例如，Cmdlet 會 `New-Item` 建立新專案。</span><span class="sxs-lookup"><span data-stu-id="ae725-166">For example, the `New-Item` cmdlet creates a new item.</span></span> <span data-ttu-id="ae725-167">在 `C:` **FileSystem** 提供者所支援的磁片磁碟機中，您可以使用 `New-Item` 建立新的檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="ae725-167">In the `C:` drive that is supported by the **FileSystem** provider, you can use `New-Item` to create a new file or folder.</span></span> <span data-ttu-id="ae725-168">在 **登錄提供者所支援的磁片** 磁碟機中，您可以使用 `New-Item` 建立新的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="ae725-168">In the drives that are supported by the **Registry** provider, you can use `New-Item` to create a new registry key.</span></span> <span data-ttu-id="ae725-169">在 `Alias:` 磁片磁碟機中，您可以使用 `New-Item` 建立新的別名。</span><span class="sxs-lookup"><span data-stu-id="ae725-169">In the `Alias:` drive, you can use `New-Item` to create a new alias.</span></span>

<span data-ttu-id="ae725-170">如需下列任何 Cmdlet 的詳細資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-170">For detailed information about any of the following cmdlets, type:</span></span>

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a><span data-ttu-id="ae725-171">Get-childitem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae725-171">ChildItem cmdlets</span></span>

- [<span data-ttu-id="ae725-172">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="ae725-172">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a><span data-ttu-id="ae725-173">Content Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae725-173">Content Cmdlets</span></span>

- [<span data-ttu-id="ae725-174">Add-Content</span><span class="sxs-lookup"><span data-stu-id="ae725-174">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="ae725-175">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="ae725-175">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="ae725-176">Get-Content</span><span class="sxs-lookup"><span data-stu-id="ae725-176">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="ae725-177">Set-Content</span><span class="sxs-lookup"><span data-stu-id="ae725-177">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a><span data-ttu-id="ae725-178">Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae725-178">Item Cmdlets</span></span>

- [<span data-ttu-id="ae725-179">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="ae725-179">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="ae725-180">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="ae725-180">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="ae725-181">Get-Item</span><span class="sxs-lookup"><span data-stu-id="ae725-181">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="ae725-182">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="ae725-182">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="ae725-183">Move-Item</span><span class="sxs-lookup"><span data-stu-id="ae725-183">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="ae725-184">New-Item</span><span class="sxs-lookup"><span data-stu-id="ae725-184">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="ae725-185">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="ae725-185">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="ae725-186">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="ae725-186">Rename-Item</span></span>](xref:Microsoft.PowerShell.Management.Rename-Item)
- [<span data-ttu-id="ae725-187">Set-Item</span><span class="sxs-lookup"><span data-stu-id="ae725-187">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a><span data-ttu-id="ae725-188">ItemProperty Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae725-188">ItemProperty cmdlets</span></span>

- [<span data-ttu-id="ae725-189">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ae725-189">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="ae725-190">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ae725-190">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [<span data-ttu-id="ae725-191">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ae725-191">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="ae725-192">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ae725-192">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [<span data-ttu-id="ae725-193">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ae725-193">New-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [<span data-ttu-id="ae725-194">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ae725-194">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="ae725-195">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ae725-195">Rename-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [<span data-ttu-id="ae725-196">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ae725-196">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a><span data-ttu-id="ae725-197">Location Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae725-197">Location cmdlets</span></span>

- [<span data-ttu-id="ae725-198">Get-Location</span><span class="sxs-lookup"><span data-stu-id="ae725-198">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="ae725-199">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="ae725-199">Pop-Location</span></span>](xref:Microsoft.PowerShell.Management.Pop-Location)
- [<span data-ttu-id="ae725-200">Push-Location</span><span class="sxs-lookup"><span data-stu-id="ae725-200">Push-Location</span></span>](xref:Microsoft.PowerShell.Management.Push-Location)
- [<span data-ttu-id="ae725-201">Set-Location</span><span class="sxs-lookup"><span data-stu-id="ae725-201">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a><span data-ttu-id="ae725-202">路徑 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae725-202">Path cmdlets</span></span>

- [<span data-ttu-id="ae725-203">Join-Path</span><span class="sxs-lookup"><span data-stu-id="ae725-203">Join-Path</span></span>](xref:Microsoft.PowerShell.Management.Join-Path)
- [<span data-ttu-id="ae725-204">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="ae725-204">Convert-Path</span></span>](xref:Microsoft.PowerShell.Management.Convert-Path)
- [<span data-ttu-id="ae725-205">Split-Path</span><span class="sxs-lookup"><span data-stu-id="ae725-205">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)
- [<span data-ttu-id="ae725-206">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="ae725-206">Resolve-Path</span></span>](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [<span data-ttu-id="ae725-207">Test-Path</span><span class="sxs-lookup"><span data-stu-id="ae725-207">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a><span data-ttu-id="ae725-208">New-psdrive Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae725-208">PSDrive cmdlets</span></span>

- [<span data-ttu-id="ae725-209">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ae725-209">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="ae725-210">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ae725-210">New-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [<span data-ttu-id="ae725-211">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ae725-211">Remove-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a><span data-ttu-id="ae725-212">PSProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae725-212">PSProvider Cmdlets</span></span>

- [<span data-ttu-id="ae725-213">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="ae725-213">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a><span data-ttu-id="ae725-214">查看提供者資料</span><span class="sxs-lookup"><span data-stu-id="ae725-214">Viewing provider data</span></span>

<span data-ttu-id="ae725-215">提供者的主要優點是它會以熟悉且一致的方式公開其資料。</span><span class="sxs-lookup"><span data-stu-id="ae725-215">The primary benefit of a provider is that it exposes its data in a familiar and consistent way.</span></span> <span data-ttu-id="ae725-216">資料展示的模型是檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ae725-216">The model for data presentation is a file system drive.</span></span>

<span data-ttu-id="ae725-217">此提供者可讓您查看、流覽和變更資料存放區中的專案，就好像它們是檔案系統中的資料一樣。</span><span class="sxs-lookup"><span data-stu-id="ae725-217">The provider allows you to view, navigate, and change items in the data store as though they were data in a file system.</span></span> <span data-ttu-id="ae725-218">資料存放區是由它所支援的磁片磁碟機名稱存取。</span><span class="sxs-lookup"><span data-stu-id="ae725-218">The data store is accessed by the name of the drive that it supports.</span></span>

<span data-ttu-id="ae725-219">磁片磁碟機會列在 Cmdlet 的預設顯示中 `Get-PSProvider` ，但您可以使用 Cmdlet 取得提供者磁片磁碟機的相關資訊 `Get-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="ae725-219">The drive is listed in the default display of the `Get-PSProvider` cmdlet, but you can get information about the provider drive using the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="ae725-220">例如，若要取得 Function：磁片磁碟機的所有屬性，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-220">For example, to get all the properties of the Function: drive, type:</span></span>

```powershell
Get-PSDrive Function | Format-List *
```

<span data-ttu-id="ae725-221">您可以在提供者磁片磁碟機中查看和移動資料，就像在檔案系統磁片磁碟機上一樣。</span><span class="sxs-lookup"><span data-stu-id="ae725-221">You can view and move through the data in a provider drive just as you would on a file system drive.</span></span>

<span data-ttu-id="ae725-222">若要查看提供者磁片磁碟機的內容，請使用 Get-Item 或 Get-ChildItem Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae725-222">To view the contents of a provider drive, use the Get-Item or Get-ChildItem cmdlets.</span></span> <span data-ttu-id="ae725-223">輸入磁片磁碟機名稱，後面接著冒號 (： ) 。</span><span class="sxs-lookup"><span data-stu-id="ae725-223">Type the drive name followed by a colon (:).</span></span> <span data-ttu-id="ae725-224">例如，若要查看 Alias：磁片磁碟機的內容，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-224">For example, to view the contents of the Alias: drive, type:</span></span>

```powershell
Get-Item alias:
```

<span data-ttu-id="ae725-225">您可以在路徑中包含磁片磁碟機名稱，以從另一個磁片磁碟機查看及管理任何磁片磁碟機中的資料。</span><span class="sxs-lookup"><span data-stu-id="ae725-225">You can view and manage the data in any drive from another drive by including the drive name in the path.</span></span> <span data-ttu-id="ae725-226">例如，若要從另一個磁片磁碟機查看 HKLM：磁片磁碟機中的 HKLM\Software 登錄機碼，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-226">For example, to view the HKLM\Software registry key in the HKLM: drive from another drive, type:</span></span>

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

<span data-ttu-id="ae725-227">若要開啟磁片磁碟機，請使用 Set-Location Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae725-227">To open the drive, use the Set-Location cmdlet.</span></span> <span data-ttu-id="ae725-228">當您指定磁片磁碟機路徑時，請記住冒號。</span><span class="sxs-lookup"><span data-stu-id="ae725-228">Remember the colon when you specify the drive path.</span></span> <span data-ttu-id="ae725-229">例如，若要將您的位置變更為 Cert：磁片磁碟機的根目錄，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-229">For example, to change your location to the root directory of the Cert: drive, type:</span></span>

```powershell
Set-Location cert:
```

<span data-ttu-id="ae725-230">然後，若要查看 Cert：磁片磁碟機的內容，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-230">Then, to view the contents of the Cert: drive, type:</span></span>

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a><span data-ttu-id="ae725-231">透過階層式資料移動</span><span class="sxs-lookup"><span data-stu-id="ae725-231">Moving through hierarchical data</span></span>

<span data-ttu-id="ae725-232">您可以透過提供者磁片磁碟機來移動，就像硬碟一樣。</span><span class="sxs-lookup"><span data-stu-id="ae725-232">You can move through a provider drive just as you would a hard disk drive.</span></span>
<span data-ttu-id="ae725-233">如果資料是在專案內的專案階層中排列，請使用反斜線 (`\`) 來表示子專案。</span><span class="sxs-lookup"><span data-stu-id="ae725-233">If the data is arranged in a hierarchy of items within items, use a backslash (`\`) to indicate a child item.</span></span> <span data-ttu-id="ae725-234">請使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="ae725-234">Use the following format:</span></span>

```
drive:\location\child-location\...
```

<span data-ttu-id="ae725-235">例如，若要將您的位置變更為 HKLM\Software 登錄機碼，請輸入 Set-Location 命令，例如：</span><span class="sxs-lookup"><span data-stu-id="ae725-235">For example, to change your location to the HKLM\Software registry key, type a Set-Location command, such as:</span></span>

```powershell
Set-Location HKLM:\SOFTWARE\
```

<span data-ttu-id="ae725-236">如果完整名稱中的任何元素包含空格，您必須將名稱括在雙引號中 (`"`) 。</span><span class="sxs-lookup"><span data-stu-id="ae725-236">If any element in the fully qualified name includes spaces, you must enclose the name in double-quotation marks (`"`).</span></span> <span data-ttu-id="ae725-237">下列範例顯示包含空格的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ae725-237">The following example shows a fully qualified path that includes spaces.</span></span>

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

<span data-ttu-id="ae725-238">您也可以使用位置的相對參考。</span><span class="sxs-lookup"><span data-stu-id="ae725-238">You can also use relative references to locations.</span></span> <span data-ttu-id="ae725-239">點 (`.`) 代表目前的位置。</span><span class="sxs-lookup"><span data-stu-id="ae725-239">A dot (`.`) represents the current location.</span></span> <span data-ttu-id="ae725-240">例如，如果您是在登錄機 `HKLM:\Software\Microsoft` 碼中，而您想要列出機碼中的登錄子機碼 `HKLM:\Software\Microsoft\PowerShell` ，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ae725-240">For example, if you are in the `HKLM:\Software\Microsoft` registry key, and you want to list the registry subkeys in the `HKLM:\Software\Microsoft\PowerShell` key, type the following command:</span></span>

```powershell
Get-ChildItem .\PowerShell
```

<span data-ttu-id="ae725-241">此外，雙點 (`..`) 指的是您目前位置正上方的目錄或容器。</span><span class="sxs-lookup"><span data-stu-id="ae725-241">Also, double-dots (`..`) refers to the directory or container directly above your current location.</span></span> <span data-ttu-id="ae725-242">您可以使用雙點 (`..`) 來流覽提供者階層。</span><span class="sxs-lookup"><span data-stu-id="ae725-242">You can use double-dots (`..`) to navigate through a provider hierarchy.</span></span>

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a><span data-ttu-id="ae725-243">提供者首頁</span><span class="sxs-lookup"><span data-stu-id="ae725-243">Provider Home</span></span>

<span data-ttu-id="ae725-244">提供者也有一個 **主** 位置。</span><span class="sxs-lookup"><span data-stu-id="ae725-244">Providers also have a **Home** location.</span></span>  <span data-ttu-id="ae725-245">此位置會由 `PSDrives` 提供者的所有支援共用。</span><span class="sxs-lookup"><span data-stu-id="ae725-245">This location is shared by all `PSDrives` backed by the provider.</span></span> <span data-ttu-id="ae725-246">您可以藉由查看提供者的 **Home** 屬性來加以取出。</span><span class="sxs-lookup"><span data-stu-id="ae725-246">It can be retrieved by viewing the **Home** property of the provider.</span></span>

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

<span data-ttu-id="ae725-247">**FileSystem** 提供者是唯一具有 **Home** 預設值的提供者。</span><span class="sxs-lookup"><span data-stu-id="ae725-247">The **FileSystem** provider is the only provider that has a default value for **Home** .</span></span> <span data-ttu-id="ae725-248">它的值與相同 `$Home` 。</span><span class="sxs-lookup"><span data-stu-id="ae725-248">It's the same value as `$Home`.</span></span> <span data-ttu-id="ae725-249">如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="ae725-249">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="ae725-250">您可以使用屬性，為目前的會話設定提供者的 **主** 目錄。</span><span class="sxs-lookup"><span data-stu-id="ae725-250">You can set the **Home** directory for a provider, for the current session, using its property.</span></span>

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

<span data-ttu-id="ae725-251">`~`字元可以用來代表提供者的主目錄。</span><span class="sxs-lookup"><span data-stu-id="ae725-251">The `~` character can be used to represent the provider's home directory.</span></span>
<span data-ttu-id="ae725-252">如果提供者沒有設定 **主** 位置，您會看到錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae725-252">If the provider doesn't have a **Home** location set, you see an error.</span></span>

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a><span data-ttu-id="ae725-253">尋找動態參數</span><span class="sxs-lookup"><span data-stu-id="ae725-253">Finding dynamic parameters</span></span>

<span data-ttu-id="ae725-254">動態參數是由提供者新增至 Cmdlet 的 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="ae725-254">Dynamic parameters are cmdlet parameters that are added to a cmdlet by a provider.</span></span> <span data-ttu-id="ae725-255">只有當 Cmdlet 與新增的提供者搭配使用時，才能使用這些參數。</span><span class="sxs-lookup"><span data-stu-id="ae725-255">These parameters are available only when the cmdlet is used with the provider that added them.</span></span>

<span data-ttu-id="ae725-256">例如， `Cert:` 磁片磁碟機會將 **CodeSigningCert** 參數新增至 `Get-Item` 和 `Get-ChildItem` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae725-256">For example, the `Cert:` drive adds the **CodeSigningCert** parameter to the `Get-Item` and `Get-ChildItem` cmdlets.</span></span> <span data-ttu-id="ae725-257">只有當您在 `Get-Item` `Get-ChildItem` 磁片磁碟機中使用或時，才能使用此參數 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="ae725-257">You can use this parameter only when you use `Get-Item` or `Get-ChildItem` in the `Cert:` drive.</span></span>

<span data-ttu-id="ae725-258">如需提供者所支援動態參數的清單，請參閱提供者的說明檔。</span><span class="sxs-lookup"><span data-stu-id="ae725-258">For a list of the dynamic parameters that a provider supports, see the Help file for the provider.</span></span> <span data-ttu-id="ae725-259">輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-259">Type:</span></span>

```
Get-Help <provider-name>
```

<span data-ttu-id="ae725-260">例如：</span><span class="sxs-lookup"><span data-stu-id="ae725-260">For example:</span></span>

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a><span data-ttu-id="ae725-261">瞭解提供者</span><span class="sxs-lookup"><span data-stu-id="ae725-261">Learning about providers</span></span>

<span data-ttu-id="ae725-262">雖然所有提供者資料都會出現在磁片磁碟機中，而且您可以使用相同的方法來移動它們，但相似性會停止。</span><span class="sxs-lookup"><span data-stu-id="ae725-262">Although all provider data appears in drives and you use the same methods to move through them, the similarity stops there.</span></span> <span data-ttu-id="ae725-263">提供者所公開的資料存放區，可以像 Active Directory 位置和 Microsoft Exchange Server 信箱一樣變化。</span><span class="sxs-lookup"><span data-stu-id="ae725-263">The data stores that the provider exposes can be as varied as Active Directory locations and Microsoft Exchange Server mailboxes.</span></span>

<span data-ttu-id="ae725-264">如需個別 PowerShell 提供者的相關資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-264">For information about individual PowerShell providers, type:</span></span>

```
Get-Help <ProviderName>
```

<span data-ttu-id="ae725-265">例如：</span><span class="sxs-lookup"><span data-stu-id="ae725-265">For example:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="ae725-266">如需提供者的說明主題清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="ae725-266">For a list of Help topics about the providers, type:</span></span>

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a><span data-ttu-id="ae725-267">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae725-267">See also</span></span>

[<span data-ttu-id="ae725-268">about_Locations</span><span class="sxs-lookup"><span data-stu-id="ae725-268">about_Locations</span></span>](about_Locations.md)

[<span data-ttu-id="ae725-269">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="ae725-269">about_Path_Syntax</span></span>](about_Path_Syntax.md)

