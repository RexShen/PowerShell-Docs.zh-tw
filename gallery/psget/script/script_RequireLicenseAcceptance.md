---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 4a2dc39c2b6c380fb4ca94f9fd071ed9cdb35049
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="980bb-103">適用於指令碼的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="980bb-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="980bb-104">接受授權並不支援指令碼。</span><span class="sxs-lookup"><span data-stu-id="980bb-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="980bb-105">不過，指令碼相依於需要接受授權之模組的案例是受到支援的。</span><span class="sxs-lookup"><span data-stu-id="980bb-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="980bb-106">指令碼命令 (Install-Script/Save-Script/Update-Script) 支援新的參數 –AcceptLicense，該參數的行為將會有如使用者已看見授權。</span><span class="sxs-lookup"><span data-stu-id="980bb-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="980bb-107">若未指定 -AcceptLicense，系統將會對使用者顯示相依模組的 license.txt，並提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="980bb-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="980bb-108">範例</span><span class="sxs-lookup"><span data-stu-id="980bb-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="980bb-109">範例 1：Install 指令碼具有要求接受授權的相依性</span><span class="sxs-lookup"><span data-stu-id="980bb-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="980bb-110">指令碼 'ScriptRequireLicenseAcceptance' 相依於模組 'ModuleRequireLicenseAcceptance'。</span><span class="sxs-lookup"><span data-stu-id="980bb-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="980bb-111">系統會提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="980bb-111">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="980bb-112">範例 2：Install 指令碼具有必須接受授權的相依性和 -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="980bb-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="980bb-113">指令碼 'ScriptRequireLicenseAcceptance' 相依於模組 'ModuleRequireLicenseAcceptance'。</span><span class="sxs-lookup"><span data-stu-id="980bb-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="980bb-114">由於已指定 -AcceptLicense，系統將不會提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="980bb-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="980bb-115">更多詳細資料</span><span class="sxs-lookup"><span data-stu-id="980bb-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="980bb-116">適用於模組的必須接受授權支援</span><span class="sxs-lookup"><span data-stu-id="980bb-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="980bb-117">PowerShellGallery 上的必須接受授權支援</span><span class="sxs-lookup"><span data-stu-id="980bb-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="980bb-118">部署至 Azure 自動化上的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="980bb-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)