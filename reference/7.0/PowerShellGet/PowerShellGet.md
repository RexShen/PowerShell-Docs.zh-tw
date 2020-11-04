---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113539
Help Version: 7.0.1.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 6da6adf79693929f75d82e1925eb67496dd9b6ef
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "93206444"
---
# <span data-ttu-id="87ff5-103">PowerShellGet 模組</span><span class="sxs-lookup"><span data-stu-id="87ff5-103">PowerShellGet Module</span></span>

## <span data-ttu-id="87ff5-104">描述</span><span class="sxs-lookup"><span data-stu-id="87ff5-104">Description</span></span>

<span data-ttu-id="87ff5-105">PowerShellGet 是一個模組，其中包含用於探索、安裝、更新及發佈 PowerShell 成品（例如模組、DSC 資源、角色功能和腳本）的命令。</span><span class="sxs-lookup"><span data-stu-id="87ff5-105">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

## <span data-ttu-id="87ff5-106">PowerShellGet Cmdlet</span><span class="sxs-lookup"><span data-stu-id="87ff5-106">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="87ff5-107">Find-Command</span><span class="sxs-lookup"><span data-stu-id="87ff5-107">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="87ff5-108">尋找模組中的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="87ff5-108">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="87ff5-109">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="87ff5-109">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="87ff5-110">尋找 Desired State Configuration (DSC) 資源。</span><span class="sxs-lookup"><span data-stu-id="87ff5-110">Finds Desired State Configuration (DSC) resources.</span></span>

### [<span data-ttu-id="87ff5-111">Find-Module</span><span class="sxs-lookup"><span data-stu-id="87ff5-111">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="87ff5-112">在存放庫中尋找符合指定準則的模組。</span><span class="sxs-lookup"><span data-stu-id="87ff5-112">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="87ff5-113">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="87ff5-113">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="87ff5-114">尋找模組中的角色功能。</span><span class="sxs-lookup"><span data-stu-id="87ff5-114">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="87ff5-115">Find-Script</span><span class="sxs-lookup"><span data-stu-id="87ff5-115">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="87ff5-116">尋找腳本。</span><span class="sxs-lookup"><span data-stu-id="87ff5-116">Finds a script.</span></span>

### [<span data-ttu-id="87ff5-117">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="87ff5-117">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="87ff5-118">取得由 PowerShellGet 安裝之電腦上的模組清單。</span><span class="sxs-lookup"><span data-stu-id="87ff5-118">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="87ff5-119">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="87ff5-119">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="87ff5-120">取得已安裝的腳本。</span><span class="sxs-lookup"><span data-stu-id="87ff5-120">Gets an installed script.</span></span>

### [<span data-ttu-id="87ff5-121">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="87ff5-121">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="87ff5-122">取得 PowerShell 存放庫。</span><span class="sxs-lookup"><span data-stu-id="87ff5-122">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="87ff5-123">Install-Module</span><span class="sxs-lookup"><span data-stu-id="87ff5-123">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="87ff5-124">從存放庫下載一或多個模組，並將它們安裝在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="87ff5-124">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="87ff5-125">Install-Script</span><span class="sxs-lookup"><span data-stu-id="87ff5-125">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="87ff5-126">安裝腳本。</span><span class="sxs-lookup"><span data-stu-id="87ff5-126">Installs a script.</span></span>

### [<span data-ttu-id="87ff5-127">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="87ff5-127">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="87ff5-128">建立含有中繼資料的指令檔。</span><span class="sxs-lookup"><span data-stu-id="87ff5-128">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="87ff5-129">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="87ff5-129">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="87ff5-130">將指定的模組從本機電腦發行至線上資源庫。</span><span class="sxs-lookup"><span data-stu-id="87ff5-130">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="87ff5-131">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="87ff5-131">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="87ff5-132">發佈腳本。</span><span class="sxs-lookup"><span data-stu-id="87ff5-132">Publishes a script.</span></span>

### [<span data-ttu-id="87ff5-133">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="87ff5-133">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="87ff5-134">註冊 PowerShell 存放庫。</span><span class="sxs-lookup"><span data-stu-id="87ff5-134">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="87ff5-135">Save-Module</span><span class="sxs-lookup"><span data-stu-id="87ff5-135">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="87ff5-136">將模組及其相依性儲存在本機電腦上，但不會安裝模組。</span><span class="sxs-lookup"><span data-stu-id="87ff5-136">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="87ff5-137">Save-Script</span><span class="sxs-lookup"><span data-stu-id="87ff5-137">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="87ff5-138">儲存腳本。</span><span class="sxs-lookup"><span data-stu-id="87ff5-138">Saves a script.</span></span>

### [<span data-ttu-id="87ff5-139">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="87ff5-139">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="87ff5-140">設定已註冊存放庫的值。</span><span class="sxs-lookup"><span data-stu-id="87ff5-140">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="87ff5-141">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="87ff5-141">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="87ff5-142">驗證腳本的批註區塊。</span><span class="sxs-lookup"><span data-stu-id="87ff5-142">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="87ff5-143">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="87ff5-143">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="87ff5-144">解除安裝模組。</span><span class="sxs-lookup"><span data-stu-id="87ff5-144">Uninstalls a module.</span></span>

### [<span data-ttu-id="87ff5-145">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="87ff5-145">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="87ff5-146">卸載腳本。</span><span class="sxs-lookup"><span data-stu-id="87ff5-146">Uninstalls a script.</span></span>

### [<span data-ttu-id="87ff5-147">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="87ff5-147">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="87ff5-148">取消註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="87ff5-148">Unregisters a repository.</span></span>

### [<span data-ttu-id="87ff5-149">Update-Module</span><span class="sxs-lookup"><span data-stu-id="87ff5-149">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="87ff5-150">將來自線上組件庫之指定模組的最新版本下載並安裝至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="87ff5-150">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="87ff5-151">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="87ff5-151">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="87ff5-152">更新模組資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="87ff5-152">Updates a module manifest file.</span></span>

### [<span data-ttu-id="87ff5-153">Update-Script</span><span class="sxs-lookup"><span data-stu-id="87ff5-153">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="87ff5-154">更新腳本。</span><span class="sxs-lookup"><span data-stu-id="87ff5-154">Updates a script.</span></span>

### [<span data-ttu-id="87ff5-155">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="87ff5-155">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="87ff5-156">更新腳本的資訊。</span><span class="sxs-lookup"><span data-stu-id="87ff5-156">Updates information for a script.</span></span>
