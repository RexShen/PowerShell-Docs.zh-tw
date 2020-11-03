---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: c42d13707e850990a8dcacfdaacec2b382c224a1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204251"
---
# <span data-ttu-id="7fa60-103">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="7fa60-103">Register-PSRepository</span></span>

## <span data-ttu-id="7fa60-104">概要</span><span class="sxs-lookup"><span data-stu-id="7fa60-104">SYNOPSIS</span></span>
<span data-ttu-id="7fa60-105">註冊 PowerShell 存放庫。</span><span class="sxs-lookup"><span data-stu-id="7fa60-105">Registers a PowerShell repository.</span></span>

## <span data-ttu-id="7fa60-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7fa60-106">SYNTAX</span></span>

### <span data-ttu-id="7fa60-107">NameParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="7fa60-107">NameParameterSet (Default)</span></span>

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### <span data-ttu-id="7fa60-108">PSGalleryParameterSet</span><span class="sxs-lookup"><span data-stu-id="7fa60-108">PSGalleryParameterSet</span></span>

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="7fa60-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7fa60-109">DESCRIPTION</span></span>

<span data-ttu-id="7fa60-110">此 `Register-PSRepository` Cmdlet 會註冊 PowerShell 模組的預設存放庫。</span><span class="sxs-lookup"><span data-stu-id="7fa60-110">The `Register-PSRepository` cmdlet registers the default repository for PowerShell modules.</span></span> <span data-ttu-id="7fa60-111">註冊存放庫之後，您可以從 `Find-Module` 、和 Cmdlet 參考它 `Install-Module` `Publish-Module` 。</span><span class="sxs-lookup"><span data-stu-id="7fa60-111">After a repository is registered, you can reference it from the `Find-Module`, `Install-Module`, and `Publish-Module` cmdlets.</span></span> <span data-ttu-id="7fa60-112">已註冊的存放庫會成為和中的預設存放庫 `Find-Module` `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="7fa60-112">The registered repository becomes the default repository in `Find-Module` and `Install-Module`.</span></span>

<span data-ttu-id="7fa60-113">已註冊的存放庫是使用者特有的。</span><span class="sxs-lookup"><span data-stu-id="7fa60-113">Registered repositories are user-specific.</span></span> <span data-ttu-id="7fa60-114">它們並未註冊在整個系統內容中。</span><span class="sxs-lookup"><span data-stu-id="7fa60-114">They are not registered in a system-wide context.</span></span>

<span data-ttu-id="7fa60-115">每個已註冊的存放庫都會與 OneGet 封裝提供者相關聯，該提供者會使用 **PackageManagementProvider** 參數來指定。</span><span class="sxs-lookup"><span data-stu-id="7fa60-115">Each registered repository is associated with a OneGet package provider, which is specified with the **PackageManagementProvider** parameter.</span></span> <span data-ttu-id="7fa60-116">每個 OneGet 提供者都是設計來與特定類型的存放庫互動。</span><span class="sxs-lookup"><span data-stu-id="7fa60-116">Each OneGet provider is designed to interact with a specific type of repository.</span></span> <span data-ttu-id="7fa60-117">例如，NuGet 提供者是設計來與以 NuGet 為基礎的存放庫互動。</span><span class="sxs-lookup"><span data-stu-id="7fa60-117">For example, the NuGet provider is designed to interact with NuGet-based repositories.</span></span> <span data-ttu-id="7fa60-118">如果在註冊期間未指定 OneGet 提供者，PowerShellGet 會嘗試尋找可處理指定來源位置的 OneGet 提供者。</span><span class="sxs-lookup"><span data-stu-id="7fa60-118">If a OneGet provider is not specified during registration, PowerShellGet attempts to find a OneGet provider that can handle the specified source location.</span></span>

## <span data-ttu-id="7fa60-119">範例</span><span class="sxs-lookup"><span data-stu-id="7fa60-119">EXAMPLES</span></span>

### <span data-ttu-id="7fa60-120">範例1：註冊存放庫</span><span class="sxs-lookup"><span data-stu-id="7fa60-120">Example 1: Register a repository</span></span>

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

<span data-ttu-id="7fa60-121">第一個命令會註冊 `https://www.myget.org/F/powershellgetdemo/` 為目前使用者的存放庫。</span><span class="sxs-lookup"><span data-stu-id="7fa60-121">The first command registers `https://www.myget.org/F/powershellgetdemo/` as a repository for the current user.</span></span> <span data-ttu-id="7fa60-122">註冊 myNuGetSource 之後，您可以在搜尋、安裝和發佈模組時明確參考它。</span><span class="sxs-lookup"><span data-stu-id="7fa60-122">After myNuGetSource is registered, you can explicitly reference it when searching for, installing, and publishing modules.</span></span> <span data-ttu-id="7fa60-123">因為未指定 **PackageManagementProvider** 參數，所以儲存機制未明確與 OneGet 封裝提供者相關聯，因此 PowerShellGet 會輪詢可用的套件提供者，並將它與 NuGet 提供者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7fa60-123">Because the **PackageManagementProvider** parameter isn't specified, the repository is not explicitly associated with a OneGet package provider, so PowerShellGet polls available package providers and associates it with the NuGet provider.</span></span>

<span data-ttu-id="7fa60-124">第二個命令會取得已註冊的存放庫，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="7fa60-124">The second command gets registered repositories and displays the results.</span></span>

## <span data-ttu-id="7fa60-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7fa60-125">PARAMETERS</span></span>

### <span data-ttu-id="7fa60-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="7fa60-126">-Credential</span></span>

<span data-ttu-id="7fa60-127">指定有權註冊存放庫之帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="7fa60-127">Specifies credentials of an account that has rights to register a repository.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-128">-Default</span><span class="sxs-lookup"><span data-stu-id="7fa60-128">-Default</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-129">->installationpolicy</span><span class="sxs-lookup"><span data-stu-id="7fa60-129">-InstallationPolicy</span></span>

<span data-ttu-id="7fa60-130">指定安裝原則。</span><span class="sxs-lookup"><span data-stu-id="7fa60-130">Specifies the installation policy.</span></span> <span data-ttu-id="7fa60-131">有效的值為：信任、不受信任。</span><span class="sxs-lookup"><span data-stu-id="7fa60-131">Valid values are: Trusted, UnTrusted.</span></span> <span data-ttu-id="7fa60-132">預設值為 [不受信任]。</span><span class="sxs-lookup"><span data-stu-id="7fa60-132">The default value is UnTrusted.</span></span>

<span data-ttu-id="7fa60-133">存放庫的安裝原則會指定從該存放庫安裝時的 PowerShell 行為。</span><span class="sxs-lookup"><span data-stu-id="7fa60-133">A repository's installation policy specifies PowerShell behavior when installing from that repository.</span></span> <span data-ttu-id="7fa60-134">從不受信任的存放庫安裝模組時，系統會提示使用者進行確認。</span><span class="sxs-lookup"><span data-stu-id="7fa60-134">When installing modules from an UnTrusted repository, the user is prompted for confirmation.</span></span>

<span data-ttu-id="7fa60-135">您可以使用 Cmdlet **InstallationPolicy** 來設定 >installationpolicy `Set-PSRepository` 。</span><span class="sxs-lookup"><span data-stu-id="7fa60-135">You can set the **InstallationPolicy** with the `Set-PSRepository` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-136">-Name</span><span class="sxs-lookup"><span data-stu-id="7fa60-136">-Name</span></span>

<span data-ttu-id="7fa60-137">指定要註冊的儲存機制名稱。</span><span class="sxs-lookup"><span data-stu-id="7fa60-137">Specifies the name of the repository to register.</span></span> <span data-ttu-id="7fa60-138">您可以使用這個名稱來指定 Cmdlet 中的儲存機制，例如 `Find-Module` 和 `Install-Module` 。</span><span class="sxs-lookup"><span data-stu-id="7fa60-138">You can use this name to specify the repository in cmdlets such as `Find-Module` and `Install-Module`.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-139">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="7fa60-139">-PackageManagementProvider</span></span>

<span data-ttu-id="7fa60-140">指定 OneGet 封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="7fa60-140">Specifies a OneGet package provider.</span></span> <span data-ttu-id="7fa60-141">如果您未指定此參數的值，PowerShellGet 會輪詢可用的封裝提供者，並將此存放庫與第一個表示它可以處理存放庫的封裝提供者產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7fa60-141">If you don't specify a value for this parameter, PowerShellGet polls available package providers and associates this repository with the first package provider that indicates it can handle the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-142">-Proxy</span><span class="sxs-lookup"><span data-stu-id="7fa60-142">-Proxy</span></span>

<span data-ttu-id="7fa60-143">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="7fa60-143">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-144">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="7fa60-144">-ProxyCredential</span></span>

<span data-ttu-id="7fa60-145">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="7fa60-145">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="7fa60-146">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="7fa60-146">-PublishLocation</span></span>

<span data-ttu-id="7fa60-147">指定發佈位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="7fa60-147">Specifies the URI of the publish location.</span></span> <span data-ttu-id="7fa60-148">例如，針對以 NuGet 為基礎的存放庫，發佈位置類似于 `https://someNuGetUrl.com/api/v2/Packages` 。</span><span class="sxs-lookup"><span data-stu-id="7fa60-148">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-149">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="7fa60-149">-ScriptPublishLocation</span></span>

<span data-ttu-id="7fa60-150">指定腳本發行位置。</span><span class="sxs-lookup"><span data-stu-id="7fa60-150">Specifies the script publish location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-151">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="7fa60-151">-ScriptSourceLocation</span></span>

<span data-ttu-id="7fa60-152">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="7fa60-152">Specifies the script source location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-153">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="7fa60-153">-SourceLocation</span></span>

<span data-ttu-id="7fa60-154">指定從這個存放庫探索和安裝模組的 URI。</span><span class="sxs-lookup"><span data-stu-id="7fa60-154">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="7fa60-155">URI 可以是 NuGet 伺服器摘要， (最常見的情況) 、HTTP、HTTPS、FTP 或檔案位置。</span><span class="sxs-lookup"><span data-stu-id="7fa60-155">A URI can be a NuGet server feed (most common situation), HTTP, HTTPS, FTP or file location.</span></span>

<span data-ttu-id="7fa60-156">例如，針對以 NuGet 為基礎的存放庫，來源位置類似于 `https://someNuGetUrl.com/api/v2` 。</span><span class="sxs-lookup"><span data-stu-id="7fa60-156">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fa60-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7fa60-157">CommonParameters</span></span>

<span data-ttu-id="7fa60-158">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7fa60-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7fa60-159">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7fa60-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7fa60-160">輸入</span><span class="sxs-lookup"><span data-stu-id="7fa60-160">INPUTS</span></span>

### <span data-ttu-id="7fa60-161">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="7fa60-161">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="7fa60-162">System.Uri</span><span class="sxs-lookup"><span data-stu-id="7fa60-162">System.Uri</span></span>

## <span data-ttu-id="7fa60-163">輸出</span><span class="sxs-lookup"><span data-stu-id="7fa60-163">OUTPUTS</span></span>

### <span data-ttu-id="7fa60-164">System.Object</span><span class="sxs-lookup"><span data-stu-id="7fa60-164">System.Object</span></span>

## <span data-ttu-id="7fa60-165">注意</span><span class="sxs-lookup"><span data-stu-id="7fa60-165">NOTES</span></span>

## <span data-ttu-id="7fa60-166">相關連結</span><span class="sxs-lookup"><span data-stu-id="7fa60-166">RELATED LINKS</span></span>

[<span data-ttu-id="7fa60-167">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="7fa60-167">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="7fa60-168">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="7fa60-168">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="7fa60-169">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="7fa60-169">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
