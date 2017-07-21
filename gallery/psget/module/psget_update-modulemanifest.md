---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Update-ModuleManifest
ms.openlocfilehash: ce3f6f173535d98648eb51adb1dbf84764e4f434
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="update-modulemanifest"></a><span data-ttu-id="4ebb7-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="4ebb7-103">Update-ModuleManifest</span></span>
<span data-ttu-id="4ebb7-104">更新模組資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-104">Updates a module manifest file.</span></span>

## <a name="description"></a><span data-ttu-id="4ebb7-105">描述</span><span class="sxs-lookup"><span data-stu-id="4ebb7-105">Description</span></span>

<span data-ttu-id="4ebb7-106">Update-ModuleManifest Cmdlet 會更新模組資訊清單 (.psd1) 檔案。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-106">The Update-ModuleManifest cmdlet updates a module manifest (.psd1) file.</span></span>

### <a name="notes"></a><span data-ttu-id="4ebb7-107">注意</span><span class="sxs-lookup"><span data-stu-id="4ebb7-107">Notes</span></span>
    - <span data-ttu-id="4ebb7-108">只有最新 5.0 版的 PowerShell 才支援 DscResourcesToExport。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-108">DscResourcesToExport is only supported on the latest PowerShell version 5.0.</span></span> <span data-ttu-id="4ebb7-109">若是在此版之前的舊版 PowerShell 上執行，便無法更新此欄位。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-109">We won’t be able to update the field if you are running on lower versions of PowerShell.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="4ebb7-110">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="4ebb7-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="4ebb7-111">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="4ebb7-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="4ebb7-112">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="4ebb7-112">Update-ModuleManifest</span></span>](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a><span data-ttu-id="4ebb7-113">範例命令</span><span class="sxs-lookup"><span data-stu-id="4ebb7-113">Example commands</span></span>

<span data-ttu-id="4ebb7-114">這個新的 Cmdlet 是用來協助以輸入屬性值更新資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-114">This new cmdlet is used to help update manifest file with input property values.</span></span> <span data-ttu-id="4ebb7-115">它會採用 New-ModuleManifest 執行的所有參數。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-115">It takes all parameters that New-ModuleManifest does.</span></span>

<span data-ttu-id="4ebb7-116">我們發現很多模組作者想要在匯出的值中指定 “\*”，如 FunctionsToExport、CmdletsToExport 等等。在模組發佈至 PowerShell Gallery 的期間，未指定的功能和命令不會正確填入到 Gallery 中。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-116">We notice that a lot of module authors would like to specify “\*” in exported values such as FunctionsToExport, CmdletsToExport, etc. During module publishing to PowerShell Gallery, unspecified functions and commands will not be populated properly onto the Gallery.</span></span> <span data-ttu-id="4ebb7-117">因此，建議模組作者以適當的值更新其資訊清單。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-117">Therefore, we suggest module authors update their manifests with proper values.</span></span>

<span data-ttu-id="4ebb7-118">如果模組有匯出的屬性，Update-ModuleManifest 會使用匯出的函式、Cmdlet、變數等資訊填滿指定的資訊清單檔案：</span><span class="sxs-lookup"><span data-stu-id="4ebb7-118">If you have modules that have exported properties, Update-ModuleManifest will fill the specified manifest file with information from exported functions, cmdlets, variables etc:</span></span>
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

<span data-ttu-id="4ebb7-119">在 Update-ModuleManifest 之後：</span><span class="sxs-lookup"><span data-stu-id="4ebb7-119">After Update-ModuleManifest:</span></span>
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

<span data-ttu-id="4ebb7-120">每個模組也還有相關聯的中繼資料欄位。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-120">For each module, there are also metadata fields associated with it.</span></span> <span data-ttu-id="4ebb7-121">為了在 PowrShell Gallery 上正確顯示中繼資料，您可以使用 Update-ModuleManifest 填入 PrivateData 下的這些欄位。</span><span class="sxs-lookup"><span data-stu-id="4ebb7-121">In order to display metadata properly on PowrShell Gallery, you can use Update-ModuleManifest to populate those fields under PrivateData.</span></span>

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

<span data-ttu-id="4ebb7-122">資訊清單檔範本的 PrivateData 雜湊表具有下列屬性</span><span class="sxs-lookup"><span data-stu-id="4ebb7-122">PrivateData hashtable from the manifest file template has the following properties</span></span>

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''
    
        # A URL to the main website for this project.
        # ProjectUri = ''
        
        # A URL to an icon representing this module.
        # IconUri = ''
        
        # ReleaseNotes of this module
        # ReleaseNotes = ''
        
        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```

