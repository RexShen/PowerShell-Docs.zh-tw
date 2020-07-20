---
title: PowerShell 命令的已核准動詞 |Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: ab3915124b1d92e3273e4ffa38cd617a03e336f9
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469679"
---
# <a name="approved-verbs-for-powershell-commands"></a>PowerShell 命令的已核准動詞

PowerShell 會針對 Cmdlet 的名稱和其衍生的 Microsoft .NET Framework 類別使用動詞-名詞配對。 例如，PowerShell 所 `Get-Command` 提供的 Cmdlet 是用來抓取在 powershell 中註冊的所有命令。 名稱的動詞部分可識別此 Cmdlet 執行的動作。 名稱的名詞部分可識別執行動作所在的實體。

> [!NOTE]
> PowerShell 使用「_動詞_」一詞來描述一個表示動作的單字，即使該單字不是英文語言的標準動詞。 例如，「_新增_」一詞是有效的 PowerShell 動詞命令名稱，因為它會隱含動作，即使它不是英文語言中的動詞。

## <a name="verb-naming-rules"></a>動詞命名規則

下列清單提供當您選擇 Cmdlet 名稱的動詞時，應考慮的指導方針：

- 當您指定指令動詞時，建議您使用 PowerShell 所提供的其中一個預先定義的動詞名稱（這些預先定義動詞的別名會包含在下表中）。 當您使用預先定義的動詞時，您會確保您所建立的 Cmdlet、PowerShell 提供的 Cmdlet，以及其他人所設計的 Cmdlet 之間的一致性。

- 使用預先定義的動詞來描述動作的一般範圍，並使用參數進一步精簡 Cmdlet 的動作。

- 若要強制執行跨 Cmdlet 的一致性，請勿使用已核准動詞的同義字。

- 僅使用本主題中所列之每個動詞的形式。 例如，使用「Get」，但不要使用「取得」或「取得」。

- 針對動詞使用 Pascal 大小寫。 在 Pascal 大小寫中，每個單字的初始字母都是大寫，例如 "ForEach"。

- 請勿使用下列保留的動詞或別名。 這些動詞適用于 PowerShell 語言，或由 PowerShell 所提供的特殊案例 Cmdlet 使用。
  - ForEach （foreach）
  - 格式（f）
  - 群組（gp）
  - 排序（sr）
  - T （te）
  - Where （wh）

您可以使用 Cmdlet 來顯示動詞的完整清單 `Get-Verb` 。

## <a name="similar-verbs-for-different-actions"></a>不同動作的類似動詞

下列類似的動詞代表不同的動作。

### <a name="new-vs-set"></a>新增與設定的比較

指令 `New` 動詞是用來建立新的資源。 `Set`動詞可用來修改現有的資源，並選擇性地建立不存在的資源（例如 `Set-Variable` Cmdlet）。

### <a name="find-vs-search"></a>尋找與搜尋

`Find`動詞可用來尋找物件。 指令 `Search` 動詞是用來建立容器中資源的參考。

### <a name="get-vs-read"></a>取得與讀取的比較

`Get`動詞用來抓取資源，例如檔案。 指令 `Read` 動詞是用來從來源取得資訊，例如檔案。

### <a name="invoke-vs-start"></a>Invoke 與 Start 的比較

`Invoke`動詞可用來執行通常是同步作業的作業，例如執行命令。 `Start`動詞是用來開始通常是非同步作業的作業，例如啟動進程。

### <a name="ping-vs-test"></a>Ping 與測試的比較

使用 `Test` 動詞。

## <a name="common-verbs"></a>一般動詞

PowerShell 會使用[VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)列舉類別來定義可套用至幾乎任何 Cmdlet 的一般動作。 下表列出大部分定義的動詞。

|動詞（別名）|動作|註解|
|--------------------|------------|--------------|
|[新增](/dotnet/api/System.Management.Automation.VerbsCommon.Add)（a）|將資源新增至容器，或將專案附加至另一個專案。 例如，Cmdlet 會 `Add-Content` 將內容新增至檔案。 這個動詞會與搭配使用 `Remove` 。|針對此動作，請勿使用 Append、Attach、串連或 Insert 等動詞。|
|[清除](/dotnet/api/System.Management.Automation.VerbsCommon.Clear)（cl）|從容器中移除所有資源，但不會刪除容器。 例如， `Clear-Content` Cmdlet 會移除檔案的內容，但不會刪除檔案。|針對此動作，請勿使用 [清除]、[清除]、[釋放]、[取消設定] 或 [使失效] 等動詞。|
|[關閉](/dotnet/api/System.Management.Automation.VerbsCommon.Close)（cs）|變更資源的狀態，使其無法存取、無法使用或無法使用。 這個動詞會與`Open.`||
|[複製](/dotnet/api/System.Management.Automation.VerbsCommon.Copy)（cp）|將資源複製到另一個名稱或另一個容器。 例如， `Copy-Item` 用來存取預存資料的 Cmdlet 會將專案從資料存放區中的一個位置複製到另一個位置。|針對此動作，請勿使用複製、複製、複寫或同步等動詞。|
|[輸入](/dotnet/api/System.Management.Automation.VerbsCommon.Enter)（et）|指定允許使用者移入資源的動作。 例如，Cmdlet 會將 `Enter-PSSession` 使用者放在互動式會話中。 這個動詞會與搭配使用 `Exit` 。|針對此動作，請勿使用 Push 或 Into 之類的動詞。|
|結束[（例如](/dotnet/api/System.Management.Automation.VerbsCommon.Exit)）|將目前的環境或內容設定為最近使用的內容。 例如， `Exit-PSSession` Cmdlet 會將使用者放在用來啟動互動式會話的會話中。 這個動詞會與搭配使用 `Enter` 。|針對此動作，請不要使用 Pop 或 Out 這類動詞。|
|[尋找](/dotnet/api/System.Management.Automation.VerbsCommon.Find)（fd）|在容器中尋找不明、隱含、選擇性或指定的物件。||
|[格式](/dotnet/api/System.Management.Automation.VerbsCommon.Format)（f）|以指定的表單或版面配置排列物件。||
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) （g）|指定抓取資源的動作。 這個動詞會與搭配使用 `Set` 。|針對此動作，請勿使用如 Read、Open、Cat、Type、Dir、取得、傾印、取得、檢查、尋找或搜尋等動詞。|
|[隱藏](/dotnet/api/System.Management.Automation.VerbsCommon.Hide)（h）|使資源無法偵測。 例如，名稱包含隱藏動詞的 Cmdlet 可能會隱藏使用者的服務。 這個動詞會與搭配使用 `Show` 。|針對此動作，請不要使用動詞，例如 Block。|
|[聯結](/dotnet/api/System.Management.Automation.VerbsCommon.Join)（j）|將資源結合成一個資源。 例如，Cmdlet 會將 `Join-Path` 路徑與其中一個子路徑結合，以建立單一路徑。 這個動詞會與搭配使用 `Split` 。|針對此動作，請勿使用 [結合]、[聯合]、[連接] 或 [關聯] 這類動詞。|
|[鎖定](/dotnet/api/System.Management.Automation.VerbsCommon.Lock)（lk）|保護資源的安全。 這個動詞會與搭配使用 `Unlock` 。|針對此動作，請勿使用 [限制] 或 [安全] 等動詞。|
|[移動](/dotnet/api/System.Management.Automation.VerbsCommon.Move)（m）|將資源從一個位置移到另一個位置。 例如，Cmdlet 會 `Move-Item` 將專案從資料存放區中的一個位置移到另一個位置。|針對此動作，請勿使用傳送、名稱或遷移等動詞。|
|[新增](/dotnet/api/System.Management.Automation.VerbsCommon.New)（n）|建立資源。 （在 `Set` 建立包含資料的資源（例如 Cmdlet）時，也可以使用動詞命令 `Set-Variable` ）。|針對此動作，請勿使用動詞，例如建立、產生、建立、建立或配置。|
|[開啟](/dotnet/api/System.Management.Automation.VerbsCommon.Open)（op）|變更資源的狀態，使其可供存取、使用或使用。 這個動詞會與搭配使用 `Close` 。||
|[優化](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize)（om）|增加資源的效率。||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) （pop）|從堆疊頂端移除專案。 例如， `Pop-Location` Cmdlet 會將目前的位置變更為最近推送到堆疊上的位置。||
|[推](/dotnet/api/System.Management.Automation.VerbsCommon.Push)播（pu）|將專案加入至堆疊的頂端。 例如，Cmdlet 會將 `Push-Location` 目前位置推送到堆疊上。||
|[重做](/dotnet/api/System.Management.Automation.VerbsCommon.Redo)（重新）|將資源重設為已復原的狀態。||
|[移除](/dotnet/api/System.Management.Automation.VerbsCommon.Remove)（r）|從容器中刪除資源。 例如，Cmdlet 會 `Remove-Variable` 刪除變數及其值。 這個動詞會與搭配使用 `Add` 。|針對此動作，請勿使用 [清除]、[剪下]、[處置]、[捨棄] 或 [清除] 這類動詞。|
|[重新命名](/dotnet/api/System.Management.Automation.VerbsCommon.Rename)（rn）|變更資源的名稱。 例如， `Rename-Item` 用來存取儲存資料的 Cmdlet 會變更資料存放區中的專案名稱。|針對此動作，請勿使用如 [變更] 的動詞。|
|[重設](/dotnet/api/System.Management.Automation.VerbsCommon.Reset)（rs）|將資源設定回其原始狀態。||
|重[設大小](/dotnet/api/System.Management.Automation.VerbsCommon.Resize)（rz）|變更資源的大小。||
|[搜尋](/dotnet/api/System.Management.Automation.VerbsCommon.Search)（sr）|建立容器中資源的參考。|針對此動作，請勿使用 [尋找] 或 [尋找] 等動詞。|
|[選取](/dotnet/api/System.Management.Automation.VerbsCommon.Select)（sc）|尋找容器中的資源。 例如，Cmdlet 會 `Select-String` 尋找字串和檔案中的文字。|針對此動作，請勿使用 [尋找] 或 [尋找] 等動詞。|
|[設定](/dotnet/api/System.Management.Automation.VerbsCommon.Set)（s）|取代現有資源上的資料，或建立包含一些資料的資源。 例如，此 `Set-Date` Cmdlet 會變更本機電腦上的系統時間。 （指令 `New` 動詞也可以用來建立資源）。這個動詞會與搭配使用 `Get` 。|針對此動作，請不要使用動詞，例如 Write、Reset、Assign 或 Configure。|
|[顯示](/dotnet/api/System.Management.Automation.VerbsCommon.Show)（sh）|讓使用者看見資源。 這個動詞會與搭配使用 `Hide` 。|針對此動作，請勿使用顯示或產生之類的動詞。|
|[略過](/dotnet/api/System.Management.Automation.VerbsCommon.Skip)（sk）|略過序列中的一或多個資源或點。|針對此動作，請勿使用「略過」或「跳躍」之類的動詞。|
|[分割](/dotnet/api/System.Management.Automation.VerbsCommon.Split)（sl）|分隔資源的各個部分。 例如，Cmdlet 會傳回 `Split-Path` 路徑的不同部分。 這個動詞會與搭配使用 `Join` 。|針對此動作，請勿使用個別的動詞。|
|[步驟](/dotnet/api/System.Management.Automation.VerbsCommon.Step)（st）|移至順序中的下一個點或資源。||
|[交換器](/dotnet/api/System.Management.Automation.VerbsCommon.Switch)（sw）|指定在兩個資源之間進行替代的動作，例如變更兩個位置、責任或狀態。||
|[復原](/dotnet/api/System.Management.Automation.VerbsCommon.Undo)（取消）|將資源設定為其先前的狀態。||
|[解除鎖定](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock)（英國）|釋放已鎖定的資源。 這個動詞會與搭配使用 `Lock` 。|針對此動作，請勿使用發行、Unrestrict 或不安全等動詞。|
|[監看](/dotnet/api/System.Management.Automation.VerbsCommon.Watch)（wc）|持續檢查或監視資源的變更。||

## <a name="communications-verbs"></a>通訊動詞

PowerShell 會使用[VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)類別來定義適用于通訊的動作。 下表列出大部分定義的動詞。

|動詞（別名）|動作|註解|
|--------------------|------------|--------------|
|[Connect](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) （cc）|建立來源與目的地之間的連結。 這個動詞會與搭配使用 `Disconnect` 。|針對此動作，請勿使用 Join 或 Telnet 等動詞。|
|[中斷連接](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect)（dc）|中斷來源與目的地之間的連結。 這個動詞會與搭配使用 `Connect` 。|針對此動作，請勿使用 Break 或登出等動詞。|
|[讀取](/dotnet/api/System.Management.Automation.VerbsCommunications.Read)（rd）|從來源取得資訊。 這個動詞會與搭配使用 `Write` 。|針對此動作，請勿使用 Get、Prompt 或 Get 等動詞。|
|[接收](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive)（rc）|接受從來源傳送的資訊。 這個動詞會與搭配使用 `Send` 。|針對此動作，請勿使用 [讀取]、[接受] 或 [查看] 這類動詞。|
|[傳送](/dotnet/api/System.Management.Automation.VerbsCommunications.Send)（sd）|將資訊傳送至目的地。 這個動詞會與搭配使用 `Receive` 。|針對此動作，請勿使用 Put、廣播、Mail 或 Fax 等動詞。|
|[Write](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) （wr）|將資訊新增至目標。 這個動詞會與搭配使用 `Read` 。|針對此動作，請勿使用 Put 或 Print 之類的動詞。|

## <a name="data-verbs"></a>資料動詞

PowerShell 會使用[VerbsData](/dotnet/api/System.Management.Automation.VerbsData)類別來定義適用于資料處理的動作。 下表列出大部分定義的動詞。

|動詞名稱（別名）|動作|註解|
|-------------------------|------------|--------------|
|[備份](/dotnet/api/System.Management.Automation.VerbsData.Backup)（ba）|藉由複寫來儲存資料。|針對此動作，請勿使用 [儲存]、[燒錄]、[複寫] 或 [同步] 等動詞。|
|[檢查點](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint)（ch）|建立資料的目前狀態或其設定的快照集。|針對此動作，請勿使用動詞，例如 Diff。|
|[比較](/dotnet/api/System.Management.Automation.VerbsData.Compare)（cr）|針對來自另一個資源的資料，評估其中一個資源的資料。|針對此動作，請勿使用動詞，例如 Diff。|
|[壓縮](/dotnet/api/System.Management.Automation.VerbsData.Compress)（cm）|壓縮資源的資料。 與配對 `Expand` 。|針對此動作，請勿使用如 Compact 的指令動詞。|
|[轉換](/dotnet/api/System.Management.Automation.VerbsData.Convert)（cv）|當 Cmdlet 支援雙向轉換，或當 Cmdlet 支援多個資料類型之間的轉換時，會將資料從一個標記法變更為另一個。|針對此動作，請勿使用如變更、調整大小或重新取樣等動詞。|
|[Convertfrom-json](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) （cf）|將輸入的一個主要類型（Cmdlet 名詞表示輸入）轉換成一或多個支援的輸出類型。|針對此動作，請勿使用如 Export、Output 或 Out 等動詞。|
|[Convertto-html](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) （ct）|從一或多個輸入類型轉換成主要輸出類型（Cmdlet 名詞表示輸出類型）。|針對此動作，請勿使用如匯入、輸入或中的動詞。|
|[卸載](/dotnet/api/System.Management.Automation.VerbsData.Dismount)（dm）|從位置卸離已命名的實體。 這個動詞會與搭配使用 `Mount` 。|針對此動作，請不要使用動詞命令，例如取消掛接或取消連結。|
|[編輯](/dotnet/api/System.Management.Automation.VerbsData.Edit)（ed）|藉由新增或移除內容來修改現有的資料。|針對此動作，請勿使用 [變更]、[更新] 或 [修改] 這類動詞。|
|[展開](/dotnet/api/System.Management.Automation.VerbsData.Expand)（en）|還原已壓縮成其原始狀態之資源的資料。 這個動詞會與搭配使用 `Compress` 。|針對此動作，請勿使用「分解」或「解壓縮」等動詞。|
|[匯出](/dotnet/api/System.Management.Automation.VerbsData.Export)（ep）|將主要輸入封裝至持續性資料存放區，例如檔案或交換格式。 這個動詞會與搭配使用 `Import` 。|針對此動作，請勿使用 [解壓縮] 或 [備份] 這類動詞。|
|[群組](/dotnet/api/System.Management.Automation.VerbsData.Group)（gp）|排列或關聯一或多個資源。|針對此動作，請勿使用 [匯總]、[排列]、[關聯] 或 [相互關聯] 等動詞。|
|匯[入](/dotnet/api/System.Management.Automation.VerbsData.Import)（ip）|從儲存在持續性資料存放區（例如檔案）或交換格式中的資料，建立資源。 例如， `Import-CSV` Cmdlet 會將逗號分隔值（CSV）檔案中的資料匯入可供其他 Cmdlet 使用的物件。 這個動詞會與搭配使用 `Export` 。|針對此動作，請不要使用動詞，例如 BulkLoad 或 Load。|
|[Initialize](/dotnet/api/System.Management.Automation.VerbsData.Initialize) （在中）|準備要使用的資源，並將它設定為預設狀態。|針對此動作，請勿使用「清除」、「初始化」、「更新」、「重建」、「重新初始化」或「設定」等動詞。|
|[限制](/dotnet/api/System.Management.Automation.VerbsData.Limit)（l）|將條件約束套用至資源。|針對此動作，請勿使用「配額」之類的動詞。|
|[合併](/dotnet/api/System.Management.Automation.VerbsData.Merge)（mg）|從多個資源建立單一資源。|針對此動作，請勿使用 [結合] 或 [聯結] 這類動詞。|
|[掛接](/dotnet/api/System.Management.Automation.VerbsData.Mount)（mt）|將已命名的實體附加至位置。 這個動詞會與搭配使用 `Dismount` 。|針對此動作，請勿使用動詞 Connect。|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) （o）|將資料傳送至環境。 例如，Cmdlet 會 `Out-Printer` 將資料傳送至印表機。||
|[發行](/dotnet/api/System.Management.Automation.VerbsData.Publish)（pb）|讓其他人可以使用資源。 這個動詞會與搭配使用 `Unpublish` 。|針對此動作，請勿使用 [部署]、[發行] 或 [安裝] 等動詞。|
|[還原](/dotnet/api/System.Management.Automation.VerbsData.Restore)（rr）|將資源設定為預先定義的狀態，例如所設定的狀態 `Checkpoint` 。 例如，此 `Restore-Computer` Cmdlet 會在本機電腦上啟動系統還原。|針對此動作，請勿使用動詞，例如 Repair、Return、Undo 或 Fix。|
|[儲存](/dotnet/api/System.Management.Automation.VerbsData.Save)（sv）|保留資料以避免遺失。||
|[同步](/dotnet/api/System.Management.Automation.VerbsData.Sync)（sy）|確認有兩個以上的資源處於相同的狀態。|針對此動作，請勿使用動詞，例如複寫、強制執行或比對。|
|解除[發佈](/dotnet/api/System.Management.Automation.VerbsData.Unpublish)（ub）|讓其他人無法使用資源。 這個動詞會與搭配使用 `Publish` 。|針對此動作，請勿使用 [卸載]、[還原] 或 [隱藏] 等動詞。|
|[更新](/dotnet/api/System.Management.Automation.VerbsData.Update)（ud）|讓資源保持在最新狀態，以維護其狀態、精確度、一致性或合規性。 例如，Cmdlet 會 `Update-FormatData` 更新並將格式檔案新增至目前的 PowerShell 主控台。|針對此動作，請勿使用 [重新整理]、[更新]、[重新計算] 或 [重新編制索引] 等動詞。|

## <a name="diagnostic-verbs"></a>診斷動詞

PowerShell 會使用[VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)類別來定義適用于診斷的動作。 下表列出大部分定義的動詞。

|動詞（別名）|動作|註解|
|--------------------|------------|--------------|
|[Debug](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) （db）|檢查資源以診斷操作問題。|針對此動作，請勿使用動詞，例如 [診斷]。|
|[量值](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure)（毫秒）|識別指定之作業所耗用的資源，或抓取資源的相關統計資料。|針對此動作，請勿使用 [計算]、[判斷] 或 [分析] 等動詞。|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) （pi）|使用 `Test` 動詞。||
|[修復](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair)（rp）|將資源還原為可用的條件|針對此動作，請勿使用 [修正] 或 [還原] 等動詞。|
|[Resolve](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) （rv）|將資源的縮寫表示對應至更完整的標記法。|針對此動作，請不要使用如展開或判斷的動詞。|
|[測試](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test)（t）|驗證資源的作業或一致性。|針對此動作，請不要使用動詞命令，例如診斷、分析、搶救或驗證。|
|[追蹤](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace)（tr）|追蹤資源的活動。|針對此動作，請勿使用追蹤、遵循、檢查或發掘等動詞。|

## <a name="lifecycle-verbs"></a>生命週期動詞

PowerShell 會使用[VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別來定義適用于資源生命週期的動作。 下表列出大部分定義的動詞。

|動詞（別名）|動作|註解|
|--------------------|------------|--------------|
|[核准](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve)（ap）|確認或同意資源或進程的狀態。||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) （as）|Affirms 資源的狀態。|針對此動作，請勿使用指令動詞，例如「認證」。|
|[組建](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build)（bd）|從一組輸入檔（通常是原始程式碼或宣告式檔）建立成品（通常是二進位檔案或檔）|已在 PowerShell v6 中新增這個動詞|
|[完成](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0)（cp）|結束作業。||
|[確認](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm)（cn）|認可、驗證或驗證資源或進程的狀態。|針對此動作，請勿使用「認可」、「同意」、「驗證」或「驗證」等動詞。|
|[拒絕](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny)（dn）|拒絕、物件、封鎖或 opposes 資源或進程的狀態。|針對此動作，請勿使用 [區塊]、[物件]、[拒絕] 或 [拒絕] 等動詞。|
|[部署](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy)（dp）|將應用程式、網站或解決方案傳送至遠端目標 [s]，讓該解決方案的取用者能夠在部署完成後存取它|已在 PowerShell v6 中新增這個動詞|
|[停](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable)用（d）|將資源設定為無法使用或非作用中狀態。 例如，此 `Disable-PSBreakpoint` Cmdlet 會使中斷點變成非作用中。 這個動詞會與搭配使用 `Enable` 。|針對此動作，請勿使用 [停止] 或 [隱藏] 等動詞。|
|[啟用](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable)（e）|將資源設定為可用或作用中狀態。 例如，此 `Enable-PSBreakpoint` Cmdlet 會使中斷點變成作用中。 這個動詞會與搭配使用 `Disable` 。|針對此動作，請不要使用動詞，例如 Start 或 Begin。|
|[安裝](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install)（是）|將資源放在某個位置，並選擇性地將其初始化。 這個動詞會與搭配使用 `Uninstall` 。|針對此動作，請不要使用動詞命令，例如安裝程式。|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) （i）|執行動作，例如執行命令或方法。|針對此動作，請勿使用 [執行] 或 [啟動] 等動詞。|
|[Register](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) （rg）|為儲存機制（例如資料庫）中的資源建立專案。 這個動詞會與搭配使用 `Unregister` 。||
|[要求](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request)（rq）|要求資源或要求許可權。||
|[重新開機](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart)（rt）|停止作業，然後重新開機作業。 例如，此 `Restart-Service` Cmdlet 會停止並啟動服務。|針對此動作，請勿使用「回收」之類的動詞。|
|[繼續](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume)（ru）|啟動已暫止的作業。 例如，此 `Resume-Service` Cmdlet 會啟動已暫停的服務。 這個動詞會與搭配使用 `Suspend` 。||
|[啟動](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start)（sa）|起始作業。 例如，此 `Start-Service` Cmdlet 會啟動服務。 這個動詞會與搭配使用 `Stop` 。|針對此動作，請勿使用啟動、起始或開機等動詞。|
|[停止](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop)（sp）|停止活動。 這個動詞會與搭配使用 `Start` 。|針對此動作，請勿使用 End、Kill、Terminate 或 Cancel 等動詞。|
|[提交](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit)（sb）|提供要核准的資源。|針對此動作，請勿使用 Post 之類的動詞。|
|[暫停](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend)（ss）|暫停活動。 例如，此 `Suspend-Service` Cmdlet 會暫停服務。 這個動詞會與搭配使用 `Resume` 。|針對此動作，請勿使用「暫停」之類的動詞。|
|[卸載](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall)（us）|從指定的位置移除資源。 這個動詞會與搭配使用 `Install` 。||
|[取消註冊](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister)（您的）|從存放庫移除資源的專案。 這個動詞會與搭配使用 `Register` 。|針對此動作，請不要使用動詞，例如 Remove。|
|[等候](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait)（w）|暫停作業，直到指定的事件發生為止。 例如， `Wait-Job` Cmdlet 會暫停作業，直到一或多個背景工作完成為止。|針對此動作，請勿使用動詞或 Pause 這類動詞。|

## <a name="security-verbs"></a>安全性動詞

PowerShell 會使用[VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)類別來定義適用于安全性的動作。 下表列出大部分定義的動詞。

|動詞（別名）|動作|註解|
|--------------------|------------|--------------|
|[Block](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) （bl）|限制對資源的存取。 這個動詞會與搭配使用 `Unblock` 。|針對此動作，請勿使用動詞，例如 [預防]、[限制] 或 [拒絕]。|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) （gr）|允許存取資源。 這個動詞會與搭配使用 `Revoke` 。|針對此動作，請不要使用動詞，例如 [允許] 或 [啟用]。|
|[保護](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect)（pt）|保護資源免于遭受攻擊或遺失。 這個動詞會與搭配使用 `Unprotect` 。|針對此動作，請勿使用 [加密]、[保護] 或 [密封] 等動詞。|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) （rk）|指定不允許存取資源的動作。 這個動詞會與搭配使用 `Grant` 。|針對此動作，請不要使用動詞，例如移除或停用。|
|[解除封鎖](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock)（ul）|移除資源的限制。 這個動詞會與搭配使用 `Block` 。|針對此動作，請勿使用 [清除] 或 [允許] 等動詞。|
|[取消保護](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect)（up）|從已新增的資源移除保護措施，以防止它遭受攻擊或遺失。 這個動詞會與搭配使用 `Protect` 。|針對此動作，請勿使用 [解密] 或 [解除密封] 等動詞。|

## <a name="other-verbs"></a>其他動詞

PowerShell 會使用[VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)類別來定義不符合特定動詞名稱類別的標準動詞名稱，例如一般、通訊、資料、生命週期或安全性動詞名稱動詞。

|動詞（別名）|動作|註解|
|--------------------|------------|--------------|
|[使用](/dotnet/api/System.Management.Automation.VerbsOther.Use)（u）|會使用或包含資源來執行某些動作。||

## <a name="see-also"></a>另請參閱

[VerbsCommon。](/dotnet/api/System.Management.Automation.VerbsCommon)

[VerbsCommunications。](/dotnet/api/System.Management.Automation.VerbsCommunications)

[VerbsData。](/dotnet/api/System.Management.Automation.VerbsData)

[VerbsDiagnostic。](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[VerbsLifeCycle。](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[VerbsSecurity。](/dotnet/api/System.Management.Automation.VerbsSecurity)

[VerbsOther。](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet 宣告](./cmdlet-class-declaration.md)

[Windows PowerShell 程式設計人員手冊](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
