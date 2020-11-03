---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Script
ms.openlocfilehash: e57a291abcc50a6bc912a36a6258583a7751a819
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204539"
---
# <span data-ttu-id="aa518-103">Update-Script</span><span class="sxs-lookup"><span data-stu-id="aa518-103">Update-Script</span></span>

## <span data-ttu-id="aa518-104">概要</span><span class="sxs-lookup"><span data-stu-id="aa518-104">SYNOPSIS</span></span>
<span data-ttu-id="aa518-105">更新腳本。</span><span class="sxs-lookup"><span data-stu-id="aa518-105">Updates a script.</span></span>

## <span data-ttu-id="aa518-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aa518-106">SYNTAX</span></span>

### <span data-ttu-id="aa518-107">全部</span><span class="sxs-lookup"><span data-stu-id="aa518-107">All</span></span>

```
Update-Script [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="aa518-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="aa518-108">DESCRIPTION</span></span>

<span data-ttu-id="aa518-109">指令 `Update-Script` 程式會更新安裝在本機電腦上的腳本。</span><span class="sxs-lookup"><span data-stu-id="aa518-109">The `Update-Script` cmdlet updates a script that is installed on the local computer.</span></span> <span data-ttu-id="aa518-110">更新的腳本會從與已安裝版本相同的存放庫下載。</span><span class="sxs-lookup"><span data-stu-id="aa518-110">The updated script is downloaded from the same repository as the installed version.</span></span>

## <span data-ttu-id="aa518-111">範例</span><span class="sxs-lookup"><span data-stu-id="aa518-111">EXAMPLES</span></span>

### <span data-ttu-id="aa518-112">範例1：更新指定的腳本</span><span class="sxs-lookup"><span data-stu-id="aa518-112">Example 1: Update the specified script</span></span>

<span data-ttu-id="aa518-113">此範例會更新已安裝的腳本，並顯示更新的版本。</span><span class="sxs-lookup"><span data-stu-id="aa518-113">This example updates an installed script and displays the updated version.</span></span>

```powershell
Update-Script -Name UpdateManagement-Template -RequiredVersion 1.1
Get-InstalledScript -Name UpdateManagement-Template
```

```Output
Version   Name                       Repository   Description
-------   ----                       ----------   -----------
1.1       UpdateManagement-Template  PSGallery    This is a template script for Update Management...
```

<span data-ttu-id="aa518-114">`Update-Script` 使用 **Name** 參數來指定要更新的腳本。</span><span class="sxs-lookup"><span data-stu-id="aa518-114">`Update-Script` uses the **Name** parameter to specify the script to update.</span></span> <span data-ttu-id="aa518-115">**RequiredVersion** 參數會指定腳本版本。</span><span class="sxs-lookup"><span data-stu-id="aa518-115">The **RequiredVersion** parameter specifies the script version.</span></span> <span data-ttu-id="aa518-116">`Get-InstalledScript` 顯示腳本的更新版本。</span><span class="sxs-lookup"><span data-stu-id="aa518-116">`Get-InstalledScript` displays the updated version of the script.</span></span>

## <span data-ttu-id="aa518-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aa518-117">PARAMETERS</span></span>

### <span data-ttu-id="aa518-118">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="aa518-118">-AcceptLicense</span></span>

<span data-ttu-id="aa518-119">如果套件需要，則會在安裝期間自動接受授權合約。</span><span class="sxs-lookup"><span data-stu-id="aa518-119">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="aa518-120">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="aa518-120">-AllowPrerelease</span></span>

<span data-ttu-id="aa518-121">可讓您使用標記為發行前版本的較新腳本來更新腳本。</span><span class="sxs-lookup"><span data-stu-id="aa518-121">Allows you to update a script with the newer script marked as a prerelease.</span></span>

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

### <span data-ttu-id="aa518-122">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aa518-122">-Confirm</span></span>

<span data-ttu-id="aa518-123">在執行之前提示您確認 `Update-Script` 。</span><span class="sxs-lookup"><span data-stu-id="aa518-123">Prompts you for confirmation before running `Update-Script`.</span></span>

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

### <span data-ttu-id="aa518-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="aa518-124">-Credential</span></span>

<span data-ttu-id="aa518-125">指定有權更新腳本的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="aa518-125">Specifies a user account that has permission to update a script.</span></span>

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

### <span data-ttu-id="aa518-126">-Force</span><span class="sxs-lookup"><span data-stu-id="aa518-126">-Force</span></span>

<span data-ttu-id="aa518-127">強制 `Update-Script` 執行而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="aa518-127">Forces `Update-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="aa518-128">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="aa518-128">-MaximumVersion</span></span>

<span data-ttu-id="aa518-129">指定要更新之腳本的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="aa518-129">Specifies the maximum, or newest, version of the script to update.</span></span> <span data-ttu-id="aa518-130">在相同的命令中不能使用 **MaximumVersion** 和 **RequiredVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="aa518-130">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="aa518-131">-Name</span><span class="sxs-lookup"><span data-stu-id="aa518-131">-Name</span></span>

<span data-ttu-id="aa518-132">指定一個腳本名稱或腳本名稱陣列以進行更新。</span><span class="sxs-lookup"><span data-stu-id="aa518-132">Specifies one script name or an array of script names to update.</span></span>

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

### <span data-ttu-id="aa518-133">-PassThru</span><span class="sxs-lookup"><span data-stu-id="aa518-133">-PassThru</span></span>

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

### <span data-ttu-id="aa518-134">-Proxy</span><span class="sxs-lookup"><span data-stu-id="aa518-134">-Proxy</span></span>

<span data-ttu-id="aa518-135">為要求指定 proxy 伺服器，而不是直接連接到網際網路資源。</span><span class="sxs-lookup"><span data-stu-id="aa518-135">Specifies a proxy server for the request rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="aa518-136">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="aa518-136">-ProxyCredential</span></span>

<span data-ttu-id="aa518-137">指定擁有使用 **proxy** 參數所指定 proxy 伺服器之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="aa518-137">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="aa518-138">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="aa518-138">-RequiredVersion</span></span>

<span data-ttu-id="aa518-139">指定要更新之腳本的確切版本號碼。</span><span class="sxs-lookup"><span data-stu-id="aa518-139">Specifies the exact version number of the script to update.</span></span> <span data-ttu-id="aa518-140">**MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。</span><span class="sxs-lookup"><span data-stu-id="aa518-140">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="aa518-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aa518-141">-WhatIf</span></span>

<span data-ttu-id="aa518-142">顯示執行時所發生 `Update-Script` 的情況。</span><span class="sxs-lookup"><span data-stu-id="aa518-142">Shows what would happen if `Update-Script` runs.</span></span> <span data-ttu-id="aa518-143">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aa518-143">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="aa518-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa518-144">CommonParameters</span></span>

<span data-ttu-id="aa518-145">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="aa518-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aa518-146">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="aa518-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aa518-147">輸入</span><span class="sxs-lookup"><span data-stu-id="aa518-147">INPUTS</span></span>

### <span data-ttu-id="aa518-148">System.String[]</span><span class="sxs-lookup"><span data-stu-id="aa518-148">System.String[]</span></span>

### <span data-ttu-id="aa518-149">System.String</span><span class="sxs-lookup"><span data-stu-id="aa518-149">System.String</span></span>

### <span data-ttu-id="aa518-150">System.Uri</span><span class="sxs-lookup"><span data-stu-id="aa518-150">System.Uri</span></span>

### <span data-ttu-id="aa518-151">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="aa518-151">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="aa518-152">輸出</span><span class="sxs-lookup"><span data-stu-id="aa518-152">OUTPUTS</span></span>

### <span data-ttu-id="aa518-153">System.Object</span><span class="sxs-lookup"><span data-stu-id="aa518-153">System.Object</span></span>

## <span data-ttu-id="aa518-154">注意</span><span class="sxs-lookup"><span data-stu-id="aa518-154">NOTES</span></span>

## <span data-ttu-id="aa518-155">相關連結</span><span class="sxs-lookup"><span data-stu-id="aa518-155">RELATED LINKS</span></span>

[<span data-ttu-id="aa518-156">Find-Script</span><span class="sxs-lookup"><span data-stu-id="aa518-156">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="aa518-157">Install-Script</span><span class="sxs-lookup"><span data-stu-id="aa518-157">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="aa518-158">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="aa518-158">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="aa518-159">Save-Script</span><span class="sxs-lookup"><span data-stu-id="aa518-159">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="aa518-160">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="aa518-160">Uninstall-Script</span></span>](Uninstall-Script.md)
