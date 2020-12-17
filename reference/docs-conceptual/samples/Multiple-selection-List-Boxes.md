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
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="04aac-104">多重選擇清單方塊</span><span class="sxs-lookup"><span data-stu-id="04aac-104">Multiple-selection List Boxes</span></span>

<span data-ttu-id="04aac-105">使用 Windows PowerShell 3.0 與更新的版本，在自訂的 Windows Form 中建立多重選擇清單方塊控制項。</span><span class="sxs-lookup"><span data-stu-id="04aac-105">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="04aac-106">建立允許多重選擇的清單方塊控制項</span><span class="sxs-lookup"><span data-stu-id="04aac-106">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="04aac-107">將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。</span><span class="sxs-lookup"><span data-stu-id="04aac-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="04aac-108">指令碼一開始會載入兩個 .NET Framework 類別：**System.Drawing** 和 **System.Windows.Forms**。</span><span class="sxs-lookup"><span data-stu-id="04aac-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="04aac-109">接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。</span><span class="sxs-lookup"><span data-stu-id="04aac-109">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="04aac-110">建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="04aac-110">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="04aac-111">**Text**。</span><span class="sxs-lookup"><span data-stu-id="04aac-111">**Text.**</span></span> <span data-ttu-id="04aac-112">這會成為視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="04aac-112">This becomes the title of the window.</span></span>

- <span data-ttu-id="04aac-113">**Size**。</span><span class="sxs-lookup"><span data-stu-id="04aac-113">**Size.**</span></span> <span data-ttu-id="04aac-114">這是表單的大小，單位為像素。</span><span class="sxs-lookup"><span data-stu-id="04aac-114">This is the size of the form, in pixels.</span></span> <span data-ttu-id="04aac-115">上述指令碼會建立 300 像素寬、200 像素高的表單。</span><span class="sxs-lookup"><span data-stu-id="04aac-115">The preceding script creates a form that's 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="04aac-116">**StartingPosition**。</span><span class="sxs-lookup"><span data-stu-id="04aac-116">**StartingPosition.**</span></span> <span data-ttu-id="04aac-117">此選擇性屬性在上述指令碼中是設定為 **CenterScreen**。</span><span class="sxs-lookup"><span data-stu-id="04aac-117">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="04aac-118">若未新增此屬性，Windows 會在表單開啟時選取一個位置。</span><span class="sxs-lookup"><span data-stu-id="04aac-118">If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="04aac-119">將 **StartingPosition** 設定為 **CenterScreen**，您就可以讓表單在每次載入時，自動顯示在畫面中間。</span><span class="sxs-lookup"><span data-stu-id="04aac-119">By setting the **StartingPosition** to **CenterScreen**, you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="04aac-120">接著，為您的表單建立 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="04aac-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="04aac-121">指定 **[確定]** 按鈕的大小與行為。</span><span class="sxs-lookup"><span data-stu-id="04aac-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="04aac-122">在此範例中，按鈕位置會距離表單上邊緣 120 像素，並距離左邊緣 75 像素。</span><span class="sxs-lookup"><span data-stu-id="04aac-122">In this example, the button position is 120 pixels from the form's top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="04aac-123">按鈕高度是 23 像素，而按鈕寬度是 75 像素。</span><span class="sxs-lookup"><span data-stu-id="04aac-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="04aac-124">指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。</span><span class="sxs-lookup"><span data-stu-id="04aac-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="04aac-125">同樣地，您也會建立 **[取消]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="04aac-125">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="04aac-126">**[取消]** 按鈕距離上邊緣 120 像素，但距離視窗左邊緣 150 像素。</span><span class="sxs-lookup"><span data-stu-id="04aac-126">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="04aac-127">接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="04aac-127">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="04aac-128">新增控制項 (在此情況下為清單方塊)，讓使用者提供您在標籤文字中描述的資訊。</span><span class="sxs-lookup"><span data-stu-id="04aac-128">Add the control (in this case, a list box) that lets users provide the information you've described in your label text.</span></span> <span data-ttu-id="04aac-129">除了文字方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 [System.Windows.Forms 命名空間](/dotnet/api/system.windows.forms)。</span><span class="sxs-lookup"><span data-stu-id="04aac-129">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms).</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="04aac-130">以下說明您想要允許使用者從清單中選取多個值的指定方式。</span><span class="sxs-lookup"><span data-stu-id="04aac-130">Here's how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="04aac-131">在下一節中，您可以指定您希望清單方塊向使用者顯示的值。</span><span class="sxs-lookup"><span data-stu-id="04aac-131">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="04aac-132">指定清單方塊控制項的最大高度。</span><span class="sxs-lookup"><span data-stu-id="04aac-132">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="04aac-133">將清單方塊控制項新增至您的表單，並指示 Windows 在開啟表單時，將其開啟在其他視窗與對話方塊之上。</span><span class="sxs-lookup"><span data-stu-id="04aac-133">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it's opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="04aac-134">新增下面這行程式碼，以在 Windows 中顯示該表單。</span><span class="sxs-lookup"><span data-stu-id="04aac-134">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="04aac-135">最後，**If** 區塊內的程式碼會指示 Windows 當使用者在清單方塊中選取一或多個並按一下 **[確定]** 或按 **Enter** 鍵時要執行的表單動作。</span><span class="sxs-lookup"><span data-stu-id="04aac-135">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="04aac-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04aac-136">See Also</span></span>

- [<span data-ttu-id="04aac-137">Weekend Scripter：修正 PowerShell GUI 範例</span><span class="sxs-lookup"><span data-stu-id="04aac-137">Weekend Scripter: Fixing PowerShell GUI Examples</span></span>](https://devblogs.microsoft.com/scripting/weekend-scripter-fixing-powershell-gui-examples/)
- <span data-ttu-id="04aac-138">[GitHub：Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates) (GitHub：Dave Wyatt 的 WinFormsExampleUpdates)</span><span class="sxs-lookup"><span data-stu-id="04aac-138">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="04aac-139">[本週 Windows PowerShell 祕訣︰本週 Windows PowerShell 秘訣︰複選清單方塊 - 及其他事項！](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730950(v=technet.10)) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="04aac-139">[Windows PowerShell Tip of the Week: Multi-Select List Boxes - And More!](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730950(v=technet.10))</span></span>
