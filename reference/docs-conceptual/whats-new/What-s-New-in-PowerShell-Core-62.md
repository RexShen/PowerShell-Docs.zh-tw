---
title: PowerShell Core 6.2 的新功能
description: PowerShell Core 6.2 中發行的新功能與變更
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995468"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="a6de6-103">PowerShell Core 6.2 的新功能</span><span class="sxs-lookup"><span data-stu-id="a6de6-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="a6de6-104">PowerShell Core 6.2 版著重於效能改進、錯誤修復，以及可提升軟體品質的較小 Cmdlet 和語言增強功能。</span><span class="sxs-lookup"><span data-stu-id="a6de6-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="a6de6-105">若要查看增強功能的完整清單，請參閱 GitHub 上的詳細[變更記錄](https://github.com/PowerShell/PowerShell/releases)。</span><span class="sxs-lookup"><span data-stu-id="a6de6-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="a6de6-106">實驗性功能</span><span class="sxs-lookup"><span data-stu-id="a6de6-106">Experimental Features</span></span>

<span data-ttu-id="a6de6-107">先前我們已啟用對[實驗性功能][]的支援。</span><span class="sxs-lookup"><span data-stu-id="a6de6-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="a6de6-108">在 6.2 版中，我們提供了四個試用的實驗性功能。請提供意見反應，協助我們進行改善，以及決定是否值得升級為主流功能。</span><span class="sxs-lookup"><span data-stu-id="a6de6-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="a6de6-109">請使用 `Get-ExperimentalFeature` 取得一份可用實驗性功能的清單。</span><span class="sxs-lookup"><span data-stu-id="a6de6-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="a6de6-110">您可以使用 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` 啟用或停用這些功能。</span><span class="sxs-lookup"><span data-stu-id="a6de6-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="a6de6-111">找不到命令建議項目</span><span class="sxs-lookup"><span data-stu-id="a6de6-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="a6de6-112">此功能會使用模糊比對方式，尋找您可能拼字錯誤的命令或 Cmdlet 的建議項目。</span><span class="sxs-lookup"><span data-stu-id="a6de6-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="a6de6-113">範例</span><span class="sxs-lookup"><span data-stu-id="a6de6-113">Example</span></span>

<span data-ttu-id="a6de6-114">在此範例中，系統在 Cmdlet 名稱拼字錯誤的情況下，透過模糊比對方式找出幾個最有可能和最不可能的建議項目。</span><span class="sxs-lookup"><span data-stu-id="a6de6-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a><span data-ttu-id="a6de6-115">隱含遠端批次處理</span><span class="sxs-lookup"><span data-stu-id="a6de6-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="a6de6-116">在管線中使用[隱含遠端](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) \(英文\) 時，PowerShell 會將管線中的每個命令視為獨立。</span><span class="sxs-lookup"><span data-stu-id="a6de6-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="a6de6-117">用戶端和遠端系統之間的物件，會在管線執行時重複序列化和 `de-serialized`。</span><span class="sxs-lookup"><span data-stu-id="a6de6-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="a6de6-118">使用此功能時，PowerShell 會分析管線，判斷命令是否安全地執行以及它是否存在於目標系統上。</span><span class="sxs-lookup"><span data-stu-id="a6de6-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="a6de6-119">若為 true，PowerShell 會從遠端執行整個管線，並只將結果序列化並 `de-serializes` 回用戶端。</span><span class="sxs-lookup"><span data-stu-id="a6de6-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="a6de6-120">實際測試`Get-Process | Sort-Object`透過 localhost 會從 10-15 秒減少至 20-30 **毫秒**。</span><span class="sxs-lookup"><span data-stu-id="a6de6-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="a6de6-121">此功能只需要在用戶端上啟用。</span><span class="sxs-lookup"><span data-stu-id="a6de6-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="a6de6-122">伺服器端不需要任何變更。</span><span class="sxs-lookup"><span data-stu-id="a6de6-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="a6de6-123">暫存磁碟機</span><span class="sxs-lookup"><span data-stu-id="a6de6-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="a6de6-124">如果在不同的作業系統上使用 PowerShell Core，會發現尋找暫存目錄的環境變數和 Windows、macOS 與 Linux 中的不一樣！</span><span class="sxs-lookup"><span data-stu-id="a6de6-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="a6de6-125">您可以透過此功能，取得稱為 `Temp:` 的 [PSDrive][]，它會自動對應至您所使用作業系統的暫存資料夾。</span><span class="sxs-lookup"><span data-stu-id="a6de6-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="a6de6-126">範例</span><span class="sxs-lookup"><span data-stu-id="a6de6-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

<span data-ttu-id="a6de6-127">請注意，原生檔案命令 (例如 Linux 上的 `ls`) 不會察覺 PSDrives 且不會看到這個 `Temp:` 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="a6de6-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="a6de6-128">展開縮寫</span><span class="sxs-lookup"><span data-stu-id="a6de6-128">Abbreviation Expansion</span></span>

<span data-ttu-id="a6de6-129">PowerShell Cmdlet 都應該有描述性名詞。</span><span class="sxs-lookup"><span data-stu-id="a6de6-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="a6de6-130">這會導致較難輸入完整名稱。</span><span class="sxs-lookup"><span data-stu-id="a6de6-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="a6de6-131">此功能可讓您只要輸入 Cmdlet 的大寫字元，然後使用 Tab 鍵自動完成來尋找相符項目。</span><span class="sxs-lookup"><span data-stu-id="a6de6-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="a6de6-132">範例</span><span class="sxs-lookup"><span data-stu-id="a6de6-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="a6de6-133">如果按下 Tab 鍵，並已安裝 Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) 模組，它會自動完成為：</span><span class="sxs-lookup"><span data-stu-id="a6de6-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="a6de6-134">此功能採用需透過互動方式使用的設計。</span><span class="sxs-lookup"><span data-stu-id="a6de6-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="a6de6-135">Cmdlet 的縮寫形式無法在系統中執行。</span><span class="sxs-lookup"><span data-stu-id="a6de6-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="a6de6-136">這並不是要取代別名的功能。</span><span class="sxs-lookup"><span data-stu-id="a6de6-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="a6de6-137">重大變更</span><span class="sxs-lookup"><span data-stu-id="a6de6-137">Breaking Changes</span></span>

- <span data-ttu-id="a6de6-138">修正 `Write-Output` 中的 `-NoEnumerate` 行為，以與 Windows PowerShell 一致。</span><span class="sxs-lookup"><span data-stu-id="a6de6-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="a6de6-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="a6de6-139">(#9069)</span></span>
- <span data-ttu-id="a6de6-140">讓 `Join-String -InputObject 1,2,3` 的結果和 `1,2,3 | Join-String` 相同 (#8611) (感謝 @sethvs！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="a6de6-141">新增 `-Stable` 至 `Sort-Object` 和相關測試 (#7862) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="a6de6-142">改善 `Start-Sleep`Cmdlet 以接受小數秒數 (#8537) (感謝 @Prototyyppi！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="a6de6-143">變更雜湊表以在所有文化特性 (Culture) 中以 `case-insensitive` 的方式使用 OrdinalIgnoreCase (#8566)</span><span class="sxs-lookup"><span data-stu-id="a6de6-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="a6de6-144">修正 `Import-Csv` 中的 **LiteralPath**，以繫結至 `Get-ChildItem` 輸出 (#8277) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a6de6-145">在 `Import-Csv` 中使用雙引號分隔符號時，不會再跳過沒有名稱的資料行 (#7899) (感謝 @Topping！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="a6de6-146">`Get-ExperimentalFeature` 不再有 `-ListAvailable` 切換功能 (#8318)</span><span class="sxs-lookup"><span data-stu-id="a6de6-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="a6de6-147">偵錯參數現在會將 `$DebugPreference` 設定為 **Continue**，而非 **Inquire** (#8195) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="a6de6-148">如果在與 pwsh 搭配使用的非互動式、重新導向、編碼命令中指定，請接受 `-OutputFormat` (#8115)</span><span class="sxs-lookup"><span data-stu-id="a6de6-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="a6de6-149">請先從模組基底路徑載入組件，然後再嘗試從 GAC 載入 (#8073)</span><span class="sxs-lookup"><span data-stu-id="a6de6-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="a6de6-150">從 Linux 預覽套件中移除波狀符號 (#8244)</span><span class="sxs-lookup"><span data-stu-id="a6de6-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="a6de6-151">將 `-WorkingDirectory` 的處理順序移到設定檔前面 (#8079)</span><span class="sxs-lookup"><span data-stu-id="a6de6-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="a6de6-152">不要在 Unix 中新增 `PATHEXT` 環境變數 (#7697) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="a6de6-153">已知問題</span><span class="sxs-lookup"><span data-stu-id="a6de6-153">Known Issues</span></span>

- <span data-ttu-id="a6de6-154">遠端登入 Windows IOT ARM 平台時，會在載入模組時發生問題。</span><span class="sxs-lookup"><span data-stu-id="a6de6-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="a6de6-155">請參閱 (#8053)</span><span class="sxs-lookup"><span data-stu-id="a6de6-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="a6de6-156">一般更新與修正</span><span class="sxs-lookup"><span data-stu-id="a6de6-156">General Updates and Fixes</span></span>

- <span data-ttu-id="a6de6-157">支援在區分大小寫的檔案系統中，使用檔案和資料夾不區分大小寫的 Tab 鍵自動完成功能 (#8128)</span><span class="sxs-lookup"><span data-stu-id="a6de6-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="a6de6-158">公開 PSVersionInfo.PSVersion 和 PSVersionInfo.PSEdition (#8054) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="a6de6-159">在 `catch{ }` 區塊中新增 `$_` / `$PSItem` 的型別推斷 (#8020) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="a6de6-160">修正靜態方法引動過程型別推斷 (#8018) (感謝 @SeeminglyScience！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="a6de6-161">建立 `Select-Object`、`Group-Object`、**PSObject** 和 **雜湊表**的推斷型別 (#7231) (感謝 @powercode！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="a6de6-162">支援包含 `ByRef-like` 型別參數的呼叫方法 (#7721)</span><span class="sxs-lookup"><span data-stu-id="a6de6-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="a6de6-163">處理 Windows PowerShell 模組路徑已在環境 PSModulePath 中的情況 (#7727)</span><span class="sxs-lookup"><span data-stu-id="a6de6-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="a6de6-164">透過儲存純文字以啟用非 Windows 的 `SecureString` Cmdlet (#9199)</span><span class="sxs-lookup"><span data-stu-id="a6de6-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="a6de6-165">改善使用 securestring 匯入 clixml 時，非 Windows 上顯示的錯誤訊息 (#7997)</span><span class="sxs-lookup"><span data-stu-id="a6de6-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="a6de6-166">新增 ReplyTo 參數至 `Send-MailMessage`(#8727) (感謝 @replicaJunction！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="a6de6-167">新增已淘汰的訊息至 `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="a6de6-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="a6de6-168">修正 `Restart-Computer` 以在沒有 WinRM 時於 `localhost` 中運作 (#9160)</span><span class="sxs-lookup"><span data-stu-id="a6de6-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="a6de6-169">讓 `Start-Job` 在裝載 PowerShell 時擲回終止錯誤 (#9128)</span><span class="sxs-lookup"><span data-stu-id="a6de6-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="a6de6-170">為 ushort、uint、ulong 及 short 常值新增 C# 樣式類型加速器和尾碼 (#7813) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="a6de6-171">已為數值常值新增新的尾碼 - 請參閱 [about_Numeric_Literals][] (#7901) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="a6de6-172">在 SupportsShouldProcess 未設定為 'true' 時，正確地報告影響層級 (#8209) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="a6de6-173">修正 Web Cmdlet 中的要求字元集問題 (#8742) (感謝 @markekraus！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="a6de6-174">修正 Web Cmdlet 中的預期 `100-continue` 問題 (#8679) (感謝 @markekraus！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="a6de6-175">修正 Web Cmdlet 中的檔案封鎖問題 (#7676) (感謝 @Claustn！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="a6de6-176">修正 `Invoke-RestMethod` 中的字碼頁剖析問題 (#8694) (感謝 @markekraus！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="a6de6-177">重構 `ConvertTo-Json` 以將 JsonObject.ConvertToJson 公開為公用 API (#8682)</span><span class="sxs-lookup"><span data-stu-id="a6de6-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="a6de6-178">透過 -Depth 增加 `ConvertFrom-Json` 中可設定的最大深度 (#8199) (感謝 @louistio！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="a6de6-179">在 `ConvertTo-Json` Cmdlet 中新增 EscapeHandling 參數 (#7775) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a6de6-180">新增 `-CustomPipeName` 至 pwsh 和 `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="a6de6-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="a6de6-181">支援在 Windows 上建立與 `New-Item` 的相對符號連結 (#8783)</span><span class="sxs-lookup"><span data-stu-id="a6de6-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="a6de6-182">允許 Windows 使用者在不需要提高權限的情況下，使用開發人員模式建立符號連結 (#8534)</span><span class="sxs-lookup"><span data-stu-id="a6de6-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="a6de6-183">支援 `Write-Information` 以接受 `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="a6de6-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="a6de6-184">修正進階函式的 `Get-Help` 以包含 MAML 說明內容 (#8353)</span><span class="sxs-lookup"><span data-stu-id="a6de6-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="a6de6-185">修正只宣告一個參數時，-Parameter 會發生的 `Get-Help`PSTypeName 問題 (#8754) (感謝 @pougetat！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="a6de6-186">修正在 ScriptBlock 上執行以取得註解說明之 `Get-Help` 的權杖計算。</span><span class="sxs-lookup"><span data-stu-id="a6de6-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="a6de6-187">(#8238) (感謝 @hubuk！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="a6de6-188">變更 `Get-Help` Cmdlet 的 -Parameter 參數，讓它能接受字串陣列 (#8454) (感謝 @sethvs！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="a6de6-189">解析其路徑中包含空格的呼叫器 (#8571) (感謝 @pougetat！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="a6de6-190">新增在函式 'help' 中使用 `less` 來指示使用者如何結束的提示 (#7998)</span><span class="sxs-lookup"><span data-stu-id="a6de6-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="a6de6-191">在 `Format-Hex`Cmdlet 中新增對列舉和 char 類型的支援 (#8191) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a6de6-192">將 ShouldProcess 自 `Format-Hex` 移除 (#8178)</span><span class="sxs-lookup"><span data-stu-id="a6de6-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="a6de6-193">在 `Format-Hex` 中新增 Offset 和 Count 參數並重構 Cmdlet (#7877) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a6de6-194">允許在 `ConvertTo-Html` 中將 'name' 做為 'label' 的別名索引鍵，允許 'width' 項目為整數 (#8426) (感謝 @mklement0！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="a6de6-195">讓以 scriptblock 為基礎的計算屬性再次於 `ConvertTo-Html` 中運作 (#8427) (感謝 @mklement0！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="a6de6-196">新增 Cmdlet `Join-String` 以從管線輸入建立文字 (#7660) (感謝 @powercode！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="a6de6-197">修正 `Join-String` Cmdlet FormatString 參數邏輯 (#8449) (感謝 @sethvs！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="a6de6-198">將 `Clear-Host` 變更回使用 `$RAWUI` 並清除，以透過遠端運作 (#8609)</span><span class="sxs-lookup"><span data-stu-id="a6de6-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="a6de6-199">將 `Clear-Host` 變更為簡單的 `[console]::clear` 並自 Unix 移除明確的別名 (#8603)</span><span class="sxs-lookup"><span data-stu-id="a6de6-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="a6de6-200">修正 `Import-Csv` 中的 LiteralPath，以繫結至 `Get-ChildItem` 輸出 (#8277) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a6de6-201">help 函式不應使用 AliasHelpInfo 的呼叫器 (#8552)</span><span class="sxs-lookup"><span data-stu-id="a6de6-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="a6de6-202">新增 `-UseMinimalHeader` 至 `Start-Transcript` 以將文字記錄標題最小化 (#8402) (感謝 @lukexjeremy！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="a6de6-203">新增 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` Cmdlet (#8318)</span><span class="sxs-lookup"><span data-stu-id="a6de6-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="a6de6-204">公開 **PSDiagnostics** 的所有 Cmdlet (如果 logman.exe 可用) (#8366)</span><span class="sxs-lookup"><span data-stu-id="a6de6-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="a6de6-205">將 **Persist** 參數自 `non-Windows` 平台上的 `New-PSDrive` 中移除 (#8291) (感謝 @lukexjeremy！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="a6de6-206">新增對 `cd +` 的支援 (#7206) (感謝 @bergmeister！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="a6de6-207">讓 `Set-Location -LiteralPath` 能處理名為 - 與 + 的資料夾 (#8089)</span><span class="sxs-lookup"><span data-stu-id="a6de6-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="a6de6-208">在指定空值或 `$null` 路徑值時，`Test-Path` 會傳回 `$false` (#8080) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="a6de6-209">允許即使路徑不符合任何提供者時也會傳回動態參數 (#7957)</span><span class="sxs-lookup"><span data-stu-id="a6de6-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="a6de6-210">支援 Unix 平台上的 `Get-PSHostProcessInfo` 和 `Enter-PSHostProcess` (#8232)</span><span class="sxs-lookup"><span data-stu-id="a6de6-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="a6de6-211">減少 `Get-Content` Cmdlet 中的配置數 (#8103) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a6de6-212">支援 `Add-Content` 在寫入內容時與其他工具共用讀取權限 (#8091)</span><span class="sxs-lookup"><span data-stu-id="a6de6-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="a6de6-213">`Get/Add-Content` 以容器為目標時，會擲回改良的錯誤 (#7823) (感謝 @kvprasoon！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="a6de6-214">將 `-Name`、`-NoUserOverrides` 和 `-ListAvailable` 參數新增至 `Get-Culture` Cmdlet (#7702) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a6de6-215">新增整合的屬性以完成 **Encoding** 參數。</span><span class="sxs-lookup"><span data-stu-id="a6de6-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="a6de6-216">(#7732) (感謝 @ThreeFive-O！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="a6de6-217">允許在 **Encoding** 參數中使用已註冊字碼頁的數字識別碼和名稱 (#7636) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="a6de6-218">修正 `Rename-Item -Path` 以包含萬用字元 (#7398) (感謝 @kwkam！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="a6de6-219">使用 `Start-Transcript` 且檔案存在時，會將檔案清空而不是刪除 (#8131) (感謝 @paalbra！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="a6de6-220">讓 `Add-Type` 開啟具有 **FileAccess.Read** 和 **FileShare.Read** 的原始程式碼檔案 (#7915) (感謝 @IISResetMe！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="a6de6-221">針對最新的 Windows 修正 `Enter-PSSession -ContainerId` (#7883)</span><span class="sxs-lookup"><span data-stu-id="a6de6-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="a6de6-222">確保 `Test-ModuleManifest` 會填入 **NestedModules** 屬性 (#7859)</span><span class="sxs-lookup"><span data-stu-id="a6de6-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="a6de6-223">新增 `%F` 案例至 `Get-Date` -UFormat (#7630) (感謝 @britishben！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="a6de6-224">修正 `Set-Service -Status Stopped` 以停止具有相依性的服務 (#5525) (感謝 @zhenggu！)</span><span class="sxs-lookup"><span data-stu-id="a6de6-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[實驗性功能]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
