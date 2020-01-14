---
ms.date: 11/06/2018
contributor: JKeithB
keywords: 資源庫,powershell,cmdlet,psgallery,psget
title: 使用本機 PSRepository
ms.openlocfilehash: c1bd905674ae76a3badd3eff50780f0e1bb5fc64
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75415828"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="82d13-103">使用私人 PowerShellGet 存放庫</span><span class="sxs-lookup"><span data-stu-id="82d13-103">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="82d13-104">PowerShellGet 模組支援 PowerShell 資源庫以外的存放庫。</span><span class="sxs-lookup"><span data-stu-id="82d13-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="82d13-105">這些 Cmdlet 會啟用下列案例：</span><span class="sxs-lookup"><span data-stu-id="82d13-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="82d13-106">支援一組受信任且預先驗證的 PowerShell 模組，以便在您的環境中使用</span><span class="sxs-lookup"><span data-stu-id="82d13-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="82d13-107">測試建置 PowerShell 模組或指令碼的 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="82d13-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="82d13-108">將 PowerShell 指令碼和模組傳遞給無法存取網際網路的系統</span><span class="sxs-lookup"><span data-stu-id="82d13-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="82d13-109">傳遞僅供您組織使用的 PowerShell 指令碼和模組</span><span class="sxs-lookup"><span data-stu-id="82d13-109">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="82d13-110">本文說明如何設定本機 PowerShell 存放庫。</span><span class="sxs-lookup"><span data-stu-id="82d13-110">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="82d13-111">本文亦涵蓋可從 PowerShell 資源庫取得的 [OfflinePowerShellGetDeploy][] 模組。</span><span class="sxs-lookup"><span data-stu-id="82d13-111">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="82d13-112">此模組所包含的 Cmdlet 可將最新版的 PowerShellGet 安裝到您的本機存放庫。</span><span class="sxs-lookup"><span data-stu-id="82d13-112">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="82d13-113">本機存放庫類型</span><span class="sxs-lookup"><span data-stu-id="82d13-113">Local repository types</span></span>

<span data-ttu-id="82d13-114">有兩種方式可用來建立本機 PSRepository：NuGet 伺服器或檔案共用。</span><span class="sxs-lookup"><span data-stu-id="82d13-114">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="82d13-115">每個類型都有優點和缺點：</span><span class="sxs-lookup"><span data-stu-id="82d13-115">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="82d13-116">NuGet 伺服器</span><span class="sxs-lookup"><span data-stu-id="82d13-116">NuGet Server</span></span>

| <span data-ttu-id="82d13-117">優點</span><span class="sxs-lookup"><span data-stu-id="82d13-117">Advantages</span></span>| <span data-ttu-id="82d13-118">缺點</span><span class="sxs-lookup"><span data-stu-id="82d13-118">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="82d13-119">精確地模擬 PowerShellGallery 功能</span><span class="sxs-lookup"><span data-stu-id="82d13-119">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="82d13-120">多層式應用程式需要作業規劃與支援</span><span class="sxs-lookup"><span data-stu-id="82d13-120">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="82d13-121">NuGet 整合了 Visual Studio，其他工具</span><span class="sxs-lookup"><span data-stu-id="82d13-121">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="82d13-122">需要驗證模型和 NuGet 帳戶管理</span><span class="sxs-lookup"><span data-stu-id="82d13-122">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="82d13-123">NuGet 支援 `.Nupkg` 套件的中繼資料</span><span class="sxs-lookup"><span data-stu-id="82d13-123">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="82d13-124">發佈需要 API 金鑰管理與維護</span><span class="sxs-lookup"><span data-stu-id="82d13-124">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="82d13-125">提供搜尋、套件管理等。</span><span class="sxs-lookup"><span data-stu-id="82d13-125">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="82d13-126">檔案共用</span><span class="sxs-lookup"><span data-stu-id="82d13-126">File Share</span></span>

| <span data-ttu-id="82d13-127">優點</span><span class="sxs-lookup"><span data-stu-id="82d13-127">Advantages</span></span>| <span data-ttu-id="82d13-128">缺點</span><span class="sxs-lookup"><span data-stu-id="82d13-128">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="82d13-129">易於設定、備份和維護</span><span class="sxs-lookup"><span data-stu-id="82d13-129">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="82d13-130">無法使用 PowerShellGet 所使用的中繼資料</span><span class="sxs-lookup"><span data-stu-id="82d13-130">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="82d13-131">簡單的安全性模式：共用上的使用者權限</span><span class="sxs-lookup"><span data-stu-id="82d13-131">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="82d13-132">除基本的檔案共用之外沒有任何 UI</span><span class="sxs-lookup"><span data-stu-id="82d13-132">No UI beyond basic file share</span></span> |
| <span data-ttu-id="82d13-133">沒有取代現有項目之類的條件約束</span><span class="sxs-lookup"><span data-stu-id="82d13-133">No constraints such as replacing existing items</span></span> | <span data-ttu-id="82d13-134">安全性有限，而且不會記錄誰負責更新哪些項目</span><span class="sxs-lookup"><span data-stu-id="82d13-134">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="82d13-135">PowerShellGet 適用於任一個類型，並支援尋找版本和相依性安裝。</span><span class="sxs-lookup"><span data-stu-id="82d13-135">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="82d13-136">不過，部分適用於 PowerShell 資源庫的功能不適用基底 NuGet 伺服器或檔案共用。</span><span class="sxs-lookup"><span data-stu-id="82d13-136">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="82d13-137">所有項目均為套件：指令碼、模組、DSC 資源或角色功能間並無任何差異。</span><span class="sxs-lookup"><span data-stu-id="82d13-137">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="82d13-138">檔案共用伺服器看不到包括標記在內的套件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="82d13-138">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="82d13-139">建立本機存放庫</span><span class="sxs-lookup"><span data-stu-id="82d13-139">Creating a local repository</span></span>

<span data-ttu-id="82d13-140">下列文章列出設定您自己 NuGet 伺服器的步驟。</span><span class="sxs-lookup"><span data-stu-id="82d13-140">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="82d13-141">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="82d13-141">[NuGet.Server][]</span></span>

<span data-ttu-id="82d13-142">遵循步驟來新增套件。</span><span class="sxs-lookup"><span data-stu-id="82d13-142">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="82d13-143">[發佈套件](#publishing-to-a-local-repository)的步驟將於本文稍後討論。</span><span class="sxs-lookup"><span data-stu-id="82d13-143">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="82d13-144">針對以檔案共用為基礎的存放庫，確定您的使用者具有存取檔案共用的權限。</span><span class="sxs-lookup"><span data-stu-id="82d13-144">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="82d13-145">註冊本機存放庫</span><span class="sxs-lookup"><span data-stu-id="82d13-145">Registering a local repository</span></span>

<span data-ttu-id="82d13-146">您必須先使用 `Register-PSRepository` 命令來註冊存放庫，才能加以使用。</span><span class="sxs-lookup"><span data-stu-id="82d13-146">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="82d13-147">在下列範例中，會將 **InstallationPolicy** 設定為 *Trusted* (假設您信任自己的存放庫)。</span><span class="sxs-lookup"><span data-stu-id="82d13-147">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="82d13-148">請記下這兩個命令如何處理 **ScriptSourceLocation** 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="82d13-148">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="82d13-149">針對以檔案共用為基礎的存放庫，**SourceLocation** 和 **ScriptSourceLocation** 必須相符。</span><span class="sxs-lookup"><span data-stu-id="82d13-149">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="82d13-150">針對以 Web 為基礎的存放庫，它們必須不同，因此在此範例中，會在 **SourceLocation** 尾端新增 "/"。</span><span class="sxs-lookup"><span data-stu-id="82d13-150">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="82d13-151">如果您想要使新建的 PSRepository 成為預設存放庫，就必須取消註冊所有其他 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="82d13-151">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="82d13-152">例如：</span><span class="sxs-lookup"><span data-stu-id="82d13-152">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="82d13-153">存放庫名稱 'PSGallery' 會保留，以供 PowerShell 資源庫使用。</span><span class="sxs-lookup"><span data-stu-id="82d13-153">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="82d13-154">您可以取消註冊 PSGallery，但無法針對任何其他存放庫重複使用 PSGallery 這個名稱。</span><span class="sxs-lookup"><span data-stu-id="82d13-154">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="82d13-155">如果您需要還原 PSGallery，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="82d13-155">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="82d13-156">發佈至本機存放庫</span><span class="sxs-lookup"><span data-stu-id="82d13-156">Publishing to a local repository</span></span>

<span data-ttu-id="82d13-157">一旦註冊本機 PSRepository 之後，就能發佈到您的本機 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="82d13-157">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="82d13-158">有兩個主要發佈案例：發佈您自己的模組和從 PSGallery 發佈模組。</span><span class="sxs-lookup"><span data-stu-id="82d13-158">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="82d13-159">發佈您所撰寫的模組</span><span class="sxs-lookup"><span data-stu-id="82d13-159">Publishing a module you authored</span></span>

<span data-ttu-id="82d13-160">使用 `Publish-Module` 和 `Publish-Script`，以您針對 PowerShell 資源庫所做的相同方式來將模組發佈到本機 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="82d13-160">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="82d13-161">指定程式碼的位置</span><span class="sxs-lookup"><span data-stu-id="82d13-161">Specify the location for your code</span></span>
- <span data-ttu-id="82d13-162">提供 API 金鑰</span><span class="sxs-lookup"><span data-stu-id="82d13-162">Supply an API key</span></span>
- <span data-ttu-id="82d13-163">指定存放庫名稱。</span><span class="sxs-lookup"><span data-stu-id="82d13-163">Specify the repository name.</span></span> <span data-ttu-id="82d13-164">例如， `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="82d13-164">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="82d13-165">您必須在 NuGet 伺服器中建立帳戶，然後登入以產生並儲存 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="82d13-165">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="82d13-166">針對檔案共用，為 NuGetApiKey 值使用任何非空白的字串。</span><span class="sxs-lookup"><span data-stu-id="82d13-166">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="82d13-167">範例：</span><span class="sxs-lookup"><span data-stu-id="82d13-167">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'
```

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="82d13-168">為確保安全性，不應將 API 金鑰硬式編碼於指令碼中。</span><span class="sxs-lookup"><span data-stu-id="82d13-168">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="82d13-169">使用安全金鑰管理系統。</span><span class="sxs-lookup"><span data-stu-id="82d13-169">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="82d13-170">從 PSGallery 發佈模組</span><span class="sxs-lookup"><span data-stu-id="82d13-170">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="82d13-171">若要從 PSGallery 將模組發佈到您的本機 PSRepository，您可以使用 'Save-Package' Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82d13-171">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="82d13-172">指定套件名稱</span><span class="sxs-lookup"><span data-stu-id="82d13-172">Specify the Name of the Package</span></span>
- <span data-ttu-id="82d13-173">指定 'NuGet' 作為提供者</span><span class="sxs-lookup"><span data-stu-id="82d13-173">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="82d13-174">指定 PSGallery 位置作為來源 (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="82d13-174">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="82d13-175">指定本機存放庫的路徑</span><span class="sxs-lookup"><span data-stu-id="82d13-175">Specify the path to your local Repository</span></span>

<span data-ttu-id="82d13-176">範例：</span><span class="sxs-lookup"><span data-stu-id="82d13-176">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="82d13-177">如果本機 PSRepository 會以 Web 為基礎，它需要額外的步驟，才能使用 nuget.exe 來發佈。</span><span class="sxs-lookup"><span data-stu-id="82d13-177">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="82d13-178">請參閱使用 [nuget.exe][] 的文件。</span><span class="sxs-lookup"><span data-stu-id="82d13-178">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="82d13-179">在中斷連線的系統上安裝 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="82d13-179">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="82d13-180">在要求系統中斷與網路網路連線的環境內，很難部署 PowerShellGet。</span><span class="sxs-lookup"><span data-stu-id="82d13-180">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="82d13-181">PowerShellGet 有一個啟動程序流程，可在第一次使用時安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="82d13-181">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="82d13-182">PowerShell 資源庫中的 OfflinePowerShellGetDeploy 模組提供支援此啟動程序流程的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82d13-182">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="82d13-183">若要啟動離線部署，您需要：</span><span class="sxs-lookup"><span data-stu-id="82d13-183">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="82d13-184">下載 OfflinePowerShellGetDeploy 並安裝至您連線到網際網路的系統和中斷連線的系統</span><span class="sxs-lookup"><span data-stu-id="82d13-184">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="82d13-185">在連線到網際網路的系統上，使用 `Save-PowerShellGetForOffline` Cmdlet 來下載 PowerShellGet 及其相依性</span><span class="sxs-lookup"><span data-stu-id="82d13-185">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="82d13-186">將 PowerShellGet 及其相依性從連線到網際網路的系統複製到中斷連線的系統</span><span class="sxs-lookup"><span data-stu-id="82d13-186">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="82d13-187">在中斷連線的系統上使用 `Install-PowerShellGetOffline`，以將 PowerShellGet 及其相依性放置於適當的資料夾</span><span class="sxs-lookup"><span data-stu-id="82d13-187">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="82d13-188">下列命令會使用 `Save-PowerShellGetForOffline`，將所有元件放入 `f:\OfflinePowerShellGet` 資料夾</span><span class="sxs-lookup"><span data-stu-id="82d13-188">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="82d13-189">此時，您必須讓 `F:\OfflinePowerShellGet` 的內容可供中斷連線的系統使用。</span><span class="sxs-lookup"><span data-stu-id="82d13-189">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="82d13-190">執行 `Install-PowerShellGetOffline` Cmdlet，以在中斷連線的系統上安裝 PowerShellGet。</span><span class="sxs-lookup"><span data-stu-id="82d13-190">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="82d13-191">執行這些命令之前，不要在 PowerShell 工作階段上執行 PowerShellGet，這點很重要。</span><span class="sxs-lookup"><span data-stu-id="82d13-191">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="82d13-192">將 PowerShellGet 載入至工作階段之後，就無法更新元件。</span><span class="sxs-lookup"><span data-stu-id="82d13-192">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="82d13-193">如果您不小心啟動了 PowerShellGet，請結束並重新啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="82d13-193">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="82d13-194">執行這些命令之後，您就已經準備好將 PowerShellGet 發佈至本機存放庫。</span><span class="sxs-lookup"><span data-stu-id="82d13-194">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="82d13-195">使用封裝解決方案來裝載 PowerShellGet 存放庫</span><span class="sxs-lookup"><span data-stu-id="82d13-195">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="82d13-196">您也可以使用封裝解決方案 (例如 Azure Artifacts) 來裝載私人或公用 PowerShellGet 存放庫。</span><span class="sxs-lookup"><span data-stu-id="82d13-196">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="82d13-197">如需詳細資訊和指示，請參閱 [Azure Artifacts 文件](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="82d13-197">For more information and instructions, see the [Azure Artifacts documentation](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82d13-198">為確保安全性，不應將 API 金鑰硬式編碼於指令碼中。</span><span class="sxs-lookup"><span data-stu-id="82d13-198">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="82d13-199">使用安全金鑰管理系統。</span><span class="sxs-lookup"><span data-stu-id="82d13-199">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
