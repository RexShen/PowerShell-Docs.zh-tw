---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 建立自訂輸入方塊
description: 本文說明如何使用 Windows PowerShell 中的 .NET Framework 表單建置功能，建立自訂輸入方塊。
ms.openlocfilehash: 18fba743b169010936d2ea83dca4e95203664fe9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500550"
---
# <a name="creating-a-custom-input-box"></a>建立自訂輸入方塊

使用 Windows PowerShell 3.0 和更新版本中 Microsoft .NET Framework 的表單建立功能，撰寫圖形化自訂輸入方塊的指令碼。

## <a name="create-a-custom-graphical-input-box"></a>建立自訂的圖形化輸入方塊

將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

指令碼一開始會載入兩個 .NET Framework 類別： **System.Drawing** 和 **System.Windows.Forms** 。 接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。

```powershell
$form = New-Object System.Windows.Forms.Form
```

建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。

- **Text** 。 這會成為視窗的標題。

- **Size** 。 這是表單的大小，單位為像素。 上述指令碼會建立 300 像素寬、200 像素高的表單。

- **StartingPosition** 。 此選擇性屬性在上述指令碼中是設定為 **CenterScreen** 。
  若未新增此屬性，Windows 會在表單開啟時選取一個位置。 將 **StartingPosition** 設定為 **CenterScreen** ，您就可以讓表單在每次載入時，自動顯示在畫面中間。

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

接著，為您的表單建立 **[確定]** 按鈕。 指定 **[確定]** 按鈕的大小與行為。 在此範例中，按鈕位置會距離表單上邊緣 120 像素，並距離左邊緣 75 像素。 按鈕高度是 23 像素，而按鈕寬度是 75 像素。 指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

同樣地，您也會建立 **[取消]** 按鈕。 **[取消]** 按鈕距離上邊緣 120 像素，但距離視窗左邊緣 150 像素。

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

新增控制項 (在此情況下為文字方塊)，讓使用者提供您在標籤文字中描述的資訊。 除了文字方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 MSDN 上的 [System.Windows.Forms Namespace (System.Windows.Forms 命名空間)](/dotnet/api/system.windows.forms)。

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

將 **Topmost** 屬性設定為 **$true** ，以強制視窗開啟在其他已開啟視窗與對話方塊的上方。

```powershell
$form.Topmost = $true
```

接下來，新增這行程式碼來啟動表單，並將焦點設定在您建立的文字方塊。

```powershell
$form.Add_Shown({$textBox.Select()})
```

新增下面這行程式碼，以在 Windows 中顯示該表單。

```powershell
$result = $form.ShowDialog()
```

最後， **If** 區塊內的程式碼會指示 Windows 當使用者在文字方塊中提供文字並按一下 [OK] 按鈕或按下 **Enter** 鍵時要執行的表單動作。

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a>另請參閱

- [GitHub：Dave Wyatt's WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10)) (GitHub：Dave Wyatt 的 WinFormsExampleUpdates)
- [Windows PowerShell Tip of the Week: Creating a Custom Input Box (本週 Windows PowerShell 秘訣︰建立自訂輸入方塊)](https://technet.microsoft.com/library/ff730941.aspx)
