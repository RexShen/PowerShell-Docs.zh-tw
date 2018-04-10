---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: Get-InstalledScript
ms.openlocfilehash: 668327905b0dab40119940a3134b674c452f538d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="get-installedscript"></a><span data-ttu-id="d044b-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="d044b-103">Get-InstalledScript</span></span>

<span data-ttu-id="d044b-104">取得電腦上的已安裝指令碼。</span><span class="sxs-lookup"><span data-stu-id="d044b-104">Gets installed scripts on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="d044b-105">描述</span><span class="sxs-lookup"><span data-stu-id="d044b-105">Description</span></span>

<span data-ttu-id="d044b-106">Get-InstalledScript Cmdlet 會取得電腦上的已安裝 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="d044b-106">The Get-InstalledScript cmdlet gets installed PowerShell scripts on a computer.</span></span>

<span data-ttu-id="d044b-107">針對每個已安裝的指令碼，Get-InstalledScript 會傳回可選擇性地傳送至 Uninstall-Script 的 PSRepositoryItemInfo 物件，以解除安裝已安裝的指令碼。</span><span class="sxs-lookup"><span data-stu-id="d044b-107">For each installed script, Get-InstalledScript returns a PSRepositoryItemInfo object which can optionally be piped to Uninstall-Script for uninstalling the installed scripts.</span></span>

- <span data-ttu-id="d044b-108">Get-InstalledScript 可以根據名稱和版本參數來篩選已安裝的指令碼。</span><span class="sxs-lookup"><span data-stu-id="d044b-108">Get-InstalledScript can filter installed scripts based on name, version parameters.</span></span>
- <span data-ttu-id="d044b-109">Get-InstalledScript 可以使用版本參數 MinimumVersion、MaximumVersion、RequiredVersion、AllVersions 進行篩選。</span><span class="sxs-lookup"><span data-stu-id="d044b-109">Get-InstalledScript can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="d044b-110">這些參數互斥 (MinmimumVersion 和 MaximumVersion 除外)。</span><span class="sxs-lookup"><span data-stu-id="d044b-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="d044b-111">只有不含任何萬用字元的單一指令碼名稱才允許使用這些版本參數。</span><span class="sxs-lookup"><span data-stu-id="d044b-111">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="d044b-112">如果未指定 RequiredVersion 參數，Get-InstalledScript 會傳回等於或大於所指定最小版本之已安裝指令碼的最新版本，或未指定最小版本之指令碼的最新版本。</span><span class="sxs-lookup"><span data-stu-id="d044b-112">If the RequiredVersion parameter is not specified, Get-InstalledScript returns the latest version of the installed script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span>
  - <span data-ttu-id="d044b-113">如果指定 RequiredVersion 參數，Get-InstalledScript 只會傳回完全符合所指定版本之已安裝指令碼的版本。</span><span class="sxs-lookup"><span data-stu-id="d044b-113">If the RequiredVersion parameter is specified, Get-InstalledScript only returns the version of installed script that exactly matches the specified version.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="d044b-114">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="d044b-114">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="d044b-115">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="d044b-115">Cmdlet online help reference</span></span>

[<span data-ttu-id="d044b-116">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="d044b-116">Get-InstalledScript</span></span>](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a><span data-ttu-id="d044b-117">範例命令</span><span class="sxs-lookup"><span data-stu-id="d044b-117">Example commands</span></span>

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```