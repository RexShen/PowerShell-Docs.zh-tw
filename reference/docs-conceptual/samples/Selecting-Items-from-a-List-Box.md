---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 從清單方塊選取項目
description: 本文說明如何使用 Windows PowerShell 中的 .NET Framework 表單建置功能，建立清單方塊控制項。
ms.openlocfilehash: d6f881f0b92f294da105ae7df5e25e8c20ce5094
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391233"
---
# <a name="selecting-items-from-a-list-box"></a>從清單方塊選取項目

使用 Windows PowerShell 3.0 和更新的版本，來建立讓使用者從清單方塊控制項選取項目的對話方塊。

## <a name="create-a-list-box-control-and-select-items-from-it"></a>建立清單方塊控制項，並從其中選取項目。

將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
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
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

指令碼一開始會載入兩個 .NET Framework 類別：**System.Drawing** 和 **System.Windows.Forms**。 接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。

- **Text**。 這會成為視窗的標題。

- **Size**。 這是表單的大小，單位為像素。 上述指令碼會建立 300 像素寬、200 像素高的表單。

- **StartingPosition**。 此選擇性屬性在上述指令碼中是設定為 **CenterScreen**。
  若未新增此屬性，Windows 會在表單開啟時選取一個位置。 將 **StartingPosition** 設定為 **CenterScreen**，您就可以讓表單在每次載入時，自動顯示在畫面中間。

```powershell
$form.Text = 'Select a Computer'
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
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
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

接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。 在此案例中，您希望使用者選取一部電腦。

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

新增控制項 (在此情況下為清單方塊)，讓使用者提供您在標籤文字中描述的資訊。 除了清單方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 [System.Windows.Forms 命名空間](/dotnet/api/system.windows.forms)。

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

在下一節中，您可以指定您希望清單方塊向使用者顯示的值。

> [!NOTE]
> 此指令碼所建立的清單方塊只允許選取一個項目。 若要建立允許多重選取的清單方塊控制項，請為 **SelectionMode** 屬性指定值，如下所示：`$listBox.SelectionMode = 'MultiExtended'`。 如需詳細資訊，請參閱[多重選擇清單方塊](Multiple-selection-List-Boxes.md)。

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
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

最後，**If** 區塊內的程式碼會指示 Windows 當使用者在清單方塊中選取選項並按一下 [OK] 或按下 **Enter** 鍵時要執行的表單動作。

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>另請參閱

- [GitHub：Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates) (GitHub：Dave Wyatt 的 WinFormsExampleUpdates)
- [本週 Windows PowerShell 祕訣︰從清單方塊選取項目](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10)) \(英文\)
