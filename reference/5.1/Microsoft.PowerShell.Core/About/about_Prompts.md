---
description: 描述函式 `Prompt` ，並示範如何建立自訂 `Prompt` 函數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 15746fe1ce2c79189dd604b5b6244e337ad389a1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207600"
---
# <a name="about-prompts"></a><span data-ttu-id="1aa60-104">關於提示字元</span><span class="sxs-lookup"><span data-stu-id="1aa60-104">About Prompts</span></span>

## <a name="short-description"></a><span data-ttu-id="1aa60-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="1aa60-105">Short description</span></span>
<span data-ttu-id="1aa60-106">描述函式 `Prompt` ，並示範如何建立自訂 `Prompt` 函數。</span><span class="sxs-lookup"><span data-stu-id="1aa60-106">Describes the `Prompt` function and demonstrates how to create a custom `Prompt` function.</span></span>

## <a name="long-description"></a><span data-ttu-id="1aa60-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="1aa60-107">Long description</span></span>

<span data-ttu-id="1aa60-108">PowerShell 命令提示字元指出 PowerShell 已準備好執行命令：</span><span class="sxs-lookup"><span data-stu-id="1aa60-108">The PowerShell command prompt indicates that PowerShell is ready to run a command:</span></span>

```
PS C:\>
```

<span data-ttu-id="1aa60-109">PowerShell 提示字元是由內建函數所決定 `Prompt` 。</span><span class="sxs-lookup"><span data-stu-id="1aa60-109">The PowerShell prompt is determined by the built-in `Prompt` function.</span></span> <span data-ttu-id="1aa60-110">您可以藉由建立自己的函 `Prompt` 式，並將它儲存在您的 PowerShell 設定檔中，來自訂提示。</span><span class="sxs-lookup"><span data-stu-id="1aa60-110">You can customize the prompt by creating your own `Prompt` function and saving it in your PowerShell profile.</span></span>

## <a name="about-the-prompt-function"></a><span data-ttu-id="1aa60-111">關於 Prompt 函數</span><span class="sxs-lookup"><span data-stu-id="1aa60-111">About the Prompt function</span></span>

<span data-ttu-id="1aa60-112">此函式會 `Prompt` 判斷 PowerShell 提示字元的外觀。</span><span class="sxs-lookup"><span data-stu-id="1aa60-112">The `Prompt` function determines the appearance of the PowerShell prompt.</span></span>
<span data-ttu-id="1aa60-113">PowerShell 隨附內建 `Prompt` 功能，但您可以藉由定義自己的函式來覆寫它 `Prompt` 。</span><span class="sxs-lookup"><span data-stu-id="1aa60-113">PowerShell comes with a built-in `Prompt` function, but you can override it by defining your own `Prompt` function.</span></span>

<span data-ttu-id="1aa60-114">`Prompt`函數具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="1aa60-114">The `Prompt` function has the following syntax:</span></span>

```powershell
function Prompt { <function-body> }
```

<span data-ttu-id="1aa60-115">`Prompt`函數必須傳回物件。</span><span class="sxs-lookup"><span data-stu-id="1aa60-115">The `Prompt` function must return an object.</span></span> <span data-ttu-id="1aa60-116">最佳做法是傳回字串或格式化為字串的物件。</span><span class="sxs-lookup"><span data-stu-id="1aa60-116">As a best practice, return a string or an object that is formatted as a string.</span></span> <span data-ttu-id="1aa60-117">建議的最大長度為 80 個字元。</span><span class="sxs-lookup"><span data-stu-id="1aa60-117">The maximum recommended length is 80 characters.</span></span>

<span data-ttu-id="1aa60-118">例如，下列函數會傳回 `Prompt` "Hello，World" 字串，後面接著右角括弧 (`>`) 。</span><span class="sxs-lookup"><span data-stu-id="1aa60-118">For example, the following `Prompt` function returns a "Hello, World" string followed by a  right angle bracket (`>`).</span></span>

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a><span data-ttu-id="1aa60-119">取得提示字元函式</span><span class="sxs-lookup"><span data-stu-id="1aa60-119">Getting the Prompt function</span></span>

<span data-ttu-id="1aa60-120">若要取得函式 `Prompt` ，請使用 `Get-Command` Cmdlet 或使用函式 `Get-Item` 磁片磁碟機中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1aa60-120">To get the `Prompt` function, use the `Get-Command` cmdlet or use the `Get-Item` cmdlet in the Function drive.</span></span>

<span data-ttu-id="1aa60-121">例如：</span><span class="sxs-lookup"><span data-stu-id="1aa60-121">For example:</span></span>

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

<span data-ttu-id="1aa60-122">若要取得設定提示值的腳本，請使用點方法來取得函數的 **ScriptBlock** 屬性 `Prompt` 。</span><span class="sxs-lookup"><span data-stu-id="1aa60-122">To get the script that sets the value of the prompt, use the dot method to get the **ScriptBlock** property of the `Prompt` function.</span></span>

<span data-ttu-id="1aa60-123">例如：</span><span class="sxs-lookup"><span data-stu-id="1aa60-123">For example:</span></span>

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

<span data-ttu-id="1aa60-124">就像所有的函式一樣，此函式 `Prompt` 會儲存在 `Function:` 磁片磁碟機中。</span><span class="sxs-lookup"><span data-stu-id="1aa60-124">Like all functions, the `Prompt` function is stored in the `Function:` drive.</span></span>
<span data-ttu-id="1aa60-125">若要顯示用來建立目前函數的腳本 `Prompt` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="1aa60-125">To display the script that creates the current `Prompt` function, type:</span></span>

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a><span data-ttu-id="1aa60-126">預設提示字元</span><span class="sxs-lookup"><span data-stu-id="1aa60-126">The default prompt</span></span>

<span data-ttu-id="1aa60-127">只有當 `Prompt` 函數產生錯誤或未傳回物件時，才會顯示預設提示字元。</span><span class="sxs-lookup"><span data-stu-id="1aa60-127">The default prompt appears only when the `Prompt` function generates an error or does not return an object.</span></span>

<span data-ttu-id="1aa60-128">預設的 PowerShell 提示字元是：</span><span class="sxs-lookup"><span data-stu-id="1aa60-128">The default PowerShell prompt is:</span></span>

```
PS>
```

<span data-ttu-id="1aa60-129">例如，下列命令會將函數設定 `Prompt` 為 `$null` ，這是不正確。</span><span class="sxs-lookup"><span data-stu-id="1aa60-129">For example, the following command sets the `Prompt` function to `$null`, which is invalid.</span></span> <span data-ttu-id="1aa60-130">因此會顯示預設提示字元。</span><span class="sxs-lookup"><span data-stu-id="1aa60-130">As a result, the default prompt appears.</span></span>

```powershell
PS C:\> function prompt {$null}
PS>
```

<span data-ttu-id="1aa60-131">因為 PowerShell 隨附內建提示，所以您通常不會看到預設提示字元。</span><span class="sxs-lookup"><span data-stu-id="1aa60-131">Because PowerShell comes with a built-in prompt, you usually do not see the default prompt.</span></span>

### <a name="built-in-prompt"></a><span data-ttu-id="1aa60-132">內建提示</span><span class="sxs-lookup"><span data-stu-id="1aa60-132">Built-in prompt</span></span>

<span data-ttu-id="1aa60-133">PowerShell 包含內建 `Prompt` 函數。</span><span class="sxs-lookup"><span data-stu-id="1aa60-133">PowerShell includes a built-in `Prompt` function.</span></span>

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="1aa60-134">此函式 `Test-Path` 會使用 Cmdlet 來判斷是否 `$PSDebugContext` 已填入自動變數。</span><span class="sxs-lookup"><span data-stu-id="1aa60-134">The function uses the `Test-Path` cmdlet to determine whether the `$PSDebugContext` automatic variable is populated.</span></span> <span data-ttu-id="1aa60-135">如果 `$PSDebugContext` 已填入，則您處於「偵測」模式，並且 `[DBG]:` 會新增至提示字元，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1aa60-135">If `$PSDebugContext` is populated, you are in debugging mode, and `[DBG]:` is added to the prompt, as follows:</span></span>

```Output
[DBG]: PS C:\ps-test>
```

<span data-ttu-id="1aa60-136">如果 `$PSDebugContext` 未填入，則函式會新增 `PS` 到提示字元。</span><span class="sxs-lookup"><span data-stu-id="1aa60-136">If `$PSDebugContext` is not populated, the function adds `PS` to the prompt.</span></span>
<span data-ttu-id="1aa60-137">而且，此函式會使用 `Get-Location` Cmdlet 來取得目前的檔案系統目錄位置。</span><span class="sxs-lookup"><span data-stu-id="1aa60-137">And, the function uses the `Get-Location` cmdlet to get the current file system directory location.</span></span> <span data-ttu-id="1aa60-138">然後，它會將右角括弧新增 (`>`) 。</span><span class="sxs-lookup"><span data-stu-id="1aa60-138">Then, it adds a right angle bracket (`>`).</span></span>

<span data-ttu-id="1aa60-139">例如：</span><span class="sxs-lookup"><span data-stu-id="1aa60-139">For example:</span></span>

```Output
PS C:\ps-test>
```

<span data-ttu-id="1aa60-140">如果您是在嵌套的提示字元中，函式會將兩個角括弧新增 (`>>`) 到提示字元。</span><span class="sxs-lookup"><span data-stu-id="1aa60-140">If you are in a nested prompt, the function adds two angle brackets (`>>`) to the prompt.</span></span> <span data-ttu-id="1aa60-141">如果自動變數的值大於1，則 (您在嵌套提示字元中 `$NestedPromptLevel` 。 ) </span><span class="sxs-lookup"><span data-stu-id="1aa60-141">(You are in a nested prompt if the value of the `$NestedPromptLevel` automatic variable is greater than 1.)</span></span>

<span data-ttu-id="1aa60-142">例如，當您在巢狀的提示字元中偵錯時，提示字元會類似下列提示字元︰</span><span class="sxs-lookup"><span data-stu-id="1aa60-142">For example, when you are debugging in a nested prompt, the prompt resembles the following prompt:</span></span>

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a><span data-ttu-id="1aa60-143">提示的變更</span><span class="sxs-lookup"><span data-stu-id="1aa60-143">Changes to the prompt</span></span>

<span data-ttu-id="1aa60-144">Cmdlet 會將 `Enter-PSSession` 遠端電腦的名稱加到目前的函式 `Prompt` 。</span><span class="sxs-lookup"><span data-stu-id="1aa60-144">The `Enter-PSSession` cmdlet prepends the name of the remote computer to the current `Prompt` function.</span></span> <span data-ttu-id="1aa60-145">當您使用 `Enter-PSSession` 指令程式來啟動遠端電腦的會話時，命令提示字元會變更為包含遠端電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="1aa60-145">When you use the `Enter-PSSession` cmdlet to start a session with a remote computer, the command prompt changes to include the name of the remote computer.</span></span> <span data-ttu-id="1aa60-146">例如：</span><span class="sxs-lookup"><span data-stu-id="1aa60-146">For example:</span></span>

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

<span data-ttu-id="1aa60-147">其他 PowerShell 主機應用程式和替代 shell 可能會有自己的自訂命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="1aa60-147">Other PowerShell host applications and alternate shells might have their own custom command prompts.</span></span>

<span data-ttu-id="1aa60-148">如需 `$PSDebugContext` 和自動變數的詳細資訊 `$NestedPromptLevel` ，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa60-148">For more information about the `$PSDebugContext` and `$NestedPromptLevel` automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

### <a name="how-to-customize-the-prompt"></a><span data-ttu-id="1aa60-149">如何自訂提示</span><span class="sxs-lookup"><span data-stu-id="1aa60-149">How to customize the prompt</span></span>

<span data-ttu-id="1aa60-150">若要自訂提示，請撰寫新的函式 `Prompt` 。</span><span class="sxs-lookup"><span data-stu-id="1aa60-150">To customize the prompt, write a new `Prompt` function.</span></span> <span data-ttu-id="1aa60-151">函式未受保護，因此可以覆寫。</span><span class="sxs-lookup"><span data-stu-id="1aa60-151">The function is not protected, so you can overwrite it.</span></span>

<span data-ttu-id="1aa60-152">若要撰寫 `Prompt` 函數，請輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="1aa60-152">To write a `Prompt` function, type the following:</span></span>

```powershell
function prompt { }
```

<span data-ttu-id="1aa60-153">然後在大括弧之間輸入命令或建立提示字元的字串。</span><span class="sxs-lookup"><span data-stu-id="1aa60-153">Then, between the braces, enter the commands or the string that creates your prompt.</span></span>

<span data-ttu-id="1aa60-154">例如，下列提示字元包含您的電腦名稱︰</span><span class="sxs-lookup"><span data-stu-id="1aa60-154">For example, the following prompt includes your computer name:</span></span>

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

<span data-ttu-id="1aa60-155">在 Server01 電腦上，提示字元會類似下列提示字元︰</span><span class="sxs-lookup"><span data-stu-id="1aa60-155">On the Server01 computer, the prompt resembles the following prompt:</span></span>

```Output
PS [Server01] >
```

<span data-ttu-id="1aa60-156">下列 `Prompt` 函數包含目前的日期和時間：</span><span class="sxs-lookup"><span data-stu-id="1aa60-156">The following `Prompt` function includes the current date and time:</span></span>

```powershell
function prompt {"$(Get-Date)> "}
```

<span data-ttu-id="1aa60-157">提示字元類似下列提示字元︰</span><span class="sxs-lookup"><span data-stu-id="1aa60-157">The prompt resembles the following prompt:</span></span>

```Output
03/15/2012 17:49:47>
```

<span data-ttu-id="1aa60-158">您也可以變更預設 `Prompt` 函數：</span><span class="sxs-lookup"><span data-stu-id="1aa60-158">You can also change the default `Prompt` function:</span></span>

<span data-ttu-id="1aa60-159">例如，下列修改過的函式 `Prompt` `[ADMIN]:` 會在使用 [以 **系統管理員身分執行** ] 選項開啟 powershell 時，新增至內建的 powershell 提示字元：</span><span class="sxs-lookup"><span data-stu-id="1aa60-159">For example, the following modified `Prompt` function adds `[ADMIN]:` to the built-in PowerShell prompt when PowerShell is opened by using the **Run as administrator** option:</span></span>

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="1aa60-160">當您使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell 時，會出現類似下列提示的提示：</span><span class="sxs-lookup"><span data-stu-id="1aa60-160">When you start PowerShell by using the **Run as administrator** option, a prompt that resembles the following prompt appears:</span></span>

```Output
[ADMIN]: PS C:\ps-test>
```

<span data-ttu-id="1aa60-161">下列函式會 `Prompt` 顯示下一個命令的歷程記錄識別碼。</span><span class="sxs-lookup"><span data-stu-id="1aa60-161">The following `Prompt` function displays the history ID of the next command.</span></span> <span data-ttu-id="1aa60-162">若要查看命令歷程記錄，請使用 `Get-History` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1aa60-162">To view the command history, use the `Get-History` cmdlet.</span></span>

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

<span data-ttu-id="1aa60-163">下列提示 `Write-Host` 會使用和 `Get-Random` Cmdlet 來建立隨機變更色彩的提示。</span><span class="sxs-lookup"><span data-stu-id="1aa60-163">The following prompt uses the `Write-Host` and `Get-Random` cmdlets to create a prompt that changes color randomly.</span></span> <span data-ttu-id="1aa60-164">因為 `Write-Host` 寫入目前的主應用程式，但不會傳回物件，所以此函式會包含 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="1aa60-164">Because `Write-Host` writes to the current host application but does not return an object, this function includes a `Return` statement.</span></span> <span data-ttu-id="1aa60-165">如果沒有，PowerShell 就會使用預設的提示字元 `PS>` 。</span><span class="sxs-lookup"><span data-stu-id="1aa60-165">Without it, PowerShell uses the default prompt, `PS>`.</span></span>

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a><span data-ttu-id="1aa60-166">儲存 Prompt 函數</span><span class="sxs-lookup"><span data-stu-id="1aa60-166">Saving the Prompt function</span></span>

<span data-ttu-id="1aa60-167">就像任何函式一樣， `Prompt` 函數只存在於目前的會話中。</span><span class="sxs-lookup"><span data-stu-id="1aa60-167">Like any function, the `Prompt` function exists only in the current session.</span></span> <span data-ttu-id="1aa60-168">若要在 `Prompt` 未來的會話中儲存函式，請將它新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="1aa60-168">To save the `Prompt` function for future sessions, add it to your PowerShell profiles.</span></span> <span data-ttu-id="1aa60-169">如需設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="1aa60-169">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1aa60-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1aa60-170">See also</span></span>

[<span data-ttu-id="1aa60-171">Get-Location</span><span class="sxs-lookup"><span data-stu-id="1aa60-171">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)

[<span data-ttu-id="1aa60-172">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="1aa60-172">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="1aa60-173">Get-History</span><span class="sxs-lookup"><span data-stu-id="1aa60-173">Get-History</span></span>](xref:Microsoft.PowerShell.Core.Get-History)

[<span data-ttu-id="1aa60-174">Get-Random</span><span class="sxs-lookup"><span data-stu-id="1aa60-174">Get-Random</span></span>](xref:Microsoft.PowerShell.Utility.Get-Random)

[<span data-ttu-id="1aa60-175">Write-Host</span><span class="sxs-lookup"><span data-stu-id="1aa60-175">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)

[<span data-ttu-id="1aa60-176">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="1aa60-176">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="1aa60-177">about_Functions</span><span class="sxs-lookup"><span data-stu-id="1aa60-177">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="1aa60-178">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="1aa60-178">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="1aa60-179">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="1aa60-179">about_Debuggers</span></span>](about_Debuggers.md)

[<span data-ttu-id="1aa60-180">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="1aa60-180">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
