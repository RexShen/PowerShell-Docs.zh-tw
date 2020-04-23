---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: 必須接受指令碼的授權
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328079"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="29505-103">必須接受指令碼的授權</span><span class="sxs-lookup"><span data-stu-id="29505-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="29505-104">接受授權並不支援指令碼。</span><span class="sxs-lookup"><span data-stu-id="29505-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="29505-105">不過，指令碼相依於需要接受授權之模組的案例是受到支援的。</span><span class="sxs-lookup"><span data-stu-id="29505-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="29505-106">指令碼命令 (Install-Script/Save-Script/Update-Script) 支援新的參數 –AcceptLicense，該參數的行為將會有如使用者已看見授權。</span><span class="sxs-lookup"><span data-stu-id="29505-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="29505-107">若未指定 -AcceptLicense，系統將會對使用者顯示相依模組的 license.txt，並提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="29505-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="29505-108">範例</span><span class="sxs-lookup"><span data-stu-id="29505-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="29505-109">範例 1：Install 指令碼具有要求接受授權的相依性</span><span class="sxs-lookup"><span data-stu-id="29505-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="29505-110">指令碼 'ScriptRequireLicenseAcceptance' 相依於模組 'ModuleRequireLicenseAcceptance'。</span><span class="sxs-lookup"><span data-stu-id="29505-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="29505-111">系統會提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="29505-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="29505-112">範例 2：Install 指令碼具有必須接受授權的相依性和 -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="29505-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="29505-113">指令碼 'ScriptRequireLicenseAcceptance' 相依於模組 'ModuleRequireLicenseAcceptance'。</span><span class="sxs-lookup"><span data-stu-id="29505-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="29505-114">由於已指定 -AcceptLicense，系統將不會提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="29505-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="29505-115">其他詳細資訊</span><span class="sxs-lookup"><span data-stu-id="29505-115">More details</span></span>

- [<span data-ttu-id="29505-116">適用於模組的必須接受授權支援</span><span class="sxs-lookup"><span data-stu-id="29505-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="29505-117">PowerShellGallery 上的必須接受授權支援</span><span class="sxs-lookup"><span data-stu-id="29505-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="29505-118">部署至 Azure 自動化上的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="29505-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
