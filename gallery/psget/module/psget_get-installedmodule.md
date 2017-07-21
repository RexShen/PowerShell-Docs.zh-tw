---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Get-InstalledModule
ms.openlocfilehash: 6f485d04503ea6d9a51a68ae7ec3d0dc2e6facab
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="get-installedmodule"></a><span data-ttu-id="08c0b-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="08c0b-103">Get-InstalledModule</span></span>

<span data-ttu-id="08c0b-104">取得電腦上的已安裝模組。</span><span class="sxs-lookup"><span data-stu-id="08c0b-104">Gets installed modules on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="08c0b-105">描述</span><span class="sxs-lookup"><span data-stu-id="08c0b-105">Description</span></span>

<span data-ttu-id="08c0b-106">Get-InstalledModule Cmdlet 會將 PowerShell 模組安裝在使用 Install-Module Cmdlet 安裝的電腦上。</span><span class="sxs-lookup"><span data-stu-id="08c0b-106">The Get-InstalledModule cmdlet gets installed PowerShell modules on a computer which were installed using Install-Module cmdlet.</span></span>

<span data-ttu-id="08c0b-107">針對每個已安裝的模組，Get-InstalledModule 會傳回可選擇性地傳送至 Uninstall-Module 的 PSRepositoryItemInfo 物件，以解除安裝已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="08c0b-107">For each installed module, Get-InstalledModule returns a PSRepositoryItemInfo object which can optionally be piped to Uninstall-Module for uninstalling the installed modules.</span></span>

- <span data-ttu-id="08c0b-108">Get-InstalledModule 可以根據名稱和版本參數來篩選已安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="08c0b-108">Get-InstalledModule can filter installed modules based on name, version parameters.</span></span>
- <span data-ttu-id="08c0b-109">Get-InstalledModule 可以使用版本參數 MinimumVersion、MaximumVersion、RequiredVersion、AllVersions 進行篩選。</span><span class="sxs-lookup"><span data-stu-id="08c0b-109">Get-InstalledModule can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="08c0b-110">這些參數互斥 (MinmimumVersion 和 MaximumVersion 除外)。</span><span class="sxs-lookup"><span data-stu-id="08c0b-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="08c0b-111">只有不含任何萬用字元的單一模組名稱才允許使用這些版本參數。</span><span class="sxs-lookup"><span data-stu-id="08c0b-111">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="08c0b-112">如果未指定 RequiredVersion 參數，Get-InstalledModule 會傳回等於或大於所指定最小版本之已安裝模組的最新版本，或未指定最小版本之模組的最新版本。</span><span class="sxs-lookup"><span data-stu-id="08c0b-112">If the RequiredVersion parameter is not specified, Get-InstalledModule returns the latest version of the installed module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span> 
  - <span data-ttu-id="08c0b-113">如果指定 RequiredVersion 參數，Get-InstalledModule 只會傳回完全符合所指定版本之已安裝模組的版本。</span><span class="sxs-lookup"><span data-stu-id="08c0b-113">If the RequiredVersion parameter is specified, Get-InstalledModule only returns the version of installed module that exactly matches the specified version.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="08c0b-114">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="08c0b-114">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Get-InstalledModule -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="08c0b-115">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="08c0b-115">Cmdlet online help reference</span></span>

[<span data-ttu-id="08c0b-116">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="08c0b-116">Get-InstalledModule</span></span>](http://go.microsoft.com/fwlink/?LinkId=526863)

## <a name="example-commands"></a><span data-ttu-id="08c0b-117">範例命令</span><span class="sxs-lookup"><span data-stu-id="08c0b-117">Example commands</span></span>

```powershell

# Get all modules installed using PowerShellGet cmdlets
Get-InstalledModule

# Get a specific installed module
Get-InstalledModule DJoin

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        DJoin                               PSGallery            This is a PowerShell frontend to the DJOIN.exe c...

# Get installed module with wildcards
Get-InstalledModule -Name AzureRM*

# Get all versions of an installed module
Get-InstalledModule -Name AzureRM.Automation -AllVersions

# Get installed module with MinimumVersion
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0

# Get installed module with MaximumVersion
Get-InstalledModule -Name AzureRM.Automation -MaximumVersion 1.0.8

# Get installed module with version range
Get-InstalledModule -Name AzureRM.Automation -MinimumVersion 1.0.0 -MaximumVersion 1.0.8

# Get installed module with RequiredVersion
Get-InstalledScript -Name AzureRM.Automation -RequiredVersion 1.0.3

# Properties of Get-InstalledModule returned object
Get-InstalledModule DJoin | Format-List * -Force

Name                       : DJoin
Version                    : 1.0
Type                       : Module
Description                : This is a PowerShell frontend to the DJOIN.exe command which provides better
                             discoverability and usability.
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 7:12:37 PM
InstalledDate              : 4/5/2016 4:13:39 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Modules\DJoin\1.0

```



## <a name="installeddate-and-updateddate-properties-in-psgetrepositoryiteminfo-object"></a><span data-ttu-id="08c0b-118">PSGetRepositoryItemInfo 物件中的 InstalledDate 和 UpdatedDate 屬性</span><span class="sxs-lookup"><span data-stu-id="08c0b-118">InstalledDate and UpdatedDate properties in PSGetRepositoryItemInfo object</span></span>

    During the install operation:
        InstalledDate: current DateTime (Get-Date) value
        UpdatedDate: null

    During the Update operation:
        InstalledDate: InstalledDate from the previous installation otherwise current DateTime (Get-Date) value
        UpdatedDate: current DateTime (Get-Date) value

```powershell
Install-Module -Name ContosoServer -RequiredVersion 1.0 -Repository INT
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM


\Update-Module -Name ContosoServer
Get-InstalledModule -Name ContosoServer | Format-Table Name, InstalledDate, UpdatedDate

Name          InstalledDate         UpdatedDate
----          -------------         -----------
ContosoServer 2/29/2016 11:59:14 AM 2/29/2016 12:00:15 PM
```

