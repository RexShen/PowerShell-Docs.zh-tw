---
title:  建立自訂輸入方塊
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  0b12e56c-299f-40ee-afbf-d30d23ed2565
---

# 建立自訂輸入方塊
使用 Windows PowerShell 3.0 和更新版本中 Microsoft .NET Framework 的表單建立功能，撰寫圖形化自訂輸入方塊的指令碼。

## 建立自訂的圖形化輸入方塊
將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
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
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label) 

$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox) 

$form.Topmost = $True

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

指令碼一開始會載入兩個 .NET Framework 類別：**System.Drawing** 和 **System.Windows.Forms**。 接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。

```
$form = New-Object System.Windows.Forms.Form
```

建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。

-   **Text。** 這會成為視窗的標題。

-   **Size。** 這是表單的大小，單位為像素。 上述指令碼會建立 300 像素寬、200 像素高的表單。

-   **StartingPosition。** 此選擇性屬性在上述指令碼中是設定為 **CenterScreen**。 若未新增此屬性，Windows 會在表單開啟時選取一個位置。 透過將 **StartingPosition** 設定為 **CenterScreen**，您可以在每次載入表單時，將表單自動顯示在畫面中間。

```
$form.Text = "Data Entry Form"
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

接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label)
```

新增控制項 (在此範例中為文字方塊)，讓使用者提供您在標籤文字中描述的資訊。 除了文字方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 MSDN 上的 [System.Windows.Forms Namespace (System.Windows.Forms 命名空間)](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx)。

```
$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox)
```

將 **Topmost** 屬性設定為 **$True**，以強制視窗開啟在其他已開啟視窗與對話方塊的上方。

```
$form.Topmost = $True
```

接下來，新增這行程式碼來啟動表單，並將焦點設定在您建立的文字方塊。

```
$form.Add_Shown({$textBox.Select()})
```

新增下面這行程式碼，以在 Windows 中顯示該表單。

```
$result = $form.ShowDialog()
```

最後，**If** 區塊內的程式碼會指示 Windows 當使用者在文字方塊中提供文字並按一下 **[確定]** 按鈕或按下 **Enter** 鍵時要執行的表單動作。

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## 另請參閱
[Hey Scripting Guy: Why don’t these PowerShell GUI examples work?](http://go.microsoft.com/fwlink/?LinkId=506644)
 (指令碼高手您好：這些 PowerShell GUI 範例為何無法運作？) [GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
 (GitHub：Dave Wyatt 的 WinFormsExampleUpdates) [本週 Windows PowerShell 秘訣︰建立自訂輸入方塊](http://technet.microsoft.com/library/ff730941.aspx)



<!--HONumber=May16_HO2-->


