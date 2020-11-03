---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 建立圖形化日期選擇器
description: 本文說明如何使用 Windows PowerShell 中的 .NET Framework 表單建置功能，建立自訂日曆樣式控制項。
ms.openlocfilehash: b73c9ba78817af7c38c20642402752765a7a3674
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500499"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="cbab3-104">建立圖形化日期選擇器</span><span class="sxs-lookup"><span data-stu-id="cbab3-104">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="cbab3-105">使用 Windows PowerShell 3.0 與更新的版本建立表單，表單上具有圖形化日曆樣式控制項，可讓使用者選取月份中的某個日期。</span><span class="sxs-lookup"><span data-stu-id="cbab3-105">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="cbab3-106">建立圖形化的日期選擇器控制項</span><span class="sxs-lookup"><span data-stu-id="cbab3-106">Create a graphical date-picker control</span></span>

<span data-ttu-id="cbab3-107">將下列程式碼複製並貼上到 Windows PowerShell ISE，然後將它儲存為 Windows PowerShell 指令碼 (.ps1)。</span><span class="sxs-lookup"><span data-stu-id="cbab3-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="cbab3-108">指令碼一開始會載入兩個 .NET Framework 類別： **System.Drawing** 和 **System.Windows.Forms** 。</span><span class="sxs-lookup"><span data-stu-id="cbab3-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="cbab3-109">接著，您會啟動新的 .NET Framework 類別 **Windows.Forms.Form** 的執行個體，這樣可以提供空白表單或視窗讓您可以開始新增控制項。</span><span class="sxs-lookup"><span data-stu-id="cbab3-109">You then start a new instance of the .NET Framework class **Windows.Forms.Form** ; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="cbab3-110">此範例會使用 **Property** 屬性與雜湊表為此類別的四個屬性指派值。</span><span class="sxs-lookup"><span data-stu-id="cbab3-110">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="cbab3-111">**StartPosition** ：若未新增此屬性，Windows 會在表單開啟時選取一個位置。</span><span class="sxs-lookup"><span data-stu-id="cbab3-111">**StartPosition** : If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="cbab3-112">將此屬性設定為 **CenterScreen** ，您就可以讓表單在每次載入時，自動顯示在畫面中間。</span><span class="sxs-lookup"><span data-stu-id="cbab3-112">By setting this property to **CenterScreen** , you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="cbab3-113">**Size** ：這是表單的大小，單位為像素。</span><span class="sxs-lookup"><span data-stu-id="cbab3-113">**Size** : This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="cbab3-114">上述指令碼會建立 243 像素寬、230 像素高的表單。</span><span class="sxs-lookup"><span data-stu-id="cbab3-114">The preceding script creates a form that's 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="cbab3-115">**Text** ：這會成為視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="cbab3-115">**Text** : This becomes the title of the window.</span></span>

4. <span data-ttu-id="cbab3-116">**Topmost** ：透過將此屬性設定為 `$true`，您可以強制視窗開啟在其他已開啟視窗與對話方塊的上方。</span><span class="sxs-lookup"><span data-stu-id="cbab3-116">**Topmost** : By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="cbab3-117">接著，在您的表單中建立並新增日曆控制項。</span><span class="sxs-lookup"><span data-stu-id="cbab3-117">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="cbab3-118">在此範例中，目前的日期並未反白顯示或圈起來。</span><span class="sxs-lookup"><span data-stu-id="cbab3-118">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="cbab3-119">使用者一次只能在日曆上選取一個日期。</span><span class="sxs-lookup"><span data-stu-id="cbab3-119">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="cbab3-120">接著，為您的表單建立 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cbab3-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="cbab3-121">指定 **[確定]** 按鈕的大小與行為。</span><span class="sxs-lookup"><span data-stu-id="cbab3-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="cbab3-122">在此範例中，按鈕位置會距離表單上邊緣 165 像素，並距離左邊緣 38 像素。</span><span class="sxs-lookup"><span data-stu-id="cbab3-122">In this example, the button position is 165 pixels from the form's top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="cbab3-123">按鈕高度是 23 像素，而按鈕寬度是 75 像素。</span><span class="sxs-lookup"><span data-stu-id="cbab3-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="cbab3-124">指令碼會使用預先定義的 Windows Forms 類型來決定按鈕行為。</span><span class="sxs-lookup"><span data-stu-id="cbab3-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

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

<span data-ttu-id="cbab3-125">同樣地，您也會建立 **[取消]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cbab3-125">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="cbab3-126">[Cancel] 按鈕距離上邊緣 165 像素，但距離視窗左邊緣 113 像素。</span><span class="sxs-lookup"><span data-stu-id="cbab3-126">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

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

<span data-ttu-id="cbab3-127">新增下面這行程式碼，以在 Windows 中顯示該表單。</span><span class="sxs-lookup"><span data-stu-id="cbab3-127">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="cbab3-128">最後， `if` 區塊內的程式碼會指示 Windows 當使用者選取日曆上的日期並按一下 [確定] 按鈕或按下 **Enter** 鍵時要執行的表單動作。</span><span class="sxs-lookup"><span data-stu-id="cbab3-128">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="cbab3-129">Windows PowerShell 會將選取的日期顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="cbab3-129">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="cbab3-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbab3-130">See Also</span></span>

- <span data-ttu-id="cbab3-131">[GitHub：Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates) (GitHub：Dave Wyatt 的 WinFormsExampleUpdates)</span><span class="sxs-lookup"><span data-stu-id="cbab3-131">[GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)</span></span>
- <span data-ttu-id="cbab3-132">[本週 Windows PowerShell 秘訣︰建立圖形化日期選擇器](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="cbab3-132">[Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))</span></span>
