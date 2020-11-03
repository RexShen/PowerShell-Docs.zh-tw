---
description: 描述如何在 PowerShell 中管理交易的作業。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_transactions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Transactions
ms.openlocfilehash: 522e0f727754b0b0153571039f3bf3966d0abf20
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207527"
---
# <a name="about-transactions"></a>關於交易

## <a name="short-description"></a>簡短描述

描述如何在 PowerShell 中管理交易的作業。

## <a name="long-description"></a>詳細描述

從 PowerShell 2.0 開始，PowerShell 支援交易。 這項功能可讓您啟動交易、指出哪些命令是交易的一部分，以及認可或回復交易。

## <a name="about-transactions"></a>關於交易

在 PowerShell 中，交易是一組一或多個以邏輯單元形式管理的命令。 交易可以 ( 「已認可」 ) 來完成，這會變更受交易影響的資料。 或者，交易可以完全復原 ( 「已復原」 ) ，讓交易不會變更受影響的資料。

由於交易中的命令是以一個單位來管理，因此會認可所有命令，否則會回復所有命令。

交易廣泛用於資料處理，最值得注意的是資料庫作業和財務交易。 當一組命令的最糟案例不是它們都失敗時，最常使用交易，但有些命令會在其他命令失敗時成功，讓系統處於損毀、假或 uninterpretable 狀態，而難以修復。

## <a name="transaction-cmdlets"></a>TRANSACTION CMDLET

PowerShell 包含數個專為管理交易而設計的 Cmdlet。

- Start-Transaction：啟動新的交易。
- 使用-Transaction：將命令或運算式加入至交易。 命令必須使用已啟用交易的物件。
- 恢復交易：回復交易，讓交易不會變更任何資料。
- Complete-Transaction：認可交易。 受交易影響的資料會變更。
- 取得交易：取得使用中交易的相關資訊。

如需交易 Cmdlet 的清單，請輸入：

```powershell
get-command *transaction
```

如需 Cmdlet 的詳細資訊，請輸入：

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a>啟用交易的元素

若要參與交易，Cmdlet 和提供者都必須支援交易。 這項功能內建于受交易影響的物件。

PowerShell 登錄提供者支援 Windows Vista 中的交易。 TransactedString 物件 (TransactedString) 可搭配任何執行 PowerShell 的作業系統使用。

其他 PowerShell 提供者可支援交易。 若要在您的會話中尋找支援交易的 PowerShell 提供者，請使用下列命令，在提供者的 [功能] 屬性中尋找「交易」值：

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

如需提供者的詳細資訊，請參閱提供者的說明。 若要取得提供者說明，請輸入：

```
get-help <provider-name>
```

例如，若要取得登錄提供者的說明，請輸入：

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a>USETRANSACTION 參數

可支援交易的 Cmdlet 具有 UseTransaction 參數。 此參數包含使用中交易中的命令。 您可以使用完整的參數名稱或其別名 "usetx"。

只有當會話包含使用中的交易時，才能使用此參數。 如果您在沒有使用中交易時輸入具有 UseTransaction 參數的命令，則命令會失敗。

若要使用 UseTransaction 參數尋找 Cmdlet，請輸入：

```powershell
get-help * -parameter UseTransaction
```

在 PowerShell core 中，設計來搭配 PowerShell 提供者使用的所有 Cmdlet 都支援交易。 因此，您可以使用提供者 Cmdlet 來管理交易。

如需 PowerShell 提供者的詳細資訊，請參閱 [about_Providers](about_Providers.md)。

## <a name="the-transaction-object"></a>TRANSACTION 物件

交易會以 PowerShell 以交易對象（即 transaction）表示。

此物件具有下列屬性：

- RollbackPreference：包含目前交易的復原喜好設定集。 當您使用 Start-Transaction 啟動交易時，可以設定復原喜好設定。

  復原喜好設定會決定自動回復交易的條件。 有效值為 Error、TerminatingError 和 Never。 預設值為 Error。

- 狀態：包含交易的目前狀態。 有效的值為作用中、已認可和 RolledBack。

- SubscriberCount：包含交易的訂閱者數目。 當您在另一個交易正在進行時，當您啟動交易時，便會將「訂閱者」新增至交易。 訂閱者認可交易時，訂閱者計數會遞減。

## <a name="active-transactions"></a>使用中交易

在 PowerShell 中，一次只能有一個作用中的交易，而且您只能管理使用中的交易。 相同會話中的多個交易可以同時進行，但只有最新啟動的交易處於作用中狀態。

因此，當您使用 transaction Cmdlet 時，無法指定特定的交易。 命令一律適用于使用中的交易。

這在 Get-Transaction Cmdlet 的行為中最明顯。 當您輸入 Get-Transaction 命令時，Get-Transaction 一律只會取得一個交易對象。 此物件是代表使用中交易的物件。

若要管理不同的交易，您必須先認可或回復使用中的交易，才能完成該交易。 當您這樣做時，先前的交易就會自動變成使用中狀態。 交易會以啟動的順序反轉，使最近啟動的交易一律為使用中狀態。

## <a name="subscribers-and-independent-transactions"></a>訂閱者與獨立交易

如果您在另一個交易正在進行時啟動交易，則 PowerShell 預設不會啟動新的交易。 相反地，它會將「訂閱者」新增至目前的交易。

當交易有多個訂閱者時，在任何時間點的單一 Undo-Transaction 命令都會針對所有訂閱者回復整個交易。 不過，若要認可交易，您必須為每個訂閱者輸入 Complete-Transaction 命令。

若要尋找交易的訂閱者數目，請檢查交易對象的 SubscriberCount 屬性。 例如，下列命令會使用 Get-Transaction Cmdlet 來取得使用中交易的 SubscriberCount 屬性值：

```powershell
(Get-Transaction).SubscriberCount
```

加入訂閱者是預設行為，因為另一個交易正在進行時所啟動的大部分交易都與原始交易相關。 在一般模型中，包含交易的腳本會呼叫包含其本身交易的 helper 腳本。 因為交易是相關的，所以應該將它們回復或作為一個單位來認可。

不過，您可以使用 Start-Transaction Cmdlet 的獨立參數，來啟動與目前交易無關的交易。

當您啟動獨立的交易時，Start-Transaction 會建立新的交易對象，而新的交易就會變成使用中的交易。
您可以認可或回復獨立交易，而不會影響原始交易。

當獨立交易完成 (認可或復原) 時，原始交易會再次成為使用中交易。

## <a name="changing-data"></a>變更資料

當您使用交易來變更資料時，在認可交易之前，將不會變更受交易影響的資料。 不過，相同的資料也可以由不屬於交易一部分的命令變更。

當您使用交易來管理共用資料時，請記住這一點。
一般而言，資料庫具有在您處理資料時鎖定資料的機制，可防止其他使用者和其他命令、腳本和函式進行變更。

但是，鎖定是資料庫的一項功能。 它與交易無關。 如果您是在已啟用交易的檔案系統或其他資料存放區中工作，則可以在交易進行時變更資料。

## <a name="examples"></a>範例

本節中的範例會使用 PowerShell 登錄提供者，並假設您已熟悉它。 如需登錄提供者的相關資訊，請輸入 "get-help Registry"。

### <a name="example-1-committing-a-transaction"></a>範例1：認可交易

若要建立交易，請使用 Start-Transaction Cmdlet。 下列命令會以預設設定啟動交易。

```powershell
start-transaction
```

若要在交易中包含命令，請使用 Cmdlet 的 UseTransaction 參數。 根據預設，命令不會包含在交易中，

例如，下列命令會將 HKCU：磁片磁碟機的軟體金鑰中的目前位置設定為不包含在交易中。

```powershell
cd hkcu:\Software
```

下列命令會建立 MyCompany 索引鍵，並使用 New-Item Cmdlet 的 UseTransaction 參數，將命令包含在使用中的交易中。

```powershell
new-item MyCompany -UseTransaction
```

此命令會傳回代表新索引鍵的物件，但是因為此命令是交易的一部分，所以登錄尚未變更。

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

若要認可交易，請使用 Complete-Transaction Cmdlet。 因為它一律會影響使用中的交易，所以您無法指定交易。

```powershell
complete-transaction
```

如此一來，就會將 MyCompany 金鑰新增至登錄中。

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-2-rolling-back-a-transaction"></a>範例2：回復交易

若要建立交易，請使用 Start-Transaction Cmdlet。 下列命令會以預設設定啟動交易。

```powershell
start-transaction
```

下列命令會建立 MyOtherCompany 索引鍵，並使用 New-Item Cmdlet 的 UseTransaction 參數，將命令包含在使用中的交易中。

```powershell
new-item MyOtherCompany -UseTransaction
```

此命令會傳回代表新索引鍵的物件，但是因為此命令是交易的一部分，所以登錄尚未變更。

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

若要回復交易，請使用 Undo-Transaction Cmdlet。 因為它一律會影響使用中的交易，所以您未指定交易。

```powershell
Undo-transaction
```

結果是 MyOtherCompany 機碼不會新增至登錄。

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-3-previewing-a-transaction"></a>範例3：預覽交易

通常，交易中使用的命令會變更資料。 不過，取得資料的命令也可用於交易中，因為它們會取得交易內的資料。 這會提供認可交易之變更的預覽。

下列範例示範如何使用 Get-ChildItem 命令 (別名是 "dir" ) 來預覽交易中的變更。

下列命令會啟動交易。

```powershell
start-transaction
```

下列命令使用 New-ItemProperty Cmdlet 將 MyKey 登錄專案新增至 MyCompany 機碼。 此命令會使用 UseTransaction 參數將命令包含在交易中。

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

此命令會傳回代表新登錄專案的物件，但不會變更登錄專案。

```
MyKey
-----
123
```

若要取得目前在登錄中的專案，請在不使用 UseTransaction 參數的情況下，使用 Get-ChildItem 命令 ( "dir" ) 。 下列命令會取得以 "M" 為開頭的專案。

```powershell
dir m*
```

結果顯示尚未將任何專案加入至 MyCompany 索引鍵。

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

若要預覽認可交易的效果，請使用 UseTransaction 參數輸入 Get-ChildItem ( "dir" ) 命令。 此命令會查看交易內的資料。

```powershell
dir m* -useTransaction
```

結果顯示，如果認可交易，則 MyKey 專案會新增至 MyCompany 索引鍵。

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a>範例4：合併交易與非交易命令

您可以在交易期間輸入非交易命令。 非交易命令會立即影響資料，但不會影響交易。
下列命令會在 HKCU： \ Software 登錄機碼中啟動交易。

```powershell
start-transaction
```

接下來的三個命令會使用 New-Item Cmdlet，將金鑰新增至登錄。
第一個和第三個命令使用 UseTransaction 參數將命令包含在交易中。 第二個命令會省略參數。 因為第二個命令未包含在交易中，所以它會立即生效。

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

若要查看登錄的目前狀態，請使用 Get-ChildItem ( "dir" ) 命令，而不使用 UseTransaction 參數。 此命令會取得以 "M" 為開頭的專案。

```powershell
dir m*
```

結果會顯示 MyCompany2 索引鍵已新增至登錄，但不會新增 MyCompany1 和 MyCompany3 索引鍵（屬於交易的一部分）。

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

下列命令會認可交易。

```powershell
complete-transaction
```

現在，新增為交易一部分的金鑰會出現在登錄中。

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
83   1 Microsoft                      {(default)}
0    0 MyCompany1                     {}
0    0 MyCompany2                     {}
0    0 MyCompany3                     {}
```

### <a name="example-5-using-automatic-rollback"></a>範例5：使用自動回復

當交易中的命令產生任何種類的錯誤時，就會自動回復交易。

此預設行為是針對執行交易的腳本所設計。 腳本通常經過妥善測試，並包含錯誤處理邏輯，因此不會發生錯誤，而且應該終止交易。

第一個命令會在 HKCU： \ Software 登錄機碼中啟動交易。

```powershell
start-transaction
```

下列命令使用 New-Item Cmdlet 將 MyCompany 機碼新增至登錄。 此命令會使用 UseTransaction 參數 (別名是 "usetx" ) 將命令包含在交易中。

```powershell
New-Item MyCompany -UseTX
```

因為 MyCompany 索引鍵已經存在於登錄中，所以命令會失敗，並回復交易。

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

Get-Transaction 命令會確認交易已回復，且 SubscriberCount 為0。

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a>範例6：變更復原喜好設定

如果您希望交易更有容錯能力，可以使用 Start-Transaction 的 RollbackPreference 參數來變更喜好設定。

下列命令會啟動復原喜好設定為 "Never" 的交易。

```powershell
start-transaction -rollbackpreference Never
```

在此情況下，當命令失敗時，不會自動回復交易。

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

因為交易仍在使用中，所以您可以將命令重新提交為交易的一部分。

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a>範例7：使用使用-TRANSACTION CMDLET

Use-Transaction Cmdlet 可讓您針對已啟用交易的 Microsoft .NET Framework 物件執行直接腳本處理。 Use-Transaction 會採用只能包含命令的腳本區塊，以及使用啟用交易 .NET Framework 物件的運算式，例如 TransactedString 類別的實例。

下列命令會啟動交易。

```powershell
start-transaction
```

下列 New-Object 命令會建立 TransactedString 類別的實例，並將它儲存在 $t 變數中。

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

下列命令會使用 TransactedString 物件的 Append 方法將文字新增至字串。 因為此命令不是交易的一部分，所以變更會立即生效。

```powershell
$t.append("Windows")
```

下列命令使用相同的 Append 方法來加入文字，但它會將文字新增為交易的一部分。 此命令會以大括弧括住，並設定為使用-Transaction 的 ScriptBlock 參數值。 需要 (UseTx) 的 UseTransaction 參數。

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

若要查看 $t 中交易字串的目前內容，請使用 TransactedString 物件的 ToString 方法。

```powershell
$t.tostring()
```

輸出顯示只有非交易的變更會生效。

```output
Windows
```

若要從交易內查看 $t 中交易字串的目前內容，請在 Use-Transaction 命令中內嵌運算式。

```powershell
use-transaction {$s.tostring()} -usetx
```

輸出會顯示交易視圖。

```output
PowerShell
```

下列命令會認可交易。

```powershell
complete-transaction
```

若要查看最終字串：

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a>範例8：管理多訂閱者交易

當您在另一個交易正在進行時啟動交易時，PowerShell 預設不會建立第二筆交易。 相反地，它會將訂閱者加入目前的交易。

此範例顯示如何查看和管理多訂閱者交易。

從在 HKCU： \ Software 金鑰中啟動交易開始。

```powershell
start-transaction
```

下列命令使用 Get-Transaction 命令來取得使用中的交易。

```powershell
get-transaction
```

結果會顯示代表使用中交易的物件。

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

下列命令會將 MyCompany 機碼新增至登錄。 此命令會使用 UseTransaction 參數將命令包含在交易中。

```powershell
new-item MyCompany -UseTransaction
```

下列命令使用 Start-Transaction 命令來啟動交易。 雖然此命令是在命令提示字元中輸入的，但當您執行包含交易的腳本時，可能會發生此情況。

```powershell
start-transaction
```

Get-Transaction 命令顯示交易對象上的訂閱者計數會遞增。 值現在是2。

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

下一個命令會使用 New-ItemProperty Cmdlet 將 MyKey 登錄專案新增至 MyCompany 機碼。 它會使用 UseTransaction 參數將命令包含在交易中。

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

MyCompany 索引鍵不存在於登錄中，但此命令會成功，因為這兩個命令是相同交易的一部分。

下列命令會認可交易。 如果回復交易，則會針對所有訂閱者回復交易。

```powershell
complete-transaction
```

Get-Transaction 命令顯示交易對象上的訂閱者計數為1，但狀態的值仍處於作用中， (未認可) 。

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

若要完成認可交易，請輸入第二個完整交易命令。 若要認可多訂閱者交易，您必須為每個 Start-Transaction 命令輸入一個 Complete-Transaction 命令。

```powershell
complete-transaction
```

另一個 Get-Transaction 命令顯示交易已認可。

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a>範例9：管理獨立交易

當您在另一個交易正在進行時啟動交易時，您可以使用 Start-Transaction 的獨立參數，讓新交易與原始交易無關。

當您這樣做時，Start-Transaction 會建立新的交易對象，並讓新交易成為使用中的交易。

從在 HKCU： Software 金鑰中啟動交易開始 \\ 。

```powershell
start-transaction
```

下列命令使用 Get-Transaction 命令來取得使用中的交易。

```powershell
get-transaction
```

結果會顯示代表使用中交易的物件。

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

下列命令會將 MyCompany 登錄機碼新增為交易的一部分。 它會使用 UseTransaction 參數 (UseTx) 將命令包含在使用中的交易中。

```powershell
new-item MyCompany -use
```

下列命令會啟動新的交易。 此命令會使用獨立參數，表示此交易不是使用中交易的訂閱者。

```powershell
start-transaction -independent
```

當您建立獨立的交易時，最近建立的新 () 交易會成為使用中的交易。 您可以使用 Get-Transaction 命令來取得使用中的交易。

```powershell
get-transaction
```

請注意，交易的 SubscriberCount 是1，表示沒有其他訂閱者，而且交易是新的。

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

必須先完成新交易 (認可或復原) ，才能管理原始交易。

下列命令會將 MyOtherCompany 機碼新增至登錄。 它會使用 UseTransaction 參數 (UseTx) 將命令包含在使用中的交易中。

```powershell
new-item MyOtherCompany -usetx
```

現在，回復交易。 如果有兩個訂閱者的單一交易，回復交易會針對所有訂閱者回復整個交易。

不過，因為這些交易是獨立的，所以回復最新的交易會取消登錄的變更，並讓原始交易成為使用中的交易。

```powershell
undo-transaction
```

Get-Transaction 命令會確認原始交易在會話中仍為使用中狀態。

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

下列命令會認可使用中交易。

```powershell
complete-transaction
```

Get-ChildItem 命令顯示登錄已經變更。

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

## <a name="see-also"></a>另請參閱

[Start-Transaction](xref:Microsoft.PowerShell.Management.Start-Transaction)

[Get-Transaction](xref:Microsoft.PowerShell.Management.Get-Transaction)

[Complete-Transaction](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[Undo-Transaction](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[Use-Transaction](xref:Microsoft.PowerShell.Management.Use-Transaction)

[Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[about_Providers](about_Providers.md)
