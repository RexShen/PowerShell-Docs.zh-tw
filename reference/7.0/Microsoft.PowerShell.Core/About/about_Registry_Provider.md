---
description: 登錄
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 登錄提供者
ms.openlocfilehash: efed68c42d46d5a44864af6b8892413c680c6b4e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206775"
---
# <a name="registry-provider"></a><span data-ttu-id="099ab-104">登錄提供者</span><span class="sxs-lookup"><span data-stu-id="099ab-104">Registry provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="099ab-105">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="099ab-105">Provider name</span></span>

<span data-ttu-id="099ab-106">登錄</span><span class="sxs-lookup"><span data-stu-id="099ab-106">Registry</span></span>

## <a name="drives"></a><span data-ttu-id="099ab-107">磁碟機</span><span class="sxs-lookup"><span data-stu-id="099ab-107">Drives</span></span>

<span data-ttu-id="099ab-108">`HKLM:`, `HKCU:`</span><span class="sxs-lookup"><span data-stu-id="099ab-108">`HKLM:`, `HKCU:`</span></span>

## <a name="capabilities"></a><span data-ttu-id="099ab-109">功能</span><span class="sxs-lookup"><span data-stu-id="099ab-109">Capabilities</span></span>

<span data-ttu-id="099ab-110">**ShouldProcess** 、 **UseTransactions**</span><span class="sxs-lookup"><span data-stu-id="099ab-110">**ShouldProcess** , **UseTransactions**</span></span>

## <a name="short-description"></a><span data-ttu-id="099ab-111">簡短描述</span><span class="sxs-lookup"><span data-stu-id="099ab-111">Short description</span></span>

<span data-ttu-id="099ab-112">提供 PowerShell 中登錄機碼、專案和值的存取權。</span><span class="sxs-lookup"><span data-stu-id="099ab-112">Provides access to the registry keys, entries, and values in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="099ab-113">詳細描述</span><span class="sxs-lookup"><span data-stu-id="099ab-113">Detailed description</span></span>

<span data-ttu-id="099ab-114">PowerShell 登錄 **提供者** 可讓您在 powershell 中取得、新增、變更、清除和刪除登錄機碼、專案和值。</span><span class="sxs-lookup"><span data-stu-id="099ab-114">The PowerShell **Registry** provider lets you get, add, change, clear, and delete registry keys, entries, and values in PowerShell.</span></span>

<span data-ttu-id="099ab-115">登錄 **磁片磁碟機** 是階層式命名空間，其中包含電腦上的登錄機碼和子機碼。</span><span class="sxs-lookup"><span data-stu-id="099ab-115">The **Registry** drives are a hierarchical namespace containing the registry keys and subkeys on your computer.</span></span> <span data-ttu-id="099ab-116">登錄項目和值不是該階層的元件。</span><span class="sxs-lookup"><span data-stu-id="099ab-116">Registry entries and values are not components of that hierarchy.</span></span> <span data-ttu-id="099ab-117">相反地，它們是每個機碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-117">Instead, they are properties of each of the keys.</span></span>

<span data-ttu-id="099ab-118">登錄 **提供者** 支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。</span><span class="sxs-lookup"><span data-stu-id="099ab-118">The **Registry** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="099ab-119">Get-Location</span><span class="sxs-lookup"><span data-stu-id="099ab-119">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="099ab-120">Set-Location</span><span class="sxs-lookup"><span data-stu-id="099ab-120">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="099ab-121">Get-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-121">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="099ab-122">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="099ab-122">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="099ab-123">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-123">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="099ab-124">Move-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-124">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="099ab-125">New-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-125">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="099ab-126">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-126">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="099ab-127">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-127">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="099ab-128">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-128">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="099ab-129">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-129">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="099ab-130">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-130">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="099ab-131">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="099ab-131">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="099ab-132">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="099ab-132">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="099ab-133">此提供者公開的類型</span><span class="sxs-lookup"><span data-stu-id="099ab-133">Types exposed by this provider</span></span>

<span data-ttu-id="099ab-134">登錄機碼會以 [node.js 類別的](/dotnet/api/microsoft.win32.registrykey) 實例來表示。</span><span class="sxs-lookup"><span data-stu-id="099ab-134">Registry keys are represented as instances of the [Microsoft.Win32.RegistryKey](/dotnet/api/microsoft.win32.registrykey) class.</span></span> <span data-ttu-id="099ab-135">登錄專案會以 [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) 類別的實例來表示。</span><span class="sxs-lookup"><span data-stu-id="099ab-135">Registry entries are represented as instances of the [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) class.</span></span>

## <a name="navigating-the-registry-drives"></a><span data-ttu-id="099ab-136">流覽登錄磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="099ab-136">Navigating the Registry drives</span></span>

<span data-ttu-id="099ab-137">登錄 **提供者會將其** 資料存放區公開為兩個預設磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="099ab-137">The **Registry** provider exposes its data store as two default drives.</span></span> <span data-ttu-id="099ab-138">登錄位置 HKEY_LOCAL_MACHINE 會對應到 `HKLM:` 磁片磁碟機，HKEY_CURRENT_USER 對應到 `HKCU:` 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="099ab-138">The registry location HKEY_LOCAL_MACHINE is mapped to the `HKLM:` drive and HKEY_CURRENT_USER is mapped to the `HKCU:` drive.</span></span> <span data-ttu-id="099ab-139">若要使用登錄，您可以使用下列命令將位置變更為 `HKLM:` 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="099ab-139">To work with the registry, you can change your location to the `HKLM:` drive using the following command.</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="099ab-140">若要返回檔案系統磁碟機，請輸入磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="099ab-140">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="099ab-141">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="099ab-141">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="099ab-142">您也可以從任何其他 PowerShell 磁片磁碟機使用 **登錄提供者** 。</span><span class="sxs-lookup"><span data-stu-id="099ab-142">You can also work with the **Registry** provider from any other PowerShell drive.</span></span> <span data-ttu-id="099ab-143">若要參考另一個位置的登錄機碼，請使用路徑中的磁片磁碟機名稱 (`HKLM:` ， `HKCU:`) 。</span><span class="sxs-lookup"><span data-stu-id="099ab-143">To reference a registry key from another location, use the drive name (`HKLM:`, `HKCU:`) in the path.</span></span> <span data-ttu-id="099ab-144">使用反斜線 (\\) 或正斜線 (/) 來表示登錄磁片磁碟機的層 **Registry** 級。</span><span class="sxs-lookup"><span data-stu-id="099ab-144">Use a backslash (\\) or a forward slash (/) to indicate a level of the **Registry** drive.</span></span>

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> <span data-ttu-id="099ab-145">PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="099ab-145">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="099ab-146">和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名，而且 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="099ab-146">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location), and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

<span data-ttu-id="099ab-147">最後一個範例會示範另一個路徑語法，您可以用來流覽 **登錄提供者** 。</span><span class="sxs-lookup"><span data-stu-id="099ab-147">This last example shows another path syntax you can use to navigate the **Registry** provider.</span></span> <span data-ttu-id="099ab-148">此語法會使用提供者名稱，後面加上兩個冒號 `::` 。</span><span class="sxs-lookup"><span data-stu-id="099ab-148">This syntax uses the provider name, followed by two colons `::`.</span></span> <span data-ttu-id="099ab-149">此語法可讓您使用完整的 HIVE 名稱，而不是對應的磁片磁碟機名稱 `HKLM` 。</span><span class="sxs-lookup"><span data-stu-id="099ab-149">This syntax allows you to use the full HIVE name, instead of the mapped drive name `HKLM`.</span></span>

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a><span data-ttu-id="099ab-150">顯示登錄機碼的內容</span><span class="sxs-lookup"><span data-stu-id="099ab-150">Displaying the contents of registry keys</span></span>

<span data-ttu-id="099ab-151">登錄會分割成機碼、子機碼和專案。</span><span class="sxs-lookup"><span data-stu-id="099ab-151">The registry is divided into keys, subkeys, and entries.</span></span> <span data-ttu-id="099ab-152">如需登錄結構的詳細資訊，請參閱登錄 [結構](/windows/desktop/sysinfo/structure-of-the-registry)。</span><span class="sxs-lookup"><span data-stu-id="099ab-152">For more information about registry structure, see [Structure of the Registry](/windows/desktop/sysinfo/structure-of-the-registry).</span></span>

<span data-ttu-id="099ab-153">**在登錄磁片磁碟機** 中，每個金鑰都是一個容器。</span><span class="sxs-lookup"><span data-stu-id="099ab-153">In a **Registry** drive, each key is a container.</span></span> <span data-ttu-id="099ab-154">索引鍵可以包含任意數目的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="099ab-154">A key can contain any number of keys.</span></span> <span data-ttu-id="099ab-155">具有父機碼的登錄機碼稱為子機碼。</span><span class="sxs-lookup"><span data-stu-id="099ab-155">A registry key that has a parent key is called a subkey.</span></span> <span data-ttu-id="099ab-156">您可以使用 `Get-ChildItem` 來查看登錄機碼，並 `Set-Location` 流覽至金鑰路徑。</span><span class="sxs-lookup"><span data-stu-id="099ab-156">You can use `Get-ChildItem` to view registry keys and `Set-Location` to navigate to a key path.</span></span>

<span data-ttu-id="099ab-157">登錄值是登錄機碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-157">Registry values are attributes of a registry key.</span></span> <span data-ttu-id="099ab-158">**在登錄磁片磁碟機** 中，它們稱為 **專案屬性** 。</span><span class="sxs-lookup"><span data-stu-id="099ab-158">In the **Registry** drive, they are called **Item Properties** .</span></span> <span data-ttu-id="099ab-159">登錄機碼可以同時具有子系索引鍵和專案屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-159">A registry key can have both children keys and item properties.</span></span>

<span data-ttu-id="099ab-160">在此範例中， `Get-Item` 會顯示和之間的差異 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="099ab-160">In this example, the difference between `Get-Item` and `Get-ChildItem` is shown.</span></span> <span data-ttu-id="099ab-161">當您在「多工緩衝處理器」 `Get-Item` 登錄機碼上使用時，可以看到它的屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-161">When you use `Get-Item` on the "Spooler" registry key, you can view its properties.</span></span>

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

<span data-ttu-id="099ab-162">每個登錄機碼也可以有子機碼。</span><span class="sxs-lookup"><span data-stu-id="099ab-162">Each registry key can also have subkeys.</span></span> <span data-ttu-id="099ab-163">當您使用 `Get-Item` 登錄機碼時，不會顯示子機碼。</span><span class="sxs-lookup"><span data-stu-id="099ab-163">When you use `Get-Item` on a registry key, the subkeys are not displayed.</span></span> <span data-ttu-id="099ab-164">此 Cmdlet 會顯示「多工緩衝處理器」索引 `Get-ChildItem` 鍵的子專案，包括每個子機碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-164">The `Get-ChildItem` cmdlet will show you children items of the "Spooler" key, including each subkey's properties.</span></span> <span data-ttu-id="099ab-165">使用時，不會顯示父索引鍵屬性 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="099ab-165">The parent keys properties are not shown when using `Get-ChildItem`.</span></span>

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

<span data-ttu-id="099ab-166">`Get-Item`Cmdlet 也可以在目前的位置上使用。</span><span class="sxs-lookup"><span data-stu-id="099ab-166">The `Get-Item` cmdlet can also be used on the current location.</span></span> <span data-ttu-id="099ab-167">下列範例會流覽至「多工緩衝處理器」登錄機碼，並取得專案屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-167">The following example navigates to the "Spooler" registry key and gets the item properties.</span></span>
<span data-ttu-id="099ab-168">點 `.` 用來表示目前的位置。</span><span class="sxs-lookup"><span data-stu-id="099ab-168">The dot `.` is used to indicate the current location.</span></span>

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

<span data-ttu-id="099ab-169">如需本節所涵蓋之 Cmdlet 的詳細資訊，請參閱下列文章。</span><span class="sxs-lookup"><span data-stu-id="099ab-169">For more information on the cmdlets covered in this section, see the following articles.</span></span>

<span data-ttu-id="099ab-170">-[取得專案](xref:Microsoft.PowerShell.Management.Get-Item) 
-[Get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="099ab-170">-[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
-[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span></span>

## <a name="viewing-registry-key-values"></a><span data-ttu-id="099ab-171">查看登錄機碼值</span><span class="sxs-lookup"><span data-stu-id="099ab-171">Viewing registry key values</span></span>

<span data-ttu-id="099ab-172">登錄機碼值會儲存為每個登錄機碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-172">Registry key values are stored as properties of each registry key.</span></span> <span data-ttu-id="099ab-173">此 `Get-ItemProperty` Cmdlet 會使用您指定的名稱來查看登錄機碼屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-173">The `Get-ItemProperty` cmdlet views registry key properties using the name you specify.</span></span> <span data-ttu-id="099ab-174">結果是包含您指定之屬性的 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="099ab-174">The result is a **PSCustomObject** containing the properties you specify.</span></span>

<span data-ttu-id="099ab-175">下列範例會使用 `Get-ItemProperty` Cmdlet 來查看所有屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-175">The Following example uses the `Get-ItemProperty` cmdlet to view all properties.</span></span> <span data-ttu-id="099ab-176">將產生的物件儲存在變數中，可讓您存取所需的屬性值。</span><span class="sxs-lookup"><span data-stu-id="099ab-176">Storing the resulting object in a variable allows you to access the desired property value.</span></span>

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

<span data-ttu-id="099ab-177">指定參數的值 `-Name` 會選取您指定的屬性，並傳回 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="099ab-177">Specifying a value for the `-Name` parameter selects the properties you specify and returns the **PSCustomObject** .</span></span>  <span data-ttu-id="099ab-178">下列範例顯示當您使用參數時，輸出中的差異 `-Name` 。</span><span class="sxs-lookup"><span data-stu-id="099ab-178">The following example shows the difference in output when you use the `-Name` parameter.</span></span>

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

<span data-ttu-id="099ab-179">從 PowerShell 5.0 開始，此 `Get-ItemPropertyValue` Cmdlet 只會傳回您指定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="099ab-179">Beginning in PowerShell 5.0, the `Get-ItemPropertyValue` cmdlet returns only the value of the property you specify.</span></span>

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

<span data-ttu-id="099ab-180">如需本節中所使用之 Cmdlet 的詳細資訊，請參閱下列文章。</span><span class="sxs-lookup"><span data-stu-id="099ab-180">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="099ab-181">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-181">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="099ab-182">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="099ab-182">Get-ItemPropertyValue</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a><span data-ttu-id="099ab-183">變更登錄機碼值</span><span class="sxs-lookup"><span data-stu-id="099ab-183">Changing registry key values</span></span>

<span data-ttu-id="099ab-184">此 `Set-ItemProperty` Cmdlet 會設定登錄機碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="099ab-184">The `Set-ItemProperty` cmdlet will set attributes for registry keys.</span></span> <span data-ttu-id="099ab-185">下列範例會使用 `Set-ItemProperty` 將多工緩衝處理器服務啟動類型變更為手動。</span><span class="sxs-lookup"><span data-stu-id="099ab-185">The following example uses `Set-ItemProperty` to change the spooler service start type to manual.</span></span> <span data-ttu-id="099ab-186">此範例會使用 Cmdlet 將 **StartType** 變更回 *自動* `Set-Service` 。</span><span class="sxs-lookup"><span data-stu-id="099ab-186">The example changes the **StartType** back to *Automatic* using the `Set-Service` cmdlet.</span></span>

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

<span data-ttu-id="099ab-187">每個登錄機碼都有 *預設* 值。</span><span class="sxs-lookup"><span data-stu-id="099ab-187">Each registry key has a *default* value.</span></span> <span data-ttu-id="099ab-188">您可以使用或來變更登錄機碼的 *預設* 值 `Set-Item` `Set-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="099ab-188">You can change the *default* value for a registry key with either `Set-Item` or `Set-ItemProperty`.</span></span>

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

<span data-ttu-id="099ab-189">如需本節中所使用之 Cmdlet 的詳細資訊，請參閱下列文章。</span><span class="sxs-lookup"><span data-stu-id="099ab-189">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="099ab-190">Set-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-190">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="099ab-191">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-191">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a><span data-ttu-id="099ab-192">建立登錄機碼和值</span><span class="sxs-lookup"><span data-stu-id="099ab-192">Creating registry keys and values</span></span>

<span data-ttu-id="099ab-193">`New-Item`Cmdlet 會以您提供的名稱建立登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="099ab-193">The `New-Item` cmdlet will create registry keys with a name that you provide.</span></span>
<span data-ttu-id="099ab-194">您也可以使用函式 `mkdir` ，它會 `New-Item` 在內部呼叫 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="099ab-194">You can also use the `mkdir` function, which calls the `New-Item` cmdlet internally.</span></span>

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

<span data-ttu-id="099ab-195">您可以使用 `New-ItemProperty` Cmdlet，在您指定的登錄機碼中建立值。</span><span class="sxs-lookup"><span data-stu-id="099ab-195">You can use the `New-ItemProperty` cmdlet to create values in a registry key that you specify.</span></span> <span data-ttu-id="099ab-196">下列範例會在 ContosoCompany 登錄機碼上建立新的 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="099ab-196">The following example creates a new DWORD value on the ContosoCompany registry key.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> <span data-ttu-id="099ab-197">請參閱本文中的「動態參數」一節，以瞭解其他允許的類型值。</span><span class="sxs-lookup"><span data-stu-id="099ab-197">Review the dynamic parameters section in this article for other allowed type values.</span></span>

<span data-ttu-id="099ab-198">如需詳細的 Cmdlet 用法，請參閱 [ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)。</span><span class="sxs-lookup"><span data-stu-id="099ab-198">For detailed cmdlet usage, see [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span></span>

## <a name="copying-registry-keys-and-values"></a><span data-ttu-id="099ab-199">複製登錄機碼和值</span><span class="sxs-lookup"><span data-stu-id="099ab-199">Copying registry keys and values</span></span>

<span data-ttu-id="099ab-200">**在登錄提供者** 中，使用 `Copy-Item` Cmdlet 複製登錄機碼和值。</span><span class="sxs-lookup"><span data-stu-id="099ab-200">In the **Registry** provider, use the `Copy-Item` cmdlet copies registry keys and values.</span></span> <span data-ttu-id="099ab-201">使用 `Copy-ItemProperty` Cmdlet 只複製登錄值。</span><span class="sxs-lookup"><span data-stu-id="099ab-201">Use the `Copy-ItemProperty` cmdlet to copy registry values only.</span></span>
<span data-ttu-id="099ab-202">下列命令會將 "Contoso" 登錄機碼及其屬性複製到指定的位置 "HKLM： \ Software\Fabrikam"。</span><span class="sxs-lookup"><span data-stu-id="099ab-202">The following command copies the "Contoso" registry key, and its properties to the specified location "HKLM:\Software\Fabrikam".</span></span>

<span data-ttu-id="099ab-203">`Copy-Item` 建立目的地金鑰（如果不存在）。</span><span class="sxs-lookup"><span data-stu-id="099ab-203">`Copy-Item` creates the destination key if it does not exist.</span></span> <span data-ttu-id="099ab-204">如果目的地金鑰存在，會 `Copy-Item` 建立來源金鑰的複本做為子專案， (子機碼) 的子專案。</span><span class="sxs-lookup"><span data-stu-id="099ab-204">If the destination key exists, `Copy-Item` creates a duplicate of the source key as a child item (subkey) of the destination key.</span></span>

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

<span data-ttu-id="099ab-205">下列命令會使用 `Copy-ItemProperty` Cmdlet，將 "Server" 值從 "Contoso" 機碼複製到 "Fabrikam" 機碼。</span><span class="sxs-lookup"><span data-stu-id="099ab-205">The following command uses the `Copy-ItemProperty` cmdlet to copy the "Server" value from the "Contoso" key to the "Fabrikam" key.</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

<span data-ttu-id="099ab-206">如需本節中所使用之 Cmdlet 的詳細資訊，請參閱下列文章。</span><span class="sxs-lookup"><span data-stu-id="099ab-206">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="099ab-207">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-207">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="099ab-208">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-208">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a><span data-ttu-id="099ab-209">移動登錄機碼和值</span><span class="sxs-lookup"><span data-stu-id="099ab-209">Moving registry keys and values</span></span>

<span data-ttu-id="099ab-210">`Move-Item`和 `Move-ItemProperty` Cmdlet 的行為就像其「複製」的對應專案。</span><span class="sxs-lookup"><span data-stu-id="099ab-210">The `Move-Item` and `Move-ItemProperty` cmdlets behave like their "Copy" counterparts.</span></span> <span data-ttu-id="099ab-211">如果目的地存在，請 `Move-Item` 將來源金鑰移至目的地機碼下方。</span><span class="sxs-lookup"><span data-stu-id="099ab-211">If the destination exists, `Move-Item` moves the source key underneath the destination key.</span></span> <span data-ttu-id="099ab-212">如果目的地機碼不存在，則會將來源索引鍵移至目的地路徑。</span><span class="sxs-lookup"><span data-stu-id="099ab-212">If the destination key does not exist, the source key is moved to the destination path.</span></span>

<span data-ttu-id="099ab-213">下列命令會將 "Contoso" 機碼移至 "HKLM： \ SOFTWARE\Fabrikam" 路徑。</span><span class="sxs-lookup"><span data-stu-id="099ab-213">The following command moves the "Contoso" key to the path "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

<span data-ttu-id="099ab-214">此命令會將所有屬性從 "HKLM： \ SOFTWARE\ContosoCompany" 移至 "HKLM： \ SOFTWARE\Fabrikam"。</span><span class="sxs-lookup"><span data-stu-id="099ab-214">This command moves all of the properties from "HKLM:\SOFTWARE\ContosoCompany" to "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

<span data-ttu-id="099ab-215">如需本節中所使用之 Cmdlet 的詳細資訊，請參閱下列文章。</span><span class="sxs-lookup"><span data-stu-id="099ab-215">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="099ab-216">Move-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-216">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="099ab-217">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-217">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a><span data-ttu-id="099ab-218">重新命名登錄機碼和值</span><span class="sxs-lookup"><span data-stu-id="099ab-218">Renaming registry keys and values</span></span>

<span data-ttu-id="099ab-219">您可以重新命名登錄機碼和值，就像是檔案和資料夾一樣。</span><span class="sxs-lookup"><span data-stu-id="099ab-219">You can rename registry keys and values just like you would files and folders.</span></span>
<span data-ttu-id="099ab-220">`Rename-Item` 重新命名登錄機碼，同時重新 `Rename-ItemProperty` 命名登錄值。</span><span class="sxs-lookup"><span data-stu-id="099ab-220">`Rename-Item` renames registry keys, while `Rename-ItemProperty` renames registry values.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a><span data-ttu-id="099ab-221">變更安全描述項</span><span class="sxs-lookup"><span data-stu-id="099ab-221">Changing security descriptors</span></span>

<span data-ttu-id="099ab-222">您可以使用和 Cmdlet 來限制對登錄機碼的存取 `Get-Acl` `Set-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="099ab-222">You can restrict access to registry keys using the `Get-Acl` and `Set-Acl` cmdlets.</span></span> <span data-ttu-id="099ab-223">下列範例會將具有完整控制權的新使用者新增至 "HKLM： \ SOFTWARE\Contoso" 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="099ab-223">The following example adds a new user with full control to the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

<span data-ttu-id="099ab-224">如需更多範例和 Cmdlet 使用方式的詳細資料，請參閱下列文章。</span><span class="sxs-lookup"><span data-stu-id="099ab-224">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="099ab-225">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="099ab-225">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="099ab-226">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="099ab-226">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a><span data-ttu-id="099ab-227">移除和清除登錄機碼和值</span><span class="sxs-lookup"><span data-stu-id="099ab-227">Removing and clearing registry keys and values</span></span>

<span data-ttu-id="099ab-228">您可以使用 [ **移除專案** ] 移除包含的專案，但如果專案包含任何其他專案，系統會提示您確認移除。</span><span class="sxs-lookup"><span data-stu-id="099ab-228">You can remove contained items by using **Remove-Item** , but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="099ab-229">下列範例會嘗試刪除機碼 "HKLM： \ SOFTWARE\Contoso"。</span><span class="sxs-lookup"><span data-stu-id="099ab-229">The following example attempts to delete a key "HKLM:\SOFTWARE\Contoso".</span></span>

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="099ab-230">若要在不提示的情況下刪除包含的專案，請指定 `-Recurse` 參數。</span><span class="sxs-lookup"><span data-stu-id="099ab-230">To delete contained items without prompting, specify the `-Recurse` parameter.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

<span data-ttu-id="099ab-231">如果您想要移除 "HKLM： \ SOFTWARE\Contoso" 中的所有專案，而不是 "HKLM： \ SOFTWARE\Contoso" 本身，請使用尾端反斜線， `\` 後面接著萬用字元。</span><span class="sxs-lookup"><span data-stu-id="099ab-231">If you wanted to remove all items within "HKLM:\SOFTWARE\Contoso" but not "HKLM:\SOFTWARE\Contoso" itself, use a trailing backslash `\` followed by a wildcard.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

<span data-ttu-id="099ab-232">此命令會刪除 "HKLM： \ SOFTWARE\Contoso" 登錄機碼中的 "ContosoTest" 登錄值。</span><span class="sxs-lookup"><span data-stu-id="099ab-232">This command deletes the "ContosoTest" registry value from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

<span data-ttu-id="099ab-233">`Clear-Item` 清除機碼的所有登錄值。</span><span class="sxs-lookup"><span data-stu-id="099ab-233">`Clear-Item` clears all registry values for a key.</span></span> <span data-ttu-id="099ab-234">下列範例會清除 "HKLM： \ SOFTWARE\Contoso" 登錄機碼中的所有值。</span><span class="sxs-lookup"><span data-stu-id="099ab-234">The following example clears all values from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span> <span data-ttu-id="099ab-235">若只要清除特定的屬性，請使用 `Clear-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="099ab-235">To clear only a specific property, use `Clear-ItemProperty`.</span></span>

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

<span data-ttu-id="099ab-236">如需更多範例和 Cmdlet 使用方式的詳細資料，請參閱下列文章。</span><span class="sxs-lookup"><span data-stu-id="099ab-236">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="099ab-237">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-237">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="099ab-238">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-238">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="099ab-239">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-239">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="099ab-240">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-240">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a><span data-ttu-id="099ab-241">動態參數</span><span class="sxs-lookup"><span data-stu-id="099ab-241">Dynamic parameters</span></span>

<span data-ttu-id="099ab-242">動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。</span><span class="sxs-lookup"><span data-stu-id="099ab-242">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="type-microsoftwin32registryvaluekind"></a><span data-ttu-id="099ab-243">輸入 <>microsoft.win32.registryvaluekind></span><span class="sxs-lookup"><span data-stu-id="099ab-243">Type <Microsoft.Win32.RegistryValueKind></span></span>

<span data-ttu-id="099ab-244">建立或變更登錄值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="099ab-244">Establishes or changes the data type of a registry value.</span></span> <span data-ttu-id="099ab-245">預設值為 `String` (REG_SZ) 。</span><span class="sxs-lookup"><span data-stu-id="099ab-245">The default is `String` (REG_SZ).</span></span>

<span data-ttu-id="099ab-246">這個參數是設計來在 [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) Cmdlet 上運作的。</span><span class="sxs-lookup"><span data-stu-id="099ab-246">This parameter works as designed on the [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet.</span></span> <span data-ttu-id="099ab-247">它也可以在登錄磁碟機中的 [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) Cmdlet 上使用，但不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="099ab-247">It is also available on the [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet in the registry drives, but it has no effect.</span></span>

|<span data-ttu-id="099ab-248">值</span><span class="sxs-lookup"><span data-stu-id="099ab-248">Value</span></span> | <span data-ttu-id="099ab-249">描述</span><span class="sxs-lookup"><span data-stu-id="099ab-249">Description</span></span> |
| ---- | ----------- |
| `String` | <span data-ttu-id="099ab-250">指定以 null 終止的字串。</span><span class="sxs-lookup"><span data-stu-id="099ab-250">Specifies a null-terminated string.</span></span> <span data-ttu-id="099ab-251">相當於 REG_SZ。</span><span class="sxs-lookup"><span data-stu-id="099ab-251">Equivalent to REG_SZ.</span></span> |
| `ExpandString` | <span data-ttu-id="099ab-252">指定包含未展開的 null 終止字串</span><span class="sxs-lookup"><span data-stu-id="099ab-252">Specifies a null-terminated string that contains unexpanded</span></span> |
|                | <span data-ttu-id="099ab-253">環境變數的參考，這些變數是在</span><span class="sxs-lookup"><span data-stu-id="099ab-253">references to environment variables that are expanded when</span></span> |
|                | <span data-ttu-id="099ab-254">此值為已抓取。</span><span class="sxs-lookup"><span data-stu-id="099ab-254">the value is retrieved.</span></span> <span data-ttu-id="099ab-255">相當於 REG_EXPAND_SZ。</span><span class="sxs-lookup"><span data-stu-id="099ab-255">Equivalent to REG_EXPAND_SZ.</span></span> |
| `Binary` | <span data-ttu-id="099ab-256">指定任意形式的二進位資料。</span><span class="sxs-lookup"><span data-stu-id="099ab-256">Specifies binary data in any form.</span></span> <span data-ttu-id="099ab-257">相當於 REG_BINARY。</span><span class="sxs-lookup"><span data-stu-id="099ab-257">Equivalent to REG_BINARY.</span></span> |
| `DWord` | <span data-ttu-id="099ab-258">指定 32 位元的二進位數字。</span><span class="sxs-lookup"><span data-stu-id="099ab-258">Specifies a 32-bit binary number.</span></span> <span data-ttu-id="099ab-259">相當於 REG_DWORD。</span><span class="sxs-lookup"><span data-stu-id="099ab-259">Equivalent to REG_DWORD.</span></span> |
| `MultiString` | <span data-ttu-id="099ab-260">指定以 null 終止的字串陣列，由</span><span class="sxs-lookup"><span data-stu-id="099ab-260">Specifies an array of null-terminated strings terminated by</span></span> |
|               | <span data-ttu-id="099ab-261">兩個 null 字元。</span><span class="sxs-lookup"><span data-stu-id="099ab-261">two null characters.</span></span> <span data-ttu-id="099ab-262">相當於 REG_MULTI_SZ。</span><span class="sxs-lookup"><span data-stu-id="099ab-262">Equivalent to REG_MULTI_SZ.</span></span> |
| `QWord` | <span data-ttu-id="099ab-263">指定 64 位元的二進位數字。</span><span class="sxs-lookup"><span data-stu-id="099ab-263">Specifies a 64-bit binary number.</span></span> <span data-ttu-id="099ab-264">相當於 REG_QWORD。</span><span class="sxs-lookup"><span data-stu-id="099ab-264">Equivalent to REG_QWORD.</span></span> |
| `Unknown` | <span data-ttu-id="099ab-265">指出不支援的登錄資料類型，例如</span><span class="sxs-lookup"><span data-stu-id="099ab-265">Indicates an unsupported registry data type, such as</span></span> |
|           | <span data-ttu-id="099ab-266">REG_RESOURCE_LIST。</span><span class="sxs-lookup"><span data-stu-id="099ab-266">REG_RESOURCE_LIST.</span></span> |

#### <a name="cmdlets-supported"></a><span data-ttu-id="099ab-267">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="099ab-267">Cmdlets supported</span></span>

- [<span data-ttu-id="099ab-268">Set-Item</span><span class="sxs-lookup"><span data-stu-id="099ab-268">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="099ab-269">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="099ab-269">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a><span data-ttu-id="099ab-270">使用管線</span><span class="sxs-lookup"><span data-stu-id="099ab-270">Using the pipeline</span></span>

<span data-ttu-id="099ab-271">提供者 Cmdlet 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="099ab-271">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="099ab-272">您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。</span><span class="sxs-lookup"><span data-stu-id="099ab-272">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span> <span data-ttu-id="099ab-273">若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="099ab-273">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="099ab-274">取得說明</span><span class="sxs-lookup"><span data-stu-id="099ab-274">Getting help</span></span>

<span data-ttu-id="099ab-275">從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。</span><span class="sxs-lookup"><span data-stu-id="099ab-275">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="099ab-276">若要取得針對檔案系統磁片磁碟機自訂的說明主題，請 `Get-Help` 在檔案系統磁片磁碟機中執行命令，或使用 **Path** 參數來指定檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="099ab-276">To get the help topics that are customized for the file system drive, run a `Get-Help` command in a file system drive or use the **Path** parameter to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a><span data-ttu-id="099ab-277">另請參閱</span><span class="sxs-lookup"><span data-stu-id="099ab-277">See also</span></span>

 [<span data-ttu-id="099ab-278">about_Providers</span><span class="sxs-lookup"><span data-stu-id="099ab-278">about_Providers</span></span>](../About/about_Providers.md)
