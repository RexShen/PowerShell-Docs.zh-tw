---
title: 從清單方塊選取項目
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
---
# 從清單方塊選取項目
使用 Windows PowerShell 3.0 和更新的版本，來建立讓使用者從清單方塊控制項選取項目的對話方塊。

## 建立清單方塊控制項，並從其中選取項目。
將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80

[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")

$form.Controls.Add($listBox) 

$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

指令碼一開始會載入兩個 .NET Framework 類別：**System.Drawing** 和 **System.Windows.Forms**。 接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。

-   **Text。** 這會成為視窗的標題。

-   **Size。** 這是表單的大小，單位為像素。 上述指令碼會建立 300 像素寬、200 像素高的表單。

-   **StartingPosition。** 此選擇性屬性在上述指令碼中是設定為 **CenterScreen**。 若未新增此屬性，Windows 會在表單開啟時選取一個位置。 透過將 **StartingPosition** 設定為 **CenterScreen**，您可以在每次載入表單時，將表單自動顯示在畫面中間。

```
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

接著，為您的表單建立 **[確定]** 按鈕。 指定 **[確定]** 按鈕的大小與行為。 在此範例中，按鈕位置是距離表單上邊緣 120 像素，並距離左邊緣 75 像素。 按鈕高度是 23 像素，而按鈕寬度是 75 像素。 指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

同樣地，您也會建立 **[取消]** 按鈕。 **[取消]** 按鈕距離上邊緣 120 像素，但距離視窗左邊緣 150 像素。

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。 在此案例中，您希望使用者選取一部電腦。

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label)
```

新增控制項 (在此案例中為清單方塊)，讓使用者提供您在標籤文字中描述的資訊。 除了清單方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 MSDN 上的 [System.Windows.Forms Namespace (System.Windows.Forms 命名空間)](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx)。

```
$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80
```

在下一節中，您可以指定您希望清單方塊向使用者顯示的值。

> [!NOTE]
> 此指令碼所建立的清單方塊只允許選取一個項目。 若要建立允許多重選取的清單方塊，請指定值給 **SelectionMode** 屬性，如下所示：`$listBox.SelectionMode = "MultiExtended"`。 如需詳細資訊，請參閱[多重選擇清單方塊](Multiple-selection-List-Boxes.md).

```
[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")
```

新增清單方塊控制項到您的表單，並指示 Windows 在開啟表單時，將它開啟在其他視窗與對話方塊之上。

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

新增下面這行程式碼，以在 Windows 中顯示該表單。

```
$result = $form.ShowDialog()
```

最後，**If** 區塊內的程式碼會指示 Windows 當使用者在清單方塊中選取選項並按一下 **[確定]** 按鈕或按 **Enter** 鍵時要執行的表單動作。

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## 另請參閱
[Hey Scripting Guy: Why don’t these PowerShell GUI examples work? (指令碼高手您好：這些 PowerShell GUI 範例為何無法運作？)](http://go.microsoft.com/fwlink/?LinkId=506644)
[GitHub: Dave Wyatt's WinFormsExampleUpdates (GitHub：Dave Wyatt 的 WinFormsExampleUpdates)](https://github.com/dlwyatt/WinFormsExampleUpdates)
[Windows PowerShell Tip of the Week: Selecting Items from a List Box (本週 Windows PowerShell 秘訣︰從清單方塊選取項目）](http://technet.microsoft.com/library/ff730949.aspx)



<!--HONumber=May16_HO2-->


