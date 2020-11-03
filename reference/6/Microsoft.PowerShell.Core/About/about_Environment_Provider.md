---
description: 環境
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 環境提供者
ms.openlocfilehash: 354d6b0d07ac93a0b1a40543ca1e301a785ca934
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207132"
---
# <a name="environment-provider"></a><span data-ttu-id="9be4d-104">環境提供者</span><span class="sxs-lookup"><span data-stu-id="9be4d-104">Environment provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="9be4d-105">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="9be4d-105">Provider name</span></span>
<span data-ttu-id="9be4d-106">環境</span><span class="sxs-lookup"><span data-stu-id="9be4d-106">Environment</span></span>

## <a name="drives"></a><span data-ttu-id="9be4d-107">磁碟機</span><span class="sxs-lookup"><span data-stu-id="9be4d-107">Drives</span></span>

`Env:`

## <a name="capabilities"></a><span data-ttu-id="9be4d-108">功能</span><span class="sxs-lookup"><span data-stu-id="9be4d-108">Capabilities</span></span>

<span data-ttu-id="9be4d-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="9be4d-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="9be4d-110">簡短描述</span><span class="sxs-lookup"><span data-stu-id="9be4d-110">Short description</span></span>

<span data-ttu-id="9be4d-111">提供 Windows 環境變數的存取。</span><span class="sxs-lookup"><span data-stu-id="9be4d-111">Provides access to the Windows environment variables.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="9be4d-112">詳細描述</span><span class="sxs-lookup"><span data-stu-id="9be4d-112">Detailed description</span></span>

<span data-ttu-id="9be4d-113">PowerShell **環境** 提供者可讓您在 powershell 中取得、新增、變更、清除及刪除環境變數和值。</span><span class="sxs-lookup"><span data-stu-id="9be4d-113">The PowerShell **Environment** provider lets you get, add, change, clear, and delete environment variables and values in PowerShell.</span></span>

<span data-ttu-id="9be4d-114">**環境** 變數是動態命名的變數，可描述您的程式執行所在的環境。</span><span class="sxs-lookup"><span data-stu-id="9be4d-114">**Environment** variables are dynamically named variables that describe the environment in which your programs run.</span></span> <span data-ttu-id="9be4d-115">Windows 和 PowerShell 使用環境變數來儲存會影響系統和進程執行的持續性資訊。</span><span class="sxs-lookup"><span data-stu-id="9be4d-115">Windows and PowerShell use environment variables to store persistent information that affect system and process execution.</span></span> <span data-ttu-id="9be4d-116">不同于 PowerShell 變數，環境變數不受限於範圍條件約束。</span><span class="sxs-lookup"><span data-stu-id="9be4d-116">Unlike PowerShell variables, environment variables are not subject to scope constraints.</span></span>

<span data-ttu-id="9be4d-117">**環境** 磁片磁碟機是一般命名空間，其中包含目前使用者會話特有的環境變數。</span><span class="sxs-lookup"><span data-stu-id="9be4d-117">The **Environment** drive is a flat namespace containing the environment variables specific to the current user's session.</span></span> <span data-ttu-id="9be4d-118">環境變數沒有任何子專案。</span><span class="sxs-lookup"><span data-stu-id="9be4d-118">The environment variables have no child items.</span></span>

<span data-ttu-id="9be4d-119">**環境** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。</span><span class="sxs-lookup"><span data-stu-id="9be4d-119">The **Environment** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="9be4d-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="9be4d-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="9be4d-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="9be4d-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="9be4d-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="9be4d-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="9be4d-123">New-Item</span><span class="sxs-lookup"><span data-stu-id="9be4d-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="9be4d-124">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9be4d-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="9be4d-125">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="9be4d-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="9be4d-126">此提供者公開的類型</span><span class="sxs-lookup"><span data-stu-id="9be4d-126">Types exposed by this provider</span></span>

<span data-ttu-id="9be4d-127">每個環境變數都是 [DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="9be4d-127">Each environment variable is an instance of the [System.Collections.DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) class.</span></span> <span data-ttu-id="9be4d-128">變數的名稱是字典索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9be4d-128">The name of the variable is the dictionary key.</span></span> <span data-ttu-id="9be4d-129">環境變數的值是字典值。</span><span class="sxs-lookup"><span data-stu-id="9be4d-129">The value of the environment variable is the dictionary value.</span></span>

## <a name="navigating-the-environment-drive"></a><span data-ttu-id="9be4d-130">流覽環境磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="9be4d-130">Navigating the Environment drive</span></span>

<span data-ttu-id="9be4d-131">**環境** 提供者會在磁片磁碟機中公開它的資料存放區 `Env:` 。</span><span class="sxs-lookup"><span data-stu-id="9be4d-131">The **Environment** provider exposes its data store in the `Env:` drive.</span></span> <span data-ttu-id="9be4d-132">若要使用環境變數，請將您的位置變更為 `Env:` 磁片磁碟機 (`Set-Location Env:`) ，或從另一個 PowerShell 磁片磁碟機工作。</span><span class="sxs-lookup"><span data-stu-id="9be4d-132">To work with environment variables, change your location to the `Env:` drive (`Set-Location Env:`), or work from another PowerShell drive.</span></span> <span data-ttu-id="9be4d-133">若要從另一個位置參考環境變數，請使用 `Env:` 路徑中的磁片磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="9be4d-133">To reference an environment variable from another location, use the `Env:` drive name in the path.</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="9be4d-134">若要返回檔案系統磁碟機，請輸入磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="9be4d-134">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="9be4d-135">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="9be4d-135">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="9be4d-136">您也可以從任何其他 PowerShell 磁片磁碟機使用 **環境** 提供者。</span><span class="sxs-lookup"><span data-stu-id="9be4d-136">You can also work with the **Environment** provider from any other PowerShell drive.</span></span> <span data-ttu-id="9be4d-137">若要從另一個位置參考環境變數，請使用路徑中的磁片磁碟機名稱 `Env:` 。</span><span class="sxs-lookup"><span data-stu-id="9be4d-137">To reference an environment variable from another location, use the drive name `Env:` in the path.</span></span>

<span data-ttu-id="9be4d-138">**環境** 提供者也會使用的變數前置詞來公開環境變數 `$env:` 。</span><span class="sxs-lookup"><span data-stu-id="9be4d-138">The **Environment** provider also exposes environment variables using a variable prefix of `$env:`.</span></span>  <span data-ttu-id="9be4d-139">下列命令會查看 **ProgramFiles** 環境變數的內容。</span><span class="sxs-lookup"><span data-stu-id="9be4d-139">The following command views the contents of the **ProgramFiles** environment variable.</span></span> <span data-ttu-id="9be4d-140">`$env:`變數前置詞可以從任何 PowerShell 磁片磁碟機使用。</span><span class="sxs-lookup"><span data-stu-id="9be4d-140">The `$env:` variable prefix can be used from any PowerShell drive.</span></span>

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

<span data-ttu-id="9be4d-141">您也可以使用變數前置詞來變更環境變數的值 `$env:` 。</span><span class="sxs-lookup"><span data-stu-id="9be4d-141">You can also change the value of an environment variable using the `$env:` variable prefix.</span></span>  <span data-ttu-id="9be4d-142">只要目前的 PowerShell 會話處於作用中狀態，任何變更都只適用于目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="9be4d-142">Any changes made only pertain to the current PowerShell session for as long as it is active.</span></span>

> [!NOTE]
> <span data-ttu-id="9be4d-143">PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="9be4d-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="9be4d-144">和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="9be4d-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="9be4d-145">和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="9be4d-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-environment-variables"></a><span data-ttu-id="9be4d-146">取得環境變數</span><span class="sxs-lookup"><span data-stu-id="9be4d-146">Getting environment variables</span></span>

<span data-ttu-id="9be4d-147">此命令會列出目前會話中的所有環境變數。</span><span class="sxs-lookup"><span data-stu-id="9be4d-147">This command lists all the environment variables in the current session.</span></span>

```powershell
Get-Item -Path Env:
```

<span data-ttu-id="9be4d-148">您可以從任何 PowerShell 磁片磁碟機使用此命令。</span><span class="sxs-lookup"><span data-stu-id="9be4d-148">You can use this command from any PowerShell drive.</span></span>

<span data-ttu-id="9be4d-149">環境提供者沒有任何容器，因此在搭配使用時，上述命令具有相同的效果 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="9be4d-149">The Environment provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a><span data-ttu-id="9be4d-150">取得選取的環境變數</span><span class="sxs-lookup"><span data-stu-id="9be4d-150">Get a selected environment variable</span></span>

<span data-ttu-id="9be4d-151">此命令會取得 `WINDIR` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="9be4d-151">This command gets the `WINDIR` environment Variable.</span></span>

```powershell
Get-ChildItem -Path Env:windir
```

<span data-ttu-id="9be4d-152">您也可以使用變數前置詞格式。</span><span class="sxs-lookup"><span data-stu-id="9be4d-152">You can also use the variable prefix format as well.</span></span>

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a><span data-ttu-id="9be4d-153">建立環境變數</span><span class="sxs-lookup"><span data-stu-id="9be4d-153">Create an environment variable</span></span>

<span data-ttu-id="9be4d-154">此命令會建立 `USERMODE` 一個值為 "非 Admin" 的環境變數。</span><span class="sxs-lookup"><span data-stu-id="9be4d-154">This command creates the `USERMODE` environment variable with a value of "Non-Admin".</span></span> <span data-ttu-id="9be4d-155">`-Path`參數值會在磁片磁碟機中建立新專案 `Env:` 。</span><span class="sxs-lookup"><span data-stu-id="9be4d-155">The `-Path` parameter value creates the new item in the `Env:` drive.</span></span> <span data-ttu-id="9be4d-156">新的環境變數僅適用于目前的 PowerShell 會話，只要它是使用中。</span><span class="sxs-lookup"><span data-stu-id="9be4d-156">The new environment variable is only usable in the current PowerShell session for as long as it is active.</span></span>

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a><span data-ttu-id="9be4d-157">變更環境變數</span><span class="sxs-lookup"><span data-stu-id="9be4d-157">Changing an environment variable</span></span>

### <a name="rename-an-environment-variable"></a><span data-ttu-id="9be4d-158">重新命名環境變數</span><span class="sxs-lookup"><span data-stu-id="9be4d-158">Rename an environment variable</span></span>

<span data-ttu-id="9be4d-159">此命令會使用 `Rename-Item` Cmdlet 來變更 `USERMODE` 您建立的環境變數名稱 `USERROLE` 。</span><span class="sxs-lookup"><span data-stu-id="9be4d-159">This command uses the `Rename-Item` cmdlet to change the name of the `USERMODE` environment variable that you created to `USERROLE`.</span></span> <span data-ttu-id="9be4d-160">請勿變更系統所使用的環境變數名稱。</span><span class="sxs-lookup"><span data-stu-id="9be4d-160">Do not change the name of an environment variable that the system uses.</span></span> <span data-ttu-id="9be4d-161">雖然這些變更只會影響目前的工作階段，但它們可能會造成系統或程式運作錯誤。</span><span class="sxs-lookup"><span data-stu-id="9be4d-161">Although these changes affect only the current session, they might cause the system or a program to operate incorrectly.</span></span>

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a><span data-ttu-id="9be4d-162">變更環境變數</span><span class="sxs-lookup"><span data-stu-id="9be4d-162">Change an environment variable</span></span>

<span data-ttu-id="9be4d-163">此命令會使用 `Set-Item` Cmdlet 將環境變數的值變更 `USERROLE` 為 "Administrator"。</span><span class="sxs-lookup"><span data-stu-id="9be4d-163">This command uses the `Set-Item` cmdlet to change the value of the `USERROLE` environment variable to "Administrator".</span></span>

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a><span data-ttu-id="9be4d-164">複製環境變數</span><span class="sxs-lookup"><span data-stu-id="9be4d-164">Copy an environment variable</span></span>

<span data-ttu-id="9be4d-165">此命令會將環境變數的值複製 `USERROLE` 到 `USERROLE2` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="9be4d-165">This command copies the value of the `USERROLE` environment variable to the `USERROLE2` environment Variable.</span></span>

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a><span data-ttu-id="9be4d-166">移除環境變數</span><span class="sxs-lookup"><span data-stu-id="9be4d-166">Remove an environment variable</span></span>

<span data-ttu-id="9be4d-167">此命令會 `USERROLE2` 從目前的會話中刪除環境變數。</span><span class="sxs-lookup"><span data-stu-id="9be4d-167">This command deletes the `USERROLE2` environment variable from the current session.</span></span>

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a><span data-ttu-id="9be4d-168">使用 Clear-Item 移除環境變數</span><span class="sxs-lookup"><span data-stu-id="9be4d-168">Remove an environment variable with Clear-Item</span></span>

<span data-ttu-id="9be4d-169">此命令會藉 `USERROLE` 由清除其值來刪除環境變數。</span><span class="sxs-lookup"><span data-stu-id="9be4d-169">This command deletes the `USERROLE` environment variable by clearing its value.</span></span>

```powershell
Clear-Item -Path Env:USERROLE
```

## <a name="using-the-pipeline"></a><span data-ttu-id="9be4d-170">使用管線</span><span class="sxs-lookup"><span data-stu-id="9be4d-170">Using the pipeline</span></span>

<span data-ttu-id="9be4d-171">提供者 Cmdlet 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="9be4d-171">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="9be4d-172">您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。</span><span class="sxs-lookup"><span data-stu-id="9be4d-172">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="9be4d-173">若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="9be4d-173">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="9be4d-174">取得說明</span><span class="sxs-lookup"><span data-stu-id="9be4d-174">Getting help</span></span>

<span data-ttu-id="9be4d-175">從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。</span><span class="sxs-lookup"><span data-stu-id="9be4d-175">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="9be4d-176">若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 的參數來指定檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="9be4d-176">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a><span data-ttu-id="9be4d-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9be4d-177">See also</span></span>

[<span data-ttu-id="9be4d-178">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9be4d-178">about_Providers</span></span>](../About/about_Providers.md)
