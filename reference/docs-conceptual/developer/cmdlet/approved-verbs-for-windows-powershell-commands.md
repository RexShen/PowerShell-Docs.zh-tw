---
ms.date: 09/07/2018
ms.topic: reference
title: 已核准的 PowerShell 命令動詞
description: 已核准的 PowerShell 命令動詞
ms.openlocfilehash: 237355ba9729cfe16c335b39f19ab20e40999457
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655832"
---
# <a name="approved-verbs-for-powershell-commands"></a>已核准的 PowerShell 命令動詞

PowerShell 會針對 Cmdlet 的名稱與其所衍生 .NET 類別使用成對的動詞與名詞。
名稱的動詞部分會識別 Cmdlet 所執行動作。 名稱的名詞部分會識別所執行動作所在的實體。 例如，`Get-Command` Cmdlet 會擷取在 PowerShell 中註冊的所有命令。

> [!NOTE]
> 即使單字並非英文語言的標準動詞，PowerShell 還是會使用「動詞」一詞來描述此隱含動作的單字。 例如，即使 _New_ 一詞並非英文語言的動詞，因為其隱含動作，所以還是有效的 PowerShell 動詞名稱。

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->

每個已核准的動詞都擁有所定義對應的 _別名前置詞_ 。
我們會在使用該動詞的命令別名中，使用此別名前置詞。
例如，`Import` 的別名前置詞為 `ip`；相對地，`Import-Module` 的別名為 `ipmo`。  這是建議而非規則；特別是其無須遵守命令別名，就能從其他環境模擬已知的命令。

## <a name="verb-naming-recommendations"></a>動詞命名建議

下列建議有助為 Cmdlet 選擇適當的動詞，以確定所建立的 Cmdlet、由 PowerShell 提供的 Cmdlet，以及由其他人設計的 Cmdlet 之間其一致性。

- 使用由 PowerShell 所提供其中一個預先定義的動詞名稱
- 使用該動詞來描述動作的一般範圍，並使用參數進一步改善 Cmdlet 的動作。
- 請勿使用已核准動詞的同義字。 例如，一律使用 `Remove`，一律不使用 `Delete` 或 `Eliminate`。
- 只使用此主題所列出每個動詞的形式。 例如，使用 `Get`，但不要使用 `Getting` 或 `Gets`。
- 請勿使用下列保留的動詞或別名。 PowerShell 語言或其中少數的 Cmdlet 會在例外情況下使用這些動詞。
    - ForEach (Foreach)
    - [Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)：以指定的表單或版面配置來排列物件
    - [Group](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)：排列一或多個資源，或將一或多個資源建立關聯
    - [Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)
    - Sort (sr)
    - TEE (te)
    - Where (wh)

您可使用 `Get-Verb` Cmdlet 取得完整的動詞清單。

## <a name="similar-verbs-for-different-actions"></a>適用於不同動作的類似動詞

下列類似動詞代表不同動作。

### <a name="new-vs-set"></a>比較 New 與設定

使用 `New` 動詞來建立新的資源。 使用 `Set` 動詞來修改現有的資源，若該資源不存在，則可選擇性將其建立 (例如 `Set-Variable` Cmdlet)。

### <a name="find-vs-search"></a>比較 Find 與搜尋

使用 `Find` 動詞來尋找物件。 使用 `Search` 動詞來建立容器中資源的參考。

### <a name="get-vs-read"></a>比較 Get 與讀取

使用 `Get` 動詞來取得有關資源 (例如檔案) 的資訊，或取得可在未來存取資源的物件。 使用 `Read` 動詞來開啟資源，並解壓縮其中包含的資訊。

### <a name="invoke-vs-start"></a>比較 Invoke 與Start

使用 `Invoke` 動詞來執行同步作業，例如執行命令並等候該其結束。 使用 `Start` 動詞來開始非同步作業，例如啟動自發處理序。

### <a name="ping-vs-test"></a>比較 Ping 與測試

使用 `Test` 動詞。

## <a name="common-verbs"></a>一般動詞

PowerShell 會使用 [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) 列舉類別來定義可套用至幾乎任何 Cmdlet 的一般動作。 下表列出大部分定義的動詞。

|動詞 (別名)|動作|要避免的同義字|
|--------------------|------------|--------------|
|[Add](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|將資源新增至容器，或將項目連結至另一個項目。 例如，`Add-Content` Cmdlet 會將內容新增至檔案。 此動詞會與 `Remove` 成對。|Append、Attach、Concatenate、Insert|
|[Clear](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|從容器移除所有物件，但不要刪除該容器。 例如，`Clear-Content` Cmdlet 會移除檔案的內容，但不會刪除檔案。|Flush、Erase、Release、Unmark、Unset、Nullify|
|[Close](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|變更資源的狀態，使其無法存取、無法提供或無法使用。 此動詞會與 `Open.` 成對||
|[Copy](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|將資源複製到另一個名稱或另一個容器。 例如，`Copy-Item` Cmdlet 會將項目 (例如檔案) 從資料存放區中的一個位置複製到另一個位置。|Duplicate、Clone、Replicate、Sync|
|[Enter](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|指定可讓使用者移入資源的動作。 例如，`Enter-PSSession` Cmdlet 會將使用者放置於互動式工作階段中。 此動詞會與 `Exit` 成對。|Push、Into|
|[Exit](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|將目前環境或內容設定為最近使用的內容。 例如，`Exit-PSSession` Cmdlet 會將使用者放置於用來啟動互動式工作階段的工作階段中。 此動詞會與 `Enter` 成對。|Pop、Out|
|[Find](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|在容器中尋找未知、隱含、選擇性或指定的物件。|搜尋|
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|指定擷取資源的動作。 此動詞會與 `Set` 成對。|Read、Open、Cat、Type、Dir、Obtain、Dump、Acquire、Examine、Find、Search|
|[Hide](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|使資源無法偵測。 例如，名稱包括 Hide 動詞的 Cmdlet 可能會隱藏使用者的服務。 此動詞會與 `Show` 成對。|封鎖|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|將多個資源合併成一個資源。 例如，`Join-Path` Cmdlet 會將路徑與其中一個子路徑合併，以建立單一路徑。 此動詞會與 `Split` 成對。|Combine、Unite、Connect、Associate|
|[Lock](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|保護資源。 此動詞會與 `Unlock` 成對。|Restrict、Secure|
|[Move](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|將資源從一個位置移至另一個。 例如，`Move-Item` Cmdlet 會將項目從資料存放區中的一個位置移至另一個位置。|Transfer、Name、Migrate|
|[New](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|建立資源。 (建立包括資料的資源 (例如 `Set-Variable` Cmdlet) 時，也可以使用 `Set` 動詞。)|Create、Generate、Build、Make、Allocate|
|[Open](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|變更資源的狀態，使其可存取、可供使用或可使用。 此動詞會與 `Close` 成對。||
|[Optimize](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|增加資源的有效性。||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|從堆疊頂端移除項目。 例如，`Pop-Location` Cmdlet 會將目前的位置變更至最近推送到堆疊上的位置。||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|將項目新增至堆疊頂端。 例如，`Push-Location` Cmdlet 會將目前的位置推送到堆疊。||
|[Redo](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|將資源重設為未完成的狀態。||
|[Remove](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|從容器刪除資源。 例如，`Remove-Variable` Cmdlet 會刪除變數與其值。 此動詞會與 `Add` 成對。|Clear、Cut、Dispose、Discard、Erase|
|[Rename](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|變更資源的名稱。 例如，`Rename-Item` Cmdlet (其用來存取儲存的資料) 會變更資料存放區中的項目名稱。|變更|
|[Reset](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|將資源設定回其原始狀態。||
|[Resize](/dotnet/api/System.Management.Automation.VerbsCommon.Resize)(rz)|變更資源大小。||
|[Search](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|建立容器中資源的參考。|Find、Locate|
|[Select](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|尋找容器中的資源。 例如，`Select-String` Cmdlet 會尋找字串與檔案中的文字。|Find、Locate|
|[Set](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|取代現有資源上的資料，或建立包含某些資料的資源。 例如，`Set-Date` Cmdlet 會變更本機電腦上的系統時間。 (`New` 動詞也可用來建立資源。)此動詞會與 `Get` 成對。|Write、Reset、Assign、Configure|
|[Show](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|讓使用者能看見資源。 此動詞會與 `Hide` 成對。|Display、Produce|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|略過順序中的一或多個資源或點。|Bypass、Jump|
|[Split](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|將資源的各個部分分開。 例如，`Split-Path` Cmdlet 會傳回路徑的不同部分。 此動詞會與 `Join` 成對。|獨立|
|[Step](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|移至順序中的下一個點或資源。||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|指定在兩個資源之間進行替代的動作，例如在兩個位置、責任或狀態之間變更。||
|[Undo](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (un)|將資源設定為其先前的狀態。||
|[Unlock](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (uk)|發行已鎖定的資源。 此動詞會與 `Lock` 成對。|Release、Unrestrict、Unsecure|
|[Watch](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|持續針對變更檢查或監視資源。||

## <a name="communications-verbs"></a>通訊動詞

PowerShell 會使用 [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) 類別來定義套用於通訊的動作。 下表列出大部分定義的動詞。

|動詞 (別名)|動作|要避免的同義字|
|--------------------|------------|--------------|
|[Connect](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|建立來源與目的地之間的連結。 此動詞會與 `Disconnect` 成對。|Join、Telnet|
|[Disconnect](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|中斷來源與目的地之間的連結。 此動詞會與 `Connect` 成對。|Break、Logoff|
|[Read](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|從來源取得資訊。 此動詞會與 `Write` 成對。|Acquire、Prompt、Get|
|[Receive](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|接受從來源傳送的資訊。 此動詞會與 `Send` 成對。|Read、Accept、Peek|
|[Send](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|將資訊傳遞到目的地。 此動詞會與 `Receive` 成對。|Put、Broadcast、Mail、Fax|
|[Write](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|將資訊新增至目標。 此動詞會與 `Read` 成對。|Put、Print|

## <a name="data-verbs"></a>資料動詞

PowerShell 會使用 [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) 類別來定義套用於資料處理的動作。 下表列出大部分定義的動詞。

|動詞名稱 (別名)|動作|要避免的同義字|
|-------------------------|------------|--------------|
|[Backup](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|透過複寫來儲存資料。|Save、Burn、Replicate、Sync|
|[Checkpoint](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|建立資料目前狀態的快照集，或其設定目前狀態的快照集。|Diff|
|[Compare](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|針對來自另一個資源的資料，評估來自其中一個資源的資料。|Diff|
|[Compress](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|壓縮資源的資料。 此動詞會與 `Expand` 成對。|精簡|
|[Convert](/dotnet/api/System.Management.Automation.VerbsData.Convert) (cv)|當 Cmdlet 支援雙向轉換，或當 Cmdlet 支援多個資料類型之間的轉換時，會將資料從一個表示法變更為另一個。|Change、Resize、Resample|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|將一個主要輸入類型 (Cmdlet 名詞表示輸入) 轉換成一或多個支援的輸出類型。|Export、Output、Out|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|從一或多個輸入類型轉換成主要輸出類型 (Cmdlet 名詞表示輸出類型)。|Import、Input、In|
|[Dismount](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|從位置中斷已命名實體的連線。 此動詞會與 `Mount` 成對。|Unmount、Unlink|
|[Edit](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|透過新增或移除內容來修改現有資料。|Change、Update、Modify|
|[Expand](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|還原已壓縮至其原始狀態的資源其資料。 此動詞會與 `Compress` 成對。|Explode、Uncompress|
|[Export](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|將主要輸入封裝至永久性資料存放區，例如檔案或交換格式。 此動詞會與 `Import` 成對。|Extract、Backup|
|[Import](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|從儲存在永久性資料存放區 (例如檔案) 或交換格式中的資料建立資源。 例如，`Import-CSV` Cmdlet 會將逗號分隔值 (CSV) 檔案中資料匯入可供其他 Cmdlet 使用的物件。 此動詞會與 `Export` 成對。|BulkLoad、Load|
|[Initialize](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|準備要使用的資源，並將其設定為預設狀態。|Erase、Init、Renew、Rebuild、Reinitialize、Setup|
|[Limit](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|將條件約束套用至資源。|Quota|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|從多個資源建立單一資源。|Combine、Join|
|[Mount](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|將已命名實體連結至位置。 此動詞會與 `Dismount` 成對。|連線|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|將資料傳送出環境。 例如，`Out-Printer` Cmdlet 會將資料傳送至印表機。||
|[Publish](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|以便其他人使用資源。 此動詞會與 `Unpublish` 成對。|Deploy、Release、Install|
|[Restore](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|將資源設定為預先定義的狀態，例如 `Checkpoint` 所設定的狀態。 例如，`Restore-Computer` Cmdlet 會在本機電腦上啟動系統還原。|Repair、Return、Undo、Fix|
|[Save](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|保留資料以避免遺失。||
|[Sync](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|確保有兩個以上的資源處於相同狀態。|Replicate、Coerce、Match|
|[Unpublish](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|讓其他人無法使用資源。 此動詞會與 `Publish` 成對。|Uninstall、Revert、Hide|
|[Update](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|將資源保持在最新狀態，以維護其狀態、精確度、符合性或合規性。 例如，`Update-FormatData` Cmdlet 會更新並將格式化檔案新增至目前的 PowerShell 主控台。|Refresh、Renew、Recalculate、Re-index|

## <a name="diagnostic-verbs"></a>診斷動詞

PowerShell 會使用 [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) 類別來定義套用於診斷的動作。 下表列出大部分定義的動詞。

|動詞 (別名)|動作|要避免的同義字|
|--------------------|------------|--------------|
|[Debug](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|檢查資源以診斷操作問題。|診斷|
|[Measure](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|識別指定作業所取用的資源，或擷取資源的有關統計資料。|Calculate、Determine、Analyze|
|[Repair](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|將資源還原至可使用的條件|Fix、Restore|
|[Resolve](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|將資源的速記表示法對應至更完整表示法。|Expand、Determine|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|確認資源的作業或一致性。|Diagnose、Analyze、Salvage、Verify|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|追蹤資源的活動。|Track、Follow、Inspect、Dig|

## <a name="lifecycle-verbs"></a>生命週期動詞

PowerShell 會使用 [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 類別來定義套用於資源生命週期的動作。 下表列出大部分已定義的動詞。

|動詞 (別名)|動作|要避免的同義字|
|--------------------|------------|--------------|
|[Approve](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|確認或同意資源或處理序的狀態。||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|確認資源的狀態。|Certify|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|從幾組輸入檔 (通常是原始程式碼或宣告式文件) 中建立成品 (通常是二進位檔或文件)。此動詞已在 PowerShell 6 中新增。||
|[Complete](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|結束作業。||
|[Confirm](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|認可、確認或驗證資源或處理序的狀態。|Acknowledge、Agree、Certify、Validate、Verify|
|[Deny](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|拒絕、反對、封鎖或抵制資源或處理序的狀態。|Block、Object、Refuse、Reject|
|[Deploy](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|將應用程式、網站或解決方案傳送至遠端目標，讓該解決方案的取用者能夠在部署完成之後加以存取。 此動詞已在 PowerShell 6 中新增。||
|[Disable](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|將資源設定為無法使用或非作用中狀態。 例如，`Disable-PSBreakpoint` Cmdlet 會讓中斷點為非作用中。 此動詞會與 `Enable` 成對。|Halt、Hide|
|[Enable](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|將資源設定為可供使用或作用中狀態。 例如，`Enable-PSBreakpoint` Cmdlet 會讓中斷點為作用中。 此動詞會與 `Disable` 成對。|Start、Begin|
|[Install](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (is)|將資源放置於某個位置，並選擇性地將其初始化。 此動詞會與 `Uninstall` 成對。|安裝程式|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|執行動作，例如執行命令或方法。|Run、Start|
|[Register](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|建立存放庫 (例如資料庫) 中資源的項目。 此動詞會與 `Unregister` 成對。||
|[Request](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|要求資源或要求權限。||
|[Restart](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|停止作業，然後再次啟動。 例如，`Restart-Service` Cmdlet 會先停止再啟動服務。|再循環|
|[Resume](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|啟動已擱置的作業。 例如，`Resume-Service` Cmdlet 會啟動已擱置的服務。 此動詞會與 `Suspend` 成對。||
|[Start](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|起始作業。 例如，`Start-Service` Cmdlet 會啟動服務。 此動詞會與 `Stop` 成對。|Launch、Initiate、Boot|
|[Stop](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|中止活動。 此動詞會與 `Start` 成對。|End、Kill、Terminate、Cancel|
|[Submit](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|顯示核准的資源。|郵寄|
|[Suspend](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|暫停活動。 例如，`Suspend-Service` Cmdlet 會暫停服務。 此動詞會與 `Resume` 成對。|暫停|
|[Uninstall](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|從指出的位置移除資源。 此動詞會與 `Install` 成對。||
|[Unregister](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (ur)|從存放庫移除資源的項目。 此動詞會與 `Register` 成對。|移除|
|[Wait](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|暫停作業，直到發生指定的事件為止。 例如，`Wait-Job` Cmdlet 會暫停作業，直到完成一或多個背景作業為止。|Sleep、Pause|

## <a name="security-verbs"></a>安全性動詞

PowerShell 會使用 [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) 類別來定義套用於安全性的動作。 下表列出大部分已定義的動詞。

|動詞 (別名)|動作|要避免的同義字|
|--------------------|------------|--------------|
|[Block](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|限制存取資源。 此動詞會與 `Unblock` 成對。|Prevent、Limit、Deny|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|允許存取資源。 此動詞會與 `Revoke` 成對。|Allow、Enable|
|[Protect](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|保護資源免於遭受攻擊或遺失。 此動詞會與 `Unprotect` 成對。|Encrypt、Safeguard、Seal|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rk)|指定不允許存取資源的動作。 此動詞會與 `Grant` 成對。|Remove、Disable|
|[Unblock](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|移除資源的限制。 此動詞會與 `Block` 成對。|Clear、Allow|
|[Unprotect](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (up)|從新增為防止遭受攻擊或遺失的資源中移除保護。 此動詞會與 `Protect` 成對。|Decrypt、Unseal|

## <a name="other-verbs"></a>其他動詞

PowerShell 會使用 [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) 類別來定義不適合特定動詞名稱類別的標準動詞名稱，例如一般、通訊、資料、生命週期或安全性動詞名稱動詞。

|動詞 (別名)|動作|要避免的同義字|
|--------------------|------------|--------------|
|[Use](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|使用或包括資源以執行某些動作。||

## <a name="see-also"></a>另請參閱

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)
- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)
- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)
- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)
- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)
- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)
- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)
- [Cmdlet 宣告](./cmdlet-class-declaration.md)
- [Windows PowerShell 程式設計人員手冊](../prog-guide/windows-powershell-programmer-s-guide.md)
- [Windows PowerShell 殼層 SDK](../windows-powershell-reference.md)
