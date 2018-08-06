# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="3b1f7-101">在 macOS 上安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="3b1f7-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="3b1f7-102">PowerShell Core 支援 macOS 10.12 和更版本。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="3b1f7-103">GitHub [版本][]頁面上提供所有套件。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="3b1f7-104">安裝套件之後，請從終端機執行 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="3b1f7-105">在 macOS 10.12+ 上透過 Homebrew 進行安裝</span><span class="sxs-lookup"><span data-stu-id="3b1f7-105">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="3b1f7-106">[Homebrew][ brew] 是 macOS 首選的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="3b1f7-107">從終端機視窗中，輸入 `brew` 來執行 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-107">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="3b1f7-108">如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-108">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="3b1f7-109">如果您過去已安裝 Homebrew，那麼，比較好的辦法是執行 'brew update-reset' 與 'brew update'。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-109">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="3b1f7-110">較舊的 Homebrew 版本會使用 tap 'caskroom/cask'，其已被取代並遷移到 'homebrew/cask'。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-110">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="3b1f7-111">詳細資訊位於 [Homebrew-cask][cask]。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-111">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="3b1f7-112">使用 'brew tap' 命令來列出您目前的點選。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-112">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="3b1f7-113">如果您看到 'caskroom/cask'，您可以使用 'brew update' 來讓 Homebrew 遷移點選。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-113">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="3b1f7-114">當您安裝/更新 Homebrew 之後，安裝 PowerShell 就很容易。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-114">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="3b1f7-115">安裝 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-115">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="3b1f7-116">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-116">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="3b1f7-117">若要結束 PowerShell 並返回 Bash，請使用 'exit' 命令。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-117">To exit PowerShell, and return to bash, use the 'exit' command.</span></span> 
```sh
exit
```

<span data-ttu-id="3b1f7-118">發行新的 PowerShell 版本時，只要更新 Homebrew 的公式並升級 PowerShell 即可：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-118">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="3b1f7-119">您可從 PowerShell (pwsh) 主機內呼叫上命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 $PSVersionTable 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="3b1f7-120">在 macOS 10.12+ 上透過 Homebrew 安裝預覽</span><span class="sxs-lookup"><span data-stu-id="3b1f7-120">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="3b1f7-121">[Homebrew][ brew] 是 macOS 首選的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-121">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="3b1f7-122">從終端機視窗中，輸入 `brew` 來執行 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-122">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="3b1f7-123">如果找不到 `brew` 命令，您需要遵循[指示][brew]安裝 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-123">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="3b1f7-124">如果您過去已安裝 Homebrew，那麼，比較好的辦法是執行 'brew update-reset' 與 'brew update'。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-124">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="3b1f7-125">接著，您必須點選 `versions` casks 存放庫來取得預覽套件：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-125">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="3b1f7-126">安裝 PowerShell 預覽：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-126">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="3b1f7-127">最後，確認您的安裝可以正常執行：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-127">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="3b1f7-128">發行新的 PowerShell 版本時，只需更新 Homebrew 的公式並升級 PowerShell 預覽即可：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-128">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="3b1f7-129">您可從 PowerShell (pwsh) 主機內呼叫上命令，但必須結束並重新啟動 PowerShell 殼層，才能完成升級並重新整理 $PSVersionTable 中顯示的值。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-129">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="3b1f7-130">透過直接下載來安裝</span><span class="sxs-lookup"><span data-stu-id="3b1f7-130">Installation via Direct Download</span></span>

<span data-ttu-id="3b1f7-131">將[版本][]頁面上的 PKG 套件 `powershell-6.0.2-osx.10.12-x64.pkg` 下載至 macOS 電腦。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-131">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="3b1f7-132">您可以按兩下檔案並依照提示執行作業，或從終端機安裝：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="3b1f7-133">二進位封存</span><span class="sxs-lookup"><span data-stu-id="3b1f7-133">Binary Archives</span></span>

<span data-ttu-id="3b1f7-134">macOS 和 Linux 平台有 PowerShell 二進位 `tar.gz` 封存，以啟用進階的部署案例。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-134">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="3b1f7-135">解除安裝 macOS 上的二進位封存</span><span class="sxs-lookup"><span data-stu-id="3b1f7-135">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="3b1f7-136">解除安裝 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="3b1f7-136">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="3b1f7-137">如果您使用 Homebrew 安裝 PowerShell，解除安裝很簡單：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-137">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="3b1f7-138">如已透過直接下載安裝 PowerShell，即必須手動移除 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="3b1f7-138">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="3b1f7-139">若要解除安裝其他的 PowerShell 路徑，請參閱本文件中的[路徑][]一節，使用 `sudo rm` 移除所要的路徑。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-139">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="3b1f7-140">如果使用 Homebrew 安裝，此即非必要。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-140">This is not necessary if you installed with Homebrew.</span></span>

[路徑]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="3b1f7-142">路徑</span><span class="sxs-lookup"><span data-stu-id="3b1f7-142">Paths</span></span>

* <span data-ttu-id="3b1f7-143">`$PSHOME` 是 `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="3b1f7-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="3b1f7-144">會從 `~/.config/powershell/profile.ps1` 讀取使用者設定檔</span><span class="sxs-lookup"><span data-stu-id="3b1f7-144">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="3b1f7-145">會從 `$PSHOME/profile.ps1` 讀取預設設定檔</span><span class="sxs-lookup"><span data-stu-id="3b1f7-145">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="3b1f7-146">會從 `~/.local/share/powershell/Modules` 讀取使用者模組</span><span class="sxs-lookup"><span data-stu-id="3b1f7-146">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3b1f7-147">會從 `/usr/local/share/powershell/Modules` 讀取共用的模組</span><span class="sxs-lookup"><span data-stu-id="3b1f7-147">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3b1f7-148">會從 `$PSHOME/Modules` 讀取預設模組</span><span class="sxs-lookup"><span data-stu-id="3b1f7-148">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="3b1f7-149">PSReadline 記錄會記錄在 `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="3b1f7-149">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="3b1f7-150">設定檔會採用 PowerShell 的每個主機設定。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-150">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="3b1f7-151">因此預設主機特定設定檔便會存在於相同位置的 `Microsoft.PowerShell_profile.ps1`。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-151">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="3b1f7-152">PowerShell 遵循 macOS 上的 [XDG 基底目錄規格][xdg-bds]。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-152">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="3b1f7-153">因為 macOS 是 BSD 的衍生項，所以使用的前置詞是 `/usr/local` 而非 `/opt`。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-153">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="3b1f7-154">因此，`$PSHOME` 是 `/usr/local/microsoft/powershell/6.0.2/`，而且符號連結放在 `/usr/local/bin/pwsh`。</span><span class="sxs-lookup"><span data-stu-id="3b1f7-154">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3b1f7-155">其他資源</span><span class="sxs-lookup"><span data-stu-id="3b1f7-155">Additional Resources</span></span>

* <span data-ttu-id="3b1f7-156">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="3b1f7-156">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="3b1f7-157">[Homebrew Github 存放庫][GitHub]</span><span class="sxs-lookup"><span data-stu-id="3b1f7-157">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="3b1f7-158">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="3b1f7-158">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[版本]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
