---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 577dc9a56da98d975b777e6cd48ecdcaafd3128d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892364"
---
# <span data-ttu-id="2b7cc-103">PowerShellGet 模組</span><span class="sxs-lookup"><span data-stu-id="2b7cc-103">PowerShellGet Module</span></span>

## <span data-ttu-id="2b7cc-104">說明</span><span class="sxs-lookup"><span data-stu-id="2b7cc-104">Description</span></span>

<span data-ttu-id="2b7cc-105">PowerShellGet 是一個模組，其中包含用於探索、安裝、更新及發佈 PowerShell 成品（例如模組、DSC 資源、角色功能和腳本）的命令。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-105">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b7cc-106">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="2b7cc-107">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="2b7cc-108">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="2b7cc-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="2b7cc-109">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="2b7cc-110">PowerShellGet Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b7cc-110">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="2b7cc-111">Find-Command</span><span class="sxs-lookup"><span data-stu-id="2b7cc-111">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="2b7cc-112">尋找模組中的 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-112">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="2b7cc-113">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="2b7cc-113">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="2b7cc-114">尋找 Desired State Configuration (DSC) 資源。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-114">Finds Desired State Configuration (DSC) resources.</span></span>

### [<span data-ttu-id="2b7cc-115">Find-Module</span><span class="sxs-lookup"><span data-stu-id="2b7cc-115">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="2b7cc-116">在存放庫中尋找符合指定準則的模組。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-116">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="2b7cc-117">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="2b7cc-117">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="2b7cc-118">尋找模組中的角色功能。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-118">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="2b7cc-119">Find-Script</span><span class="sxs-lookup"><span data-stu-id="2b7cc-119">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="2b7cc-120">尋找腳本。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-120">Finds a script.</span></span>

### [<span data-ttu-id="2b7cc-121">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="2b7cc-121">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="2b7cc-122">取得由 PowerShellGet 安裝之電腦上的模組清單。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-122">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="2b7cc-123">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="2b7cc-123">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="2b7cc-124">取得已安裝的腳本。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-124">Gets an installed script.</span></span>

### [<span data-ttu-id="2b7cc-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="2b7cc-125">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="2b7cc-126">取得 PowerShell 存放庫。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-126">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="2b7cc-127">Install-Module</span><span class="sxs-lookup"><span data-stu-id="2b7cc-127">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="2b7cc-128">從存放庫下載一或多個模組，並將它們安裝在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-128">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="2b7cc-129">Install-Script</span><span class="sxs-lookup"><span data-stu-id="2b7cc-129">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="2b7cc-130">安裝腳本。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-130">Installs a script.</span></span>

### [<span data-ttu-id="2b7cc-131">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="2b7cc-131">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="2b7cc-132">建立含有中繼資料的指令檔。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-132">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="2b7cc-133">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="2b7cc-133">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="2b7cc-134">將指定的模組從本機電腦發行至線上資源庫。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-134">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="2b7cc-135">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="2b7cc-135">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="2b7cc-136">發佈腳本。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-136">Publishes a script.</span></span>

### [<span data-ttu-id="2b7cc-137">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="2b7cc-137">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="2b7cc-138">註冊 PowerShell 存放庫。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-138">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="2b7cc-139">Save-Module</span><span class="sxs-lookup"><span data-stu-id="2b7cc-139">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="2b7cc-140">將模組及其相依性儲存在本機電腦上，但不會安裝模組。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-140">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="2b7cc-141">Save-Script</span><span class="sxs-lookup"><span data-stu-id="2b7cc-141">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="2b7cc-142">儲存腳本。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-142">Saves a script.</span></span>

### [<span data-ttu-id="2b7cc-143">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="2b7cc-143">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="2b7cc-144">設定已註冊存放庫的值。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-144">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="2b7cc-145">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="2b7cc-145">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="2b7cc-146">驗證腳本的批註區塊。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-146">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="2b7cc-147">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="2b7cc-147">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="2b7cc-148">解除安裝模組。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-148">Uninstalls a module.</span></span>

### [<span data-ttu-id="2b7cc-149">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="2b7cc-149">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="2b7cc-150">卸載腳本。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-150">Uninstalls a script.</span></span>

### [<span data-ttu-id="2b7cc-151">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="2b7cc-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="2b7cc-152">取消註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-152">Unregisters a repository.</span></span>

### [<span data-ttu-id="2b7cc-153">Update-Module</span><span class="sxs-lookup"><span data-stu-id="2b7cc-153">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="2b7cc-154">將來自線上組件庫之指定模組的最新版本下載並安裝至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-154">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="2b7cc-155">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="2b7cc-155">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="2b7cc-156">更新模組資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-156">Updates a module manifest file.</span></span>

### [<span data-ttu-id="2b7cc-157">Update-Script</span><span class="sxs-lookup"><span data-stu-id="2b7cc-157">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="2b7cc-158">更新腳本。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-158">Updates a script.</span></span>

### [<span data-ttu-id="2b7cc-159">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="2b7cc-159">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="2b7cc-160">更新腳本的資訊。</span><span class="sxs-lookup"><span data-stu-id="2b7cc-160">Updates information for a script.</span></span>
