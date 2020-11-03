---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: 43f70d400cc2d9b81e2bf59a6d2b3bb986737c69
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201515"
---
# <span data-ttu-id="d8c75-103">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="d8c75-103">Get-PackageProvider</span></span>

## <span data-ttu-id="d8c75-104">概要</span><span class="sxs-lookup"><span data-stu-id="d8c75-104">SYNOPSIS</span></span>
<span data-ttu-id="d8c75-105">傳回連接到套件管理的封裝提供者清單。</span><span class="sxs-lookup"><span data-stu-id="d8c75-105">Returns a list of package providers that are connected to Package Management.</span></span>

## <span data-ttu-id="d8c75-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8c75-106">SYNTAX</span></span>

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="d8c75-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d8c75-107">DESCRIPTION</span></span>

<span data-ttu-id="d8c75-108">**Install-packageprovider** 指令程式會傳回連接至套件管理的封裝提供者清單。</span><span class="sxs-lookup"><span data-stu-id="d8c75-108">The **Get-PackageProvider** cmdlet returns a list of package providers that are connected to Package Management.</span></span>
<span data-ttu-id="d8c75-109">這些提供者的範例包括 PSModule、NuGet 和 Chocolatey。</span><span class="sxs-lookup"><span data-stu-id="d8c75-109">Examples of these providers include PSModule, NuGet, and Chocolatey.</span></span>
<span data-ttu-id="d8c75-110">您可以根據一或多個提供者名稱的所有或部分來篩選結果。</span><span class="sxs-lookup"><span data-stu-id="d8c75-110">You can filter the results based on all or part of one or more provider names.</span></span>

## <span data-ttu-id="d8c75-111">範例</span><span class="sxs-lookup"><span data-stu-id="d8c75-111">EXAMPLES</span></span>

### <span data-ttu-id="d8c75-112">範例1：取得所有目前載入的封裝提供者</span><span class="sxs-lookup"><span data-stu-id="d8c75-112">Example 1: Get all currently loaded package providers</span></span>

```
PS C:\> Get-PackageProvider
```

<span data-ttu-id="d8c75-113">此命令會取得目前在本機電腦上載入之所有封裝提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="d8c75-113">This command gets a list of all the package providers that are currently loaded on the local computer.</span></span>

### <span data-ttu-id="d8c75-114">範例2：取得所有可用的封裝提供者</span><span class="sxs-lookup"><span data-stu-id="d8c75-114">Example 2: Get all available package providers</span></span>

```
PS C:\> Get-PackageProvider -ListAvailable
```

<span data-ttu-id="d8c75-115">此命令會取得本機電腦上可用的所有封裝提供者清單。</span><span class="sxs-lookup"><span data-stu-id="d8c75-115">This command gets a list of all package providers that are available on the local computer.</span></span>

### <span data-ttu-id="d8c75-116">範例3：動態取得封裝提供者</span><span class="sxs-lookup"><span data-stu-id="d8c75-116">Example 3: Dynamically get a package provider</span></span>

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

<span data-ttu-id="d8c75-117">如果您的電腦未安裝 Chocolatey 提供者，此命令會自動安裝 Chocolatey 提供者。</span><span class="sxs-lookup"><span data-stu-id="d8c75-117">This command automatically installs the Chocolatey provider if your computer does not have the Chocolatey provider installed.</span></span>

## <span data-ttu-id="d8c75-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8c75-118">PARAMETERS</span></span>

### <span data-ttu-id="d8c75-119">-Force</span><span class="sxs-lookup"><span data-stu-id="d8c75-119">-Force</span></span>

<span data-ttu-id="d8c75-120">指出此 Cmdlet 會使用可強制執行的這個 Cmdlet 來強制執行所有其他動作。</span><span class="sxs-lookup"><span data-stu-id="d8c75-120">Indicates that this cmdlet forces all other actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="d8c75-121">在 **install-packageprovider** 中，這表示 *Force* 參數的作用與 *ForceBootstrap* 參數相同。</span><span class="sxs-lookup"><span data-stu-id="d8c75-121">In **Get-PackageProvider** , this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="d8c75-122">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d8c75-122">-ForceBootstrap</span></span>

<span data-ttu-id="d8c75-123">指出此 Cmdlet 會強制套件管理自動安裝封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="d8c75-123">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="d8c75-124">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="d8c75-124">-ListAvailable</span></span>

<span data-ttu-id="d8c75-125">取得所有已安裝的提供者。</span><span class="sxs-lookup"><span data-stu-id="d8c75-125">Gets all installed providers.</span></span>
<span data-ttu-id="d8c75-126">**Install-packageprovider** 會取得 **PSModulePath** 環境變數所列路徑中的提供者，以及套件提供者元件資料夾：</span><span class="sxs-lookup"><span data-stu-id="d8c75-126">**Get-PackageProvider** gets provider in paths listed in the **PSModulePath** environment variable as well as the package provider assembly folders:</span></span>

<span data-ttu-id="d8c75-127">**$env:P rogramfiles\packagemanagement\providerassemblies** **$env： localappdata\packagemanagement\providerassemblies 有舊版**</span><span class="sxs-lookup"><span data-stu-id="d8c75-127">**$env:ProgramFiles\PackageManagement\ProviderAssemblies** **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span></span>

<span data-ttu-id="d8c75-128">如果沒有這個參數， **install-packageprovider** 只會取得目前會話中載入的提供者。</span><span class="sxs-lookup"><span data-stu-id="d8c75-128">Without this parameter, **Get-PackageProvider** gets only the providers loaded in the current session.</span></span>

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

### <span data-ttu-id="d8c75-129">-Name</span><span class="sxs-lookup"><span data-stu-id="d8c75-129">-Name</span></span>

<span data-ttu-id="d8c75-130">指定一或多個提供者名稱，或部分提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="d8c75-130">Specifies one or more provider names, or partial provider names.</span></span>
<span data-ttu-id="d8c75-131">以逗號分隔多個提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="d8c75-131">Separate multiple provider names with commas.</span></span>
<span data-ttu-id="d8c75-132">這個參數的有效值包括您隨封裝安裝的提供者名稱;PackageManagement 隨附一組預設的提供者，包括 **PSModule** 和 **MSI** 提供者。</span><span class="sxs-lookup"><span data-stu-id="d8c75-132">Valid values for this parameter include names of providers that you have installed with packages; PackageManagement ships with a set of default providers, including the **PSModule** and **MSI** providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8c75-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8c75-133">CommonParameters</span></span>

<span data-ttu-id="d8c75-134">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8c75-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8c75-135">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8c75-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8c75-136">輸入</span><span class="sxs-lookup"><span data-stu-id="d8c75-136">INPUTS</span></span>

## <span data-ttu-id="d8c75-137">輸出</span><span class="sxs-lookup"><span data-stu-id="d8c75-137">OUTPUTS</span></span>

### <span data-ttu-id="d8c75-138">Install-packageprovider []</span><span class="sxs-lookup"><span data-stu-id="d8c75-138">PackageProvider[]</span></span>

## <span data-ttu-id="d8c75-139">注意</span><span class="sxs-lookup"><span data-stu-id="d8c75-139">NOTES</span></span>

## <span data-ttu-id="d8c75-140">相關連結</span><span class="sxs-lookup"><span data-stu-id="d8c75-140">RELATED LINKS</span></span>

[<span data-ttu-id="d8c75-141">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d8c75-141">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d8c75-142">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d8c75-142">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="d8c75-143">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d8c75-143">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="d8c75-144">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d8c75-144">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
