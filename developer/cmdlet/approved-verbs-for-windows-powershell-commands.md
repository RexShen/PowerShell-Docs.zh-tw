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
ms.openlocfilehash: d8a0561d6fbb4447a691c434e0518e3e16ce41e7
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56863664"
---
# <a name="approved-verbs-for-powershell-commands"></a>PowerShell 命令的已核准的動詞

PowerShell 會使用動詞-名詞 」 組個 cmdlet 的名稱和其衍生的 Microsoft.NET Framework 類別。
比方說， `Get-Command` PowerShell 所提供的 cmdlet 用以擷取註冊在 PowerShell 中的所有命令。
名稱的動詞部分會識別此 cmdlet 會執行的動作。
名稱的名詞部分會識別在其執行此動作的實體。

> [!NOTE]
> PowerShell 會使用這個詞彙*動詞*來描述表示動作，即使該文字不是一個標準動詞的英文語言的字組。
> 例如，詞彙*新增*是有效的 PowerShell 動詞名稱，因為這表示即使不在英文中的動詞命令的動作。

## <a name="verb-naming-rules"></a>動詞命令命名規則

下列清單提供您選擇的 cmdlet 名稱的動詞命令時要考量的指導方針：

* 當您指定的動詞時，我們建議您使用 PowerShell 所提供的預先定義的指令動詞名稱之一 （包含下表中的這些預先定義的動詞命令的別名）。
  當您使用預先定義的動詞命令時，您會確定您所建立的 cmdlet、 提供的 PowerShell cmdlet 與其他人所設計的 cmdlet 之間的一致性。

* 使用預先定義的動詞命令來描述一般範圍的動作，並使用參數來進一步精簡指令程式的動作。

* 若要強制所有 cmdlet 的一致性，請勿使用已核准的動詞的同義字。

* 使用本主題會列出每個動詞命令的格式。
  例如，使用"Get"，但不是會使用 「 取得 」 或 「 取得 」。

* 使用 pascal 命名法大小寫的動詞命令。
  在 依照 pascal 命名法大小寫的每個字首字母被大寫，例如"ForEach"。

* 請勿使用下列保留的動詞命令或別名。
  PowerShell 語言的一部分，或由 PowerShell 所提供的特殊案例指令程式，會使用這些動詞命令。
  - ForEach (foreach)
  - 格式 (f)
  - 群組 (gp)
  - 排序 (sr)
  - Tee (t)
  - 位置 （北）

## <a name="similar-verbs-for-different-actions"></a>類似的動詞命令，針對不同動作

以下的類似動詞會代表不同的動作。

### <a name="new-vs-set"></a>新的 vs。設定
`New`動詞命令用來建立新的資源。
`Set`動詞命令用來修改現有的資源，選擇性地建立資源，如果它不存在，例如`Set-Variable`cmdlet。

### <a name="find-vs-search"></a>尋找與。搜尋
`Find`動詞命令用來尋找物件。
`Search`動詞命令用來在容器中建立資源的參考。

### <a name="get-vs-read"></a>取得 vs。讀取
`Get`動詞命令用來擷取資源，例如檔案。
`Read`動詞命令用來從來源，例如檔案中取得資訊。

### <a name="invoke-vs-start"></a>叫用 vs。啟動
`Invoke`動詞命令用來執行的作業，通常是一項同步作業，例如執行命令。
`Start`動詞命令用來開始作業，通常是非同步作業，例如啟動處理程序。

### <a name="ping-vs-test"></a>Ping vs。Test
使用`Test`動詞命令。

## <a name="common-verbs"></a>常見的動詞命令

PowerShell 會使用[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)列舉類別，來定義可套用到幾乎任何 cmdlet 的一般動作。
下表列出了大部分的定義的動詞命令。

|動詞命令 （別名）|動作|評價|
|--------------------|------------|--------------|
|[新增](/dotnet/api/System.Management.Automation.VerbsCommon.Add)(a)|將資源加入至容器，或將項目附加至另一個項目。 比方說， `Add-Content` cmdlet 會將內容新增至檔案。 此動詞命令搭配`Remove`。|這項動作，請勿使用動詞命令，例如 Append，附加，串連或插入。|
|[清除](/dotnet/api/System.Management.Automation.VerbsCommon.Clear)(cl)|移除容器中的所有資源，但不會刪除容器。 比方說， `Clear-Content` cmdlet 會移除檔案的內容，但不會刪除檔案。|這項動作，請勿使用動詞命令，例如排清、 清除、 發行、 取消、 取消設定或設為空值。|
|[關閉](/dotnet/api/System.Management.Automation.VerbsCommon.Close)(cs)|若要讓它無法存取，無法使用，或無法使用資源的狀態變更。 此動詞命令搭配 `Open.`||
|[複製](/dotnet/api/System.Management.Automation.VerbsCommon.Copy)(cp)|另一個名稱或另一個容器，請將複製的資源。 比方說， `Copy-Item` cmdlet 用來存取儲存的資料，將項目從資料存放區中的某個位置複製到另一個位置。|這項動作，請勿使用動詞命令，例如重複、 複製、 複寫或同步處理。|
|[輸入](/dotnet/api/System.Management.Automation.VerbsCommon.Enter)(et)|指定可讓使用者將移至資源的動作。 比方說， `Enter-PSSession` cmdlet 會將使用者放在互動式工作階段。 此動詞命令搭配`Exit`。|這項動作，請勿使用動詞命令，例如推送或 Into。|
|[結束](/dotnet/api/System.Management.Automation.VerbsCommon.Exit)（例如）|將目前的環境或內容設定最近使用過的內容。 比方說， `Exit-PSSession` cmdlet 會置於用來啟動互動式工作階段的工作階段中的使用者。 此動詞命令搭配`Enter`。|這項動作，請勿使用動詞命令，例如 Pop 或相應放大。|
|[尋找](/dotnet/api/System.Management.Automation.VerbsCommon.Find)(fd)|會尋找不明、 隱含、 選擇性的或指定的容器中的物件。||
|[格式](/dotnet/api/System.Management.Automation.VerbsCommon.Format)(f)|以指定的表單或版面配置排列物件。||
|[取得](/dotnet/api/System.Management.Automation.VerbsCommon.Get)(g)|指定擷取資源的動作。 此動詞命令搭配`Set`。|這項動作，請勿使用動詞命令，例如讀取、 開啟、 Cat、 類型、 Dir、 取得、 傾印、 取得、 檢查、 尋找或搜尋此動作。|
|[隱藏](/dotnet/api/System.Management.Automation.VerbsCommon.Hide)(h)|讓資源無法偵測到。 比方說，其名稱包含隱藏動詞的 cmdlet 可能會隱藏來自使用者的服務。 此動詞命令搭配`Show`。|這項動作，請勿使用動詞命令，例如區塊。|
|[加入](/dotnet/api/System.Management.Automation.VerbsCommon.Join)(j)|將資源結合成一個資源。 比方說， `Join-Path` cmdlet 結合使用其中一個來建立單一路徑及其子路徑的路徑。 此動詞命令搭配`Split`。|這項動作，請勿使用例如結合、 Unite、 連接或關聯的動詞命令。|
|[鎖定](/dotnet/api/System.Management.Automation.VerbsCommon.Lock)(lk)|保護資源。 此動詞命令搭配`Unlock`。|這項動作，請勿使用動詞命令，例如限制或安全。|
|[移動](/dotnet/api/System.Management.Automation.VerbsCommon.Move)(m)|將資源從一個位置移到另一個。 比方說， `Move-Item` cmdlet 將項目從資料存放區中的一個位置移至另一個位置。|這項動作，請勿使用動詞命令，例如傳輸、 名稱或移轉。|
|[新](/dotnet/api/System.Management.Automation.VerbsCommon.New)(n)|建立資源。 (`Set`時建立的資源，包括資料，例如，可以也使用動詞`Set-Variable`指令程式。)|這項動作，請勿使用動詞命令，例如 Create、 產生、 組建、 樣式或配置。|
|[開啟](/dotnet/api/System.Management.Automation.VerbsCommon.Open)(op)|若要讓它可存取、 使用，或使用資源的狀態變更。 此動詞命令搭配`Close`。||
|[最佳化](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize)(om)|增加資源的效率。||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|從堆疊頂端移除項目。 比方說， `Pop-Location` cmdlet 將目前的位置變更至最近推送至堆疊的位置。||
|[推播](/dotnet/api/System.Management.Automation.VerbsCommon.Push)(pu)|將項目至堆疊的頂端。 比方說， `Push-Location` cmdlet 推送至堆疊的目前位置。||
|[重做](/dotnet/api/System.Management.Automation.VerbsCommon.Redo)(re)|重設資源狀態復原。||
|[移除](/dotnet/api/System.Management.Automation.VerbsCommon.Remove)(r)|從容器中刪除資源。 比方說， `Remove-Variable` cmdlet 會刪除變數和其值。 此動詞命令搭配`Add`。|這項動作，請勿使用這類的動詞命令為清楚、 剪下、 處置，捨棄，或清除。|
|[重新命名](/dotnet/api/System.Management.Automation.VerbsCommon.Rename)(rn)|變更資源的名稱。 比方說， `Rename-Item` cmdlet，這用來存取儲存的資料，變更的資料存放區中的項目名稱。|這項動作，請勿使用動詞命令，例如變更。|
|[重設](/dotnet/api/System.Management.Automation.VerbsCommon.Reset)(rs)|將資源設定回其原始狀態。||
|[搜尋](/dotnet/api/System.Management.Automation.VerbsCommon.Search)(sr)|在容器中建立資源的參考。|這項動作，請勿使用動詞命令，例如 [尋找] 或 [尋找]。|
|[選取](/dotnet/api/System.Management.Automation.VerbsCommon.Select)(sc)|在容器中，找出資源。 比方說， `Select-String` cmdlet 尋找字串和檔案中的文字。|這項動作，請勿使用動詞命令，例如 [尋找] 或 [尋找]。|
|[設定](/dotnet/api/System.Management.Automation.VerbsCommon.Set)(s)|取代現有的資源上的資料，或建立資源，包含某些資料。 比方說， `Set-Date` cmdlet 會變更本機電腦上的系統時間。 (`New`動詞也可用來建立資源。)此動詞命令搭配`Get`。|這項動作，請勿使用例如寫入、 重設、 指派或設定動詞命令。|
|[顯示](/dotnet/api/System.Management.Automation.VerbsCommon.Show)(sh)|讓使用者可以看見的資源。 此動詞命令搭配`Hide`。|這項動作，請勿使用例如顯示器或產生的指令動詞。|
|[略過](/dotnet/api/System.Management.Automation.VerbsCommon.Skip)(sk)|會略過一個或多個資源中一連串的點。|這項動作，請勿使用的動詞命令，例如略過或跳躍。|
|[分割](/dotnet/api/System.Management.Automation.VerbsCommon.Split)(sl)|區隔資源的組件。 比方說， `Split-Path` cmdlet 會傳回不同的組件的路徑。 此動詞命令搭配`Join`。|這項動作，請勿使用動詞命令這類不同。|
|[步驟](/dotnet/api/System.Management.Automation.VerbsCommon.Step)(st）)|移至下一個點或序列中的資源。||
|[交換器](/dotnet/api/System.Management.Automation.VerbsCommon.Switch)(sw)|指定交替使用兩個資源，例如變更兩個位置、 責任、 或狀態之間的動作。||
|[復原](/dotnet/api/System.Management.Automation.VerbsCommon.Undo)(un)|為先前的狀態設定資源。||
|[解除鎖定](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock)（英國）|釋放已鎖定的資源。 此動詞命令搭配`Lock`。|這項動作，請勿使用動詞命令，例如版本、 Unrestrict 或不安全。|
|[監看式](/dotnet/api/System.Management.Automation.VerbsCommon.Watch)(wc)|持續檢查，或監視變更的資源。||

## <a name="communications-verbs"></a>通訊動詞命令

PowerShell 會使用[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)類別來定義可套用到通訊動作。
下表列出了大部分的定義的動詞命令。

|動詞命令 （別名）|動作|評價|
|--------------------|------------|--------------|
|[連接](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect)(cc)|建立來源和目的地之間的連結。 此動詞命令搭配`Disconnect`。|這項動作，請勿使用動詞命令，例如聯結或 Telnet。|
|[中斷連線](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect)(dc)|中斷來源與目的地之間的連結。 此動詞命令搭配`Connect`。|這項動作，請勿使用動詞命令，例如中斷或登出。|
|[讀取](/dotnet/api/System.Management.Automation.VerbsCommunications.Read)(rd)|取得來源的資訊。 此動詞命令搭配`Write`。|這項動作，請勿使用取得，例如的動詞命令提示字元中，或取得。|
|[接收](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive)(rc)|接受從來源傳送的資訊。 此動詞命令搭配`Send`。|這項動作，請勿使用動詞命令，例如讀取、 接受，或查看。|
|[傳送](/dotnet/api/System.Management.Automation.VerbsCommunications.Send)(sd)|將資訊傳遞到目的地。 此動詞命令搭配`Receive`。|這項動作，請勿使用動詞命令，例如 Put、 廣播、 郵件或傳真。|
|[撰寫](/dotnet/api/System.Management.Automation.VerbsCommunications.Write)（寫入）|將資訊加入至目標。 此動詞命令搭配`Read`。|這項動作，請勿使用動詞命令，例如 Put 或列印。|

## <a name="data-verbs"></a>資料的動詞命令

PowerShell 會使用[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)類別來定義將套用至資料處理動作。
下表列出了大部分的定義的動詞命令。

|動詞命令名稱 （別名）|動作|評價|
|-------------------------|------------|--------------|
|[備份](/dotnet/api/System.Management.Automation.VerbsData.Backup)(ba)|將資料儲存進行複寫。|這項動作，請勿使用這類儲存 Burn、 複寫或同步處理的動詞命令。|
|[檢查點](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint)(ch)|建立目前狀態的資料，或其組態的快照的集。|此動作，請勿使用動詞命令，例如差異。|
|[比較](/dotnet/api/System.Management.Automation.VerbsData.Compare)(c)|評估將資料從一個資源對另一個資源的資料。|此動作，請勿使用動詞命令，例如差異。|
|[壓縮](/dotnet/api/System.Management.Automation.VerbsData.Compress)(cm)|壓縮資料的資源。 配對`Expand`。|這項動作，請勿例如 Compact 使用動詞命令。|
|[轉換](/dotnet/api/System.Management.Automation.VerbsData.Convert)(cv)|將資料從一個表示法到另一個當 cmdlet 支援雙向轉換或變更 cmdlet 支援多個資料類型之間轉換。|這項動作，請勿使用動詞命令，例如變更、 調整大小，或重新取樣。|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|將一或多個支援的輸出類型的輸入 （cmdlet 名詞表示輸入） 的一種主要類型。|這項動作，請勿使用動詞命令，例如匯出、 輸出或外。|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|從一或多個類型的輸入 （cmdlet 名詞則表示輸出型別） 的主要輸出型別轉換。|此動作，請勿使用動詞命令，例如匯入，輸入，或在。|
|[卸載](/dotnet/api/System.Management.Automation.VerbsData.Dismount)(dm)|中斷連結從某個位置的具名的實體。 此動詞命令搭配`Mount`。|這項動作，請勿使用動詞命令，例如取消掛接或取消連結。|
|[編輯](/dotnet/api/System.Management.Automation.VerbsData.Edit)(ed)|藉由新增或移除的內容修改現有的資料。|此動作，請勿使用動詞命令，例如變更、 更新或修改這項動作。|
|[展開](/dotnet/api/System.Management.Automation.VerbsData.Expand)(en)|將資源已經壓縮的資料還原至其原始狀態。 此動詞命令搭配`Compress`。|這項動作，請勿使用動詞命令，例如 Explode 或解壓縮。|
|[匯出](/dotnet/api/System.Management.Automation.VerbsData.Export)(ep)|封裝的主要輸入至永續性資料存放區，例如檔案或交換格式。 此動詞命令搭配`Import`。|這項動作，請勿使用動詞命令，例如擷取或備份。|
|[群組](/dotnet/api/System.Management.Automation.VerbsData.Group)(gp)|排列，或將一或多個資源。|這項動作，請勿使用動詞命令，例如彙總、 排列、 關聯或相互關聯。|
|[匯入](/dotnet/api/System.Management.Automation.VerbsData.Import)(ip)|從儲存在永續性資料存放區 （例如檔案），或以交換格式的資料來建立資源。 比方說， `Import-CSV` cmdlet 會將資料從逗號分隔值 (CSV) 檔案可供其他 cmdlet 的物件。 此動詞命令搭配`Export`。|這項動作，請勿使用動詞命令，例如大量載入或載入。|
|[初始化](/dotnet/api/System.Management.Automation.VerbsData.Initialize)(in)|準備的資源使用，並將其設為預設狀態。|這項動作，請勿使用動詞命令，例如清除、 Init、 更新、 重建、 重新初始化或安裝程式。|
|[限制](/dotnet/api/System.Management.Automation.VerbsData.Limit)(l)|套用到資源的條件約束。|這項動作，請勿使用動詞命令，例如配額。|
|[合併](/dotnet/api/System.Management.Automation.VerbsData.Merge)(mg)|從多個資源建立單一資源。|這項動作，請勿使用動詞命令，例如合併或聯結。|
|[掛接](/dotnet/api/System.Management.Automation.VerbsData.Mount)(mt)|將具名的實體附加至的位置。 此動詞命令搭配`Dismount`。|這項動作，請勿使用連接的動詞命令。|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|傳送的環境中的資料。 比方說， `Out-Printer` cmdlet 會將資料傳送至印表機。||
|[發行](/dotnet/api/System.Management.Automation.VerbsData.Publish)(pb)|提供資源給其他人。 此動詞命令搭配`Unpublish`。|這項動作，請勿使用動詞命令，例如部署、 版本，或安裝。|
|[還原](/dotnet/api/System.Management.Automation.VerbsData.Restore)(rr)|預先定義的狀態，例如設定的狀態設定資源`Checkpoint`。 比方說，`Restore-Computer`指令程式可啟動系統還原本機電腦上。|這項動作，請勿使用動詞命令，例如修復、 Return、 恢復或修正。|
|[儲存](/dotnet/api/System.Management.Automation.VerbsData.Save)(sv)|保留資料以避免遺失。||
|[同步處理](/dotnet/api/System.Management.Automation.VerbsData.Sync)(sy)|可確保兩個或多個資源位於相同的狀態。|這項動作，請勿使用動詞命令，例如複寫，強制轉型，或比對。|
|[解除發佈](/dotnet/api/System.Management.Automation.VerbsData.Unpublish)(ub)|使資源無法供其他人。 此動詞命令搭配`Publish`。|這項動作，請勿使用動詞命令，例如解除安裝、 還原，或隱藏。|
|[更新](/dotnet/api/System.Management.Automation.VerbsData.Update)(ud)|會維護其狀態、 精確度、 合規性或合規性的最新的資源。 比方說，`Update-FormatData`指令程式更新，並將格式化檔案新增至目前的 PowerShell 主控台。|這項動作，請勿使用動詞命令，例如重新整理、 更新、 重新計算，或重新建立索引。|

## <a name="diagnostic-verbs"></a>診斷的指令動詞

PowerShell 會使用[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)類別來定義可套用到診斷動作。
下表列出了大部分的定義的動詞命令。

|動詞命令 （別名）|動作|評價|
|--------------------|------------|--------------|
|[偵錯](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug)(db)|會檢查要診斷作業問題的資源。|這項動作，請勿使用動詞命令，例如診斷。|
|[量值](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure)（毫秒）|識別所指定的作業，耗用的資源，或擷取的資源相關的統計資料。|這項動作，請勿使用動詞命令，例如計算、 判斷或進行分析。|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|使用`Test`動詞命令。||
|[修復](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair)(rp)|將資源還原成可使用的狀況|這項動作，請勿使用動詞命令，例如修正或還原。|
|[解決](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve)(rv)|將資源的縮寫表示對應至的更完整的表示法中。|這項動作，請勿使用例如展開或判斷的動詞命令。|
|[測試](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test)(t)|請確認資源的一致性的作業。|這項動作，請勿使用動詞命令，例如診斷、 分析、 搶救或確認。|
|[追蹤](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace)(tr)|追蹤資源的活動。|這項動作，請勿使用動詞命令，例如播放軌上、 後續，檢查，或有提供。|

## <a name="lifecycle-verbs"></a>生命週期的動詞命令

PowerShell 會使用[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別來定義可套用至資源的生命週期的動作。
下表列出了大部分的定義的動詞命令。

|動詞命令 （別名）|動作|評價|
|--------------------|------------|--------------|
|[核准](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve)(ap)|確認或同意資源或處理程序的狀態。||
|[判斷提示](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert)（，）|Affirms 資源的狀態。|這項動作，請勿使用動詞命令，例如 Certify。|
|[建置](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build)(bd)|建立構件 （通常是二進位檔或文件） 的輸入檔 （通常是原始碼或宣告式的文件） 的某些集合|此動詞命令已加入 PowerShell v6|
|[完成](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0)(cp)|結束作業。||
|[確認](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm)(cn)|認可、 驗證，或驗證資源或處理程序的狀態。|這項動作，請勿使用動詞命令，例如通知、 同意、 Certify，驗證或確認。|
|[拒絕](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny)(dn)|拒絕，物件，會封鎖，或 opposes 資源或處理程序的狀態。|這項動作，請勿使用動詞命令，例如區塊中，物件、 拒絕或拒絕。|
|[部署](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy)(dp)|傳送至遠端目標 [s] 的方式，該解決方案的取用者可以存取部署完成後的應用程式、 網站或解決方案|此動詞命令已加入 PowerShell v6|
|[停用](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable)(d)|設定要為無法使用或非作用中狀態的資源。 比方說， `Disable-PSBreakpoint` cmdlet 會讓中斷點非使用中。 此動詞命令搭配`Enable`。|這項動作，請勿使用動詞命令，例如停滯或隱藏。|
|[啟用](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable)(e)|設定要使用或作用中狀態的資源。 比方說， `Enable-PSBreakpoint` cmdlet 會讓中斷點作用中。 此動詞命令搭配`Disable`。|這項動作，請勿使用動詞命令，例如啟動或開始。|
|[安裝](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install)（是）|將資源放在一個位置，並選擇性地將它初始化。 此動詞命令搭配`Uninstall`。|此動作，請執行不等安裝程式使用動詞命令。|
|[叫用](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke)(i)|執行動作，例如執行命令或方法。|這項動作，請勿使用動詞命令，例如執行或啟動。|
|[註冊](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register)(rg)|建立資源的項目，例如資料庫的儲存機制中。 此動詞命令搭配`Unregister`。||
|[要求](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request)(rq)|要求的資源，或要求權限。||
|[重新啟動](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart)(rt)|停止作業，並重新啟動它。 比方說， `Restart-Service` cmdlet 會停止，並再啟動服務。|這項動作，請勿使用動詞命令，例如回收。|
|[繼續](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume)(ru)|啟動已暫止作業。 比方說，`Resume-Service`指令程式可啟動已暫止的服務。 此動詞命令搭配`Suspend`。||
|[啟動](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start)(sa)|啟始的作業。 比方說，`Start-Service`指令程式可啟動服務。 此動詞命令搭配`Stop`。|這項動作，請勿使用動詞命令，例如啟動、 起始或開機。|
|[停止](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop)(sp)|停止活動。 此動詞命令搭配`Start`。|這項動作，請勿使用動詞命令，例如結束時，終止、 終止或取消。|
|[提交](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit)(sb)|提供核准的資源。|這項動作，請勿使用例如 Post 動詞命令。|
|[暫止](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend)(ss)|暫停活動。 比方說， `Suspend-Service` cmdlet 會暫停服務。 此動詞命令搭配`Resume`。|這項動作，請勿使用動詞命令，例如暫停。|
|[解除安裝](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall)(us)|從指定位置移除資源。 此動詞命令搭配`Install`。||
|[取消註冊](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister)（您）|從存放庫移除資源的項目。 此動詞命令搭配`Register`。|這項動作，請勿使用動詞命令，例如移除。|
|[等候](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait)(w)|指定的事件發生之前，請暫停作業。 比方說， `Wait-Job` cmdlet 會暫停作業，直到其中一個或多個背景工作已完成。|這項動作，請勿使用動詞命令，例如睡眠狀態或暫停。|

## <a name="security-verbs"></a>安全性動詞命令

PowerShell 會使用[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)類別來定義可套用到安全性動作。
下表列出了大部分的定義的動詞命令。

|動詞命令 （別名）|動作|評價|
|--------------------|------------|--------------|
|[區塊](/dotnet/api/System.Management.Automation.VerbsSecurity.Block)(bl)|會限制資源存取。 此動詞命令搭配`Unblock`。|這項動作，請勿使用例如防止、 限制或 拒絕指令動詞。|
|[授與](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant)(gr)|可讓資源的存取權。 此動詞命令搭配`Revoke`。|這項動作，請勿使用動詞命令，例如 允許 或 啟用。|
|[保護](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect)(pt)|保護從攻擊或遺失的資源。 此動詞命令搭配`Unprotect`。|這項動作，請勿使用動詞命令，例如加密、 保護、 或徽章。|
|[撤銷](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke)(rk)|指定不允許資源的存取權的動作。 此動詞命令搭配`Grant`。|這項動作，請勿使用動詞命令，例如移除或停用。|
|[解除封鎖](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock)(ul)|移除資源的限制。 此動詞命令搭配`Block`。|這項動作，請勿使用例如 清除 或 允許的動詞命令。|
|[取消保護](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect)（最多）|從已加入至防止攻擊或遺失的資源中移除的保護措施。 此動詞命令搭配`Protect`。|這項動作，請勿使用例如解密或 Unseal 的動詞命令。|

## <a name="other-verbs"></a>其他動詞命令

PowerShell 會使用[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)類別來定義不適合在一般、 通訊、 資料、 生命週期，例如特定的指令動詞名稱類別的標準動詞名稱或安全性動詞名稱動詞命令。

|動詞命令 （別名）|動作|評價|
|--------------------|------------|--------------|
|[使用](/dotnet/api/System.Management.Automation.VerbsOther.Use)(u)|使用或包含執行一些動作的資源。||

## <a name="see-also"></a>另請參閱

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[指令程式宣告](./cmdlet-class-declaration.md)

[Windows PowerShell 程式設計人員指南](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
