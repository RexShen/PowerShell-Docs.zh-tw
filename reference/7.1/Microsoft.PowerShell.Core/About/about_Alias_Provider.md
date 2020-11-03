---
description: Alias
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 別名提供者
ms.openlocfilehash: 8edd1a406862e6bf1dcbc5e8215b60c93ac7b13f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207764"
---
# <a name="alias-provider"></a><span data-ttu-id="eaf97-104">別名提供者</span><span class="sxs-lookup"><span data-stu-id="eaf97-104">Alias provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="eaf97-105">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="eaf97-105">Provider name</span></span>
<span data-ttu-id="eaf97-106">Alias</span><span class="sxs-lookup"><span data-stu-id="eaf97-106">Alias</span></span>

## <a name="drives"></a><span data-ttu-id="eaf97-107">磁碟機</span><span class="sxs-lookup"><span data-stu-id="eaf97-107">Drives</span></span>

`Alias:`

## <a name="capabilities"></a><span data-ttu-id="eaf97-108">功能</span><span class="sxs-lookup"><span data-stu-id="eaf97-108">Capabilities</span></span>

<span data-ttu-id="eaf97-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="eaf97-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="eaf97-110">簡短描述</span><span class="sxs-lookup"><span data-stu-id="eaf97-110">Short description</span></span>

<span data-ttu-id="eaf97-111">提供 PowerShell 別名和它們所代表之值的存取權。</span><span class="sxs-lookup"><span data-stu-id="eaf97-111">Provides access to the PowerShell aliases and the values that they represent.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="eaf97-112">詳細描述</span><span class="sxs-lookup"><span data-stu-id="eaf97-112">Detailed description</span></span>

<span data-ttu-id="eaf97-113">PowerShell **別名** 提供者可讓您在 powershell 中取得、新增、變更、清除和刪除別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-113">The PowerShell **Alias** provider lets you get, add, change, clear, and delete aliases in PowerShell.</span></span>

<span data-ttu-id="eaf97-114">別名是 Cmdlet、函式、可執行檔（包括腳本）的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf97-114">An alias is an alternate name for a cmdlet, function, executable file, including scripts.</span></span> <span data-ttu-id="eaf97-115">PowerShell 包含一組內建的別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-115">PowerShell includes a set of built-in aliases.</span></span> <span data-ttu-id="eaf97-116">您可以將自己的別名新增至目前的會話和您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="eaf97-116">You can add your own aliases to the current session and to your PowerShell profile.</span></span>

<span data-ttu-id="eaf97-117">**別名** 磁片磁碟機是只包含別名物件的一般命名空間。</span><span class="sxs-lookup"><span data-stu-id="eaf97-117">The **Alias** drive is a flat namespace that contains only the alias objects.</span></span>
<span data-ttu-id="eaf97-118">別名沒有任何子項目。</span><span class="sxs-lookup"><span data-stu-id="eaf97-118">The aliases have no child items.</span></span>

<span data-ttu-id="eaf97-119">**別名** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。</span><span class="sxs-lookup"><span data-stu-id="eaf97-119">The **Alias** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="eaf97-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="eaf97-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="eaf97-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="eaf97-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="eaf97-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="eaf97-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="eaf97-123">New-Item</span><span class="sxs-lookup"><span data-stu-id="eaf97-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="eaf97-124">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="eaf97-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="eaf97-125">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="eaf97-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="eaf97-126">PowerShell 包含一組設計來查看和變更別名的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eaf97-126">PowerShell includes a set of cmdlets that are designed to view and to change aliases.</span></span> <span data-ttu-id="eaf97-127">當您使用 **Alias** Cmdlet 時，不需要 `Alias:` 在名稱中指定磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="eaf97-127">When you use **Alias** cmdlets, you do not need to specify the `Alias:` drive in the name.</span></span> <span data-ttu-id="eaf97-128">本文未涵蓋 **別名** Cmdlet 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="eaf97-128">This article does not cover working with **Alias** cmdlets.</span></span>

- [<span data-ttu-id="eaf97-129">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="eaf97-129">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="eaf97-130">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="eaf97-130">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="eaf97-131">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="eaf97-131">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="eaf97-132">New-Alias</span><span class="sxs-lookup"><span data-stu-id="eaf97-132">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="eaf97-133">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="eaf97-133">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="eaf97-134">此提供者公開的類型</span><span class="sxs-lookup"><span data-stu-id="eaf97-134">Types exposed by this provider</span></span>

<span data-ttu-id="eaf97-135">每個別名都是 [system.management.automation.aliasinfo](/dotnet/api/system.management.automation.aliasinfo) 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="eaf97-135">Each alias is an instance of the [System.Management.Automation.AliasInfo](/dotnet/api/system.management.automation.aliasinfo) class.</span></span>

## <a name="navigating-the-alias-drive"></a><span data-ttu-id="eaf97-136">流覽別名磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="eaf97-136">Navigating the Alias drive</span></span>

<span data-ttu-id="eaf97-137">**別名** 提供者會在磁片磁碟機中公開它的資料存放區 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-137">The **Alias** provider exposes its data store in the `Alias:` drive.</span></span> <span data-ttu-id="eaf97-138">若要使用別名，您可以使用下列命令將位置變更為 `Alias:` 磁片磁碟機：</span><span class="sxs-lookup"><span data-stu-id="eaf97-138">To work with aliases, you can change your location to the `Alias:` drive by using the following command:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="eaf97-139">若要返回檔案系統磁碟機，請輸入磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf97-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="eaf97-140">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="eaf97-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="eaf97-141">您也可以從任何其他 PowerShell 磁片磁碟機使用別名提供者。</span><span class="sxs-lookup"><span data-stu-id="eaf97-141">You can also work with the Alias provider from any other PowerShell drive.</span></span> <span data-ttu-id="eaf97-142">若要從其他位置參照別名，請 `Alias:` 在路徑中使用磁片磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf97-142">To reference an alias from another location, use the `Alias:` drive name in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="eaf97-143">PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="eaf97-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="eaf97-144">和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="eaf97-145">和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

### <a name="displaying-the-contents-of-the-alias-drive"></a><span data-ttu-id="eaf97-146">顯示 Alias：磁片磁碟機的內容</span><span class="sxs-lookup"><span data-stu-id="eaf97-146">Displaying the Contents of the Alias: drive</span></span>

<span data-ttu-id="eaf97-147">當目前位置是磁片磁碟機時，此命令會取得所有別名的清單 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-147">This command gets the list of all the aliases when the current location is the `Alias:` drive.</span></span> <span data-ttu-id="eaf97-148">它會使用萬用字元 `*` 來指出目前位置的所有內容。</span><span class="sxs-lookup"><span data-stu-id="eaf97-148">It uses a wildcard character `*` to indicate all the contents of the current location.</span></span>

```powershell
PS Alias:\> Get-Item -Path *
```

<span data-ttu-id="eaf97-149">在 `Alias:` 磁片磁碟機中，代表目前位置的點， `.` 以及 `*` 代表目前位置中所有專案的萬用字元，都具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="eaf97-149">In the `Alias:` drive, a dot `.`, which represents the current location, and a wildcard character `*`, which represents all items in the current location, have the same effect.</span></span> <span data-ttu-id="eaf97-150">例如， `Get-Item -Path .` 或 `Get-Item \*` 產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="eaf97-150">For example, `Get-Item -Path .` or `Get-Item \*` produce the same result.</span></span>

<span data-ttu-id="eaf97-151">別名提供者沒有任何容器，因此在搭配使用時，上述命令具有相同的效果 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-151">The Alias provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a><span data-ttu-id="eaf97-152">取得選取的別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-152">Get a selected alias</span></span>

<span data-ttu-id="eaf97-153">此命令會取得 `ls` 別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-153">This command gets the `ls` alias.</span></span>
<span data-ttu-id="eaf97-154">因為它包含路徑，所以您可以在任何 PowerShell 磁片磁碟機中使用它。</span><span class="sxs-lookup"><span data-stu-id="eaf97-154">Because it includes the path, you can use it in any PowerShell drive.</span></span>

```powershell
Get-Item -Path Alias:ls
```

<span data-ttu-id="eaf97-155">如果您是在 `Alias:` 磁片磁碟機中，您可以省略路徑中的磁片磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf97-155">If you are in the `Alias:` drive, you can omit the drive name from the path.</span></span>

<span data-ttu-id="eaf97-156">您也可以在提供者路徑前面加上貨幣符號 () ，以取得別名的定義 `$` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-156">You can also retrieve the definition for an alias by prefixing the provider path with the dollar sign (`$`).</span></span>

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a><span data-ttu-id="eaf97-157">取得特定 Cmdlet 的所有別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-157">Get all aliases for a specific cmdlet</span></span>

<span data-ttu-id="eaf97-158">此命令會取得與 Cmdlet 相關聯的別名清單 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-158">This command gets a list of the aliases that are associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="eaf97-159">它會使用 **定義** 屬性，它會儲存 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="eaf97-159">It uses the **Definition** property, which stores the cmdlet name.</span></span>

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a><span data-ttu-id="eaf97-160">建立別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-160">Creating aliases</span></span>

### <a name="create-an-alias-from-the-alias-drive"></a><span data-ttu-id="eaf97-161">從 Alias：磁片磁碟機建立別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-161">Create an alias from the Alias: drive</span></span>

<span data-ttu-id="eaf97-162">此命令會建立 `serv` Cmdlet 的別名 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-162">This command creates the `serv` alias for the `Get-Service` cmdlet.</span></span> <span data-ttu-id="eaf97-163">因為目前的位置是在 `Alias:` 磁片磁碟機中，所以 `-Path` 不需要參數。</span><span class="sxs-lookup"><span data-stu-id="eaf97-163">Because the current location is in the `Alias:` drive, the `-Path` parameter is not needed.</span></span>

<span data-ttu-id="eaf97-164">此命令也會使用 `-Options` 動態參數來設定別名上的 **AllScope** 選項。</span><span class="sxs-lookup"><span data-stu-id="eaf97-164">This command also uses the `-Options` dynamic parameter to set the **AllScope** option on the alias.</span></span> <span data-ttu-id="eaf97-165">`-Options` `New-Item` 只有當您在磁片磁碟機中時，才可以在 Cmdlet 中使用參數 `Alias:` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-165">The `-Options` parameter is available in the `New-Item` cmdlet only when you are in the `Alias:` drive.</span></span> <span data-ttu-id="eaf97-166">點 (`.`) 表示目前的目錄，也就是別名磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="eaf97-166">The dot (`.`) indicates the current directory, which is the alias drive.</span></span>

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a><span data-ttu-id="eaf97-167">建立具有絕對路徑的別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-167">Create an alias with an absolute path</span></span>

<span data-ttu-id="eaf97-168">您可以針對任何叫用命令的項目建立別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-168">You can create an alias for any item that invokes a command.</span></span>
<span data-ttu-id="eaf97-169">此命令會建立的 `np` 別名 `Notepad.exe` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-169">This command creates the `np` alias for `Notepad.exe`.</span></span>

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a><span data-ttu-id="eaf97-170">建立新函式的別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-170">Create an alias to a new function</span></span>

<span data-ttu-id="eaf97-171">您可以針對任何函式建立別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-171">You can create an alias for any function.</span></span> <span data-ttu-id="eaf97-172">您可以使用此功能來建立包含 Cmdlet 及其參數的別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-172">You can use this feature to create an alias that includes both a cmdlet and its parameters.</span></span>

<span data-ttu-id="eaf97-173">第一個命令會建立函式，此函式會將 `CD32` 目前的目錄變更為 `System32` 目錄。</span><span class="sxs-lookup"><span data-stu-id="eaf97-173">The first command creates the `CD32` function, which changes the current directory to the `System32` directory.</span></span> <span data-ttu-id="eaf97-174">第二個命令會建立函式的 `go` 別名 `CD32` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-174">The second command creates the `go` alias for the `CD32` function.</span></span>

<span data-ttu-id="eaf97-175">當命令完成時，您可以使用 `CD32` 或來叫用 `go` 函數。</span><span class="sxs-lookup"><span data-stu-id="eaf97-175">When the command is complete, you can use either `CD32` or `go` to invoke the function.</span></span>

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a><span data-ttu-id="eaf97-176">變更別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-176">Changing aliases</span></span>

### <a name="change-the-options-of-an-alias"></a><span data-ttu-id="eaf97-177">變更別名的選項</span><span class="sxs-lookup"><span data-stu-id="eaf97-177">Change the options of an alias</span></span>

<span data-ttu-id="eaf97-178">您可以使用 `Set-Item` Cmdlet 搭配 `-Options` 動態參數來變更 `-Options` 別名的屬性值。</span><span class="sxs-lookup"><span data-stu-id="eaf97-178">You can use the `Set-Item` cmdlet with the `-Options` dynamic parameter to change the value of the `-Options` property of an alias.</span></span>

<span data-ttu-id="eaf97-179">此命令會為別名設定 **AllScope** 和 **ReadOnly** 選項 `dir` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-179">This command sets the **AllScope** and **ReadOnly** options for the `dir` alias.</span></span> <span data-ttu-id="eaf97-180">此命令會使用 `-Options` Cmdlet 的動態參數 `Set-Item` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-180">The command uses the `-Options` dynamic parameter of the `Set-Item` cmdlet.</span></span> <span data-ttu-id="eaf97-181">`-Options` `Set-Item` 當您搭配 **別名** 或 **函數** 提供者使用參數時，就可以使用參數。</span><span class="sxs-lookup"><span data-stu-id="eaf97-181">The `-Options` parameter is available in `Set-Item` when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a><span data-ttu-id="eaf97-182">變更別名參考命令</span><span class="sxs-lookup"><span data-stu-id="eaf97-182">Change an aliases referenced command</span></span>

<span data-ttu-id="eaf97-183">此命令會使用 `Set-Item` Cmdlet 來變更 `gp` 別名，使其代表 Cmdlet， `Get-Process` 而不是 `Get-ItemProperty` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eaf97-183">This command uses the `Set-Item` cmdlet to change the `gp` alias so that it represents the `Get-Process` cmdlet instead of the `Get-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="eaf97-184">此 `-Force` 參數為必要參數，因為別名的 **Options** 屬性值 `gp` 設定為 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-184">The `-Force` parameter is required because the value of the **Options** property of the `gp` alias is set to `ReadOnly`.</span></span> <span data-ttu-id="eaf97-185">因為命令是從磁片磁碟機中提交的 `Alias:` ，所以不會在路徑中指定磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="eaf97-185">Because the command is submitted from within the `Alias:` drive, the drive is not specified in the path.</span></span>

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

<span data-ttu-id="eaf97-186">變更會影響定義別名與命令之間的關聯的四個屬性。</span><span class="sxs-lookup"><span data-stu-id="eaf97-186">The change affects the four properties that define the association between the alias and the command.</span></span> <span data-ttu-id="eaf97-187">若要查看變更的效果，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="eaf97-187">To view the effect of the change, type the following command:</span></span>

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a><span data-ttu-id="eaf97-188">重新命名別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-188">Rename an alias</span></span>

<span data-ttu-id="eaf97-189">此命令會使用 `Rename-Item` Cmdlet 將別名變更 `popd` 為 `pop` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-189">This command uses the `Rename-Item` cmdlet to change the `popd` alias to `pop`.</span></span>

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a><span data-ttu-id="eaf97-190">複製別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-190">Copying an alias</span></span>

<span data-ttu-id="eaf97-191">此命令會複製 `pushd` 別名，以 `push` 建立 Cmdlet 的新別名 `Push-Location` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-191">This command copies the `pushd` alias so that a new `push` alias is created for the `Push-Location` cmdlet.</span></span>

<span data-ttu-id="eaf97-192">建立新的別名時，其 **Description** 屬性會有 null 值。</span><span class="sxs-lookup"><span data-stu-id="eaf97-192">When the new alias is created, its **Description** property has a null value.</span></span>
<span data-ttu-id="eaf97-193">而且，它的 **Option** 屬性值為 `None` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-193">And, its **Option** property has a value of `None`.</span></span> <span data-ttu-id="eaf97-194">如果命令是從磁片磁碟機內發出的 `Alias:` ，您可以從參數的值中省略磁片磁碟機名稱 `-Path` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-194">If the command is issued from within the `Alias:` drive, you can omit the drive name from the value of the `-Path` parameter.</span></span>

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a><span data-ttu-id="eaf97-195">刪除別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-195">Deleting an alias</span></span>

<span data-ttu-id="eaf97-196">此命令會刪除 `serv` 目前會話中的別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-196">This command deletes the `serv` alias from the current session.</span></span>
<span data-ttu-id="eaf97-197">您可以在任何 PowerShell 磁片磁碟機中使用此命令。</span><span class="sxs-lookup"><span data-stu-id="eaf97-197">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Item -Path Alias:serv
```

<span data-ttu-id="eaf97-198">此命令會刪除開頭為 "s" 的別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-198">This command deletes aliases that begin with "s".</span></span>
<span data-ttu-id="eaf97-199">它不會刪除唯讀的別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-199">It does not delete read-only aliases.</span></span>

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a><span data-ttu-id="eaf97-200">刪除唯讀別名</span><span class="sxs-lookup"><span data-stu-id="eaf97-200">Delete read-only aliases</span></span>

<span data-ttu-id="eaf97-201">此命令會刪除目前會話中的所有別名，但 `Constant` 其 **Options** 屬性的值除外。</span><span class="sxs-lookup"><span data-stu-id="eaf97-201">This command deletes all aliases from the current session, except those with a value of `Constant` for their **Options** property.</span></span> <span data-ttu-id="eaf97-202">`-Force`參數可讓命令刪除 **Options** 屬性具有值的別名 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-202">The `-Force` parameter allows the command to delete aliases whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a><span data-ttu-id="eaf97-203">動態參數</span><span class="sxs-lookup"><span data-stu-id="eaf97-203">Dynamic parameters</span></span>

<span data-ttu-id="eaf97-204">動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。</span><span class="sxs-lookup"><span data-stu-id="eaf97-204">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="eaf97-205">選項 [ScopedItemOptions]</span><span class="sxs-lookup"><span data-stu-id="eaf97-205">Options [System.Management.Automation.ScopedItemOptions]</span></span>

<span data-ttu-id="eaf97-206">判斷別名的 **Options** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="eaf97-206">Determines the value of the **Options** property of an alias.</span></span>

- <span data-ttu-id="eaf97-207">**無** ：無選項。</span><span class="sxs-lookup"><span data-stu-id="eaf97-207">**None** : No options.</span></span> <span data-ttu-id="eaf97-208">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="eaf97-208">This value is the default.</span></span>
- <span data-ttu-id="eaf97-209">**常數** ：無法刪除別名，而且無法變更其屬性。</span><span class="sxs-lookup"><span data-stu-id="eaf97-209">**Constant** :The alias cannot be deleted and its properties cannot be changed.</span></span>
  <span data-ttu-id="eaf97-210">只有在您建立別名時才能使用 **常數** 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-210">**Constant** is available only when you create an alias.</span></span> <span data-ttu-id="eaf97-211">您無法將現有別名的選項變更為 **常數** 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-211">You cannot change the option of an existing alias to **Constant** .</span></span>
- <span data-ttu-id="eaf97-212">**私** 用：別名只會顯示在目前的範圍中，而不是在子範圍中。</span><span class="sxs-lookup"><span data-stu-id="eaf97-212">**Private** :The alias is visible only in the current scope, not in the child  scopes.</span></span>
- <span data-ttu-id="eaf97-213">**ReadOnly** ：除非使用參數，否則無法變更別名的屬性 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="eaf97-213">**ReadOnly** :The properties of the alias cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="eaf97-214">您可以使用 `Remove-Item` 刪除別名。</span><span class="sxs-lookup"><span data-stu-id="eaf97-214">You can use `Remove-Item` to delete the alias.</span></span>
- <span data-ttu-id="eaf97-215">**AllScope** ：別名會複製到所建立的任何新範圍。</span><span class="sxs-lookup"><span data-stu-id="eaf97-215">**AllScope** :The alias is copied to any new scopes that are created.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="eaf97-216">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eaf97-216">Cmdlets supported</span></span>

- [<span data-ttu-id="eaf97-217">New-Item</span><span class="sxs-lookup"><span data-stu-id="eaf97-217">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="eaf97-218">Set-Item</span><span class="sxs-lookup"><span data-stu-id="eaf97-218">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="eaf97-219">使用管線</span><span class="sxs-lookup"><span data-stu-id="eaf97-219">Using the pipeline</span></span>

<span data-ttu-id="eaf97-220">提供者 Cmdlet 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="eaf97-220">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="eaf97-221">您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。</span><span class="sxs-lookup"><span data-stu-id="eaf97-221">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="eaf97-222">若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="eaf97-222">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="eaf97-223">取得說明</span><span class="sxs-lookup"><span data-stu-id="eaf97-223">Getting help</span></span>

<span data-ttu-id="eaf97-224">從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。</span><span class="sxs-lookup"><span data-stu-id="eaf97-224">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="eaf97-225">若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 的參數來指定檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="eaf97-225">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a><span data-ttu-id="eaf97-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaf97-226">See also</span></span>

[<span data-ttu-id="eaf97-227">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="eaf97-227">about_Aliases</span></span>](../About/about_Aliases.md)

[<span data-ttu-id="eaf97-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="eaf97-228">about_Providers</span></span>](../About/about_Providers.md)

