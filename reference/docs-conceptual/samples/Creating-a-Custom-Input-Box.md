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
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="93bef-104">建立自訂輸入方塊</span><span class="sxs-lookup"><span data-stu-id="93bef-104">Creating a Custom Input Box</span></span>

<span data-ttu-id="93bef-105">使用 Windows PowerShell 3.0 和更新版本中 Microsoft .NET Framework 的表單建立功能，撰寫圖形化自訂輸入方塊的指令碼。</span><span class="sxs-lookup"><span data-stu-id="93bef-105">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="93bef-106">建立自訂的圖形化輸入方塊</span><span class="sxs-lookup"><span data-stu-id="93bef-106">Create a custom, graphical input box</span></span>

<span data-ttu-id="93bef-107">將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。</span><span class="sxs-lookup"><span data-stu-id="93bef-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="93bef-108">指令碼一開始會載入兩個 .NET Framework 類別： **System.Drawing** 和 **System.Windows.Forms** 。</span><span class="sxs-lookup"><span data-stu-id="93bef-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="93bef-109">接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。</span><span class="sxs-lookup"><span data-stu-id="93bef-109">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form** ; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="93bef-110">建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="93bef-110">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="93bef-111">**Text** 。</span><span class="sxs-lookup"><span data-stu-id="93bef-111">**Text.**</span></span> <span data-ttu-id="93bef-112">這會成為視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="93bef-112">This becomes the title of the window.</span></span>

- <span data-ttu-id="93bef-113">**Size** 。</span><span class="sxs-lookup"><span data-stu-id="93bef-113">**Size.**</span></span> <span data-ttu-id="93bef-114">這是表單的大小，單位為像素。</span><span class="sxs-lookup"><span data-stu-id="93bef-114">This is the size of the form, in pixels.</span></span> <span data-ttu-id="93bef-115">上述指令碼會建立 300 像素寬、200 像素高的表單。</span><span class="sxs-lookup"><span data-stu-id="93bef-115">The preceding script creates a form that's 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="93bef-116">**StartingPosition** 。</span><span class="sxs-lookup"><span data-stu-id="93bef-116">**StartingPosition.**</span></span> <span data-ttu-id="93bef-117">此選擇性屬性在上述指令碼中是設定為 **CenterScreen** 。</span><span class="sxs-lookup"><span data-stu-id="93bef-117">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="93bef-118">若未新增此屬性，Windows 會在表單開啟時選取一個位置。</span><span class="sxs-lookup"><span data-stu-id="93bef-118">If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="93bef-119">將 **StartingPosition** 設定為 **CenterScreen** ，您就可以讓表單在每次載入時，自動顯示在畫面中間。</span><span class="sxs-lookup"><span data-stu-id="93bef-119">By setting the **StartingPosition** to **CenterScreen** , you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="93bef-120">接著，為您的表單建立 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="93bef-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="93bef-121">指定 **[確定]** 按鈕的大小與行為。</span><span class="sxs-lookup"><span data-stu-id="93bef-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="93bef-122">在此範例中，按鈕位置會距離表單上邊緣 120 像素，並距離左邊緣 75 像素。</span><span class="sxs-lookup"><span data-stu-id="93bef-122">In this example, the button position is 120 pixels from the form's top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="93bef-123">按鈕高度是 23 像素，而按鈕寬度是 75 像素。</span><span class="sxs-lookup"><span data-stu-id="93bef-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="93bef-124">指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。</span><span class="sxs-lookup"><span data-stu-id="93bef-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="93bef-125">同樣地，您也會建立 **[取消]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="93bef-125">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="93bef-126">**[取消]** 按鈕距離上邊緣 120 像素，但距離視窗左邊緣 150 像素。</span><span class="sxs-lookup"><span data-stu-id="93bef-126">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="93bef-127">接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="93bef-127">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="93bef-128">新增控制項 (在此情況下為文字方塊)，讓使用者提供您在標籤文字中描述的資訊。</span><span class="sxs-lookup"><span data-stu-id="93bef-128">Add the control (in this case, a text box) that lets users provide the information you've described in your label text.</span></span> <span data-ttu-id="93bef-129">除了文字方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 MSDN 上的 [System.Windows.Forms Namespace (System.Windows.Forms 命名空間)](/dotnet/api/system.windows.forms)。</span><span class="sxs-lookup"><span data-stu-id="93bef-129">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="93bef-130">將 **Topmost** 屬性設定為 **$true** ，以強制視窗開啟在其他已開啟視窗與對話方塊的上方。</span><span class="sxs-lookup"><span data-stu-id="93bef-130">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="93bef-131">接下來，新增這行程式碼來啟動表單，並將焦點設定在您建立的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="93bef-131">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="93bef-132">新增下面這行程式碼，以在 Windows 中顯示該表單。</span><span class="sxs-lookup"><span data-stu-id="93bef-132">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="93bef-133">最後， **If** 區塊內的程式碼會指示 Windows 當使用者在文字方塊中提供文字並按一下 [OK] 按鈕或按下 **Enter** 鍵時要執行的表單動作。</span><span class="sxs-lookup"><span data-stu-id="93bef-133">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="93bef-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93bef-134">See Also</span></span>

- <span data-ttu-id="93bef-135">[GitHub：Dave Wyatt's WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10)) (GitHub：Dave Wyatt 的 WinFormsExampleUpdates)</span><span class="sxs-lookup"><span data-stu-id="93bef-135">[GitHub: Dave Wyatt's WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))</span></span>
- [<span data-ttu-id="93bef-136">Windows PowerShell Tip of the Week: Creating a Custom Input Box (本週 Windows PowerShell 秘訣︰建立自訂輸入方塊)</span><span class="sxs-lookup"><span data-stu-id="93bef-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)
