---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: 74eb0b105674c4e007cfade8d8a16799b5c366f2
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892084"
---
# <span data-ttu-id="78d3e-103">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="78d3e-103">Set-PSRepository</span></span>

## <span data-ttu-id="78d3e-104">概要</span><span class="sxs-lookup"><span data-stu-id="78d3e-104">SYNOPSIS</span></span>
<span data-ttu-id="78d3e-105">設定已註冊存放庫的值。</span><span class="sxs-lookup"><span data-stu-id="78d3e-105">Sets values for a registered repository.</span></span>

## <span data-ttu-id="78d3e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="78d3e-106">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="78d3e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="78d3e-107">DESCRIPTION</span></span>

<span data-ttu-id="78d3e-108">`Set-PSRepository`Cmdlet 會為已註冊的模組存放庫設定值。</span><span class="sxs-lookup"><span data-stu-id="78d3e-108">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="78d3e-109">目前使用者的設定是持續性的，適用于為該使用者安裝的所有 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="78d3e-109">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="78d3e-110">範例</span><span class="sxs-lookup"><span data-stu-id="78d3e-110">EXAMPLES</span></span>

### <span data-ttu-id="78d3e-111">範例1：設定存放庫的安裝原則</span><span class="sxs-lookup"><span data-stu-id="78d3e-111">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="78d3e-112">此命令會將 **myInternalSource** 存放庫的安裝原則設定為 **受信任**，如此一來，在從該來源安裝模組之前，系統不會提示您。</span><span class="sxs-lookup"><span data-stu-id="78d3e-112">This command sets the installation policy for the **myInternalSource** repository to **Trusted**, so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="78d3e-113">範例2：設定存放庫的來源和發佈位置</span><span class="sxs-lookup"><span data-stu-id="78d3e-113">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="78d3e-114">此命令會將 **myInternalSource** 的來源位置和發佈位置設定為指定的 uri。</span><span class="sxs-lookup"><span data-stu-id="78d3e-114">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="78d3e-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="78d3e-115">PARAMETERS</span></span>

### <span data-ttu-id="78d3e-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="78d3e-116">-Credential</span></span>

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

### <span data-ttu-id="78d3e-117">->installationpolicy</span><span class="sxs-lookup"><span data-stu-id="78d3e-117">-InstallationPolicy</span></span>

<span data-ttu-id="78d3e-118">指定安裝原則。</span><span class="sxs-lookup"><span data-stu-id="78d3e-118">Specifies the installation policy.</span></span> <span data-ttu-id="78d3e-119">有效的值為： **信任**、 **不受** 信任。</span><span class="sxs-lookup"><span data-stu-id="78d3e-119">Valid values are: **Trusted**, **Untrusted**.</span></span>

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

### <span data-ttu-id="78d3e-120">-Name</span><span class="sxs-lookup"><span data-stu-id="78d3e-120">-Name</span></span>

<span data-ttu-id="78d3e-121">指定存放庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="78d3e-121">Specifies the name of the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="78d3e-122">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="78d3e-122">-PackageManagementProvider</span></span>

<span data-ttu-id="78d3e-123">指定套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="78d3e-123">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="78d3e-124">-Proxy</span><span class="sxs-lookup"><span data-stu-id="78d3e-124">-Proxy</span></span>

<span data-ttu-id="78d3e-125">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="78d3e-125">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="78d3e-126">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="78d3e-126">-ProxyCredential</span></span>

<span data-ttu-id="78d3e-127">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="78d3e-127">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="78d3e-128">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="78d3e-128">-PublishLocation</span></span>

<span data-ttu-id="78d3e-129">指定發佈位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="78d3e-129">Specifies the URI of the publish location.</span></span> <span data-ttu-id="78d3e-130">例如，針對以 NuGet 為基礎的存放庫，發佈位置類似于 `https://someNuGetUrl.com/api/v2/Packages` 。</span><span class="sxs-lookup"><span data-stu-id="78d3e-130">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="78d3e-131">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="78d3e-131">-ScriptPublishLocation</span></span>

<span data-ttu-id="78d3e-132">指定腳本發行位置。</span><span class="sxs-lookup"><span data-stu-id="78d3e-132">Specifies the script publish location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="78d3e-133">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="78d3e-133">-ScriptSourceLocation</span></span>

<span data-ttu-id="78d3e-134">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="78d3e-134">Specifies the script source location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="78d3e-135">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="78d3e-135">-SourceLocation</span></span>

<span data-ttu-id="78d3e-136">指定從這個存放庫探索和安裝模組的 URI。</span><span class="sxs-lookup"><span data-stu-id="78d3e-136">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="78d3e-137">例如，針對以 NuGet 為基礎的存放庫，來源位置類似于 `https://someNuGetUrl.com/api/v2` 。</span><span class="sxs-lookup"><span data-stu-id="78d3e-137">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="78d3e-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="78d3e-138">CommonParameters</span></span>

<span data-ttu-id="78d3e-139">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="78d3e-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="78d3e-140">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="78d3e-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="78d3e-141">輸入</span><span class="sxs-lookup"><span data-stu-id="78d3e-141">INPUTS</span></span>

### <span data-ttu-id="78d3e-142">System.String</span><span class="sxs-lookup"><span data-stu-id="78d3e-142">System.String</span></span>

### <span data-ttu-id="78d3e-143">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="78d3e-143">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="78d3e-144">System.Uri</span><span class="sxs-lookup"><span data-stu-id="78d3e-144">System.Uri</span></span>

## <span data-ttu-id="78d3e-145">輸出</span><span class="sxs-lookup"><span data-stu-id="78d3e-145">OUTPUTS</span></span>

### <span data-ttu-id="78d3e-146">System.Object</span><span class="sxs-lookup"><span data-stu-id="78d3e-146">System.Object</span></span>

## <span data-ttu-id="78d3e-147">注意</span><span class="sxs-lookup"><span data-stu-id="78d3e-147">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78d3e-148">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="78d3e-148">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="78d3e-149">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="78d3e-149">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="78d3e-150">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="78d3e-150">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="78d3e-151">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="78d3e-151">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="78d3e-152">相關連結</span><span class="sxs-lookup"><span data-stu-id="78d3e-152">RELATED LINKS</span></span>

[<span data-ttu-id="78d3e-153">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="78d3e-153">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="78d3e-154">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="78d3e-154">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="78d3e-155">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="78d3e-155">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
