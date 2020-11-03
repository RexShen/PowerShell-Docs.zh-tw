---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: 9d4ec71a5f754b1fba090129d026d38bd32a8bc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204139"
---
# <span data-ttu-id="999f8-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="999f8-103">Get-InstalledModule</span></span>

## <span data-ttu-id="999f8-104">概要</span><span class="sxs-lookup"><span data-stu-id="999f8-104">SYNOPSIS</span></span>
<span data-ttu-id="999f8-105">取得由 PowerShellGet 安裝之電腦上的模組清單。</span><span class="sxs-lookup"><span data-stu-id="999f8-105">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="999f8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="999f8-106">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="999f8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="999f8-107">DESCRIPTION</span></span>

<span data-ttu-id="999f8-108">此 `Get-InstalledModule` Cmdlet 會使用 PowerShellGet 取得安裝在電腦上的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="999f8-108">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="999f8-109">若要查看系統上安裝的所有模組，請使用 `Get-Module -ListAvailable` 命令。</span><span class="sxs-lookup"><span data-stu-id="999f8-109">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="999f8-110">範例</span><span class="sxs-lookup"><span data-stu-id="999f8-110">EXAMPLES</span></span>

### <span data-ttu-id="999f8-111">範例1：取得所有已安裝的模組</span><span class="sxs-lookup"><span data-stu-id="999f8-111">Example 1: Get all installed modules</span></span>

```powershell
Get-InstalledModule
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
2.0.0      PSGTEST-UploadMultipleVersionOfP... Module     GalleryINT     Module for DAC functionality
1.3.5      AzureAutomationDebug                Module     PSGallery      Module for debugging Azure Automation runbooks, emulating AA native cmdlets
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="999f8-112">此命令會取得所有已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="999f8-112">This command gets all installed modules.</span></span>

### <span data-ttu-id="999f8-113">範例2：取得模組的特定版本</span><span class="sxs-lookup"><span data-stu-id="999f8-113">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="999f8-114">此命令會從1.0 到2.0 版的 AzureRM 取得 Automation 模組版本。</span><span class="sxs-lookup"><span data-stu-id="999f8-114">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="999f8-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="999f8-115">PARAMETERS</span></span>

### <span data-ttu-id="999f8-116">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="999f8-116">-AllowPrerelease</span></span>

<span data-ttu-id="999f8-117">包含在標記為發行前版本的結果模組中。</span><span class="sxs-lookup"><span data-stu-id="999f8-117">Includes in the results modules marked as a prerelease.</span></span>

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

### <span data-ttu-id="999f8-118">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="999f8-118">-AllVersions</span></span>

<span data-ttu-id="999f8-119">指出您想要取得模組的所有可用版本。</span><span class="sxs-lookup"><span data-stu-id="999f8-119">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="999f8-120">您無法搭配 **MinimumVersion** 、 **MaximumVersion** 或 **RequiredVersion** 參數使用 **allversions 進行篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="999f8-120">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="999f8-121">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="999f8-121">-MaximumVersion</span></span>

<span data-ttu-id="999f8-122">指定要取得之模組的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="999f8-122">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="999f8-123">**MaximumVersion** 和 **RequiredVersion** 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="999f8-123">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="999f8-124">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="999f8-124">-MinimumVersion</span></span>

<span data-ttu-id="999f8-125">指定要取得之單一模組的最小版本。</span><span class="sxs-lookup"><span data-stu-id="999f8-125">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="999f8-126">**MinimumVersion** 和 **RequiredVersion** 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="999f8-126">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="999f8-127">-Name</span><span class="sxs-lookup"><span data-stu-id="999f8-127">-Name</span></span>

<span data-ttu-id="999f8-128">指定要取得的模組名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="999f8-128">Specifies an array of names of modules to get.</span></span>

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

### <span data-ttu-id="999f8-129">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="999f8-129">-RequiredVersion</span></span>

<span data-ttu-id="999f8-130">指定要取得之模組的確切版本。</span><span class="sxs-lookup"><span data-stu-id="999f8-130">Specifies the exact version of a module to get.</span></span>

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

### <span data-ttu-id="999f8-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="999f8-131">CommonParameters</span></span>

<span data-ttu-id="999f8-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="999f8-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="999f8-133">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="999f8-133">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="999f8-134">輸入</span><span class="sxs-lookup"><span data-stu-id="999f8-134">INPUTS</span></span>

### <span data-ttu-id="999f8-135">System.String[]</span><span class="sxs-lookup"><span data-stu-id="999f8-135">System.String[]</span></span>

### <span data-ttu-id="999f8-136">System.String</span><span class="sxs-lookup"><span data-stu-id="999f8-136">System.String</span></span>

## <span data-ttu-id="999f8-137">輸出</span><span class="sxs-lookup"><span data-stu-id="999f8-137">OUTPUTS</span></span>

### <span data-ttu-id="999f8-138">System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="999f8-138">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="999f8-139">注意</span><span class="sxs-lookup"><span data-stu-id="999f8-139">NOTES</span></span>

## <span data-ttu-id="999f8-140">相關連結</span><span class="sxs-lookup"><span data-stu-id="999f8-140">RELATED LINKS</span></span>

