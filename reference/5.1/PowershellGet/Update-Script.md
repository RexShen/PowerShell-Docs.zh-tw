---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: b7c89da6ec7228ca9f095d9288b108dd997f7aef
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892564"
---
# <span data-ttu-id="a6b63-103">Update-Script</span><span class="sxs-lookup"><span data-stu-id="a6b63-103">Update-Script</span></span>

## <span data-ttu-id="a6b63-104">概要</span><span class="sxs-lookup"><span data-stu-id="a6b63-104">SYNOPSIS</span></span>
<span data-ttu-id="a6b63-105">更新腳本。</span><span class="sxs-lookup"><span data-stu-id="a6b63-105">Updates a script.</span></span>

## <span data-ttu-id="a6b63-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a6b63-106">SYNTAX</span></span>

### <span data-ttu-id="a6b63-107">全部</span><span class="sxs-lookup"><span data-stu-id="a6b63-107">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a6b63-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a6b63-108">DESCRIPTION</span></span>

<span data-ttu-id="a6b63-109">指令 `Update-Script` 程式會更新安裝在本機電腦上的腳本。</span><span class="sxs-lookup"><span data-stu-id="a6b63-109">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="a6b63-110">更新的腳本會從與已安裝版本相同的存放庫下載。</span><span class="sxs-lookup"><span data-stu-id="a6b63-110">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="a6b63-111">範例</span><span class="sxs-lookup"><span data-stu-id="a6b63-111">EXAMPLES</span></span>

### <span data-ttu-id="a6b63-112">範例1：更新指定的腳本</span><span class="sxs-lookup"><span data-stu-id="a6b63-112">Example 1: Update the specified script</span></span>

<span data-ttu-id="a6b63-113">此範例會更新已安裝的腳本，並顯示更新的版本。</span><span class="sxs-lookup"><span data-stu-id="a6b63-113">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="a6b63-114">`Update-Script` 使用 **Name** 參數來指定要更新的腳本。</span><span class="sxs-lookup"><span data-stu-id="a6b63-114">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="a6b63-115">**RequiredVersion** 參數會指定腳本版本。</span><span class="sxs-lookup"><span data-stu-id="a6b63-115">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="a6b63-116">`Get-InstalledScript` 顯示腳本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="a6b63-116">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="a6b63-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a6b63-117">PARAMETERS</span></span>

### <span data-ttu-id="a6b63-118">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="a6b63-118">-AcceptLicense</span></span>

<span data-ttu-id="a6b63-119">如果套件需要，則會在安裝期間自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="a6b63-119">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="a6b63-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="a6b63-120">-AllowPrerelease</span></span>

<span data-ttu-id="a6b63-121">可讓您使用標記為發行前版本的較新腳本來更新腳本。</span><span class="sxs-lookup"><span data-stu-id="a6b63-121">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="a6b63-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a6b63-122">-Confirm</span></span>

<span data-ttu-id="a6b63-123">在執行之前提示您確認 `Update-Script` 。</span><span class="sxs-lookup"><span data-stu-id="a6b63-123">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="a6b63-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="a6b63-124">-Credential</span></span>

<span data-ttu-id="a6b63-125">指定有權更新腳本的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a6b63-125">Specifies a user account that has permission to update a script.</span></span>

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

### <span data-ttu-id="a6b63-126">-Force</span><span class="sxs-lookup"><span data-stu-id="a6b63-126">-Force</span></span>

<span data-ttu-id="a6b63-127">強制 `Update-Script` 執行而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="a6b63-127">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="a6b63-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a6b63-128">-MaximumVersion</span></span>

<span data-ttu-id="a6b63-129">指定要更新之腳本的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="a6b63-129">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="a6b63-130">在相同的命令中不能使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="a6b63-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="a6b63-131">-Name</span><span class="sxs-lookup"><span data-stu-id="a6b63-131">-Name</span></span>

<span data-ttu-id="a6b63-132">指定一個腳本名稱或腳本名稱陣列以進行更新。</span><span class="sxs-lookup"><span data-stu-id="a6b63-132">Specifies one script name or an array of script names to update.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a6b63-133">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a6b63-133">-PassThru</span></span>

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

### <span data-ttu-id="a6b63-134">-Proxy</span><span class="sxs-lookup"><span data-stu-id="a6b63-134">-Proxy</span></span>

<span data-ttu-id="a6b63-135">為要求指定 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="a6b63-135">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="a6b63-136">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a6b63-136">-ProxyCredential</span></span>

<span data-ttu-id="a6b63-137">指定擁有使用 **proxy** 參數所指定 proxy 伺服器之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a6b63-137">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="a6b63-138">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a6b63-138">-RequiredVersion</span></span>

<span data-ttu-id="a6b63-139">指定要更新之腳本的確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a6b63-139">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="a6b63-140">**MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="a6b63-140">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="a6b63-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a6b63-141">-WhatIf</span></span>

<span data-ttu-id="a6b63-142">顯示執行時所發生 `Update-Script` 的情況。</span><span class="sxs-lookup"><span data-stu-id="a6b63-142">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="a6b63-143">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a6b63-143">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="a6b63-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6b63-144">CommonParameters</span></span>

<span data-ttu-id="a6b63-145">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a6b63-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a6b63-146">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a6b63-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a6b63-147">輸入</span><span class="sxs-lookup"><span data-stu-id="a6b63-147">INPUTS</span></span>

## <span data-ttu-id="a6b63-148">輸出</span><span class="sxs-lookup"><span data-stu-id="a6b63-148">OUTPUTS</span></span>

## <span data-ttu-id="a6b63-149">注意</span><span class="sxs-lookup"><span data-stu-id="a6b63-149">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6b63-150">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="a6b63-150">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a6b63-151">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="a6b63-151">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a6b63-152">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="a6b63-152">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a6b63-153">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="a6b63-153">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="a6b63-154">相關連結</span><span class="sxs-lookup"><span data-stu-id="a6b63-154">RELATED LINKS</span></span>

[<span data-ttu-id="a6b63-155">Find-Script</span><span class="sxs-lookup"><span data-stu-id="a6b63-155">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="a6b63-156">Install-Script</span><span class="sxs-lookup"><span data-stu-id="a6b63-156">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="a6b63-157">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="a6b63-157">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="a6b63-158">Save-Script</span><span class="sxs-lookup"><span data-stu-id="a6b63-158">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="a6b63-159">卸載-腳本</span><span class="sxs-lookup"><span data-stu-id="a6b63-159">Uninstall-Script</span></span>](Uninstall-Script.md)
