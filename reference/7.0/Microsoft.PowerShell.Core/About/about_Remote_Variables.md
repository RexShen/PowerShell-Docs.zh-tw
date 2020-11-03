---
description: 說明如何在遠端命令中使用區域和遠端變數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 2260e1a6ba4553cbdba0057972f491d17c61382d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208155"
---
# <a name="about-remote-variables"></a><span data-ttu-id="d4d85-104">關於遠端變數</span><span class="sxs-lookup"><span data-stu-id="d4d85-104">About Remote Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="d4d85-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="d4d85-105">Short description</span></span>

<span data-ttu-id="d4d85-106">說明如何在遠端命令中使用區域和遠端變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-106">Explains how to use local and remote variables in remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="d4d85-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="d4d85-107">Long description</span></span>

<span data-ttu-id="d4d85-108">您可以在遠端電腦上執行的命令中使用變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-108">You can use variables in commands that you run on remote computers.</span></span> <span data-ttu-id="d4d85-109">將值指派給變數，然後使用變數來取代該值。</span><span class="sxs-lookup"><span data-stu-id="d4d85-109">Assign a value to the variable and then use the variable in place of the value.</span></span>

<span data-ttu-id="d4d85-110">根據預設，會假設在執行命令的會話中定義遠端命令中的變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-110">By default, the variables in remote commands are assumed to be defined in the session that runs the command.</span></span> <span data-ttu-id="d4d85-111">在本機會話中定義的變數，必須在命令中識別為本機變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-111">Variables that are defined in a local session, must be identified as local variables in the command.</span></span>

## <a name="using-remote-variables"></a><span data-ttu-id="d4d85-112">使用遠端變數</span><span class="sxs-lookup"><span data-stu-id="d4d85-112">Using remote variables</span></span>

<span data-ttu-id="d4d85-113">PowerShell 假設遠端命令中使用的變數是在命令執行所在的會話中定義。</span><span class="sxs-lookup"><span data-stu-id="d4d85-113">PowerShell assumes that the variables used in remote commands are defined in the session in which the command runs.</span></span>

<span data-ttu-id="d4d85-114">在此範例中， `$ps` 變數是在命令執行所在的暫存會話中定義 `Get-WinEvent` 。</span><span class="sxs-lookup"><span data-stu-id="d4d85-114">In this example, the `$ps` variable is defined in the temporary session in which the `Get-WinEvent` command runs.</span></span>

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

<span data-ttu-id="d4d85-115">當命令在持續性會話（ **PSSession** ）中執行時，必須在該會話中定義遠端變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-115">When the command runs in a persistent session, **PSSession** , the remote variable must be defined in that session.</span></span>

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a><span data-ttu-id="d4d85-116">使用本機變數</span><span class="sxs-lookup"><span data-stu-id="d4d85-116">Using local variables</span></span>

<span data-ttu-id="d4d85-117">您可以在遠端命令中使用本機變數，但必須在本機會話中定義變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-117">You can use local variables in remote commands, but the variable must be defined in the local session.</span></span>

<span data-ttu-id="d4d85-118">從 PowerShell 3.0 開始，您可以使用 `Using` 範圍修飾符來識別遠端命令中的本機變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-118">Beginning in PowerShell 3.0, you can use the `Using` scope modifier to identify a local variable in a remote command.</span></span>

<span data-ttu-id="d4d85-119">的語法如下所示 `Using` ：</span><span class="sxs-lookup"><span data-stu-id="d4d85-119">The syntax of `Using` is as follows:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="d4d85-120">在下列範例中， `$ps` 會在本機會話中建立變數，但會在執行命令的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="d4d85-120">In the following example, the `$ps` variable is created in the local session, but is used in the session in which the command runs.</span></span> <span data-ttu-id="d4d85-121">`Using`範圍修飾詞會識別 `$ps` 為本機變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-121">The `Using` scope modifier identifies `$ps` as a local variable.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

<span data-ttu-id="d4d85-122">`Using`範圍修飾詞可用於 **PSSession** 中。</span><span class="sxs-lookup"><span data-stu-id="d4d85-122">The `Using` scope modifier can be used in a **PSSession** .</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

<span data-ttu-id="d4d85-123">變數參考，例如 `$using:var` 從呼叫端的內容展開至變數的值 `$var` 。</span><span class="sxs-lookup"><span data-stu-id="d4d85-123">A variable reference such as `$using:var` expands to the value of variable `$var` from the caller's context.</span></span> <span data-ttu-id="d4d85-124">您無法存取呼叫端的變數物件。</span><span class="sxs-lookup"><span data-stu-id="d4d85-124">You do not get access to the caller's variable object.</span></span>
<span data-ttu-id="d4d85-125">`Using`範圍修飾詞不能用來修改 **PSSession** 內的本機變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-125">The `Using` scope modifier cannot be used to modify a local variable within the **PSSession** .</span></span> <span data-ttu-id="d4d85-126">例如，下列程式碼無法運作：</span><span class="sxs-lookup"><span data-stu-id="d4d85-126">For example, the following code does not work:</span></span>

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

<span data-ttu-id="d4d85-127">如需的詳細資訊 `Using` ，請參閱 [about_Scopes](./about_Scopes.md)</span><span class="sxs-lookup"><span data-stu-id="d4d85-127">For more information about `Using`, see [about_Scopes](./about_Scopes.md)</span></span>

### <a name="using-splatting"></a><span data-ttu-id="d4d85-128">使用展開</span><span class="sxs-lookup"><span data-stu-id="d4d85-128">Using splatting</span></span>

<span data-ttu-id="d4d85-129">PowerShell 展開會將參數名稱和值的集合傳遞至命令。</span><span class="sxs-lookup"><span data-stu-id="d4d85-129">PowerShell splatting passes a collection of parameter names and values to a command.</span></span> <span data-ttu-id="d4d85-130">如需詳細資訊，請參閱 [about_Splatting](about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d85-130">For more information, see [about_Splatting](about_Splatting.md).</span></span>

<span data-ttu-id="d4d85-131">在此範例中，展開變數 `$Splat` 是在本機電腦上設定的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="d4d85-131">In this example, the splatting variable, `$Splat` is a hash table that is set up on the local computer.</span></span> <span data-ttu-id="d4d85-132">`Invoke-Command`連接至遠端電腦會話。</span><span class="sxs-lookup"><span data-stu-id="d4d85-132">The `Invoke-Command` connects to a remote computer session.</span></span> <span data-ttu-id="d4d85-133">**ScriptBlock** 使用 `Using` 範圍修飾詞搭配 At (`@`) 符號來表示 splatted 變數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-133">The **ScriptBlock** uses the `Using` scope modifier with the At (`@`) symbol to represent the splatted variable.</span></span>

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a><span data-ttu-id="d4d85-134">需要 ' Using ' 範圍修飾詞的其他情況</span><span class="sxs-lookup"><span data-stu-id="d4d85-134">Other situations where the 'Using' scope modifier is needed</span></span>

<span data-ttu-id="d4d85-135">針對任何執行的腳本或命令，您必須 `Using` 要有範圍修飾詞，才能從呼叫會話範圍內嵌變數值，讓會話外的程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="d4d85-135">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="d4d85-136">`Using`下列內容支援範圍修飾符：</span><span class="sxs-lookup"><span data-stu-id="d4d85-136">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="d4d85-137">從遠端執行的命令，從 `Invoke-Command` 使用 **ComputerName** 、 **HostName** 、 **SSHConnection** 或 **Session** 參數開始， (遠端會話) </span><span class="sxs-lookup"><span data-stu-id="d4d85-137">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** , **HostName** , **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="d4d85-138">背景工作，以 `Start-Job` (跨進程會話開始) </span><span class="sxs-lookup"><span data-stu-id="d4d85-138">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="d4d85-139">執行緒作業，透過 `Start-ThreadJob` 或 `ForEach-Object -Parallel` (個別的執行緒會話啟動) </span><span class="sxs-lookup"><span data-stu-id="d4d85-139">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="d4d85-140">視內容而定，內嵌變數值是呼叫端範圍中資料的獨立複本，或是對它的參考。</span><span class="sxs-lookup"><span data-stu-id="d4d85-140">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="d4d85-141">在遠端和跨進程的會話中，它們一律是獨立的複本。</span><span class="sxs-lookup"><span data-stu-id="d4d85-141">In remote and out-of-process sessions, they are always independent copies.</span></span> <span data-ttu-id="d4d85-142">線上程會話中，它們是以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="d4d85-142">In thread sessions, they are passed by reference.</span></span>

## <a name="serialization-of-variable-values"></a><span data-ttu-id="d4d85-143">變數值的序列化</span><span class="sxs-lookup"><span data-stu-id="d4d85-143">Serialization of variable values</span></span>

<span data-ttu-id="d4d85-144">遠端執行的命令和背景工作會跨進程執行。</span><span class="sxs-lookup"><span data-stu-id="d4d85-144">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="d4d85-145">跨進程會話使用以 XML 為基礎的序列化和還原序列化，讓變數的值可以跨進程界限使用。</span><span class="sxs-lookup"><span data-stu-id="d4d85-145">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="d4d85-146">序列化程式會將物件轉換為包含原始物件屬性但不包含其方法的 **PSObject** 。</span><span class="sxs-lookup"><span data-stu-id="d4d85-146">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="d4d85-147">針對一組有限的類型，還原序列化會將解除凍結物件回原始型別。</span><span class="sxs-lookup"><span data-stu-id="d4d85-147">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="d4d85-148">解除凍結物件是原始物件實例的複本。</span><span class="sxs-lookup"><span data-stu-id="d4d85-148">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="d4d85-149">它具有類型屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="d4d85-149">It has the type properties and methods.</span></span> <span data-ttu-id="d4d85-150">針對簡單類型（例如 **system.object** ），複本是精確的。</span><span class="sxs-lookup"><span data-stu-id="d4d85-150">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="d4d85-151">如果是複雜類型，則會完美複製。</span><span class="sxs-lookup"><span data-stu-id="d4d85-151">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="d4d85-152">例如，解除凍結憑證物件不包含私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="d4d85-152">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="d4d85-153">所有其他類型的實例都是 **PSObject** 實例。</span><span class="sxs-lookup"><span data-stu-id="d4d85-153">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="d4d85-154">**PSTypeNames** 屬性包含 **前面加上** 還原序列化的原始型別名稱，例如 **Deserialized.System。Data DataTable**</span><span class="sxs-lookup"><span data-stu-id="d4d85-154">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

## <a name="using-local-variables-with-argumentlist-parameter"></a><span data-ttu-id="d4d85-155">使用本機變數搭配 **ArgumentList** 參數</span><span class="sxs-lookup"><span data-stu-id="d4d85-155">Using local variables with **ArgumentList** parameter</span></span>

<span data-ttu-id="d4d85-156">您可以在遠端命令中使用區域變數，方法是定義遠端命令的參數，並使用 Cmdlet 的 **ArgumentList** 參數 `Invoke-Command` 將區域變數指定為參數值。</span><span class="sxs-lookup"><span data-stu-id="d4d85-156">You can use local variables in a remote command by defining parameters for the remote command and using the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

- <span data-ttu-id="d4d85-157">使用 `param` 關鍵字來定義遠端命令的參數。</span><span class="sxs-lookup"><span data-stu-id="d4d85-157">Use the `param` keyword to define parameters for the remote command.</span></span> <span data-ttu-id="d4d85-158">參數名稱是預留位置，不需要符合區域變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4d85-158">The parameter names are placeholders that don't need to match the local variable's name.</span></span>

- <span data-ttu-id="d4d85-159">在命令中使用關鍵字所定義的參數 `param` 。</span><span class="sxs-lookup"><span data-stu-id="d4d85-159">Use the parameters defined by the `param` keyword in the command.</span></span>

- <span data-ttu-id="d4d85-160">使用 Cmdlet 的 **ArgumentList** 參數 `Invoke-Command` ，將區域變數指定為參數值。</span><span class="sxs-lookup"><span data-stu-id="d4d85-160">Use the **ArgumentList** parameter of the `Invoke-Command` cmdlet to specify the local variable as the parameter value.</span></span>

<span data-ttu-id="d4d85-161">例如，下列命令 `$ps` 會定義本機會話中的變數，然後在遠端命令中使用它。</span><span class="sxs-lookup"><span data-stu-id="d4d85-161">For example, the following commands define the `$ps` variable in the local session and then use it in a remote command.</span></span> <span data-ttu-id="d4d85-162">此命令會使用 `$log` 做為參數名稱和區域變數， `$ps` 做為其值。</span><span class="sxs-lookup"><span data-stu-id="d4d85-162">The command uses `$log` as the parameter name and the local variable, `$ps`, as its value.</span></span>

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a><span data-ttu-id="d4d85-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4d85-163">See also</span></span>

[<span data-ttu-id="d4d85-164">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="d4d85-164">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="d4d85-165">about_Remote</span><span class="sxs-lookup"><span data-stu-id="d4d85-165">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="d4d85-166">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="d4d85-166">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="d4d85-167">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="d4d85-167">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="d4d85-168">about_Variables</span><span class="sxs-lookup"><span data-stu-id="d4d85-168">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="d4d85-169">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="d4d85-169">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="d4d85-170">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="d4d85-170">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="d4d85-171">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="d4d85-171">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="d4d85-172">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="d4d85-172">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)

[<span data-ttu-id="d4d85-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="d4d85-173">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
