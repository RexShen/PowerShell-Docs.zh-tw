---
ms.date: 06/09/2017
title: 必須接受授權的模組
description: 此文章說明如何使用在 PowerShell 資源庫中所發佈、要求您必須接受終端使用者授權的模組。
ms.openlocfilehash: a9486e10b10569ce8bcde47d5c8acf0796a93851
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656108"
---
# <a name="modules-requiring-license-acceptance"></a>必須接受授權的模組

## <a name="synopsis"></a>概要

某些模組發行者的法務部門會要求客戶明確接受授權，以從 PowerShell 資源庫安裝他們的模組。 若使用者使用 PowerShellGet 安裝、更新或儲存模組 (無論是直接或以另一個套件之相依性的形式)，且該模組要求使用者同意授權，則該使用者必須表示他們接受該授權，否則作業將會失敗。

## <a name="publish-requirements-for-modules"></a>針對模組的發行要求

想要求使用者接受授權的模組，應該要滿足下列需求：

- 模組資訊清單的 PSData 區段應包含 RequireLicenseAcceptance = $True。
- 模組的根目錄應包含 license.txt 檔案。
- 模組資訊清單應包含授權 URI。
- 模組應使用 PowerShellGet 格式版本 2.0 版及更新版本發行。

## <a name="impact-on-installsaveupdate-module"></a>對 Install/Save/Update-Module 的影響

- 安裝/儲存/更新 Cmdlet 支援新的參數 **AcceptLicense** ，該參數的行為將會有如使用者已看見授權。
- 若 **RequiredLicenseAcceptance** 為 True 且未指定 **AcceptLicense** ，系統將為使用者顯示 `license.txt`，並提示：`Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`。
  - 若授權已被接受
    - **Save-Module：** 系統會將模組複製到使用者的系統
    - **Install-Module：** 系統會將模組複製到使用者系統上適當的資料夾 (根據範圍)
    - **Update-Module：** 系統會更新模組。
  - 若授權已被拒絕。
    - 操作已取消。
    - 所有 Cmdlet 都會針對表示必須接受授權的中繼資料 ( **requireLicenseAcceptance** 與格式版本) 進行檢查
    - 若用戶端的格式版本早於 2.0 版，作業會失敗並要求使用者更新用戶端。
    - 若模組是以早於 2.0 版的格式版本發行，則系統會忽略 requireLicenseAcceptance 旗標。

## <a name="module-dependencies"></a>模組相依性

- 在安裝/儲存/更新作業期間，若相依模組 (相依於模組的其他項目) 必須接受授權，則會要求 (上述的) 授權接受行為。
- 如果模組版本已於本機目錄中列為已安裝在系統上，將會略過授權檢查。
- 在安裝/儲存/更新作業期間，若相依模組要求授權，且授權接受並沒有發生，則該作業會失敗，並依循套件安裝/儲存/更新失敗的一般程序執行。

## <a name="impact-on--force"></a>對 -Force 的影響

指定 `–Force` 並不足以接受授權。 需要 `–AcceptLicense` 以取得安裝的權限。 若指定 `–Force` 且 RequiredLicenseAcceptance 為 True，而且未指定 `–AcceptLicense`，則作業會失敗。

## <a name="examples"></a>範例

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>範例 1：更新模組資訊清單以要求接受授權

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

此命令會更新資訊清單檔案，並將 RequireLicenseAcceptance 旗標設定為 True。

### <a name="example-2-install-module-requiring-license-acceptance"></a>範例 2：Install 模組要求接受授權

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

此命令會顯示來自 `license.txt` 檔案的授權，並提示使用者接受授權。

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>範例 3：Install 模組要求接受授權並搭配 -AcceptLicense

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

模組會在沒有任何接受授權的提示之下安裝。

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>範例 4：Install 模組要求接受授權並搭配 -Force

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

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>範例 5：Install 模組具有要求接受授權的相依性

模組 **ModuleWithDependency** 相依於模組 **ModuleRequireLicenseAcceptance** 。 系統會提示使用者接受授權。

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>範例 6：Install 模組具有必須接受授權的相依性和 -AcceptLicense

模組 **ModuleWithDependency** 相依於模組 **ModuleRequireLicenseAcceptance** 。 由於已指定 **AcceptLicense** ，系統不會提示使用者接受授權。

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>範例 7：Install 模組在早於 PSGetFormatVersion 2.0 的用戶端上要求接受授權

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion
'2.0' is not supported by the current version of PowerShellGet. Get the latest version of the
PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>範例 8：Save 模組要求接受授權

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

此命令會顯示來自 `license.txt` 檔案的授權，並提示使用者接受授權。

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>範例 9：Save 模組要求接受授權並搭配 -AcceptLicense

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

模組會在沒有任何接受授權的提示之下儲存。

### <a name="example-10-update-module-requiring-license-acceptance"></a>範例 10：Update 模組要求接受授權

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

此命令會顯示來自 `license.txt` 檔案的授權，並提示使用者接受授權。

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>範例 11：Update 模組要求接受授權並搭配 -AcceptLicense

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

模組會在沒有任何接受授權的提示之下更新。

## <a name="more-details"></a>其他詳細資訊

[適用於指令碼的必須接受授權](./script-license-acceptance.md)

[PowerShellGallery 上的必須接受授權支援](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[部署至 Azure 自動化上的必須接受授權](../how-to/working-with-packages/deploy-to-azure-automation.md)
