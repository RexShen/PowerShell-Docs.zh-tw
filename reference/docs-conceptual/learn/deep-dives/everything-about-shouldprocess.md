---
title: 您想知道有關於 ShouldProcess 的一切 (英文)
description: ShouldProcess 是一項經常遭到忽視的重要功能。 WhatIf 和 Confirm 參數可讓您輕鬆地將這項功能新增至您的函式。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 6bd4dbd5255203f2daf804163aa2a84d992d6697
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469730"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a>您想知道有關於 ShouldProcess 的一切 (英文)

PowerShell 函式有多項功能，可大幅改善使用者與其互動的方式。
經常遭到忽視的一項重要功能是 `-WhatIf` 和 `-Confirm` 支援，而且這項功能可以很輕鬆地新增至您的函式。 在本文中，我們將深入探討如何實作這項功能。

> [!NOTE]
> 本文的[原始版本][]出自 [@KevinMarquette][] 所撰寫的部落格。 PowerShell 小組感謝 Kevin 分享的內容。 請前往 [PowerShellExplained.com][] 瀏覽他的部落格。

這是您可以在函式中啟用的簡單功能，為需要的使用者提供安全的網路。 沒有什麼會比第一次執行您知道可能會有危險的命令更可怕的。 選擇使用 `-WhatIf` 執行命令，會有很大的差異。

## <a name="commonparameters"></a>CommonParameters

在探討如何執行這些 [常見的][] 參數之前，我想要快速瞭解它們的使用方式。

## <a name="using--whatif"></a>使用 -WhatIf

當命令支援 `-WhatIf` 參數時，可讓您查看命令所執行的動作，而不是進行變更。 這是測試命令影響的好方法，特別是在您執行一些破壞性的動作之前。

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

如果命令正確地實作 `ShouldProcess`，應該會顯示其所進行的所有變更。 以下是使用萬用字元來刪除多個檔案的範例。

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a>使用 -Confirm

支援 `-WhatIf` 的命令也支援 `-Confirm`。 這可讓您在執行動作之前，先行確認。

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

在此情況下，您有多種選擇可讓您繼續、略過變更或停止執行指令碼。 說明提示會描述諸如此類的每個選項。

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a>當地語系化

此提示會在 PowerShell 中當地語系化，因此語言會根據您作業系統的語言而變更。 這也是 PowerShell 為您管理的又一件事。

### <a name="switch-parameters"></a>切換參數

讓我們快速查看將值傳遞給切換參數的方法。 我呼叫此函式的主要原因，是您通常會想要將參數值傳遞給您呼叫的函式。

第一種方法是特定的參數語法，可用於所有參數，不過您大多會看到它用於切換參數。 您可以指定冒號，將值附加至參數。

```powershell
Remove-Item -Path:* -WhatIf:$true
```

您可以使用變數來執行相同的動作。

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

第二種方法是使用雜湊表來展開值。

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

如果您不熟悉雜湊表或展開，我還有另一篇文章，其中涵蓋 [您想知道的雜湊表所有相關內容][]。

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

啟用 `-WhatIf` 和 `-Confirm` 支援的第一個步驟，是在函式的 `CmdletBinding` 中指定 `SupportsShouldProcess`。

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

藉由以這種方式指定 `SupportsShouldProcess`，我們現在可以使用 `-WhatIf` (或 `-Confirm`) 來呼叫函數。

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

請注意，我並未建立名稱為 `-WhatIf` 的參數。 指定 `SupportsShouldProcess` 會自動為我們將其建立。 當我們在 `Test-ShouldProcess`上指定 `-WhatIf` 參數時，我們所呼叫的某些項目也會執行 `-WhatIf` 處理流程。

### <a name="trust-but-verify"></a>信任但需要確認

這裡存在一些危險，那就是信任您所呼叫的所有項目都會繼承 `-WhatIf` 值。 在其餘的範例中，我將假設它沒有作用，而且在呼叫其他命令時非常明確。 建議您採取相同動作。

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

稍後當您進一步瞭解所有過程中的所有部分之後，我將會更清楚地回顧細節。

## <a name="pscmdletshouldprocess"></a>$PSCmdlet.ShouldProcess

可讓您執行 `SupportsShouldProcess` 的方法是 `$PSCmdlet.ShouldProcess`。 您會呼叫 `$PSCmdlet.ShouldProcess(...)`，查看是否應該處理一些邏輯，而 PowerShell 會負責其餘部分。 讓我們從以下範例開始：

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

`$PSCmdlet.ShouldProcess($file.name)` 的呼叫會檢查 `-WhatIf` (和 `-Confirm` 參數)，然後據此加以處理。 `-WhatIf` 會導致 `ShouldProcess` 輸出變更的描述，並傳回 `$false`：

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

使用 `-Confirm` 的呼叫會暫停執行指令碼，並提示使用者選擇繼續進行。 如果使用者選取 `Y`，它會傳回 `$true`。

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

`$PSCmdlet.ShouldProcess` 很棒的功能，就是它會提高詳細資訊輸出至雙倍。 在執行 `ShouldProcess` 時，我經常會依賴這項功能。

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a>多載

有幾個適用於 `$PSCmdlet.ShouldProcess` 的不同多載 (具有不同的參數) 可用於自訂訊息。 我們已經看到上述範例中的第一個。 讓我們仔細檢視。

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

這會產生包含函式名稱和目標 (參數值) 的輸出。

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

將第二個參數指定為會使用作業值的作業，而不是訊息中的函數名稱。

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

下一個選項是指定三個參數，可以充分自訂訊息。 使用三個參數時，第一個是完整的訊息。 第二個參數仍會在 `-Confirm` 訊息輸出中使用。

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a>快速參數參考

如果您只是要找出應該使用的參數，以下是快速參考，顯示參數如何變更不同 `-WhatIf` 情況中的訊息。

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

我通常會搭配兩個參數來使用它。

### <a name="shouldprocessreason"></a>ShouldProcessReason

我們有第四個多載，比其他多載更進階。 它可讓您取得執行 `ShouldProcess` 的原因。 我在這裡只是為了完整性而加入此內容，因為我們可以改為只檢查 `$WhatIf` 是否為 `$true`。

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

我們必須將 `$reason` 變數傳遞至第四個參數，做為具有 `[ref]` 的參考變數。 `ShouldProcess` 以 `None` 或 `WhatIf` 值填入 `$reason`。 我不會說這個很實用，而且我沒有理由要使用它。

### <a name="where-to-place-it"></a>放置位置

您可以使用 `ShouldProcess` 讓指令碼更安全。 當您的指令碼進行變更時，就會用到它。 我想要盡可能將 `$PSCmdlet.ShouldProcess` 呼叫放在最接近變更的位置。

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

如果我正在處理項目集合，則會針對每個項目呼叫它。 因此，呼叫會放在 foreach 迴圈內。

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

我緊鄰變更放置 `ShouldProcess` 的原因，就是在指定 `-WhatIf` 時，我想要盡可能多執行程式碼。 若是可以，我想要執行設定和驗證，讓使用者看到那些錯誤。

我也想要在驗證我的專案的 Pester 測試中使用這項功能。 如果我有一個很難在 pester 中模擬的邏輯，我通常可以將它包裝在 `ShouldProcess` 中，然後在我的測試中使用 `-WhatIf` 來呼叫它。 您最好是測試部分程式碼，而不是什麼程式碼都不進行測試。

### <a name="whatifpreference"></a>$WhatIfPreference

我們所擁有的第一個喜好設定變數是 `$WhatIfPreference`。 依預設，這會是 `$false`。 如果您將它設定為 `$true` 則您的函式會執行，如同您指定 `-WhatIf` 一樣。 如果您在工作階段中進行這項設定，則所有命令都會執行 `-WhatIf` 執行。

當您使用 `-WhatIf` 呼叫函式時，`$WhatIfPreference` 的值會設定為函式範圍內的 `$true`。

## <a name="confirmimpact"></a>ConfirmImpact

我大部分的範例都適用於 `-WhatIf`，但目前為止的所有內容也可以搭配 `-Confirm` 一起使用，藉此提示使用者。 您可以將函式的 `ConfirmImpact` 設定為 [高]，它會提示使用者，如同使用 `-Confirm` 呼叫一般。

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

因為 `High` 的影響，`Test-ShouldProcess` 的這個呼叫正在執行 `-Confirm` 動作。

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

最顯著的問題是，缺少了提示使用者之後，在其他指令碼中就更不方便使用了。 在此案例中，我們可以將 `$false` 傳遞至 `-Confirm` 以隱藏提示。

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

我將在稍後的章節中討論如何新增 `-Force` 支援。

### <a name="confirmpreference"></a>$ConfirmPreference

`$ConfirmPreference` 是自動變數，可控制 `ConfirmImpact` 要求您確認執行的時機。 以下為適用於 `$ConfirmPreference` 與 `ConfirmImpact` 的可能值。

- `High`
- `Medium`
- `Low`
- `None`

使用這些值，您可以針對每個函式指定不同的影響層級。 如果您的 `$ConfirmPreference` 設定為高於 `ConfirmImpact` 的值，系統就不會提示您確認執行。

根據預設，`$ConfirmPreference` 會設為 `High` 且 `ConfirmImpact` 為 `Medium`。 如果您想要讓函式自動提示使用者，請將您的 `ConfirmImpact` 設定為 `High`。 若它具有破壞性，請將其設定為 `Medium`；如果在生產環境中執行此命令始終安全無虞，則使用 `Low`。 如果您將其設定為 `none`，即使已指定 `-Confirm` 也不會提示 (但仍會提供您 `-WhatIf` 支援)。

若是使用 `-Confirm` 呼叫函式，則 `$ConfirmPreference` 的值會設定為函式範圍內的 `Low`。

### <a name="suppressing-nested-confirm-prompts"></a>隱藏已嵌套的確認提示

您所呼叫的函式可以挑選 `$ConfirmPreference`。 這可以建立您新增確認提示的情況，而您呼叫的函式也會提示使用者。

我要做的是，指定當我已經處理提示時，所呼叫的命令上指定 `-Confirm:$false`。

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

這會讓我們回到先前的警告：當 `-WhatIf` 未傳遞至函式，以及 `-Confirm` 傳遞至函式時，會有一些細微的差異。 我保證我稍後會回頭探討這個。

## <a name="pscmdletshouldcontinue"></a>$PSCmdlet.ShouldContinue

如果您需要的控制比 `ShouldProcess` 提供的更多，您可以使用 `ShouldContinue`直接觸發提示。 `ShouldContinue` 會忽略 `$ConfirmPreference`、`ConfirmImpact`、`-Confirm`、`$WhatIfPreference` 和 `-WhatIf`，因為它會在每次執行時發出提示。

快速概覽，`ShouldProcess` 和 `ShouldContinue` 很容易混淆。 我通常會記得使用 `ShouldProcess`，因為該參數在 `CmdletBinding` 中稱為 `SupportsShouldProcess`。
在幾乎所有情況下，您都應該使用 `ShouldProcess`。 這就是我先討論此方法的原因。

讓我們看看 `ShouldContinue` 運作的狀況。

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

這可讓我們以較少的選項來提供更簡單的提示。

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

`ShouldContinue` 的最大問題是，它會要求使用者以互動方式執行，因為它會一律提示使用者。 您應該一律建立可供其他指令碼使用的工具。 藉由執行 `-Force`，您就可以執行此動作。 我稍後會重新探討這個想法。

### <a name="yes-to-all"></a>全部皆是

這會自動使用 `ShouldProcess` 來處理，但我們必須針對 `ShouldContinue` 執行更多工作。 有第二個方法多載，我們必須以按照參考資料傳入幾個值來控制邏輯。

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

我新增了一個 `foreach` 迴圈和一個集合，以顯示顯示其運作狀況。 我從 `if` 的陳述式中提取了 `ShouldContinue` 呼叫，使其更便於讀取。 使用四個參數來呼叫方法，開始變得有點累贅，但我嘗試讓它看起來像我一樣乾淨俐落。

## <a name="implementing--force"></a>實作 -Force

`ShouldProcess` 而 `ShouldContinue` 需要以不同的方式來實作 `-Force`。 這些實作的訣竅在於應該一律執行 `ShouldProcess`，但如果指定 `-Force`，則不應該執行 `ShouldContinue`。

### <a name="shouldprocess--force"></a>ShouldProcess -Force

如果您將 `ConfirmImpact` 設定為 `high`，則使用者要嘗試的第一件事，就是以 `-Force` 將它隱藏。 總之，這是我做的第一件事。

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

如果您還記得 `ConfirmImpact` 一節，他們實際上需要呼叫它，如下所示：

```powershell
Test-ShouldProcess -Confirm:$false
```

並非所有人都瞭解他們需要這麼做，而且 `-Confirm:$false` 不會隱藏 `ShouldContinue`。
因此，我們應該為使用者的例行性實作 `-Force`。 請在此檢視這個完整範例：

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force -and -not $Confirm){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

我們會新增自己的 `-Force` 參數作為參數，並使用在 `CmdletBinding` 中新增 `SupportsShouldProcess` 時可用的 `$Confirm` 自動參數。

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

專注在這裡的 `-Force` 邏輯：

```powershell
if ($Force -and -not $Confirm){
    $ConfirmPreference = 'None'
}
```

如果使用者指定 `-Force`，除非使用者也指定 `-Confirm`，否則我們會想要隱藏確認提示。 這可讓使用者強制執行變更，但仍會確認變更。 然後，我們會在本機範圍中設定 `$ConfirmPreference`，讓我們呼叫 `ShouldProcess` 探索它。

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

如果有人同時指定 `-Force` 和 `-WhatIf`，則 `-WhatIf` 需要優先執行。 這個方法會保留 `-WhatIf` 流程，因為 `ShouldProcess` 一律會執行。

請勿在 `ShouldProcess` 的 `if` 陳述式內新增 `$Force` 值的檢查。 這是此特定情況的反模式，僅管這是我在下一節中針對 `ShouldContinue` 所告訴您的內容。

### <a name="shouldcontinue--force"></a>ShouldContinue -Force

這是使用 `ShouldContinue` 執行 `-Force` 的正確方式。

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

只要將 `$Force` 放在 `-or` 運算子的左側，就可以優先接受評估。 以這種方式撰寫，會導致 `if` 陳述式的執行發生短路。 如果 `$force` 為 `$true`，則不會執行 `ShouldContinue`。

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

在此情況下，我們不需要擔心 `-Confirm` 或 `-WhatIf`，因為 `ShouldContinue` 不提供支援。 這就是為什麼需要以不同於 `ShouldProcess` 的方式來處理。

## <a name="scope-issues"></a>範圍問題

使用 `-WhatIf` 和 `-Confirm` 應該會套用至函式內的所有項目，以及它們所呼叫的所有項目。 若要這麼做，請在函式的本機範圍中，將 `$WhatIfPreference` 設定為 `$true`，或將 `$ConfirmPreference` 設定為 `Low`。 當您呼叫其他函式時，`ShouldProcess` 的呼叫會使用這些值。

在大部分的情況下，這實際上會正常運作。 每當您在相同的範圍內呼叫內建 Cmdlet 或函式時，這個方法都會正常運作。 當您從主控台呼叫指令碼模組中的指令碼或函式時，這個方法也會正常運作。

當指令碼或指令碼模組呼叫其他指令碼模組中的函式時，在該單一特定位置，這個方法就是無法運作。 這可能不是很大的問題，但您建立或從 PSGallery 中提取的大部分模組都是指令碼模組。

核心問題在於，若從其他指令碼模組中的函式呼叫，則指令碼模組不會繼承 `$WhatIfPreference` 或 `$ConfirmPreference` (以及其他數個參數) 的值。

將此摘要當做一般規則的最佳方式在於，此方式適用於二進位模組，而且絕對不會信任它來處理指令碼模組。 如果您不確定，無論是進行測試或是直接假設它無法正常運作，

我個人都認為這樣非常危險；因為它會產生一些情況，讓您將 `-WhatIf` 支援新增至多個模組，以便在隔離中正常運作，但無法在彼此呼叫時正常運作。

我們有 GitHub RFC 致力於修正此問題。 如需詳細資訊，請參閱 [將執行喜好設定傳播至指令碼模組範圍之外][RFC]。

## <a name="in-closing"></a>關閉時

我必須在每次需要使用 `ShouldProcess` 時，都要查閱如何使用。 我花了很長的時間來區分 `ShouldProcess` 與 `ShouldContinue`。 我幾乎都需要查詢要使用的參數。 因此，如果您仍不時感到困惑，請不用擔心。 我們會在您需要時提供這篇文章。 我確定我自己會經常參考它。

如果您喜歡這篇文章，請使用下列連結，在 Twitter 上與我分享您的看法。 我總是喜歡收到因為我所寫的內容而獲致價值的使用者的消息。

<!-- link references -->
[原始版本]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[常見的]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[您想知道的雜湊表所有相關內容]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
