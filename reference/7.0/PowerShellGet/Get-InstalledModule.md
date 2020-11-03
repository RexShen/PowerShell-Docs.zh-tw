---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: 8c96b4cd56073a9185ca4b0f0f13b866b839931d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201408"
---
# <span data-ttu-id="0ada5-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="0ada5-103">Get-InstalledModule</span></span>

## <span data-ttu-id="0ada5-104">概要</span><span class="sxs-lookup"><span data-stu-id="0ada5-104">SYNOPSIS</span></span>
<span data-ttu-id="0ada5-105">取得由 PowerShellGet 安裝之電腦上的模組清單。</span><span class="sxs-lookup"><span data-stu-id="0ada5-105">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="0ada5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0ada5-106">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="0ada5-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0ada5-107">DESCRIPTION</span></span>

<span data-ttu-id="0ada5-108">此 `Get-InstalledModule` Cmdlet 會使用 PowerShellGet 取得安裝在電腦上的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="0ada5-108">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="0ada5-109">若要查看系統上安裝的所有模組，請使用 `Get-Module -ListAvailable` 命令。</span><span class="sxs-lookup"><span data-stu-id="0ada5-109">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="0ada5-110">範例</span><span class="sxs-lookup"><span data-stu-id="0ada5-110">EXAMPLES</span></span>

### <span data-ttu-id="0ada5-111">範例1：取得所有已安裝的模組</span><span class="sxs-lookup"><span data-stu-id="0ada5-111">Example 1: Get all installed modules</span></span>

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

<span data-ttu-id="0ada5-112">此命令會取得所有已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="0ada5-112">This command gets all installed modules.</span></span>

### <span data-ttu-id="0ada5-113">範例2：取得模組的特定版本</span><span class="sxs-lookup"><span data-stu-id="0ada5-113">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="0ada5-114">此命令會從1.0 到2.0 版的 AzureRM 取得 Automation 模組版本。</span><span class="sxs-lookup"><span data-stu-id="0ada5-114">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="0ada5-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0ada5-115">PARAMETERS</span></span>

### <span data-ttu-id="0ada5-116">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0ada5-116">-AllowPrerelease</span></span>

<span data-ttu-id="0ada5-117">包含在標記為發行前版本的結果模組中。</span><span class="sxs-lookup"><span data-stu-id="0ada5-117">Includes in the results modules marked as a prerelease.</span></span>

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

### <span data-ttu-id="0ada5-118">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="0ada5-118">-AllVersions</span></span>

<span data-ttu-id="0ada5-119">指出您想要取得模組的所有可用版本。</span><span class="sxs-lookup"><span data-stu-id="0ada5-119">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="0ada5-120">您無法搭配 **MinimumVersion** 、 **MaximumVersion** 或 **RequiredVersion** 參數使用 **allversions 進行篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="0ada5-120">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="0ada5-121">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="0ada5-121">-MaximumVersion</span></span>

<span data-ttu-id="0ada5-122">指定要取得之模組的最大或最新版本。</span><span class="sxs-lookup"><span data-stu-id="0ada5-122">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="0ada5-123">**MaximumVersion** 和 **RequiredVersion** 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="0ada5-123">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="0ada5-124">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="0ada5-124">-MinimumVersion</span></span>

<span data-ttu-id="0ada5-125">指定要取得之單一模組的最小版本。</span><span class="sxs-lookup"><span data-stu-id="0ada5-125">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="0ada5-126">**MinimumVersion** 和 **RequiredVersion** 參數是互斥的；您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="0ada5-126">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="0ada5-127">-Name</span><span class="sxs-lookup"><span data-stu-id="0ada5-127">-Name</span></span>

<span data-ttu-id="0ada5-128">指定要取得的模組名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="0ada5-128">Specifies an array of names of modules to get.</span></span>

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

### <span data-ttu-id="0ada5-129">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0ada5-129">-RequiredVersion</span></span>

<span data-ttu-id="0ada5-130">指定要取得之模組的確切版本。</span><span class="sxs-lookup"><span data-stu-id="0ada5-130">Specifies the exact version of a module to get.</span></span>

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

### <span data-ttu-id="0ada5-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0ada5-131">CommonParameters</span></span>

<span data-ttu-id="0ada5-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0ada5-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0ada5-133">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0ada5-133">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0ada5-134">輸入</span><span class="sxs-lookup"><span data-stu-id="0ada5-134">INPUTS</span></span>

### <span data-ttu-id="0ada5-135">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0ada5-135">System.String[]</span></span>

### <span data-ttu-id="0ada5-136">System.String</span><span class="sxs-lookup"><span data-stu-id="0ada5-136">System.String</span></span>

## <span data-ttu-id="0ada5-137">輸出</span><span class="sxs-lookup"><span data-stu-id="0ada5-137">OUTPUTS</span></span>

### <span data-ttu-id="0ada5-138">System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="0ada5-138">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="0ada5-139">注意</span><span class="sxs-lookup"><span data-stu-id="0ada5-139">NOTES</span></span>

## <span data-ttu-id="0ada5-140">相關連結</span><span class="sxs-lookup"><span data-stu-id="0ada5-140">RELATED LINKS</span></span>
