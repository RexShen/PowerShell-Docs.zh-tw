---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 建立圖形化日期選擇器
ms.openlocfilehash: b748e301b24ed643488079b547e2da1a5a7a6551
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706118"
---
# <a name="creating-a-graphical-date-picker"></a>建立圖形化日期選擇器

使用 Windows PowerShell 3.0 與更新的版本建立表單，表單上具有圖形化日曆樣式控制項，可讓使用者選取月份中的某個日期。

## <a name="create-a-graphical-date-picker-control"></a>建立圖形化的日期選擇器控制項

將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

指令碼一開始會載入兩個 .NET Framework 類別：**System.Drawing** 和 **System.Windows.Forms**。 接著，您會啟動新的 .NET Framework 類別 **Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

此範例會使用 **Property** 屬性與雜湊表為此類別的四個屬性指派值。

1. **StartPosition**：若未新增此屬性，Windows 會在表單開啟時選取一個位置。 透過將此屬性 設定為 **CenterScreen**，您可以在每次載入表單時，將表單自動顯示在畫面中間。

2. **Size**：這是表單的大小，單位為像素。
   上述指令碼會建立 243 像素寬、230 像素高的表單。

3. **Text**：這會成為視窗的標題。

4. **Topmost**：透過將此屬性設定為 `$true`，您可以強制視窗開啟在其他已開啟視窗與對話方塊的上方。

接著，在您的表單中建立並新增日曆控制項。
在此範例中，目前的日期並未反白顯示或圈起來。
使用者一次只能在日曆上選取一個日期。

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

接著，為您的表單建立 **[確定]** 按鈕。 指定 **[確定]** 按鈕的大小與行為。 在此範例中，按鈕位置是距離表單上邊緣 165 像素，並距離左邊緣 38 像素。 按鈕高度是 23 像素，而按鈕寬度是 75 像素。 指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。

```powershell
$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

同樣地，您也會建立 **[取消]** 按鈕。
**[取消]** 按鈕距離上邊緣 165 像素，但距離視窗左邊緣 113 像素。

```powershell
$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

新增下面這行程式碼，以在 Windows 中顯示該表單。

```powershell
$result = $form.ShowDialog()
```

最後， `if` 區塊內的程式碼會指示 Windows 當使用者選取日曆上的日期並按一下 [確定]  按鈕或按下 **Enter** 鍵時要執行的表單動作。 Windows PowerShell 會將選取的日期顯示給使用者。

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>另請參閱

- [GitHub：Dave Wyatt 的 WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates) \(英文\)
- [本週 Windows PowerShell 祕訣︰建立圖形化日期選擇器](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10)) \(英文\)
