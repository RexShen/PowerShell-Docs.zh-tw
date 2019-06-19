---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 多重選擇清單方塊
ms.openlocfilehash: dcfa43ac8e7cc4ba6147f71791edbf7989af3583
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030088"
---
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="4132e-103">多重選擇清單方塊</span><span class="sxs-lookup"><span data-stu-id="4132e-103">Multiple-selection List Boxes</span></span>

<span data-ttu-id="4132e-104">使用 Windows PowerShell 3.0 與更新的版本，在自訂的 Windows Form 中建立多重選擇清單方塊控制項。</span><span class="sxs-lookup"><span data-stu-id="4132e-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="4132e-105">建立允許多重選擇的清單方塊控制項</span><span class="sxs-lookup"><span data-stu-id="4132e-105">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="4132e-106">將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。</span><span class="sxs-lookup"><span data-stu-id="4132e-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="4132e-107">指令碼一開始會載入兩個 .NET Framework 類別：**System.Drawing** 和 **System.Windows.Forms**。</span><span class="sxs-lookup"><span data-stu-id="4132e-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="4132e-108">接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。</span><span class="sxs-lookup"><span data-stu-id="4132e-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="4132e-109">建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="4132e-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="4132e-110">**Text**。</span><span class="sxs-lookup"><span data-stu-id="4132e-110">**Text.**</span></span> <span data-ttu-id="4132e-111">這會成為視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="4132e-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="4132e-112">**Size**。</span><span class="sxs-lookup"><span data-stu-id="4132e-112">**Size.**</span></span> <span data-ttu-id="4132e-113">這是表單的大小，單位為像素。</span><span class="sxs-lookup"><span data-stu-id="4132e-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="4132e-114">上述指令碼會建立 300 像素寬、200 像素高的表單。</span><span class="sxs-lookup"><span data-stu-id="4132e-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="4132e-115">**StartingPosition**。</span><span class="sxs-lookup"><span data-stu-id="4132e-115">**StartingPosition.**</span></span> <span data-ttu-id="4132e-116">此選擇性屬性在上述指令碼中是設定為 **CenterScreen**。</span><span class="sxs-lookup"><span data-stu-id="4132e-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="4132e-117">若未新增此屬性，Windows 會在表單開啟時選取一個位置。</span><span class="sxs-lookup"><span data-stu-id="4132e-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="4132e-118">透過將 **StartingPosition** 設定為 **CenterScreen**，您可以在每次載入表單時，將表單自動顯示在畫面中間。</span><span class="sxs-lookup"><span data-stu-id="4132e-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="4132e-119">接著，為您的表單建立 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4132e-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="4132e-120">指定 **[確定]** 按鈕的大小與行為。</span><span class="sxs-lookup"><span data-stu-id="4132e-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="4132e-121">在此範例中，按鈕位置是距離表單上邊緣 120 像素，並距離左邊緣 75 像素。</span><span class="sxs-lookup"><span data-stu-id="4132e-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="4132e-122">按鈕高度是 23 像素，而按鈕寬度是 75 像素。</span><span class="sxs-lookup"><span data-stu-id="4132e-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="4132e-123">指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。</span><span class="sxs-lookup"><span data-stu-id="4132e-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="4132e-124">同樣地，您也會建立 **[取消]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4132e-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="4132e-125">**[取消]** 按鈕距離上邊緣 120 像素，但距離視窗左邊緣 150 像素。</span><span class="sxs-lookup"><span data-stu-id="4132e-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="4132e-126">接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="4132e-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="4132e-127">新增控制項 (在此案例中為清單方塊)，讓使用者提供您在標籤文字中描述的資訊。</span><span class="sxs-lookup"><span data-stu-id="4132e-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="4132e-128">除了文字方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 MSDN 上的 [System.Windows.Forms Namespace (System.Windows.Forms 命名空間)](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx)。</span><span class="sxs-lookup"><span data-stu-id="4132e-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="4132e-129">以下說明您如何指定您希望允許使用者從清單中選取多個值。</span><span class="sxs-lookup"><span data-stu-id="4132e-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="4132e-130">在下一節中，您可以指定您希望清單方塊向使用者顯示的值。</span><span class="sxs-lookup"><span data-stu-id="4132e-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="4132e-131">指定清單方塊控制項的最大高度。</span><span class="sxs-lookup"><span data-stu-id="4132e-131">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="4132e-132">新增清單方塊控制項到您的表單，並指示 Windows 在開啟表單時，將它開啟在其他視窗與對話方塊之上。</span><span class="sxs-lookup"><span data-stu-id="4132e-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="4132e-133">新增下面這行程式碼，以在 Windows 中顯示該表單。</span><span class="sxs-lookup"><span data-stu-id="4132e-133">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="4132e-134">最後，**If** 區塊內的程式碼會指示 Windows 當使用者在清單方塊中選取一或多個並按一下 **[確定]** 或按 **Enter** 鍵時要執行的表單動作。</span><span class="sxs-lookup"><span data-stu-id="4132e-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="4132e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4132e-135">See Also</span></span>

- <span data-ttu-id="4132e-136">[指令碼高手您好：PowerShell GUI 範例為什麼動不起來？](https://go.microsoft.com/fwlink/?LinkId=506644) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="4132e-136">[Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?](https://go.microsoft.com/fwlink/?LinkId=506644)</span></span>
- <span data-ttu-id="4132e-137">[GitHub：Dave Wyatt 的 WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="4132e-137">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="4132e-138">[本週 Windows PowerShell 祕訣︰本週 Windows PowerShell 秘訣︰複選清單方塊 - 及其他事項！](https://technet.microsoft.com/library/ff730950.aspx) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="4132e-138">[Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!](https://technet.microsoft.com/library/ff730950.aspx)</span></span>
