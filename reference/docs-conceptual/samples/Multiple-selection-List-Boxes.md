---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 多重選擇清單方塊
description: 本文說明如何使用 Windows PowerShell 中的 .NET Framework 表單建置功能，建立多重選擇清單方塊控制項。
ms.openlocfilehash: 2724188695f054d1115b385987cda8a578c102de
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391522"
---
# <a name="multiple-selection-list-boxes"></a>多重選擇清單方塊

使用 Windows PowerShell 3.0 與更新的版本，在自訂的 Windows Form 中建立多重選擇清單方塊控制項。

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>建立允許多重選擇的清單方塊控制項

將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

指令碼一開始會載入兩個 .NET Framework 類別：**System.Drawing** 和 **System.Windows.Forms**。 接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。

```powershell
$form = New-Object System.Windows.Forms.Form
```

建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。

- **Text**。 這會成為視窗的標題。

- **Size**。 這是表單的大小，單位為像素。 上述指令碼會建立 300 像素寬、200 像素高的表單。

- **StartingPosition**。 此選擇性屬性在上述指令碼中是設定為 **CenterScreen**。
  若未新增此屬性，Windows 會在表單開啟時選取一個位置。 將 **StartingPosition** 設定為 **CenterScreen**，您就可以讓表單在每次載入時，自動顯示在畫面中間。

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

接著，為您的表單建立 **[確定]** 按鈕。 指定 **[確定]** 按鈕的大小與行為。 在此範例中，按鈕位置會距離表單上邊緣 120 像素，並距離左邊緣 75 像素。 按鈕高度是 23 像素，而按鈕寬度是 75 像素。 指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

同樣地，您也會建立 **[取消]** 按鈕。 **[取消]** 按鈕距離上邊緣 120 像素，但距離視窗左邊緣 150 像素。

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

新增控制項 (在此情況下為清單方塊)，讓使用者提供您在標籤文字中描述的資訊。 除了文字方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 [System.Windows.Forms 命名空間](/dotnet/api/system.windows.forms)。

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

以下說明您想要允許使用者從清單中選取多個值的指定方式。

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

在下一節中，您可以指定您希望清單方塊向使用者顯示的值。

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

指定清單方塊控制項的最大高度。

```powershell
$listBox.Height = 70
```

將清單方塊控制項新增至您的表單，並指示 Windows 在開啟表單時，將其開啟在其他視窗與對話方塊之上。

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

新增下面這行程式碼，以在 Windows 中顯示該表單。

```powershell
$result = $form.ShowDialog()
```

最後，**If** 區塊內的程式碼會指示 Windows 當使用者在清單方塊中選取一或多個並按一下 **[確定]** 或按 **Enter** 鍵時要執行的表單動作。

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>另請參閱

- [Weekend Scripter：修正 PowerShell GUI 範例](https://devblogs.microsoft.com/scripting/weekend-scripter-fixing-powershell-gui-examples/)
- [GitHub：Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates) (GitHub：Dave Wyatt 的 WinFormsExampleUpdates)
- [本週 Windows PowerShell 祕訣︰本週 Windows PowerShell 秘訣︰複選清單方塊 - 及其他事項！](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730950(v=technet.10)) \(英文\)
