---
description: PSModulePath 環境變數包含要搜尋以尋找模組和資源的資料夾位置清單。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: b904b01cc3fc63f32151885d040fe7b0e618f6d5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208112"
---
# <a name="about-psmodulepath"></a><span data-ttu-id="3d016-104">關於 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="3d016-104">About PSModulePath</span></span>

<span data-ttu-id="3d016-105">`$env:PSModulePath`環境變數包含要搜尋以尋找模組和資源的資料夾位置清單。</span><span class="sxs-lookup"><span data-stu-id="3d016-105">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="3d016-106">依預設，指派給的有效位置 `$env:PSModulePath` 為：</span><span class="sxs-lookup"><span data-stu-id="3d016-106">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="3d016-107">全系統位置：這些資料夾包含 PowerShell 隨附的模組。</span><span class="sxs-lookup"><span data-stu-id="3d016-107">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="3d016-108">這些模組會儲存在 `$PSHOME\Modules` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3d016-108">These modules are store in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="3d016-109">這也是安裝 Windows 管理模組的位置。</span><span class="sxs-lookup"><span data-stu-id="3d016-109">This is also the location where the Windows management modules are installed.</span></span>

- <span data-ttu-id="3d016-110">使用者安裝的模組：這些是使用者所安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="3d016-110">User-installed modules: These are modules installed by the user.</span></span>
  <span data-ttu-id="3d016-111">`Install-Module` 具有 **範圍** 參數，可讓您指定是否為目前的使用者或所有使用者安裝模組。</span><span class="sxs-lookup"><span data-stu-id="3d016-111">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="3d016-112">如需詳細資訊，請參閱 [Install 模組](xref:PowerShellGet.Install-Module)。</span><span class="sxs-lookup"><span data-stu-id="3d016-112">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  - <span data-ttu-id="3d016-113">在 Windows 中，使用者專屬 **CurrentUser** 範圍的位置是 `$HOME\Documents\PowerShell\Modules` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3d016-113">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="3d016-114">**AllUsers** 範圍的位置是 `$env:ProgramFiles\PowerShell\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="3d016-114">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
  - <span data-ttu-id="3d016-115">在非 Windows 系統上，使用者專屬 **CurrentUser** 範圍的位置是 `$HOME/.local/share/powershell/Modules` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3d016-115">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="3d016-116">**AllUsers** 範圍的位置是 `/usr/local/share/powershell/Modules` 。</span><span class="sxs-lookup"><span data-stu-id="3d016-116">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

<span data-ttu-id="3d016-117">此外，在其他目錄中安裝模組的安裝程式（例如 [Program Files] 目錄）可以將其位置附加至的值 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="3d016-117">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

> [!NOTE]
> <span data-ttu-id="3d016-118">在 Windows 中，使用者專屬的位置是 `PowerShell\Modules` 位於使用者設定檔的 [ **檔** ] 資料夾中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3d016-118">On Windows, the user-specific location is the `PowerShell\Modules` folder located in the **Documents** folder in your user profile.</span></span> <span data-ttu-id="3d016-119">該位置的特定路徑會因 Windows 版本而異，以及您是否正在使用資料夾重新導向。</span><span class="sxs-lookup"><span data-stu-id="3d016-119">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="3d016-120">Microsoft OneDrive 也可以變更您的 [ **檔** ] 資料夾的位置。</span><span class="sxs-lookup"><span data-stu-id="3d016-120">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span> <span data-ttu-id="3d016-121">您可以使用下列命令來確認 [ **檔** ] 資料夾的位置： `[Environment]::GetFolderPath('MyDocuments')` 。</span><span class="sxs-lookup"><span data-stu-id="3d016-121">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

## <a name="modifying-psmodulepath"></a><span data-ttu-id="3d016-122">修改 PSModulePath</span><span class="sxs-lookup"><span data-stu-id="3d016-122">Modifying PSModulePath</span></span>

<span data-ttu-id="3d016-123">若要變更目前會話的預設模組目錄，請使用下列命令格式來變更 `PSModulePath` 環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="3d016-123">To change the default module directories for the current session, use the following command format to change the value of the `PSModulePath` environment variable.</span></span>

<span data-ttu-id="3d016-124">例如，若要將 `C:\Program Files\Fabrikam\Modules` 目錄新增至 PSModulePath 環境變數的值，請輸入：</span><span class="sxs-lookup"><span data-stu-id="3d016-124">For example, to add the `C:\Program Files\Fabrikam\Modules` directory to the value of the PSModulePath environment variable, type:</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

<span data-ttu-id="3d016-125">命令中的分號 (`;`) 會將新路徑與清單中該路徑前面的路徑隔開。</span><span class="sxs-lookup"><span data-stu-id="3d016-125">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span> <span data-ttu-id="3d016-126">在非 Windows 平臺上，冒號 (`:`) 分隔環境變數中的路徑位置。</span><span class="sxs-lookup"><span data-stu-id="3d016-126">On non-Windows platforms, the colon (`:`) separates the path locations in the environment variable.</span></span>

<span data-ttu-id="3d016-127">若要變更 `PSModulePath` 每個會話中的值，請將上述命令新增至 PowerShell 設定檔，或使用 **環境** 類別的 **SetEnvironmentVariable** 方法。</span><span class="sxs-lookup"><span data-stu-id="3d016-127">To change the value of `PSModulePath` in every session, add the previous command to your PowerShell profile or use the **SetEnvironmentVariable** method of the **Environment** class.</span></span>

<span data-ttu-id="3d016-128">下列命令會使用 **GetEnvironmentVariable** 方法來取得的電腦設定 `PSModulePath` ，並使用 **SetEnvironmentVariable** 方法將 `C:\Program Files\Fabrikam\Modules` 路徑新增至值。</span><span class="sxs-lookup"><span data-stu-id="3d016-128">The following command uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

<span data-ttu-id="3d016-129">若要將路徑新增至使用者設定，請將目標值變更為 [ **使用者** ]。</span><span class="sxs-lookup"><span data-stu-id="3d016-129">To add a path to the user setting, change the target value to **User** .</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

<span data-ttu-id="3d016-130">如需 **System. 環境** 類別方法的詳細資訊，請參閱 [環境方法](/dotnet/api/system.environment)。</span><span class="sxs-lookup"><span data-stu-id="3d016-130">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="powershell-psmodulepath-construction"></a><span data-ttu-id="3d016-131">PowerShell PSModulePath 結構</span><span class="sxs-lookup"><span data-stu-id="3d016-131">PowerShell PSModulePath construction</span></span>

<span data-ttu-id="3d016-132">`$env:PSModulePath`每次 PowerShell 啟動時，就會建立的值。</span><span class="sxs-lookup"><span data-stu-id="3d016-132">The value of `$env:PSModulePath` is constructed each time PowerShell starts.</span></span>
<span data-ttu-id="3d016-133">值會因 PowerShell 版本和其啟動方式而有所不同。</span><span class="sxs-lookup"><span data-stu-id="3d016-133">The value varies by version of PowerShell and how it is launched.</span></span>

### <a name="windows-powershell-startup"></a><span data-ttu-id="3d016-134">Windows PowerShell 啟動</span><span class="sxs-lookup"><span data-stu-id="3d016-134">Windows PowerShell startup</span></span>

<span data-ttu-id="3d016-135">Windows PowerShell 會在啟動時使用下列邏輯來建立 `PSModulePath` ：</span><span class="sxs-lookup"><span data-stu-id="3d016-135">Windows PowerShell uses the following logic to construct the `PSModulePath` at startup:</span></span>

- <span data-ttu-id="3d016-136">如果 `PSModulePath` 不存在，請結合 **CurrentUser** 、 **AllUsers** 和 `$PSHOME` 模組路徑</span><span class="sxs-lookup"><span data-stu-id="3d016-136">If `PSModulePath` doesn't exist, combine **CurrentUser** , **AllUsers** , and the `$PSHOME` modules paths</span></span>
- <span data-ttu-id="3d016-137">如果 `PSModulePath` 存在：</span><span class="sxs-lookup"><span data-stu-id="3d016-137">If `PSModulePath` does exist:</span></span>
  - <span data-ttu-id="3d016-138">如果 `PSModulePath` 包含 `$PSHOME` 模組路徑：</span><span class="sxs-lookup"><span data-stu-id="3d016-138">If `PSModulePath` contains `$PSHOME` modules path:</span></span>
    - <span data-ttu-id="3d016-139">在模組路徑之前插入 **AllUsers** 模組路徑 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="3d016-139">**AllUsers** modules path is inserted before `$PSHOME` modules path</span></span>
  - <span data-ttu-id="3d016-140">還：</span><span class="sxs-lookup"><span data-stu-id="3d016-140">else:</span></span>
    - <span data-ttu-id="3d016-141">只是 `PSModulePath` 使用者刻意移除位置之後，才使用定義 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="3d016-141">Just use `PSModulePath` as defined since the user deliberately removed the `$PSHOME` location</span></span>

<span data-ttu-id="3d016-142">只有當使用者範圍不存在時，才會加上 **CurrentUser** 模組路徑的前置詞 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="3d016-142">The **CurrentUser** module path is prefixed only if User scope `$env:PSModulePath` doesn't exist.</span></span> <span data-ttu-id="3d016-143">否則， `$env:PSModulePath` 會使用如定義的使用者範圍。</span><span class="sxs-lookup"><span data-stu-id="3d016-143">Otherwise, the User scope `$env:PSModulePath` is used as defined.</span></span>

### <a name="powershell-core-6-startup"></a><span data-ttu-id="3d016-144">PowerShell Core 6 啟動</span><span class="sxs-lookup"><span data-stu-id="3d016-144">PowerShell Core 6 startup</span></span>

<span data-ttu-id="3d016-145">PowerShell Core 6 `$env:PSModulePath` 如果偵測到它是從 PowerShell 啟動，就不會使用的內容。</span><span class="sxs-lookup"><span data-stu-id="3d016-145">PowerShell Core 6 doesn't use contents of `$env:PSModulePath` if it detects it was started from PowerShell.</span></span> <span data-ttu-id="3d016-146">它會以下列內容覆寫：</span><span class="sxs-lookup"><span data-stu-id="3d016-146">It overwrites it with:</span></span>

- <span data-ttu-id="3d016-147">**CurrentUser** 模組路徑 + **AllUsers** 模組路徑 + `$PSHOME` 模組路徑 + Windows PowerShell `$PSHOME` 模組路徑。</span><span class="sxs-lookup"><span data-stu-id="3d016-147">**CurrentUser** modules path + **AllUsers** modules path + `$PSHOME` modules path + Windows PowerShell `$PSHOME` modules path.</span></span>

### <a name="powershell-7-startup"></a><span data-ttu-id="3d016-148">PowerShell 7 啟動</span><span class="sxs-lookup"><span data-stu-id="3d016-148">PowerShell 7 startup</span></span>

<span data-ttu-id="3d016-149">在 Windows 中，在大部分的環境變數中，如果使用者範圍變數存在，則新的進程只會使用該值，即使有相同名稱的電腦範圍變數存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="3d016-149">In Windows, for most environment variables, if the User-scoped variable exists, a new process uses that value only even if a Machine-scoped variable of the same name exists.</span></span>

<span data-ttu-id="3d016-150">在 PowerShell 7 中，的 `PSModulePath` 處理方式類似于 `Path` Windows 上處理環境變數的方式。</span><span class="sxs-lookup"><span data-stu-id="3d016-150">In PowerShell 7, `PSModulePath` is treated similar to how the `Path` environment variable is treated on Windows.</span></span> <span data-ttu-id="3d016-151">在 Windows 上， `Path` 會以不同于其他環境變數的方式處理。</span><span class="sxs-lookup"><span data-stu-id="3d016-151">On Windows, `Path` is treated differently from other environment variables.</span></span> <span data-ttu-id="3d016-152">當處理常式啟動時，Windows 會將使用者範圍 `Path` 與電腦範圍結合在一起 `Path` 。</span><span class="sxs-lookup"><span data-stu-id="3d016-152">When a process is started, Windows combines the User-scoped `Path` with the Machine-scoped `Path`.</span></span>

- <span data-ttu-id="3d016-153">取出使用者範圍 `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="3d016-153">Retrieve the User-scoped `PSModulePath`</span></span>
- <span data-ttu-id="3d016-154">與進程繼承的 `PSModulePath` 環境變數比較</span><span class="sxs-lookup"><span data-stu-id="3d016-154">Compare to process inherited `PSModulePath` environment variable</span></span>
  - <span data-ttu-id="3d016-155">如果相同：</span><span class="sxs-lookup"><span data-stu-id="3d016-155">If the same:</span></span>
    - <span data-ttu-id="3d016-156">將 **AllUsers** 附加 `PSModulePath` 至 `Path` 環境變數之語義後面的結尾</span><span class="sxs-lookup"><span data-stu-id="3d016-156">Append the **AllUsers** `PSModulePath` to the end following the semantics of the `Path` environment variable</span></span>
    - <span data-ttu-id="3d016-157">Windows `System32` 路徑來自訂的電腦， `PSModulePath` 因此不需要明確新增</span><span class="sxs-lookup"><span data-stu-id="3d016-157">The Windows `System32` path comes from the machine defined `PSModulePath` so does not need to be added explicitly</span></span>
  - <span data-ttu-id="3d016-158">如果不同，請將視為使用者明確修改它，而不要附加 **AllUsers**`PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="3d016-158">If different, treat as though user explicitly modified it and don't append **AllUsers** `PSModulePath`</span></span>
- <span data-ttu-id="3d016-159">以該順序 PS7 使用者、系統和路徑的前置詞 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="3d016-159">Prefix with PS7 User, System, and `$PSHOME` paths in that order</span></span>
  - <span data-ttu-id="3d016-160">如果 `powershell.config.json` 包含使用者範圍 `PSModulePath` ，請使用此值，而不是使用者的預設值。</span><span class="sxs-lookup"><span data-stu-id="3d016-160">If `powershell.config.json` contains a user scoped `PSModulePath`, use that instead of the default for the user</span></span>
  - <span data-ttu-id="3d016-161">如果 `powershell.config.json` 包含已設定範圍的系統 `PSModulePath` ，請使用此值，而不是系統的預設值。</span><span class="sxs-lookup"><span data-stu-id="3d016-161">If `powershell.config.json` contains a system scoped `PSModulePath`, use that instead of the default for the system</span></span>

<span data-ttu-id="3d016-162">Unix 系統沒有使用者和系統內容變數的分隔。</span><span class="sxs-lookup"><span data-stu-id="3d016-162">Unix systems don't have a separation of User and System environment variables.</span></span>
<span data-ttu-id="3d016-163">`PSModulePath` 會被繼承，而且 PS7 特定路徑的前置詞（如果尚未定義的話）。</span><span class="sxs-lookup"><span data-stu-id="3d016-163">`PSModulePath` is inherited and the PS7-specific paths are prefixed if not already defined.</span></span>

### <a name="starting-windows-powershell-from-powershell-7"></a><span data-ttu-id="3d016-164">從 PowerShell 7 開始 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d016-164">Starting Windows PowerShell from PowerShell 7</span></span>

<span data-ttu-id="3d016-165">在此討論中， _Windows PowerShell_ 表示 `powershell.exe` 和 `powershell_ise.exe` 。</span><span class="sxs-lookup"><span data-stu-id="3d016-165">For this discussion, _Windows PowerShell_ means both `powershell.exe` and `powershell_ise.exe`.</span></span>

<span data-ttu-id="3d016-166">的值 `$env:PSModulePath` 會複製到， `WinPSModulePath` 並進行下列修改：</span><span class="sxs-lookup"><span data-stu-id="3d016-166">The value of `$env:PSModulePath` is copied to `WinPSModulePath` with the following modifications:</span></span>

- <span data-ttu-id="3d016-167">移除 PS7 使用者模組路徑</span><span class="sxs-lookup"><span data-stu-id="3d016-167">Remove PS7 the User module path</span></span>
- <span data-ttu-id="3d016-168">移除 PS7 系統模組路徑</span><span class="sxs-lookup"><span data-stu-id="3d016-168">Remove PS7 the System module path</span></span>
- <span data-ttu-id="3d016-169">移除 `$PSHOME` 模組路徑的 PS7</span><span class="sxs-lookup"><span data-stu-id="3d016-169">Remove PS7 the `$PSHOME` module path</span></span>

<span data-ttu-id="3d016-170">PS7 路徑會被移除，因此不會在 Windows PowerShell 中載入 PS7 模組。</span><span class="sxs-lookup"><span data-stu-id="3d016-170">The PS7 paths are removed so that PS7 modules don't get loaded in Windows PowerShell.</span></span> <span data-ttu-id="3d016-171">`WinPSModulePath`開始 Windows PowerShell 時，會使用此值。</span><span class="sxs-lookup"><span data-stu-id="3d016-171">The `WinPSModulePath` value is used when starting Windows PowerShell.</span></span>

### <a name="starting-powershell-7-from-windows-powershell"></a><span data-ttu-id="3d016-172">從 Windows PowerShell 啟動 PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="3d016-172">Starting PowerShell 7 from Windows PowerShell</span></span>

<span data-ttu-id="3d016-173">PowerShell 7 啟動會依原樣繼續進行，並新增 Windows PowerShell 新增的繼承路徑。</span><span class="sxs-lookup"><span data-stu-id="3d016-173">The PowerShell 7 startup continues as-is with the addition of inheriting paths that Windows PowerShell added.</span></span> <span data-ttu-id="3d016-174">由於 PS7 特定的路徑會加上前置詞，因此沒有任何功能性問題。</span><span class="sxs-lookup"><span data-stu-id="3d016-174">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

### <a name="starting-powershell-6-from-powershell-7"></a><span data-ttu-id="3d016-175">從 PowerShell 7 啟動 PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="3d016-175">Starting PowerShell 6 from PowerShell 7</span></span>

<span data-ttu-id="3d016-176">PowerShell Core 6 覆寫 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="3d016-176">PowerShell Core 6 overwrites `$env:PSModulePath`.</span></span> <span data-ttu-id="3d016-177">未進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="3d016-177">No changes are made.</span></span>

### <a name="starting-powershell-7-from-powershell-6"></a><span data-ttu-id="3d016-178">從 PowerShell 6 啟動 PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="3d016-178">Starting PowerShell 7 from PowerShell 6</span></span>

<span data-ttu-id="3d016-179">PowerShell 7 啟動會繼續進行，並新增 PowerShell Core 6 新增的繼承路徑。</span><span class="sxs-lookup"><span data-stu-id="3d016-179">The PowerShell 7 startup continues as-is with the addition of inheriting paths that PowerShell Core 6 added.</span></span> <span data-ttu-id="3d016-180">由於 PS7 特定的路徑會加上前置詞，因此沒有任何功能性問題。</span><span class="sxs-lookup"><span data-stu-id="3d016-180">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d016-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d016-181">See also</span></span>

- [<span data-ttu-id="3d016-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="3d016-182">about_Modules</span></span>](about_Modules.md)
- [<span data-ttu-id="3d016-183">環境方法</span><span class="sxs-lookup"><span data-stu-id="3d016-183">Environment Methods</span></span>](/dotnet/api/system.environment)
