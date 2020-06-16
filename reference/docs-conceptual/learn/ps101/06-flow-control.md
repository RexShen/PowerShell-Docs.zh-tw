---
title: 流量控制
description: PowerShell 提供方法來建立迴圈、進行決策，並以邏輯方式控制指令碼中的程式碼流程。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437989"
---
# <a name="chapter-6---flow-control"></a>第 6 章 - 流程控制

## <a name="scripting"></a>指令碼

從撰寫 PowerShell 單行程式碼轉換到撰寫指令碼時，聽起來很複雜，實際上卻不然。 指令碼只是您會在 PowerShell 主控台中以互動方式執行的相同或類似命令，不同的是，系統會將其儲存為 `.PS1` 檔案。 有一些指令碼建構可供您使用，例如 `foreach` 迴圈，而不是 `ForEach-Object` Cmdlet。 對於初學者來說，當您認為 `foreach` 同時是指令碼建構和 `ForEach-Object` Cmdlet 的別名時，這些差異可能會造成混淆。

## <a name="looping"></a>迴圈

PowerShell 的其中一個絕佳功能就是，一旦您了解如何對某個項目執行一些動作，就幾乎可以針對數百個項目執行相同動作。 只要使用 PowerShell 中許多不同類型的迴圈中的其中一個，就能對項目重複執行。

### <a name="foreach-object"></a>ForEach-Object

`ForEach-Object` 是用來逐一查看管線中項目 (例如使用 PowerShell 單行程式碼) 的 Cmdlet。 `ForEach-Object` 會透過管線串流物件。

雖然 `Get-Command` 的 **Module** 參數會接受多個字串值，但只會透過屬性名稱的管線輸入或透過參數輸入接受它們。 在下列案例中，如果我想要以 by value 值方式將兩個字串以管線傳送至 `Get-Command`，以便與 **Module** 參數搭配使用，我就必須使用 `ForEach-Object` Cmdlet。

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

在上述範例中，`$_` 是目前的物件。 從 PowerShell 3.0 版開始，您可以使用 `$PSItem`，而不是 `$_`。 但我發現，大部分經驗豐富的 PowerShell 使用者仍然偏好使用 `$_`，因為它具回溯相容且要輸入的字較少。

使用 `foreach` 關鍵字時，您必須先將所有項目儲存在記憶體中，然後再逐一查看，如果您不知道要處理多少個項目，則這可能會很棘手。

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

許多時候，`foreach` 或 `ForEach-Object` 之類的迴圈都是必要的。 否則，您會收到錯誤訊息。

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

其他時候，您可以取得相同的結果，同時將迴圈完全消除。 請參閱 Cmdlet 說明以了解您的選項。

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

如您在先前的範例中所見，`Get-ADComputer` 的 **Identity** 參數只會在透過參數輸入提供時接受單一值，但在透過管線輸入提供輸入時，則會允許多個項目。

### <a name="for"></a>For

當指定的條件為 true 時，`for` 迴圈會逐一查看。 `for` 迴圈不是我經常使用的項目，但它有其用途。

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

在上述範例中，迴圈會逐一查看四次，從數字一開始，且只要計數器變數 `$i` 小於 5，就會繼續進行。 它總計會睡眠 10 秒。

### <a name="do"></a>要做的事

PowerShell 中有兩個不同的 `do` 迴圈。 `Do Until` 會在指定的條件為 false 時執行。

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

先前的範例是數字遊戲，會繼續進行，直到您猜測的值等於 `Get-Random` Cmdlet 產生的相同數字。

`Do While` 就正好相反。 只要指定的條件評估為 true，它就會執行。

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

藉由將測試條件反轉為不等於，使用 `Do While` 迴圈即可達成相同的結果。

`Do` 迴圈一律會至少執行一次，因為會在迴圈結尾評估條件。

### <a name="while"></a>While

與 `Do While` 迴圈類似，只要指定的條件為 true，`While` 迴圈就會執行。 但差異在於，`While` 迴圈會在執行任何程式碼之前，在迴圈頂端評估條件。 因此，如果條件評估為 false，則不會執行。

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

上一個範例會計算在美國的感恩節是在哪一天。 它一律是在 11 月的第四個星期四。 如此一來，迴圈就會從 11 月 22 日開始，並在星期幾不等於星期四時加一天。 如果 22 日為星期四，則完全不會執行迴圈。

## <a name="break-continue-and-return"></a>Break、Continue 和 Return

`Break` 的設計目的是要中斷迴圈。 它通常也會與 `switch` 陳述式搭配使用。

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

上一個範例中所示的 `break` 陳述式會導致迴圈在第一次反覆項目時結束。

Continue 的設計則是要跳到迴圈的下一個反覆項目。

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

上一個範例會輸出數字 1、2、4 和 5。 它會略過數字 3，並繼續進行迴圈的下一個反覆項目。 類似於 `break`，`continue` 會中斷迴圈，但目前的反覆項目除外。 執行會繼續進行下一個反覆項目，而不是中斷迴圈並停止。

Return 的設計目的是要結束現有的範圍。

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

請注意，在上述範例中，Return 會輸出第一個結果，然後從迴圈結束。 如需更完整結果陳述式的說明，請參閱我的其中一個部落格文章：[「PowerShell Return 關鍵字」][]。

## <a name="summary"></a>摘要

在本章中，您已了解 PowerShell 中存在的不同類型迴圈。

## <a name="review"></a>檢閱

1. `ForEach-Object` Cmdlet 與 foreach 指令碼建構中有何差異？
1. 使用 While 迴圈而不是 Do While 或 Do Until 迴圈的主要優點為何？
1. Break 和 Continue 陳述式有何不同？

## <a name="recommended-reading"></a>建議閱讀資料

- [ForEach-Object][]
- [about_ForEach][]
- [about_For][]
- [about_Do][]
- [about_While][]
- [about_Break][]
- [about_Continue][]
- [about_Return][]

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
[「PowerShell Return 關鍵字」]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
