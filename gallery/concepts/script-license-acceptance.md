---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: 必須接受指令碼的授權
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048231"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="9f1dd-103">必須接受指令碼的授權</span><span class="sxs-lookup"><span data-stu-id="9f1dd-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="9f1dd-104">接受授權並不支援指令碼。</span><span class="sxs-lookup"><span data-stu-id="9f1dd-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="9f1dd-105">不過，指令碼相依於需要接受授權之模組的案例是受到支援的。</span><span class="sxs-lookup"><span data-stu-id="9f1dd-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="9f1dd-106">指令碼命令 (Install-Script/Save-Script/Update-Script) 支援新的參數 –AcceptLicense，該參數的行為將會有如使用者已看見授權。</span><span class="sxs-lookup"><span data-stu-id="9f1dd-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="9f1dd-107">若未指定 -AcceptLicense，系統將會對使用者顯示相依模組的 license.txt，並提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="9f1dd-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="9f1dd-108">範例</span><span class="sxs-lookup"><span data-stu-id="9f1dd-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="9f1dd-109">範例 1：Install 指令碼具有要求接受授權的相依性</span><span class="sxs-lookup"><span data-stu-id="9f1dd-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="9f1dd-110">指令碼 'ScriptRequireLicenseAcceptance' 相依於模組 'ModuleRequireLicenseAcceptance'。</span><span class="sxs-lookup"><span data-stu-id="9f1dd-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="9f1dd-111">系統會提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="9f1dd-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="9f1dd-112">範例 2：Install 指令碼具有必須接受授權的相依性和 -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="9f1dd-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="9f1dd-113">指令碼 'ScriptRequireLicenseAcceptance' 相依於模組 'ModuleRequireLicenseAcceptance'。</span><span class="sxs-lookup"><span data-stu-id="9f1dd-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="9f1dd-114">由於已指定 -AcceptLicense，系統將不會提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="9f1dd-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="9f1dd-115">更多詳細資料</span><span class="sxs-lookup"><span data-stu-id="9f1dd-115">More details</span></span>

- [<span data-ttu-id="9f1dd-116">適用於模組的必須接受授權支援</span><span class="sxs-lookup"><span data-stu-id="9f1dd-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="9f1dd-117">PowerShellGallery 上的必須接受授權支援</span><span class="sxs-lookup"><span data-stu-id="9f1dd-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [<span data-ttu-id="9f1dd-118">部署至 Azure 自動化上的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="9f1dd-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)