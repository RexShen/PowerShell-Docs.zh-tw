---
ms.date: 06/09/2017
title: 必須接受指令碼的授權
description: 此文章說明如何使用在 PowerShell 資源庫中所發佈、要求您必須接受終端使用者授權的指令碼。
ms.openlocfilehash: d82974810fd1e73ef8d9e5771fc430d0f7964e87
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656077"
---
# <a name="requiring-license-acceptance-for-scripts"></a>必須接受指令碼的授權

接受授權並不支援指令碼。 不過，指令碼相依於需要接受授權之模組的案例是受到支援的。

PowerShellGet 指令碼命令支援 **AcceptLicense** 參數，此參數的行為就像使用者看到授權一樣。 若未指定 **AcceptLicense** ，系統將會向使用者顯示相依模組的 `license.txt` 檔案，並提示接受授權。

## <a name="examples"></a>範例

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>範例 1：Install 指令碼具有要求接受授權的相依性

指令碼 'ScriptRequireLicenseAcceptance' 相依於模組 'ModuleRequireLicenseAcceptance'。 系統會提示使用者接受授權。

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>範例 2：Install 指令碼具有必須接受授權的相依性和 -AcceptLicense

指令碼 'ScriptRequireLicenseAcceptance' 相依於模組 'ModuleRequireLicenseAcceptance'。 由於已指定 -AcceptLicense，系統將不會提示使用者接受授權。

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>其他詳細資訊

- [適用於模組的必須接受授權支援](module-license-acceptance.md)
- [PowerShellGallery 上的必須接受授權支援](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [部署至 Azure 自動化上的必須接受授權](../how-to/working-with-packages/deploy-to-azure-automation.md)
