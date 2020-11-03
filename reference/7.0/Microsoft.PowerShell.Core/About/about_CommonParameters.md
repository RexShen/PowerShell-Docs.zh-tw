---
description: 描述可以搭配任何 Cmdlet 使用的參數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 949fabca6052a75d2cc4f8cf71e0a88b170a3b36
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207447"
---
# <a name="about-commonparameters"></a>關於 CommonParameters

## <a name="short-description"></a>簡短描述

描述可以搭配任何 Cmdlet 使用的參數。

## <a name="long-description"></a>詳細描述

一般參數是一組您可以搭配任何 Cmdlet 使用的 Cmdlet 參數。 它們是由 PowerShell 所執行，不是由 Cmdlet 開發人員所執行，而且會自動提供給任何 Cmdlet 使用。

您可以搭配任何 Cmdlet 使用一般參數，但它們可能不會影響所有 Cmdlet。 例如，如果 Cmdlet 不會產生任何詳細資訊輸出，使用 **verbose** 一般參數沒有任何作用。

一般參數也適用于使用 **CmdletBinding** 屬性或 **參數** 屬性的 advanced 函數。

數個常見參數會覆寫您使用 PowerShell 喜好設定變數設定的系統預設值或喜好設定。 和喜好設定變數不同的是，一般參數只會影響使用它們的命令。

如需詳細資訊，請參閱 [about_Preference_Variables](./about_Preference_Variables.md)。

下列清單顯示一般參數。 其別名會列在括弧中。

- **Debug** (db)
- **ErrorAction** (ea) 
- **ErrorVariable** (ev) 
- **InformationAction** (infa) 
- **可使用 informationvariable** (iv) 
- **OutVariable** (ov) 
- **OutBuffer** (ob) 
- **PipelineVariable** (pv) 
- **Verbose** (vb) 
- **WarningAction** (wa) 
- **WarningVariable** (wv) 

**動作** 參數是 **ActionPreference** 類型值。
**ActionPreference** 是具有下列值的列舉：

| Name             | 值 |
|------------------|-------|
| 暫止          | 5     |
| 略過           | 4     |
| 詢問          | 3     |
| 繼續         | 2     |
| 停止             | 1     |
| SilentlyContinue | 0     |

您可以使用名稱或值搭配參數。

除了一般參數之外，許多 Cmdlet 也提供風險降低參數。 牽涉到系統或使用者資料風險的 Cmdlet 通常會提供這些參數。

風險降低的參數包括：

- **WhatIf** (wi-fi) 
- **確認** (cf) 

### <a name="common-parameter-descriptions"></a>一般參數描述

#### <a name="debug"></a>偵錯

顯示命令所執行之作業的程式設計人員層級詳細資料。 只有當命令產生調試訊息時，此參數才有效。 例如，當命令包含 Cmdlet 時，此參數會運作 `Write-Debug` 。

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

根據預設，不會顯示偵錯工具訊息，因為變數的值 `$DebugPreference` 是 **SilentlyContinue** 。

在互動模式中， **Debug** 參數會覆寫 `$DebugPreference` 目前命令的變數值，並將的值設定 `$DebugPreference` 為 **Inquire** 。

在非互動模式中， **Debug** 參數會覆寫 `$DebugPreference` 目前命令的變數值，將的值設定 `$DebugPreference` 為 **Continue** 。

`-Debug:$true` 的效果與相同 `-Debug` 。 `-Debug:$false`當 `$DebugPreference` 不是 **SilentlyContinue** （這是預設值）時，使用來抑制偵錯工具訊息的顯示。

#### <a name="erroraction"></a>ErrorAction

決定 Cmdlet 如何回應來自命令的非終止錯誤。
此參數只適用于命令產生非終止錯誤，例如來自 Cmdlet 的錯誤 `Write-Error` 。

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

**ErrorAction** 參數會覆寫 `$ErrorActionPreference` 目前命令的變數值。 因為變數的預設值 `$ErrorActionPreference` 為 **Continue** ，所以會顯示錯誤訊息並繼續執行，除非您使用 **ErrorAction** 參數。

**ErrorAction** 參數不會影響終止錯誤 (例如遺漏資料、不正確參數或許可權不足) 導致命令無法順利完成。

`-ErrorAction:Continue` 顯示錯誤訊息，並繼續執行命令。 `Continue` 是預設值。

`-ErrorAction:Ignore` 隱藏錯誤訊息，並繼續執行命令。 不同于 **SilentlyContinue** ， **Ignore** 不會將錯誤訊息加入至 `$Error` 自動變數。 **忽略** 值是在 PowerShell 3.0 中引進。

`-ErrorAction:Inquire` 顯示錯誤訊息，並在繼續執行之前提示您確認。 此值很少使用。

`-ErrorAction:SilentlyContinue` 隱藏錯誤訊息，並繼續執行命令。

`-ErrorAction:Stop` 顯示錯誤訊息，並停止執行命令。

`-ErrorAction:Suspend` 僅適用于 PowerShell 6 和以上版本中不支援的工作流程。

> [!NOTE]
> **ErrorAction** 參數會覆寫，但在 `$ErrorAction` 命令中使用參數來執行腳本或函式時，不會取代喜好設定變數的值。

#### <a name="errorvariable"></a>ErrorVariable

**ErrorVariable** 會將命令相關的錯誤訊息儲存在指定的變數和 `$Error` 自動變數中。 如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

根據預設，新的錯誤訊息會覆寫已儲存在變數中的錯誤訊息。 若要將錯誤訊息附加至變數內容，請在 `+` 變數名稱之前輸入加號 () 。

例如，下列命令 `$a` 會建立變數，然後在其中儲存任何錯誤：

```powershell
Get-Process -Id 6 -ErrorVariable a
```

下列命令會將任何錯誤訊息新增至 `$a` 變數：

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

下列命令會顯示的內容 `$a` ：

```powershell
$a
```

您可以使用這個參數來建立只包含來自特定命令之錯誤訊息的變數，而不會影響 `$Error` 自動變數的行為。 `$Error`自動變數包含會話中所有命令的錯誤訊息。 您可以使用陣列標記法（例如 `$a[0]` 或） `$error[1,2]` 來參考儲存在變數中的特定錯誤。

> [!NOTE]
> 自訂錯誤變數包含命令所產生的所有錯誤，包括呼叫嵌套函數或腳本的錯誤。

#### <a name="informationaction"></a>InformationAction

在 PowerShell 5.0 中引進。 在使用它的命令或腳本內， **InformationAction** 一般參數會覆寫 `$InformationPreference` 喜好設定變數的值，此值預設會設定為 **SilentlyContinue** 。 當您 `Write-Information` 在腳本中使用 **InformationAction** 時， `Write-Information` 會根據 **InformationAction** 參數的值顯示值。 如需的詳細資訊 `$InformationPreference` ，請參閱 [about_Preference_Variables](./about_Preference_Variables.md)。

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

`-InformationAction:Stop` 在命令出現時停止命令或腳本 `Write-Information` 。

`-InformationAction:Ignore` 抑制參考用訊息，並繼續執行命令。 不同于 **SilentlyContinue** ，請 **略** 過完全忘記密碼的告知性訊息;它不會將參考用訊息新增至資訊串流。

`-InformationAction:Inquire` 顯示您在命令中指定的參考用訊息 `Write-Information` ，然後詢問您是否要繼續。

`-InformationAction:Continue` 顯示資訊訊息，並繼續執行。

`-InformationAction:Suspend` PowerShell Core 不受支援，因為它僅適用于工作流程。

`-InformationAction:SilentlyContinue` 沒有任何作用，因為參考用訊息不 (預設) 顯示，腳本會繼續執行而不會中斷。

> [!NOTE]
> **InformationAction** 參數會覆寫，但在 `$InformationAction` 命令中使用參數來執行腳本或函式時，不會取代喜好設定變數的值。

#### <a name="informationvariable"></a>可使用 informationvariable

在 PowerShell 5.0 中引進。 在使用它的命令或腳本內， **可使用 informationvariable** 一般參數會將字串儲存在變數中，而您可以藉由新增命令來指定該字串 `Write-Information` 。 `Write-Information` 系統會根據 **InformationAction** 一般參數的值來顯示值;如果您未加入 **InformationAction** 一般參數，則 `Write-Information` 會根據喜好設定變數的值來顯示字串 `$InformationPreference` 。 如需的詳細資訊 `$InformationPreference` ，請參閱 [about_Preference_Variables](./about_Preference_Variables.md)。

> [!NOTE]
> 資訊變數包含命令所產生的所有資訊訊息，包括呼叫嵌套函數或腳本的資訊訊息。

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a>OutBuffer

決定在透過管線傳送任何物件之前，要在緩衝區中累積的物件數目。 如果您省略此參數，則會在產生物件時傳送物件。

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

此資源管理參數是針對 advanced 使用者所設計。 當您使用此參數時，PowerShell 會以批次方式將資料傳送至下一個 Cmdlet `OutBuffer + 1` 。

下列範例替代項 `ForEach-Object` 會顯示使用此 Cmdlet 的進程區塊 `Write-Host` 。 顯示會以2或的批次方式來替代 `OutBuffer + 1` 。

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a>OutVariable

除了透過管線傳送輸出外，還會將命令中的輸出物件儲存在指定的變數中。

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

若要將輸出新增至變數，而不是取代任何可能已儲存在該處的輸出，請在 `+` 變數名稱之前輸入加號 () 。

例如，下列命令 `$out` 會建立變數，並將處理常式物件儲存在其中：

```powershell
Get-Process PowerShell -OutVariable out
```

下列命令會將處理常式物件新增至 `$out` 變數：

```powershell
Get-Process iexplore -OutVariable +out
```

下列命令會顯示變數的內容 `$out` ：

```powershell
$out
```

> [!NOTE]
> **OutVariable** 參數所建立的變數是 `[System.Collections.ArrayList]` 。

#### <a name="pipelinevariable"></a>PipelineVariable

當任何命名命令流經管線時， **PipelineVariable** 會將目前的管線元素值儲存為變數。

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

有效的值是字串，與任何變數名稱的值相同。

以下是 **PipelineVariable** 運作方式的範例。 在此範例中， **PipelineVariable** 參數會加入至 `Foreach-Object` 命令，以將命令的結果儲存在變數中。 從1到10的數位範圍會輸送到第一個 `Foreach-Object` 命令，其結果會儲存在名為 **Left** 的變數中。

第一個命令的結果 `Foreach-Object` 會輸送到第二個 `Foreach-Object` 命令，以篩選第一個命令所傳回的物件 `Foreach-Object` 。 第二個命令的結果會儲存在名為 **Right** 的變數中。

第三 `Foreach-Object` 個命令 `Foreach-Object` 會使用乘法運算子來處理前兩個輸送命令的結果（由 **左** 和 **右** 變數所表示）。 此命令會指示在 **左右** 變數中儲存的物件要相乘 **，並指定** 結果應顯示為「左範圍成員 * 右範圍成員 = 產品」。

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a>「詳細資訊」

顯示命令所執行之操作的詳細資訊。 這項資訊與追蹤或交易記錄檔中的資訊類似。 此參數只適用于命令產生詳細訊息時。 例如，當命令包含 Cmdlet 時，此參數會運作 `Write-Verbose` 。

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

**Verbose** 參數會覆寫 `$VerbosePreference` 目前命令的變數值。 因為變數的預設值 `$VerbosePreference` 是 **SilentlyContinue** ，所以預設不會顯示詳細訊息。

`-Verbose:$true` 的效果與 `-Verbose`

`-Verbose:$false` 抑制詳細資訊訊息的顯示。 當 `$VerbosePreference` (預設) 不會 **SilentlyContinue** 的值時，請使用此參數。

#### <a name="warningaction"></a>WarningAction

決定 Cmdlet 如何回應命令的警告。 [ **繼續** ] 是預設值。 只有當命令產生警告訊息時，此參數才有效。 例如，當命令包含 Cmdlet 時，此參數會運作 `Write-Warning` 。

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

**WarningAction** 參數會覆寫 `$WarningPreference` 目前命令的變數值。 因為變數的預設值 `$WarningPreference` 為 **Continue** ，所以會顯示警告並繼續執行，除非您使用 **WarningAction** 參數。

`-WarningAction:Continue` 顯示警告訊息，並繼續執行命令。 `Continue` 是預設值。

`-WarningAction:Inquire` 顯示警告訊息，並在繼續執行之前提示您確認。 此值很少使用。

`-WarningAction:SilentlyContinue` 隱藏警告訊息，並繼續執行命令。

`-WarningAction:Stop` 顯示警告訊息，並停止執行命令。

> [!NOTE]
> **WarningAction** 參數會覆寫，但在 `$WarningAction` 命令中使用參數來執行腳本或函式時，不會取代喜好設定變數的值。

#### <a name="warningvariable"></a>WarningVariable

將命令相關警告儲存在指定的變數中。

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

所有產生的警告都會儲存在變數中，即使這些警告不會顯示給使用者。

若要將警告附加至變數內容，而不是取代任何可能已儲存在該處的警告，請在 `+` 變數名稱之前輸入加號 () 。

例如，下列命令 `$a` 會建立變數，並在其中儲存任何警告：

```powershell
Get-Process -Id 6 -WarningVariable a
```

下列命令會將任何警告新增至 `$a` 變數：

```powershell
Get-Process -Id 2 -WarningVariable +a
```

下列命令會顯示的內容 `$a` ：

```powershell
$a
```

您可以使用這個參數來建立只包含特定命令之警告的變數。 您可以使用陣列標記法（例如 `$a[0]` 或） `$warning[1,2]` 來參考儲存在變數中的特定警告。

> [!NOTE]
> 警告變數包含命令所產生的所有警告，包括呼叫嵌套函數或腳本的警告。

### <a name="risk-management-parameter-descriptions"></a>風險管理參數描述

#### <a name="whatif"></a>WhatIf

顯示描述命令效果的訊息，而不是執行命令。

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

**WhatIf** 參數會覆寫 `$WhatIfPreference` 目前命令的變數值。 因為變數的預設值 `$WhatIfPreference` 為 0 (停用) ，所以不會在沒有 **whatif** 參數的情況下執行 **whatif** 行為。 如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)

`-WhatIf:$true` 的效果與相同 `-WhatIf` 。

`-WhatIf:$false` 隱藏變數的值為1時，所產生的自動 WhatIf 行為 `$WhatIfPreference` 。

例如，下列命令會 `-WhatIf` 在命令中使用參數 `Remove-Item` ：

```powershell
Remove-Item Date.csv -WhatIf
```

PowerShell 不會移除該專案，而是會列出其所進行的作業，以及會受影響的專案。 此命令會產生下列輸出：

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a>確認

在執行命令之前提示您確認。

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

**Confirm** 參數會覆寫 `$ConfirmPreference` 目前命令的變數值。 預設值為 true。 如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)

`-Confirm:$true` 的效果與相同 `-Confirm` 。

`-Confirm:$false` 抑制自動確認，這會在的值 `$ConfirmPreference` 小於或等於 Cmdlet 的預估風險時發生。

例如，下列命令會搭配命令使用 **Confirm** 參數 `Remove-Item` 。 在移除專案之前，PowerShell 會列出其所進行的作業，以及會受影響的專案，並要求核准。

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

確認回應選項如下所示：

|回應       |結果                                                     |
|---------------|-----------------------------------------------------------|
|是 (Y)         |執行動作。                                        |
|是所有 ()  |執行所有動作並隱藏後續的確認查詢|
|               |適用于此命令。                                          |
|無 (N) ：        |請勿執行此動作。                                 |
|所有 (L) ： |請勿執行任何動作，並隱藏後續的確認 |
|               |此命令的查詢。                                  |
|暫止 (S) ：   |暫停命令並建立暫時會話。          |
|協助 (？ )        |顯示這些選項的說明。                            |

**暫** 止選項會將命令放在保留位置，並建立暫時的嵌套會話，讓您可以在準備好選擇 **確認** 選項之前工作。 嵌套會話的命令提示字元有兩個額外的游標 ( # A2) ，表示它是原始父命令的子系操作。 您可以在嵌套的會話中執行命令和腳本。 若要結束嵌套會話並返回原始命令的 Confirm 選項，請輸入 "exit"。

在下列範例中，當使用者檢查命令參數的說明時，會使用 **暫停** 選項 (S) 來暫時中止命令。 取得所需的資訊之後，使用者會輸入 "exit" 來結束嵌套提示字元，然後選取 [是] (y) 回應至 [確認] 查詢。

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a>關鍵 字

about_Common_Parameters

## <a name="see-also"></a>另請參閱

[about_Preference_Variables](about_Preference_Variables.md)

[Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)

[Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)

[Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error)

[Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
