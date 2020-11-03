---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: 0734bda0a3462e39f799570c853cffa3e267c5db
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203895"
---
# <span data-ttu-id="8eba2-103">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8eba2-103">Set-PSRepository</span></span>

## <span data-ttu-id="8eba2-104">概要</span><span class="sxs-lookup"><span data-stu-id="8eba2-104">SYNOPSIS</span></span>
<span data-ttu-id="8eba2-105">設定已註冊存放庫的值。</span><span class="sxs-lookup"><span data-stu-id="8eba2-105">Sets values for a registered repository.</span></span>

## <span data-ttu-id="8eba2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8eba2-106">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="8eba2-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8eba2-107">DESCRIPTION</span></span>

<span data-ttu-id="8eba2-108">`Set-PSRepository`Cmdlet 會為已註冊的模組存放庫設定值。</span><span class="sxs-lookup"><span data-stu-id="8eba2-108">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="8eba2-109">目前使用者的設定是持續性的，適用于為該使用者安裝的所有 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="8eba2-109">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="8eba2-110">範例</span><span class="sxs-lookup"><span data-stu-id="8eba2-110">EXAMPLES</span></span>

### <span data-ttu-id="8eba2-111">範例1：設定存放庫的安裝原則</span><span class="sxs-lookup"><span data-stu-id="8eba2-111">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="8eba2-112">此命令會將 **myInternalSource** 存放庫的安裝原則設定為 **受信任** ，如此一來，在從該來源安裝模組之前，系統不會提示您。</span><span class="sxs-lookup"><span data-stu-id="8eba2-112">This command sets the installation policy for the **myInternalSource** repository to **Trusted** , so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="8eba2-113">範例2：設定存放庫的來源和發佈位置</span><span class="sxs-lookup"><span data-stu-id="8eba2-113">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="8eba2-114">此命令會將 **myInternalSource** 的來源位置和發佈位置設定為指定的 uri。</span><span class="sxs-lookup"><span data-stu-id="8eba2-114">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="8eba2-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8eba2-115">PARAMETERS</span></span>

### <span data-ttu-id="8eba2-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="8eba2-116">-Credential</span></span>

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

### <span data-ttu-id="8eba2-117">->installationpolicy</span><span class="sxs-lookup"><span data-stu-id="8eba2-117">-InstallationPolicy</span></span>

<span data-ttu-id="8eba2-118">指定安裝原則。</span><span class="sxs-lookup"><span data-stu-id="8eba2-118">Specifies the installation policy.</span></span> <span data-ttu-id="8eba2-119">有效的值為： **信任** 、 **不受** 信任。</span><span class="sxs-lookup"><span data-stu-id="8eba2-119">Valid values are: **Trusted** , **Untrusted** .</span></span>

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

### <span data-ttu-id="8eba2-120">-Name</span><span class="sxs-lookup"><span data-stu-id="8eba2-120">-Name</span></span>

<span data-ttu-id="8eba2-121">指定存放庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="8eba2-121">Specifies the name of the repository.</span></span>

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

### <span data-ttu-id="8eba2-122">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="8eba2-122">-PackageManagementProvider</span></span>

<span data-ttu-id="8eba2-123">指定套件管理提供者。</span><span class="sxs-lookup"><span data-stu-id="8eba2-123">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="8eba2-124">-Proxy</span><span class="sxs-lookup"><span data-stu-id="8eba2-124">-Proxy</span></span>

<span data-ttu-id="8eba2-125">指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="8eba2-125">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="8eba2-126">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="8eba2-126">-ProxyCredential</span></span>

<span data-ttu-id="8eba2-127">指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8eba2-127">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="8eba2-128">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="8eba2-128">-PublishLocation</span></span>

<span data-ttu-id="8eba2-129">指定發佈位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="8eba2-129">Specifies the URI of the publish location.</span></span> <span data-ttu-id="8eba2-130">例如，針對以 NuGet 為基礎的存放庫，發佈位置類似于 `https://someNuGetUrl.com/api/v2/Packages` 。</span><span class="sxs-lookup"><span data-stu-id="8eba2-130">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="8eba2-131">->scriptpublishlocation</span><span class="sxs-lookup"><span data-stu-id="8eba2-131">-ScriptPublishLocation</span></span>

<span data-ttu-id="8eba2-132">指定腳本發行位置。</span><span class="sxs-lookup"><span data-stu-id="8eba2-132">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="8eba2-133">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="8eba2-133">-ScriptSourceLocation</span></span>

<span data-ttu-id="8eba2-134">指定腳本來源位置。</span><span class="sxs-lookup"><span data-stu-id="8eba2-134">Specifies the script source location.</span></span>

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

### <span data-ttu-id="8eba2-135">-SourceLocation</span><span class="sxs-lookup"><span data-stu-id="8eba2-135">-SourceLocation</span></span>

<span data-ttu-id="8eba2-136">指定從這個存放庫探索和安裝模組的 URI。</span><span class="sxs-lookup"><span data-stu-id="8eba2-136">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="8eba2-137">例如，針對以 NuGet 為基礎的存放庫，來源位置類似于 `https://someNuGetUrl.com/api/v2` 。</span><span class="sxs-lookup"><span data-stu-id="8eba2-137">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

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

### <span data-ttu-id="8eba2-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8eba2-138">CommonParameters</span></span>

<span data-ttu-id="8eba2-139">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8eba2-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8eba2-140">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8eba2-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8eba2-141">輸入</span><span class="sxs-lookup"><span data-stu-id="8eba2-141">INPUTS</span></span>

### <span data-ttu-id="8eba2-142">System.String</span><span class="sxs-lookup"><span data-stu-id="8eba2-142">System.String</span></span>

### <span data-ttu-id="8eba2-143">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="8eba2-143">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="8eba2-144">System.Uri</span><span class="sxs-lookup"><span data-stu-id="8eba2-144">System.Uri</span></span>

## <span data-ttu-id="8eba2-145">輸出</span><span class="sxs-lookup"><span data-stu-id="8eba2-145">OUTPUTS</span></span>

### <span data-ttu-id="8eba2-146">System.Object</span><span class="sxs-lookup"><span data-stu-id="8eba2-146">System.Object</span></span>

## <span data-ttu-id="8eba2-147">注意</span><span class="sxs-lookup"><span data-stu-id="8eba2-147">NOTES</span></span>

## <span data-ttu-id="8eba2-148">相關連結</span><span class="sxs-lookup"><span data-stu-id="8eba2-148">RELATED LINKS</span></span>

[<span data-ttu-id="8eba2-149">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8eba2-149">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="8eba2-150">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8eba2-150">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="8eba2-151">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8eba2-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
