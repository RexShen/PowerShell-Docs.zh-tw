---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: a3b176101bebf7081febd8629bddcfa0ae1e7540
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="8f174-102">Import-DscResource 關鍵字支援 -ModuleVersion 參數</span><span class="sxs-lookup"><span data-stu-id="8f174-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="8f174-103">我們將新的參數新增至撰寫 DSC 設定時可用的 `Import-DscResource` 動態關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8f174-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="8f174-104">設定作者現在可以指定要從哪個模組版本中載入 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="8f174-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="8f174-105">新關鍵字的語法為︰</span><span class="sxs-lookup"><span data-stu-id="8f174-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="8f174-106">**名稱**︰要匯入之一個或多個資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f174-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="8f174-107">**ModuleName**︰要匯入之一個或多個模組的名稱或 ModuleSpecification 物件。</span><span class="sxs-lookup"><span data-stu-id="8f174-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="8f174-108">**ModuleVersion**︰要匯入的模組版本。</span><span class="sxs-lookup"><span data-stu-id="8f174-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="8f174-109">如果使用了的話，ModuleName 必須只以名稱代表一個模組。</span><span class="sxs-lookup"><span data-stu-id="8f174-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="8f174-110">在 Windows PowerShell ISE 中，它和 IntelliSense 一同顯示：</span><span class="sxs-lookup"><span data-stu-id="8f174-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="8f174-111">**注意：**`–ModuleVersion` 參數只能搭配 `–ModuleName` 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="8f174-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="8f174-112">它不能搭配僅以 `–Name` 參數作為名稱的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="8f174-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="8f174-113">在這之前，載入 DSC 資源時指定模組版本的唯一方法是使用模組規格物件，例如︰`–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="8f174-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>