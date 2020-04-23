---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: 必須接受授權的模組
ms.openlocfilehash: a2f7ed72aae8579a6723f65b86dd0993f1a22afd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "80082821"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="5d59d-103">必須接受授權的模組</span><span class="sxs-lookup"><span data-stu-id="5d59d-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="5d59d-104">概要</span><span class="sxs-lookup"><span data-stu-id="5d59d-104">SYNOPSIS</span></span>

<span data-ttu-id="5d59d-105">某些模組發行者的法務部門會要求客戶明確接受授權，以從 PowerShell 資源庫安裝他們的模組。</span><span class="sxs-lookup"><span data-stu-id="5d59d-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="5d59d-106">若使用者使用 PowerShellGet 安裝、更新或儲存模組 (無論是直接或以另一個套件之相依性的形式)，且該模組要求使用者同意授權，則該使用者必須表示他們接受該授權，否則作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5d59d-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another package, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="5d59d-107">針對模組的發行要求</span><span class="sxs-lookup"><span data-stu-id="5d59d-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="5d59d-108">想要求使用者接受授權的模組，應該要滿足下列需求：</span><span class="sxs-lookup"><span data-stu-id="5d59d-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="5d59d-109">模組資訊清單的 PSData 區段應包含 RequireLicenseAcceptance = $True。</span><span class="sxs-lookup"><span data-stu-id="5d59d-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="5d59d-110">模組的根目錄應包含 license.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="5d59d-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="5d59d-111">模組資訊清單應包含授權 URI。</span><span class="sxs-lookup"><span data-stu-id="5d59d-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="5d59d-112">模組應使用 PowerShellGet 格式版本 2.0 版及更新版本發行。</span><span class="sxs-lookup"><span data-stu-id="5d59d-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="5d59d-113">對 Install/Save/Update-Module 的影響</span><span class="sxs-lookup"><span data-stu-id="5d59d-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="5d59d-114">安裝/儲存/更新 Cmdlet 支援新的參數 **AcceptLicense**，該參數的行為將會有如使用者已看見授權。</span><span class="sxs-lookup"><span data-stu-id="5d59d-114">Install/Save/Update cmdlets support a new parameter **AcceptLicense** that behaves as though the user saw the license.</span></span>
- <span data-ttu-id="5d59d-115">若 **RequiredLicenseAcceptance** 為 True 且未指定 **AcceptLicense**，系統將為使用者顯示 `license.txt`，並提示：`Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`。</span><span class="sxs-lookup"><span data-stu-id="5d59d-115">If **RequiredLicenseAcceptance** is True and **AcceptLicense** is not specified, the user is shown the `license.txt`, and prompted with: `Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`.</span></span>
  - <span data-ttu-id="5d59d-116">若授權已被接受</span><span class="sxs-lookup"><span data-stu-id="5d59d-116">If the license is accepted</span></span>
    - <span data-ttu-id="5d59d-117">**Save-Module：** 系統會將模組複製到使用者的系統</span><span class="sxs-lookup"><span data-stu-id="5d59d-117">**Save-Module:** the module is copied to the user's system</span></span>
    - <span data-ttu-id="5d59d-118">**Install-Module：** 系統會將模組複製到使用者系統上適當的資料夾 (根據範圍)</span><span class="sxs-lookup"><span data-stu-id="5d59d-118">**Install-Module:** the module is copied to the user's system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="5d59d-119">**Update-Module：** 系統會更新模組。</span><span class="sxs-lookup"><span data-stu-id="5d59d-119">**Update-Module:** the module is updated.</span></span>
  - <span data-ttu-id="5d59d-120">若授權已被拒絕。</span><span class="sxs-lookup"><span data-stu-id="5d59d-120">If the license is declined.</span></span>
    - <span data-ttu-id="5d59d-121">操作已取消。</span><span class="sxs-lookup"><span data-stu-id="5d59d-121">Operation is canceled.</span></span>
    - <span data-ttu-id="5d59d-122">所有 Cmdlet 都會針對表示必須接受授權的中繼資料 (**requireLicenseAcceptance** 與格式版本) 進行檢查</span><span class="sxs-lookup"><span data-stu-id="5d59d-122">All cmdlets check for the metadata (**requireLicenseAcceptance** and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="5d59d-123">若用戶端的格式版本早於 2.0 版，作業會失敗並要求使用者更新用戶端。</span><span class="sxs-lookup"><span data-stu-id="5d59d-123">If format version of client is older than 2.0, operation fails and asks the user to update the client.</span></span>
    - <span data-ttu-id="5d59d-124">若模組是以早於 2.0 版的格式版本發行，則系統會忽略 requireLicenseAcceptance 旗標。</span><span class="sxs-lookup"><span data-stu-id="5d59d-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag is ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="5d59d-125">模組相依性</span><span class="sxs-lookup"><span data-stu-id="5d59d-125">Module Dependencies</span></span>

- <span data-ttu-id="5d59d-126">在安裝/儲存/更新作業期間，若相依模組 (相依於模組的其他項目) 必須接受授權，則會要求 (上述的) 授權接受行為。</span><span class="sxs-lookup"><span data-stu-id="5d59d-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) is required.</span></span>
- <span data-ttu-id="5d59d-127">如果模組版本已於本機目錄中列為已安裝在系統上，將會略過授權檢查。</span><span class="sxs-lookup"><span data-stu-id="5d59d-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="5d59d-128">在安裝/儲存/更新作業期間，若相依模組要求授權，且授權接受並沒有發生，則該作業會失敗，並依循套件安裝/儲存/更新失敗的一般程序執行。</span><span class="sxs-lookup"><span data-stu-id="5d59d-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation fails and follows normal processes for the package failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="5d59d-129">對 -Force 的影響</span><span class="sxs-lookup"><span data-stu-id="5d59d-129">Impact on -Force</span></span>

<span data-ttu-id="5d59d-130">指定 `–Force` 並不足以接受授權。</span><span class="sxs-lookup"><span data-stu-id="5d59d-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="5d59d-131">需要 `–AcceptLicense` 以取得安裝的權限。</span><span class="sxs-lookup"><span data-stu-id="5d59d-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="5d59d-132">若指定 `–Force` 且 RequiredLicenseAcceptance 為 True，而且未指定 `–AcceptLicense`，則作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="5d59d-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation fails.</span></span>

## <a name="examples"></a><span data-ttu-id="5d59d-133">範例</span><span class="sxs-lookup"><span data-stu-id="5d59d-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="5d59d-134">範例 1：更新模組資訊清單以要求接受授權</span><span class="sxs-lookup"><span data-stu-id="5d59d-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="5d59d-135">此命令會更新資訊清單檔案，並將 RequireLicenseAcceptance 旗標設定為 True。</span><span class="sxs-lookup"><span data-stu-id="5d59d-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="5d59d-136">範例 2：Install 模組要求接受授權</span><span class="sxs-lookup"><span data-stu-id="5d59d-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="5d59d-137">此命令會顯示來自 `license.txt` 檔案的授權，並提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="5d59d-137">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="5d59d-138">範例 3：Install 模組要求接受授權並搭配 -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="5d59d-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="5d59d-139">模組會在沒有任何接受授權的提示之下安裝。</span><span class="sxs-lookup"><span data-stu-id="5d59d-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="5d59d-140">範例 4：Install 模組要求接受授權並搭配 -Force</span><span class="sxs-lookup"><span data-stu-id="5d59d-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```Output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="5d59d-141">範例 5：Install 模組具有要求接受授權的相依性</span><span class="sxs-lookup"><span data-stu-id="5d59d-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="5d59d-142">模組 **ModuleWithDependency** 相依於模組 **ModuleRequireLicenseAcceptance**。</span><span class="sxs-lookup"><span data-stu-id="5d59d-142">Module **ModuleWithDependency** depends on module **ModuleRequireLicenseAcceptance**.</span></span> <span data-ttu-id="5d59d-143">系統會提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="5d59d-143">User is prompted to accept license.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```Output
License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="5d59d-144">範例 6：Install 模組具有必須接受授權的相依性和 -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="5d59d-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="5d59d-145">模組 **ModuleWithDependency** 相依於模組 **ModuleRequireLicenseAcceptance**。</span><span class="sxs-lookup"><span data-stu-id="5d59d-145">Module **ModuleWithDependency** depends on module **ModuleRequireLicenseAcceptance**.</span></span> <span data-ttu-id="5d59d-146">由於已指定 **AcceptLicense**，系統不會提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="5d59d-146">User is not prompted to accept license as **AcceptLicense** is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="5d59d-147">範例 7：Install 模組在早於 PSGetFormatVersion 2.0 的用戶端上要求接受授權</span><span class="sxs-lookup"><span data-stu-id="5d59d-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion
'2.0' is not supported by the current version of PowerShellGet. Get the latest version of the
PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="5d59d-148">範例 8：Save 模組要求接受授權</span><span class="sxs-lookup"><span data-stu-id="5d59d-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="5d59d-149">此命令會顯示來自 `license.txt` 檔案的授權，並提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="5d59d-149">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="5d59d-150">範例 9：Save 模組要求接受授權並搭配 -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="5d59d-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="5d59d-151">模組會在沒有任何接受授權的提示之下儲存。</span><span class="sxs-lookup"><span data-stu-id="5d59d-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="5d59d-152">範例 10：Update 模組要求接受授權</span><span class="sxs-lookup"><span data-stu-id="5d59d-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="5d59d-153">此命令會顯示來自 `license.txt` 檔案的授權，並提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="5d59d-153">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="5d59d-154">範例 11：Update 模組要求接受授權並搭配 -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="5d59d-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="5d59d-155">模組會在沒有任何接受授權的提示之下更新。</span><span class="sxs-lookup"><span data-stu-id="5d59d-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="5d59d-156">其他詳細資訊</span><span class="sxs-lookup"><span data-stu-id="5d59d-156">More details</span></span>

[<span data-ttu-id="5d59d-157">適用於指令碼的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="5d59d-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="5d59d-158">PowerShellGallery 上的必須接受授權支援</span><span class="sxs-lookup"><span data-stu-id="5d59d-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[<span data-ttu-id="5d59d-159">部署至 Azure 自動化上的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="5d59d-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
