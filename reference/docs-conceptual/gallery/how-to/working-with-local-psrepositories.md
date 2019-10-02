---
ms.date: 11/06/2018
contributor: JKeithB
keywords: 資源庫,powershell,cmdlet,psgallery,psget
title: 使用本機 PSRepository
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327989"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="38fd8-103">使用本機 PowerShellGet 存放庫</span><span class="sxs-lookup"><span data-stu-id="38fd8-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="38fd8-104">PowerShellGet 模組支援 PowerShell 資源庫以外的存放庫。</span><span class="sxs-lookup"><span data-stu-id="38fd8-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="38fd8-105">這些 Cmdlet 會啟用下列案例：</span><span class="sxs-lookup"><span data-stu-id="38fd8-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="38fd8-106">支援一組受信任且預先驗證的 PowerShell 模組，以便在您的環境中使用</span><span class="sxs-lookup"><span data-stu-id="38fd8-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="38fd8-107">測試建置 PowerShell 模組或指令碼的 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="38fd8-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="38fd8-108">將 PowerShell 指令碼和模組傳遞給無法存取網際網路的系統</span><span class="sxs-lookup"><span data-stu-id="38fd8-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="38fd8-109">本文說明如何設定本機 PowerShell 存放庫。</span><span class="sxs-lookup"><span data-stu-id="38fd8-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="38fd8-110">本文亦涵蓋可從 PowerShell 資源庫取得的 [OfflinePowerShellGetDeploy][] 模組。</span><span class="sxs-lookup"><span data-stu-id="38fd8-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="38fd8-111">此模組所包含的 Cmdlet 可將最新版的 PowerShellGet 安裝到您的本機存放庫。</span><span class="sxs-lookup"><span data-stu-id="38fd8-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="38fd8-112">本機存放庫類型</span><span class="sxs-lookup"><span data-stu-id="38fd8-112">Local repository types</span></span>

<span data-ttu-id="38fd8-113">有兩種方式可用來建立本機 PSRepository：NuGet 伺服器或檔案共用。</span><span class="sxs-lookup"><span data-stu-id="38fd8-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="38fd8-114">每個類型都有優點和缺點：</span><span class="sxs-lookup"><span data-stu-id="38fd8-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="38fd8-115">NuGet 伺服器</span><span class="sxs-lookup"><span data-stu-id="38fd8-115">NuGet Server</span></span>

| <span data-ttu-id="38fd8-116">優點</span><span class="sxs-lookup"><span data-stu-id="38fd8-116">Advantages</span></span>| <span data-ttu-id="38fd8-117">缺點</span><span class="sxs-lookup"><span data-stu-id="38fd8-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="38fd8-118">精確地模擬 PowerShellGallery 功能</span><span class="sxs-lookup"><span data-stu-id="38fd8-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="38fd8-119">多層式應用程式需要作業規劃與支援</span><span class="sxs-lookup"><span data-stu-id="38fd8-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="38fd8-120">NuGet 整合了 Visual Studio，其他工具</span><span class="sxs-lookup"><span data-stu-id="38fd8-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="38fd8-121">需要驗證模型和 NuGet 帳戶管理</span><span class="sxs-lookup"><span data-stu-id="38fd8-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="38fd8-122">NuGet 支援 `.Nupkg` 套件的中繼資料</span><span class="sxs-lookup"><span data-stu-id="38fd8-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="38fd8-123">發佈需要 API 金鑰管理與維護</span><span class="sxs-lookup"><span data-stu-id="38fd8-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="38fd8-124">提供搜尋、套件管理等。</span><span class="sxs-lookup"><span data-stu-id="38fd8-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="38fd8-125">檔案共用</span><span class="sxs-lookup"><span data-stu-id="38fd8-125">File Share</span></span>

| <span data-ttu-id="38fd8-126">優點</span><span class="sxs-lookup"><span data-stu-id="38fd8-126">Advantages</span></span>| <span data-ttu-id="38fd8-127">缺點</span><span class="sxs-lookup"><span data-stu-id="38fd8-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="38fd8-128">易於設定、備份和維護</span><span class="sxs-lookup"><span data-stu-id="38fd8-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="38fd8-129">無法使用 PowerShellGet 所使用的中繼資料</span><span class="sxs-lookup"><span data-stu-id="38fd8-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="38fd8-130">簡單的安全性模式：共用上的使用者權限</span><span class="sxs-lookup"><span data-stu-id="38fd8-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="38fd8-131">除基本的檔案共用之外沒有任何 UI</span><span class="sxs-lookup"><span data-stu-id="38fd8-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="38fd8-132">沒有取代現有項目之類的條件約束</span><span class="sxs-lookup"><span data-stu-id="38fd8-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="38fd8-133">安全性有限，而且不會記錄誰負責更新哪些項目</span><span class="sxs-lookup"><span data-stu-id="38fd8-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="38fd8-134">PowerShellGet 適用於任一個類型，並支援尋找版本和相依性安裝。</span><span class="sxs-lookup"><span data-stu-id="38fd8-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="38fd8-135">不過，部分適用於 PowerShell 資源庫的功能不適用基底 NuGet 伺服器或檔案共用。</span><span class="sxs-lookup"><span data-stu-id="38fd8-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="38fd8-136">所有項目均為套件：指令碼、模組、DSC 資源或角色功能間並無任何差異。</span><span class="sxs-lookup"><span data-stu-id="38fd8-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="38fd8-137">檔案共用伺服器看不到包括標記在內的套件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="38fd8-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="38fd8-138">建立本機存放庫</span><span class="sxs-lookup"><span data-stu-id="38fd8-138">Creating a local repository</span></span>

<span data-ttu-id="38fd8-139">下列文章列出設定您自己 NuGet 伺服器的步驟。</span><span class="sxs-lookup"><span data-stu-id="38fd8-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="38fd8-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="38fd8-140">[NuGet.Server][]</span></span>

<span data-ttu-id="38fd8-141">遵循步驟來新增套件。</span><span class="sxs-lookup"><span data-stu-id="38fd8-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="38fd8-142">[發佈套件](#publishing-to-a-local-repository)的步驟將於本文稍後討論。</span><span class="sxs-lookup"><span data-stu-id="38fd8-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="38fd8-143">針對以檔案共用為基礎的存放庫，確定您的使用者具有存取檔案共用的權限。</span><span class="sxs-lookup"><span data-stu-id="38fd8-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="38fd8-144">註冊本機存放庫</span><span class="sxs-lookup"><span data-stu-id="38fd8-144">Registering a local repository</span></span>

<span data-ttu-id="38fd8-145">您必須先使用 `Register-PSRepository` 命令來註冊存放庫，才能加以使用。</span><span class="sxs-lookup"><span data-stu-id="38fd8-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="38fd8-146">在下列範例中，會將 **InstallationPolicy** 設定為 *Trusted* (假設您信任自己的存放庫)。</span><span class="sxs-lookup"><span data-stu-id="38fd8-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="38fd8-147">請記下這兩個命令如何處理 **ScriptSourceLocation** 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="38fd8-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="38fd8-148">針對以檔案共用為基礎的存放庫，**SourceLocation** 和 **ScriptSourceLocation** 必須相符。</span><span class="sxs-lookup"><span data-stu-id="38fd8-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="38fd8-149">針對以 Web 為基礎的存放庫，它們必須不同，因此在此範例中，會在 **SourceLocation** 尾端新增 "/"。</span><span class="sxs-lookup"><span data-stu-id="38fd8-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="38fd8-150">如果您想要使新建的 PSRepository 成為預設存放庫，就必須取消註冊所有其他 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="38fd8-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="38fd8-151">例如：</span><span class="sxs-lookup"><span data-stu-id="38fd8-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="38fd8-152">存放庫名稱 'PSGallery' 會保留，以供 PowerShell 資源庫使用。</span><span class="sxs-lookup"><span data-stu-id="38fd8-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="38fd8-153">您可以取消註冊 PSGallery，但無法針對任何其他存放庫重複使用 PSGallery 這個名稱。</span><span class="sxs-lookup"><span data-stu-id="38fd8-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="38fd8-154">如果您需要還原 PSGallery，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="38fd8-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="38fd8-155">發佈至本機存放庫</span><span class="sxs-lookup"><span data-stu-id="38fd8-155">Publishing to a local repository</span></span>

<span data-ttu-id="38fd8-156">一旦註冊本機 PSRepository 之後，就能發佈到您的本機 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="38fd8-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="38fd8-157">有兩個主要發佈案例：發佈您自己的模組和從 PSGallery 發佈模組。</span><span class="sxs-lookup"><span data-stu-id="38fd8-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="38fd8-158">發佈您所撰寫的模組</span><span class="sxs-lookup"><span data-stu-id="38fd8-158">Publishing a module you authored</span></span>

<span data-ttu-id="38fd8-159">使用 `Publish-Module` 和 `Publish-Script`，以您針對 PowerShell 資源庫所做的相同方式來將模組發佈到本機 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="38fd8-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="38fd8-160">指定程式碼的位置</span><span class="sxs-lookup"><span data-stu-id="38fd8-160">Specify the location for your code</span></span>
- <span data-ttu-id="38fd8-161">提供 API 金鑰</span><span class="sxs-lookup"><span data-stu-id="38fd8-161">Supply an API key</span></span>
- <span data-ttu-id="38fd8-162">指定存放庫名稱。</span><span class="sxs-lookup"><span data-stu-id="38fd8-162">Specify the repository name.</span></span> <span data-ttu-id="38fd8-163">例如，`-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="38fd8-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="38fd8-164">您必須在 NuGet 伺服器中建立帳戶，然後登入以產生並儲存 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="38fd8-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="38fd8-165">針對檔案共用，為 NuGetApiKey 值使用任何非空白的字串。</span><span class="sxs-lookup"><span data-stu-id="38fd8-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="38fd8-166">範例：</span><span class="sxs-lookup"><span data-stu-id="38fd8-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="38fd8-167">為確保安全性，不應將 API 金鑰硬式編碼於指令碼中。</span><span class="sxs-lookup"><span data-stu-id="38fd8-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="38fd8-168">使用安全金鑰管理系統。</span><span class="sxs-lookup"><span data-stu-id="38fd8-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="38fd8-169">從 PSGallery 發佈模組</span><span class="sxs-lookup"><span data-stu-id="38fd8-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="38fd8-170">若要從 PSGallery 將模組發佈到您的本機 PSRepository，您可以使用 'Save-Package' Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="38fd8-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="38fd8-171">指定套件名稱</span><span class="sxs-lookup"><span data-stu-id="38fd8-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="38fd8-172">指定 'NuGet' 作為提供者</span><span class="sxs-lookup"><span data-stu-id="38fd8-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="38fd8-173">指定 PSGallery 位置作為來源 (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="38fd8-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="38fd8-174">指定本機存放庫的路徑</span><span class="sxs-lookup"><span data-stu-id="38fd8-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="38fd8-175">範例：</span><span class="sxs-lookup"><span data-stu-id="38fd8-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="38fd8-176">如果本機 PSRepository 會以 Web 為基礎，它需要額外的步驟，才能使用 nuget.exe 來發佈。</span><span class="sxs-lookup"><span data-stu-id="38fd8-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="38fd8-177">請參閱使用 [nuget.exe][] 的文件。</span><span class="sxs-lookup"><span data-stu-id="38fd8-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="38fd8-178">在中斷連線的系統上安裝 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="38fd8-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="38fd8-179">在要求系統中斷與網路網路連線的環境內，很難部署 PowerShellGet。</span><span class="sxs-lookup"><span data-stu-id="38fd8-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="38fd8-180">PowerShellGet 有一個啟動程序流程，可在第一次使用時安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="38fd8-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="38fd8-181">PowerShell 資源庫中的 OfflinePowerShellGetDeploy 模組提供支援此啟動程序流程的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="38fd8-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="38fd8-182">若要啟動離線部署，您需要：</span><span class="sxs-lookup"><span data-stu-id="38fd8-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="38fd8-183">下載 OfflinePowerShellGetDeploy 並安裝至您連線到網際網路的系統和中斷連線的系統</span><span class="sxs-lookup"><span data-stu-id="38fd8-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="38fd8-184">在連線到網際網路的系統上，使用 `Save-PowerShellGetForOffline` Cmdlet 來下載 PowerShellGet 及其相依性</span><span class="sxs-lookup"><span data-stu-id="38fd8-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="38fd8-185">將 PowerShellGet 及其相依性從連線到網際網路的系統複製到中斷連線的系統</span><span class="sxs-lookup"><span data-stu-id="38fd8-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="38fd8-186">在中斷連線的系統上使用 `Install-PowerShellGetOffline`，以將 PowerShellGet 及其相依性放置於適當的資料夾</span><span class="sxs-lookup"><span data-stu-id="38fd8-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="38fd8-187">下列命令會使用 `Save-PowerShellGetForOffline`，將所有元件放入 `f:\OfflinePowerShellGet` 資料夾</span><span class="sxs-lookup"><span data-stu-id="38fd8-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="38fd8-188">此時，您必須讓 `F:\OfflinePowerShellGet` 的內容可供中斷連線的系統使用。</span><span class="sxs-lookup"><span data-stu-id="38fd8-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="38fd8-189">執行 `Install-PowerShellGetOffline` Cmdlet，以在中斷連線的系統上安裝 PowerShellGet。</span><span class="sxs-lookup"><span data-stu-id="38fd8-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="38fd8-190">執行這些命令之前，不要在 PowerShell 工作階段上執行 PowerShellGet，這點很重要。</span><span class="sxs-lookup"><span data-stu-id="38fd8-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="38fd8-191">將 PowerShellGet 載入至工作階段之後，就無法更新元件。</span><span class="sxs-lookup"><span data-stu-id="38fd8-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="38fd8-192">如果您不小心啟動了 PowerShellGet，請結束並重新啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="38fd8-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="38fd8-193">執行這些命令之後，您就已經準備好將 PowerShellGet 發佈至本機存放庫。</span><span class="sxs-lookup"><span data-stu-id="38fd8-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="38fd8-194">為確保安全性，不應將 API 金鑰硬式編碼於指令碼中。</span><span class="sxs-lookup"><span data-stu-id="38fd8-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="38fd8-195">使用安全金鑰管理系統。</span><span class="sxs-lookup"><span data-stu-id="38fd8-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
