---
ms.date: 11/06/2018
contributor: JKeithB
keywords: 資源庫,powershell,cmdlet,psgallery,psget
title: 使用本機 PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679283"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="c98de-103">使用本機 PowerShellGet 存放庫</span><span class="sxs-lookup"><span data-stu-id="c98de-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="c98de-104">PowerShellGet 模組支援的存放庫以外的 「 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="c98de-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="c98de-105">這些 cmdlet 會啟用下列案例：</span><span class="sxs-lookup"><span data-stu-id="c98de-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="c98de-106">支援在您的環境中使用的一組受信任且預先驗證的 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="c98de-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="c98de-107">測試建置 PowerShell 模組或指令碼的 CI/CD 管線</span><span class="sxs-lookup"><span data-stu-id="c98de-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="c98de-108">將 PowerShell 指令碼和模組傳遞給無法存取網際網路的系統</span><span class="sxs-lookup"><span data-stu-id="c98de-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="c98de-109">本文說明如何設定本機的 PowerShell 存放庫。</span><span class="sxs-lookup"><span data-stu-id="c98de-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="c98de-110">本文亦涵蓋[OfflinePowerShellGetDeploy][]模組可從 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="c98de-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="c98de-111">此模組包含 cmdlet 來安裝最新版的 PowerShellGet 到您的本機儲存機制。</span><span class="sxs-lookup"><span data-stu-id="c98de-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="c98de-112">本機存放庫類型</span><span class="sxs-lookup"><span data-stu-id="c98de-112">Local repository types</span></span>

<span data-ttu-id="c98de-113">有兩種方式可建立本機的 PSRepository:NuGet 伺服器或檔案共用。</span><span class="sxs-lookup"><span data-stu-id="c98de-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="c98de-114">每個類型都有其優缺點：</span><span class="sxs-lookup"><span data-stu-id="c98de-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="c98de-115">NuGet 伺服器</span><span class="sxs-lookup"><span data-stu-id="c98de-115">NuGet Server</span></span>

| <span data-ttu-id="c98de-116">優點</span><span class="sxs-lookup"><span data-stu-id="c98de-116">Advantages</span></span>| <span data-ttu-id="c98de-117">缺點</span><span class="sxs-lookup"><span data-stu-id="c98de-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="c98de-118">精確地模擬 powershell 資源庫功能</span><span class="sxs-lookup"><span data-stu-id="c98de-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="c98de-119">多層式應用程式所需作業計劃與支援</span><span class="sxs-lookup"><span data-stu-id="c98de-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="c98de-120">NuGet 整合了 Visual Studio 中，其他工具</span><span class="sxs-lookup"><span data-stu-id="c98de-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="c98de-121">驗證模型和所需的 NuGet 帳戶管理</span><span class="sxs-lookup"><span data-stu-id="c98de-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="c98de-122">NuGet 支援中的中繼資料`.Nupkg`套件</span><span class="sxs-lookup"><span data-stu-id="c98de-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="c98de-123">發行需要 API 金鑰管理與維護</span><span class="sxs-lookup"><span data-stu-id="c98de-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="c98de-124">提供搜尋、 套件管理等。</span><span class="sxs-lookup"><span data-stu-id="c98de-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="c98de-125">檔案共用</span><span class="sxs-lookup"><span data-stu-id="c98de-125">File Share</span></span>

| <span data-ttu-id="c98de-126">優點</span><span class="sxs-lookup"><span data-stu-id="c98de-126">Advantages</span></span>| <span data-ttu-id="c98de-127">缺點</span><span class="sxs-lookup"><span data-stu-id="c98de-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="c98de-128">易於設定、 備份和維護</span><span class="sxs-lookup"><span data-stu-id="c98de-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="c98de-129">PowerShellGet 所使用的中繼資料無法使用</span><span class="sxs-lookup"><span data-stu-id="c98de-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="c98de-130">簡單的安全性模式-使用者共用的權限</span><span class="sxs-lookup"><span data-stu-id="c98de-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="c98de-131">沒有 UI，超過基本的檔案共用</span><span class="sxs-lookup"><span data-stu-id="c98de-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="c98de-132">沒有條件約束，例如取代現有的項目</span><span class="sxs-lookup"><span data-stu-id="c98de-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="c98de-133">有限的安全性並沒有記錄，誰負責更新項目</span><span class="sxs-lookup"><span data-stu-id="c98de-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="c98de-134">PowerShellGet 適用於型別和尋找版本和相依性安裝支援。</span><span class="sxs-lookup"><span data-stu-id="c98de-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="c98de-135">不過，適用於 「 PowerShell 資源庫的某些功能不適用於基底的 NuGet 伺服器或檔案共用。</span><span class="sxs-lookup"><span data-stu-id="c98de-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="c98de-136">一切都已封裝-指令碼、 模組、 DSC 資源，或角色功能沒有任何差異。</span><span class="sxs-lookup"><span data-stu-id="c98de-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="c98de-137">檔案共用伺服器看不見套件中繼資料，包括標記。</span><span class="sxs-lookup"><span data-stu-id="c98de-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="c98de-138">建立本機儲存機制</span><span class="sxs-lookup"><span data-stu-id="c98de-138">Creating a local repository</span></span>

<span data-ttu-id="c98de-139">下列文章列出的步驟設定您自己的 NuGet 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c98de-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="c98de-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="c98de-140">[NuGet.Server][]</span></span>

<span data-ttu-id="c98de-141">請遵循新增套件的點為止的步驟。</span><span class="sxs-lookup"><span data-stu-id="c98de-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="c98de-142">步驟[發行套件](#publishing-to-a-local-repository)本文稍後所述。</span><span class="sxs-lookup"><span data-stu-id="c98de-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="c98de-143">檔案共用為基礎儲存機制中，請確定您的使用者具有存取檔案共用的權限。</span><span class="sxs-lookup"><span data-stu-id="c98de-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="c98de-144">註冊本機存放庫</span><span class="sxs-lookup"><span data-stu-id="c98de-144">Registering a local repository</span></span>

<span data-ttu-id="c98de-145">可用的存放庫之前，必須註冊使用`Register-PSRepository`命令。</span><span class="sxs-lookup"><span data-stu-id="c98de-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="c98de-146">在以下範例中， **InstallationPolicy**設為*信任*，假設您信任您自己的存放庫。</span><span class="sxs-lookup"><span data-stu-id="c98de-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="c98de-147">請記下的兩個命令的處理方式之間的差異**ScriptSourceLocation**。</span><span class="sxs-lookup"><span data-stu-id="c98de-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="c98de-148">檔案共用為基礎的存放庫，如**SourceLocation**並**ScriptSourceLocation**必須相符。</span><span class="sxs-lookup"><span data-stu-id="c98de-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="c98de-149">針對 web 為基礎的存放庫，它們必須不同，因此在此範例中的尾端"/"新增至**SourceLocation**。</span><span class="sxs-lookup"><span data-stu-id="c98de-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="c98de-150">如果您想要預設存放庫新建的 PSRepository 時，您必須取消註冊所有其他 PSRepositories。</span><span class="sxs-lookup"><span data-stu-id="c98de-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="c98de-151">例如：</span><span class="sxs-lookup"><span data-stu-id="c98de-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="c98de-152">存放庫名稱 'PSGallery' 被保留給使用 「 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="c98de-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="c98de-153">您可以取消註冊 PSGallery，但您無法重複使用任何其他存放庫名稱 PSGallery。</span><span class="sxs-lookup"><span data-stu-id="c98de-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="c98de-154">如果您需要還原 PSGallery，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c98de-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="c98de-155">發行至本機存放庫</span><span class="sxs-lookup"><span data-stu-id="c98de-155">Publishing to a local repository</span></span>

<span data-ttu-id="c98de-156">一旦您已註冊本機 PSRepository，您可以發行至您的本機 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="c98de-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="c98de-157">有兩個主要的發行案例： 發佈您自己的模組和發行 PSGallery 的模組。</span><span class="sxs-lookup"><span data-stu-id="c98de-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="c98de-158">發行您所撰寫的模組</span><span class="sxs-lookup"><span data-stu-id="c98de-158">Publishing a module you authored</span></span>

<span data-ttu-id="c98de-159">使用`Publish-Module`和`Publish-Script`發佈您的模組到您本機的 PSRepository 由 PowerShell 資源庫的相同方式。</span><span class="sxs-lookup"><span data-stu-id="c98de-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="c98de-160">指定您的程式碼的位置</span><span class="sxs-lookup"><span data-stu-id="c98de-160">Specify the location for your code</span></span>
- <span data-ttu-id="c98de-161">提供 API 金鑰</span><span class="sxs-lookup"><span data-stu-id="c98de-161">Supply an API key</span></span>
- <span data-ttu-id="c98de-162">指定存放庫名稱。</span><span class="sxs-lookup"><span data-stu-id="c98de-162">Specify the repository name.</span></span> <span data-ttu-id="c98de-163">例如，`-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="c98de-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="c98de-164">您必須在 NuGet 伺服器中，建立帳戶，然後登入，以產生並儲存的 API 金鑰。</span><span class="sxs-lookup"><span data-stu-id="c98de-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="c98de-165">檔案共用，使用任何非空白字串做為 NuGetApiKey 值。</span><span class="sxs-lookup"><span data-stu-id="c98de-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="c98de-166">範例：</span><span class="sxs-lookup"><span data-stu-id="c98de-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="c98de-167">若要確保安全性，API 金鑰不應該硬式編碼在指令碼中。</span><span class="sxs-lookup"><span data-stu-id="c98de-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="c98de-168">使用安全金鑰管理系統。</span><span class="sxs-lookup"><span data-stu-id="c98de-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="c98de-169">發行來自 PSGallery 的模組</span><span class="sxs-lookup"><span data-stu-id="c98de-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="c98de-170">若要發行到您本機的 PSRepository PSGallery 的模組，您可以使用 '儲存封裝' cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c98de-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="c98de-171">指定封裝的名稱</span><span class="sxs-lookup"><span data-stu-id="c98de-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="c98de-172">指定 'NuGet' 作為提供者</span><span class="sxs-lookup"><span data-stu-id="c98de-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="c98de-173">PSGallery 位置指定的來源 （ https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="c98de-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="c98de-174">指定本機儲存機制的路徑</span><span class="sxs-lookup"><span data-stu-id="c98de-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="c98de-175">範例：</span><span class="sxs-lookup"><span data-stu-id="c98de-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="c98de-176">如果您本機的 PSRepository 是以 web 為基礎，它會需要額外的步驟來發佈使用 nuget.exe。</span><span class="sxs-lookup"><span data-stu-id="c98de-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="c98de-177">請參閱使用文件[nuget.exe][]。</span><span class="sxs-lookup"><span data-stu-id="c98de-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="c98de-178">在中斷連線的系統上安裝 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c98de-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="c98de-179">部署 PowerShellGet 會要求系統，以從網際網路中斷連線的環境中難以就行了。</span><span class="sxs-lookup"><span data-stu-id="c98de-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="c98de-180">PowerShellGet 已安裝最新版本的第一次使用它的啟動程序。</span><span class="sxs-lookup"><span data-stu-id="c98de-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="c98de-181">PowerShell 資源庫中的 OfflinePowerShellGetDeploy 模組提供支援此啟動程序的處理序的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c98de-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="c98de-182">若要啟動離線部署，您需要：</span><span class="sxs-lookup"><span data-stu-id="c98de-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="c98de-183">下載並安裝 OfflinePowerShellGetDeploy 您連線到網際網路的系統和中斷連線的系統</span><span class="sxs-lookup"><span data-stu-id="c98de-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="c98de-184">下載 PowerShellGet 和其相依性連線網際網路的系統使用`Save-PowerShellGetForOffline`cmdlet</span><span class="sxs-lookup"><span data-stu-id="c98de-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="c98de-185">從連線網際網路的系統的 PowerShellGet 和其相依性複製到已中斷連線的系統</span><span class="sxs-lookup"><span data-stu-id="c98de-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="c98de-186">使用`Install-PowerShellGetOffline`PowerShellGet 和其相依性放置於適當的資料夾已中斷連線的系統上</span><span class="sxs-lookup"><span data-stu-id="c98de-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="c98de-187">下列命令使用`Save-PowerShellGetForOffline`放資料夾中的所有元件 `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="c98de-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="c98de-188">此時，您必須進行的內容`F:\OfflinePowerShellGet`能夠中斷連線的系統。</span><span class="sxs-lookup"><span data-stu-id="c98de-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="c98de-189">執行`Install-PowerShellGetOffline`中斷連線的系統上安裝 PowerShellGet cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c98de-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="c98de-190">很重要，您無法執行 PowerShellGet 中的 PowerShell 工作階段，再執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c98de-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="c98de-191">PowerShellGet 載入工作階段之後, 就無法更新的元件。</span><span class="sxs-lookup"><span data-stu-id="c98de-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="c98de-192">如果您不小心啟動 PowerShellGet，結束並重新啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c98de-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="c98de-193">執行這些命令之後，您已準備好發佈至本機存放庫的 PowerShellGet 項目。</span><span class="sxs-lookup"><span data-stu-id="c98de-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="c98de-194">若要確保安全性，API 金鑰不應該硬式編碼在指令碼中。</span><span class="sxs-lookup"><span data-stu-id="c98de-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="c98de-195">使用安全金鑰管理系統。</span><span class="sxs-lookup"><span data-stu-id="c98de-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
