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
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="28351-104">從清單方塊選取項目</span><span class="sxs-lookup"><span data-stu-id="28351-104">Selecting Items from a List Box</span></span>

<span data-ttu-id="28351-105">使用 Windows PowerShell 3.0 和更新的版本，來建立讓使用者從清單方塊控制項選取項目的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="28351-105">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="28351-106">建立清單方塊控制項，並從其中選取項目。</span><span class="sxs-lookup"><span data-stu-id="28351-106">Create a list box control, and select items from it</span></span>

<span data-ttu-id="28351-107">將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。</span><span class="sxs-lookup"><span data-stu-id="28351-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="28351-108">指令碼一開始會載入兩個 .NET Framework 類別：**System.Drawing** 和 **System.Windows.Forms**。</span><span class="sxs-lookup"><span data-stu-id="28351-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="28351-109">接著，您會啟動新的 .NET Framework 類別 **System.Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。</span><span class="sxs-lookup"><span data-stu-id="28351-109">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="28351-110">建立 Form 類別的執行個體之後，指派值給此類別的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="28351-110">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="28351-111">**Text**。</span><span class="sxs-lookup"><span data-stu-id="28351-111">**Text.**</span></span> <span data-ttu-id="28351-112">這會成為視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="28351-112">This becomes the title of the window.</span></span>

- <span data-ttu-id="28351-113">**Size**。</span><span class="sxs-lookup"><span data-stu-id="28351-113">**Size.**</span></span> <span data-ttu-id="28351-114">這是表單的大小，單位為像素。</span><span class="sxs-lookup"><span data-stu-id="28351-114">This is the size of the form, in pixels.</span></span> <span data-ttu-id="28351-115">上述指令碼會建立 300 像素寬、200 像素高的表單。</span><span class="sxs-lookup"><span data-stu-id="28351-115">The preceding script creates a form that's 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="28351-116">**StartingPosition**。</span><span class="sxs-lookup"><span data-stu-id="28351-116">**StartingPosition.**</span></span> <span data-ttu-id="28351-117">此選擇性屬性在上述指令碼中是設定為 **CenterScreen**。</span><span class="sxs-lookup"><span data-stu-id="28351-117">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="28351-118">若未新增此屬性，Windows 會在表單開啟時選取一個位置。</span><span class="sxs-lookup"><span data-stu-id="28351-118">If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="28351-119">將 **StartingPosition** 設定為 **CenterScreen**，您就可以讓表單在每次載入時，自動顯示在畫面中間。</span><span class="sxs-lookup"><span data-stu-id="28351-119">By setting the **StartingPosition** to **CenterScreen**, you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="28351-120">接著，為您的表單建立 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="28351-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="28351-121">指定 **[確定]** 按鈕的大小與行為。</span><span class="sxs-lookup"><span data-stu-id="28351-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="28351-122">在此範例中，按鈕位置會距離表單上邊緣 120 像素，並距離左邊緣 75 像素。</span><span class="sxs-lookup"><span data-stu-id="28351-122">In this example, the button position is 120 pixels from the form's top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="28351-123">按鈕高度是 23 像素，而按鈕寬度是 75 像素。</span><span class="sxs-lookup"><span data-stu-id="28351-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="28351-124">指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。</span><span class="sxs-lookup"><span data-stu-id="28351-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

<span data-ttu-id="28351-125">同樣地，您也會建立 **[取消]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="28351-125">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="28351-126">**[取消]** 按鈕距離上邊緣 120 像素，但距離視窗左邊緣 150 像素。</span><span class="sxs-lookup"><span data-stu-id="28351-126">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="28351-127">接下來，在您的視窗上提供標籤文字，以描述您希望使用者提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="28351-127">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="28351-128">在此案例中，您希望使用者選取一部電腦。</span><span class="sxs-lookup"><span data-stu-id="28351-128">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="28351-129">新增控制項 (在此情況下為清單方塊)，讓使用者提供您在標籤文字中描述的資訊。</span><span class="sxs-lookup"><span data-stu-id="28351-129">Add the control (in this case, a list box) that lets users provide the information you've described in your label text.</span></span> <span data-ttu-id="28351-130">除了清單方塊外，還有許多其他您可以套用的控制項；如需更多控制項，請參閱 [System.Windows.Forms 命名空間](/dotnet/api/system.windows.forms)。</span><span class="sxs-lookup"><span data-stu-id="28351-130">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms).</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="28351-131">在下一節中，您可以指定您希望清單方塊向使用者顯示的值。</span><span class="sxs-lookup"><span data-stu-id="28351-131">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="28351-132">此指令碼所建立的清單方塊只允許選取一個項目。</span><span class="sxs-lookup"><span data-stu-id="28351-132">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="28351-133">若要建立允許多重選取的清單方塊控制項，請為 **SelectionMode** 屬性指定值，如下所示：`$listBox.SelectionMode = 'MultiExtended'`。</span><span class="sxs-lookup"><span data-stu-id="28351-133">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following: `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="28351-134">如需詳細資訊，請參閱[多重選擇清單方塊](Multiple-selection-List-Boxes.md)。</span><span class="sxs-lookup"><span data-stu-id="28351-134">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="28351-135">將清單方塊控制項新增至您的表單，並指示 Windows 在開啟表單時，將其開啟在其他視窗與對話方塊之上。</span><span class="sxs-lookup"><span data-stu-id="28351-135">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it's opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="28351-136">新增下面這行程式碼，以在 Windows 中顯示該表單。</span><span class="sxs-lookup"><span data-stu-id="28351-136">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="28351-137">最後，**If** 區塊內的程式碼會指示 Windows 當使用者在清單方塊中選取選項並按一下 [OK] 或按下 **Enter** 鍵時要執行的表單動作。</span><span class="sxs-lookup"><span data-stu-id="28351-137">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="28351-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28351-138">See Also</span></span>

- <span data-ttu-id="28351-139">[GitHub：Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates) (GitHub：Dave Wyatt 的 WinFormsExampleUpdates)</span><span class="sxs-lookup"><span data-stu-id="28351-139">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="28351-140">[本週 Windows PowerShell 祕訣︰從清單方塊選取項目](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10)) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="28351-140">[Windows PowerShell Tip of the Week: Selecting Items from a List Box](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))</span></span>
