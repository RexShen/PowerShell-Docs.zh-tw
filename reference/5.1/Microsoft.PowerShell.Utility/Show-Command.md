---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: d3ff6fe599873edafdda04b3fe17ae01d88c049d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203123"
---
# <span data-ttu-id="80d05-103">Show-Command</span><span class="sxs-lookup"><span data-stu-id="80d05-103">Show-Command</span></span>

## <span data-ttu-id="80d05-104">概要</span><span class="sxs-lookup"><span data-stu-id="80d05-104">SYNOPSIS</span></span>
<span data-ttu-id="80d05-105">在圖形視窗中顯示 PowerShell 命令資訊。</span><span class="sxs-lookup"><span data-stu-id="80d05-105">Displays PowerShell command information in a graphical window.</span></span>

## <span data-ttu-id="80d05-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="80d05-106">SYNTAX</span></span>

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="80d05-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="80d05-107">DESCRIPTION</span></span>

<span data-ttu-id="80d05-108">此 `Show-Command` Cmdlet 可讓您在命令視窗中建立 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-108">The `Show-Command` cmdlet lets you create a PowerShell command in a command window.</span></span> <span data-ttu-id="80d05-109">您可以使用命令視窗的功能來執行命令，或讓它向您傳回命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-109">You can use the features of the command window to run the command or have it return the command to you.</span></span>

<span data-ttu-id="80d05-110">`Show-Command` 是非常有用的教學與學習工具。</span><span class="sxs-lookup"><span data-stu-id="80d05-110">`Show-Command` is a very useful teaching and learning tool.</span></span> <span data-ttu-id="80d05-111">`Show-Command` 適用于所有命令類型，包括 Cmdlet、函式、工作流程及 CIM 命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-111">`Show-Command` works on all command types, including cmdlets, functions, workflows and CIM commands.</span></span>

<span data-ttu-id="80d05-112">如果沒有參數， `Show-Command` 則會顯示命令視窗，其中會列出所有已安裝模組中的所有可用命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-112">Without parameters, `Show-Command` displays a command window that lists all available commands in all installed modules.</span></span> <span data-ttu-id="80d05-113">若要尋找模組中的命令，請從模組下拉式清單中選取模組。</span><span class="sxs-lookup"><span data-stu-id="80d05-113">To find the commands in a module, select the module from the Modules drop-down list.</span></span> <span data-ttu-id="80d05-114">若要選取命令，請按一下命令名稱。</span><span class="sxs-lookup"><span data-stu-id="80d05-114">To select a command, click the command name.</span></span>

<span data-ttu-id="80d05-115">若要使用命令視窗，請選取命令，方法是使用名稱，或按一下 **命令清單中** 的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="80d05-115">To use the command window, select a command, either by using the Name or by clicking the command name in the **Commands** list.</span></span> <span data-ttu-id="80d05-116">每個參數集都會顯示在個別的索引標籤上。星號表示必要參數。</span><span class="sxs-lookup"><span data-stu-id="80d05-116">Each parameter set is displayed on a separate tab. Asterisks indicate the mandatory parameters.</span></span> <span data-ttu-id="80d05-117">若要輸入參數值，請在文字方塊中輸入值，或從下拉式清單方塊中選取值。</span><span class="sxs-lookup"><span data-stu-id="80d05-117">To enter values for a parameter, type the value in the text box or select the value from the drop-down box.</span></span> <span data-ttu-id="80d05-118">若要新增切換參數，請按一下參數核取方塊來加以選取。</span><span class="sxs-lookup"><span data-stu-id="80d05-118">To add a switch parameter, click to select the parameter check box.</span></span>

<span data-ttu-id="80d05-119">當您準備好時，您可以按一下 **Copy** 來將您已經建立的命令複製到剪貼簿或按一下 **Run** 來執行命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-119">When you're ready, you can click **Copy** to copy the command that you've created to the clipboard or click **Run** to run the command.</span></span> <span data-ttu-id="80d05-120">您也可以使用 **PassThru** 參數將命令傳回到主機程式，例如 PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="80d05-120">You can also use the **PassThru** parameter to return the command to the host program, such as the PowerShell console.</span></span> <span data-ttu-id="80d05-121">若要取消命令選取範圍並返回顯示所有命令的視圖，請按 Ctrl 並按一下選取的命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-121">To cancel the command selection and return to the view that displays all commands, press Ctrl and click the selected command.</span></span>

<span data-ttu-id="80d05-122">在 (ISE) 的 PowerShell 整合式腳本環境中， `Show-Command` 預設會顯示視窗的變化。</span><span class="sxs-lookup"><span data-stu-id="80d05-122">In the PowerShell Integrated Scripting Environment (ISE), a variation of the `Show-Command` window is displayed by default.</span></span> <span data-ttu-id="80d05-123">如需使用此命令視窗的詳細資訊，請參閱 PowerShell ISE 說明主題。</span><span class="sxs-lookup"><span data-stu-id="80d05-123">For information about using this command window, see the PowerShell ISE Help topics.</span></span>

<span data-ttu-id="80d05-124">此 Cmdlet 是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="80d05-124">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="80d05-125">由於此 Cmdlet 需要使用者介面，因此無法在 Windows Server Core 或 Windows Nano Server 上運作。</span><span class="sxs-lookup"><span data-stu-id="80d05-125">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="80d05-126">只有支援 Windows 桌面的 Windows 系統才能使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80d05-126">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="80d05-127">範例</span><span class="sxs-lookup"><span data-stu-id="80d05-127">EXAMPLES</span></span>

### <span data-ttu-id="80d05-128">範例1：開啟 [命令] 視窗</span><span class="sxs-lookup"><span data-stu-id="80d05-128">Example 1: Open the Commands window</span></span>

<span data-ttu-id="80d05-129">此範例會顯示視窗的預設視圖 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="80d05-129">This example displays the default view of the `Show-Command` window.</span></span> <span data-ttu-id="80d05-130">[ **命令** ] 視窗會顯示電腦上已安裝的所有模組中所有命令的清單。</span><span class="sxs-lookup"><span data-stu-id="80d05-130">The **Commands** window displays a list of all commands in all modules that are installed on the computer.</span></span>

```powershell
Show-Command
```

### <span data-ttu-id="80d05-131">範例2：在 [命令] 視窗中開啟 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80d05-131">Example 2: Open a cmdlet in the Commands window</span></span>

<span data-ttu-id="80d05-132">此範例會 `Invoke-Command` 在 **命令** 視窗中顯示 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80d05-132">This example display the `Invoke-Command` cmdlet in the **Command** window.</span></span> <span data-ttu-id="80d05-133">您可以使用此顯示來執行 `Invoke-Command` 命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-133">You can use this display to run `Invoke-Command` commands.</span></span>

```powershell
Show-Command -Name "Invoke-Command"
```

### <span data-ttu-id="80d05-134">範例3：使用指定的參數開啟 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80d05-134">Example 3: Open a cmdlet with specified parameters</span></span>

<span data-ttu-id="80d05-135">此命令會開啟 `Show-Command` Cmdlet 的視窗 `Connect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="80d05-135">This command opens a `Show-Command` window for the`Connect-PSSession`cmdlet.</span></span>

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

<span data-ttu-id="80d05-136">**Height** 和 **Width** 參數指定命令視窗的維度。</span><span class="sxs-lookup"><span data-stu-id="80d05-136">The **Height** and **Width** parameters specify the dimension of the command window.</span></span> <span data-ttu-id="80d05-137">**ErrorPopup** 參數會顯示錯誤命令視窗。</span><span class="sxs-lookup"><span data-stu-id="80d05-137">The **ErrorPopup** parameter displays the error command window.</span></span>

<span data-ttu-id="80d05-138">當您按一下 [ **執行** ] 時， `Connect-PSSession` 命令就會執行，就如同您在 `Connect-PSSession` 命令列輸入命令一樣。</span><span class="sxs-lookup"><span data-stu-id="80d05-138">When you click **Run** , the `Connect-PSSession` command runs, just as would if you typed the `Connect-PSSession` command at the command line.</span></span>

### <span data-ttu-id="80d05-139">範例4：指定 Cmdlet 的新預設參數值</span><span class="sxs-lookup"><span data-stu-id="80d05-139">Example 4: Specify new default parameter values for a cmdlet</span></span>

<span data-ttu-id="80d05-140">此範例會使用 `$PSDefaultParameterValues` 自動變數，為 Cmdlet 的 **高度** 、 **寬度** 和 **ErrorPopup** 參數設定新的預設值 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="80d05-140">This example uses the `$PSDefaultParameterValues` automatic variable to set new default values for the **Height** , **Width** , and **ErrorPopup** parameters of the `Show-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

<span data-ttu-id="80d05-141">現在當您執行 `Show-Command` 命令時，會自動套用新的預設值。</span><span class="sxs-lookup"><span data-stu-id="80d05-141">Now when you run a `Show-Command` command, the new defaults are applied automatically.</span></span> <span data-ttu-id="80d05-142">若要在每個 PowerShell 會話中使用這些預設值，請將 `$PSDefaultParameterValues` 變數新增至您的 powershell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="80d05-142">To use these default values in every PowerShell session, add the `$PSDefaultParameterValues` variable to your PowerShell profile.</span></span> <span data-ttu-id="80d05-143">如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) 和 [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md)。</span><span class="sxs-lookup"><span data-stu-id="80d05-143">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) and [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).</span></span>

### <span data-ttu-id="80d05-144">範例5：將輸出傳送至方格視圖</span><span class="sxs-lookup"><span data-stu-id="80d05-144">Example 5: Send output to a grid view</span></span>

<span data-ttu-id="80d05-145">此命令顯示如何 `Show-Command` 搭配使用和 `Out-GridView` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80d05-145">This command shows how to use the `Show-Command` and `Out-GridView` cmdlets together.</span></span>

```powershell
Show-Command Get-ChildItem | Out-GridView
```

<span data-ttu-id="80d05-146">此命令會使用 `Show-Command` Cmdlet 來開啟 Cmdlet 的命令視窗 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="80d05-146">The command uses the `Show-Command` cmdlet to open a command window for the`Get-ChildItem`cmdlet.</span></span>
<span data-ttu-id="80d05-147">當您按一下 [ **執行** ] 按鈕時， `Get-ChildItem` 命令會執行並產生輸出。</span><span class="sxs-lookup"><span data-stu-id="80d05-147">When you click the **Run** button, the `Get-ChildItem` command runs and generates output.</span></span> <span data-ttu-id="80d05-148">管線運算子 ( |) 將命令的輸出傳送 `Get-ChildItem` 至 `Out-GridView` Cmdlet，此 Cmdlet 會 `Get-ChildItem` 在互動式視窗中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="80d05-148">The pipeline operator ( | ) sends the output of the `Get-ChildItem` command to the `Out-GridView` cmdlet, which displays the `Get-ChildItem` output in an interactive window.</span></span>

### <span data-ttu-id="80d05-149">範例6：顯示您在命令視窗中建立的命令</span><span class="sxs-lookup"><span data-stu-id="80d05-149">Example 6: Display a command that you create in the Commands window</span></span>

<span data-ttu-id="80d05-150">此範例顯示您在視窗中建立的命令 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="80d05-150">This example shows the command that you created in the `Show-Command` window.</span></span> <span data-ttu-id="80d05-151">此命令會使用 **PassThru** 參數，它會 `Show-Command` 在字串中傳回結果。</span><span class="sxs-lookup"><span data-stu-id="80d05-151">The command uses the **PassThru** parameter, which returns the `Show-Command` results in a string.</span></span>

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

<span data-ttu-id="80d05-152">例如，如果您使用此 `Show-Command` 視窗來建立一個命令，以 `Get-EventLog` 取得 Windows PowerShell 事件記錄檔中的五個最新事件，然後按一下 **[確定]** ，命令會傳回上面顯示的輸出。</span><span class="sxs-lookup"><span data-stu-id="80d05-152">For example, if you use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log, and then click **OK** , the command returns the output shown above.</span></span> <span data-ttu-id="80d05-153">查看命令字串可協助您瞭解 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="80d05-153">Viewing the command string helps you learn PowerShell.</span></span>

### <span data-ttu-id="80d05-154">範例7：將命令儲存至變數</span><span class="sxs-lookup"><span data-stu-id="80d05-154">Example 7: Save a command to a variable</span></span>

<span data-ttu-id="80d05-155">此範例示範如何執行當您使用 Cmdlet 的 **PassThru** 參數時所取得的命令字串 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="80d05-155">This example shows how to run the command string that you get when you use the **PassThru** parameter of the `Show-Command` cmdlet.</span></span> <span data-ttu-id="80d05-156">這項策略可讓您看到命令並使用命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-156">This strategy lets you see the command and use it.</span></span>

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

<span data-ttu-id="80d05-157">第一個命令會使用 Cmdlet 的 **PassThru** 參數 `Show-Command` ，並將命令的結果儲存在變數中 `$C` 。</span><span class="sxs-lookup"><span data-stu-id="80d05-157">The first command uses the **PassThru** parameter of the `Show-Command` cmdlet and saves the results of the command in the `$C` variable.</span></span> <span data-ttu-id="80d05-158">在此情況下，我們會使用 `Show-Command` 視窗來建立 `Get-EventLog` 命令，以取得 Windows PowerShell 事件記錄檔中的五個最新事件。</span><span class="sxs-lookup"><span data-stu-id="80d05-158">In this case, we use the `Show-Command` window to create a `Get-EventLog` command that gets the five newest events in the Windows PowerShell event log.</span></span> <span data-ttu-id="80d05-159">當您按一下 **[確定]** 時， `Show-Command` 會傳回命令字串，該字串會儲存在 `$C` 變數中。</span><span class="sxs-lookup"><span data-stu-id="80d05-159">When you click **OK** , `Show-Command` returns the command string, which is saved in the `$C` variable.</span></span>

### <span data-ttu-id="80d05-160">範例8：將命令的輸出儲存至變數</span><span class="sxs-lookup"><span data-stu-id="80d05-160">Example 8: Save the output of a command to a variable</span></span>

<span data-ttu-id="80d05-161">此範例使用 **ErrorPopup** 參數，將命令的輸出儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="80d05-161">This example uses the **ErrorPopup** parameter to save the output of a command in a variable.</span></span>

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

<span data-ttu-id="80d05-162">除了在視窗中顯示錯誤之外， **ErrorPopup** 還會將命令輸出傳回目前的命令，而不是建立新的命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-162">In addition to displaying errors in a window, **ErrorPopup** returns command output to the current command, instead of creating a new command.</span></span> <span data-ttu-id="80d05-163">當您執行此命令時， `Show-Command` 會開啟視窗。</span><span class="sxs-lookup"><span data-stu-id="80d05-163">When you run this command, the `Show-Command` window opens.</span></span> <span data-ttu-id="80d05-164">您可以使用視窗功能來設定參數值。</span><span class="sxs-lookup"><span data-stu-id="80d05-164">You can use the window features to set parameter values.</span></span> <span data-ttu-id="80d05-165">若要執行命令，請按一下視窗中的 [ **執行** `Show-Command` ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="80d05-165">To run the command, click the **Run** button in the `Show-Command` window.</span></span>

## <span data-ttu-id="80d05-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="80d05-166">PARAMETERS</span></span>

### <span data-ttu-id="80d05-167">-ErrorPopup</span><span class="sxs-lookup"><span data-stu-id="80d05-167">-ErrorPopup</span></span>

<span data-ttu-id="80d05-168">指出 Cmdlet 除了在命令列顯示錯誤之外，還會在快顯視窗中顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="80d05-168">Indicates that the cmdlet displays errors in a pop-up window, in addition to displaying them at the command line.</span></span> <span data-ttu-id="80d05-169">根據預設，當視窗中執行的命令 `Show-Command` 產生錯誤時，錯誤只會在命令列中顯示。</span><span class="sxs-lookup"><span data-stu-id="80d05-169">By default, when a command that is run in a `Show-Command` window generates an error, the error is displayed only at the command line.</span></span>

<span data-ttu-id="80d05-170">此外，當您使用視窗) 中的 [ **執行** ] 按鈕來執行命令 (時 `Show-Command` ， **ErrorPopup** 參數會將命令結果傳回給目前的命令，而不是執行命令並將其輸出傳回至新的命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-170">Also, when you run the command (by using the **Run** button in the `Show-Command` window), the **ErrorPopup** parameter returns the command results to the current command, instead of running the command and returning its output to a new command.</span></span> <span data-ttu-id="80d05-171">您可以使用這項功能將命令結果儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="80d05-171">You can use this feature to save the command results in a variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80d05-172">-高度</span><span class="sxs-lookup"><span data-stu-id="80d05-172">-Height</span></span>

<span data-ttu-id="80d05-173">指定視窗的高度（ `Show-Command` 以圖元為單位）。</span><span class="sxs-lookup"><span data-stu-id="80d05-173">Specifies the height of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="80d05-174">輸入一個介於 300 和螢幕解析度像素數目之間的值。</span><span class="sxs-lookup"><span data-stu-id="80d05-174">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="80d05-175">如果值太大而無法在畫面上顯示命令視窗，則會 `Show-Command` 產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="80d05-175">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="80d05-176">預設高度為 600 像素。</span><span class="sxs-lookup"><span data-stu-id="80d05-176">The default height is 600 pixels.</span></span> <span data-ttu-id="80d05-177">針對 `Show-Command` 包含 **Name** 參數的命令，預設高度為300圖元。</span><span class="sxs-lookup"><span data-stu-id="80d05-177">For a `Show-Command` command that includes the **Name** parameter, the default height is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80d05-178">-Name</span><span class="sxs-lookup"><span data-stu-id="80d05-178">-Name</span></span>

<span data-ttu-id="80d05-179">顯示指定命令的命令視窗。</span><span class="sxs-lookup"><span data-stu-id="80d05-179">Displays a command window for the specified command.</span></span> <span data-ttu-id="80d05-180">輸入一個命令的名稱，例如 Cmdlet、function 或 CIM 命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="80d05-180">Enter the name of one command, such as the name of a cmdlet, function, or CIM command.</span></span> <span data-ttu-id="80d05-181">如果您省略此參數，則會 `Show-Command` 顯示命令視窗，其中會列出電腦上安裝的所有模組中的所有 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="80d05-181">If you omit this parameter, `Show-Command` displays a command window that lists all of the PowerShell commands in all modules installed on the computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80d05-182">-NoCommonParameter</span><span class="sxs-lookup"><span data-stu-id="80d05-182">-NoCommonParameter</span></span>

<span data-ttu-id="80d05-183">指出此 Cmdlet 會省略命令顯示的一般參數區段。</span><span class="sxs-lookup"><span data-stu-id="80d05-183">Indicates that this cmdlet omits the Common Parameters section of the command display.</span></span> <span data-ttu-id="80d05-184">根據預設，一般參數會出現在命令視窗底部的可展開區段中。</span><span class="sxs-lookup"><span data-stu-id="80d05-184">By default, the Common Parameters appear in an expandable section at the bottom of the command window.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80d05-185">-PassThru</span><span class="sxs-lookup"><span data-stu-id="80d05-185">-PassThru</span></span>

<span data-ttu-id="80d05-186">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="80d05-186">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="80d05-187">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="80d05-187">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="80d05-188">若要執行命令字串，請在命令提示字元中複製並貼上，或將它儲存在變數中，然後使用 `Invoke-Expression` Cmdlet 來執行變數中的字串。</span><span class="sxs-lookup"><span data-stu-id="80d05-188">To run the command string, copy and paste it at the command prompt or save it in a variable and use the `Invoke-Expression` cmdlet to run the string in the variable.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80d05-189">-Width</span><span class="sxs-lookup"><span data-stu-id="80d05-189">-Width</span></span>

<span data-ttu-id="80d05-190">指定視窗的寬度 `Show-Command` （以圖元為單位）。</span><span class="sxs-lookup"><span data-stu-id="80d05-190">Specifies the width of the `Show-Command` window in pixels.</span></span> <span data-ttu-id="80d05-191">輸入一個介於 300 和螢幕解析度像素數目之間的值。</span><span class="sxs-lookup"><span data-stu-id="80d05-191">Enter a value between 300 and the number of pixels in the screen resolution.</span></span> <span data-ttu-id="80d05-192">如果值太大而無法在畫面上顯示命令視窗，則會 `Show-Command` 產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="80d05-192">If the value is too large to display the command window on the screen, `Show-Command` generates an error.</span></span> <span data-ttu-id="80d05-193">預設寬度為 300 像素。</span><span class="sxs-lookup"><span data-stu-id="80d05-193">The default width is 300 pixels.</span></span>

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="80d05-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="80d05-194">CommonParameters</span></span>

<span data-ttu-id="80d05-195">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="80d05-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="80d05-196">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="80d05-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="80d05-197">輸入</span><span class="sxs-lookup"><span data-stu-id="80d05-197">INPUTS</span></span>

### <span data-ttu-id="80d05-198">無</span><span class="sxs-lookup"><span data-stu-id="80d05-198">None</span></span>

<span data-ttu-id="80d05-199">您無法透過管道傳送輸入 `Show-Command` 。</span><span class="sxs-lookup"><span data-stu-id="80d05-199">You cannot pipe input to `Show-Command`.</span></span>

## <span data-ttu-id="80d05-200">輸出</span><span class="sxs-lookup"><span data-stu-id="80d05-200">OUTPUTS</span></span>

### <span data-ttu-id="80d05-201">None、System.string、System.object</span><span class="sxs-lookup"><span data-stu-id="80d05-201">None, System.String, System.Object</span></span>

<span data-ttu-id="80d05-202">當您使用 **PassThru** 參數時，會傳回 `Show-Command` 命令字串。</span><span class="sxs-lookup"><span data-stu-id="80d05-202">When you use the **PassThru** parameter, `Show-Command` returns a command string.</span></span> <span data-ttu-id="80d05-203">當您使用 **ErrorPopup** 參數時，會將 `Show-Command` 命令輸出 (任何物件) 傳回。</span><span class="sxs-lookup"><span data-stu-id="80d05-203">When you use the **ErrorPopup** parameter, `Show-Command` returns the command output (any object).</span></span> <span data-ttu-id="80d05-204">否則，不 `Show-Command` 會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="80d05-204">Otherwise, `Show-Command` does not generate any output.</span></span>

## <span data-ttu-id="80d05-205">注意</span><span class="sxs-lookup"><span data-stu-id="80d05-205">NOTES</span></span>

<span data-ttu-id="80d05-206">`Show-Command` 在遠端會話中無法運作。</span><span class="sxs-lookup"><span data-stu-id="80d05-206">`Show-Command` does not work in remote sessions.</span></span>

## <span data-ttu-id="80d05-207">相關連結</span><span class="sxs-lookup"><span data-stu-id="80d05-207">RELATED LINKS</span></span>
