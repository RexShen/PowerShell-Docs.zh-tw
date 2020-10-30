---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用登錄項目
description: 本文討論如何使用 PowerShell 來處理登錄項目。
ms.openlocfilehash: 65f8b4ed7b2f9af26bfd22f34577a4bd52f35e70
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501451"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="32ec6-104">使用登錄項目</span><span class="sxs-lookup"><span data-stu-id="32ec6-104">Working with Registry Entries</span></span>

<span data-ttu-id="32ec6-105">因為登錄項目是機碼的屬性，所以無法直接瀏覽，在使用時，必須採取稍微不同的方法。</span><span class="sxs-lookup"><span data-stu-id="32ec6-105">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="32ec6-106">列出登錄項目</span><span class="sxs-lookup"><span data-stu-id="32ec6-106">Listing Registry Entries</span></span>

<span data-ttu-id="32ec6-107">有許多方法可以檢查登錄項目。</span><span class="sxs-lookup"><span data-stu-id="32ec6-107">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="32ec6-108">最簡單的方法是取得與機碼相關聯的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="32ec6-108">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="32ec6-109">例如，若要查看登錄機碼 `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion` 中的項目名稱，請使用 `Get-Item`。</span><span class="sxs-lookup"><span data-stu-id="32ec6-109">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="32ec6-110">登錄機碼有一個具有一般名稱 "Property" 的屬性，是機碼中之登錄項目的清單。</span><span class="sxs-lookup"><span data-stu-id="32ec6-110">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="32ec6-111">下列命令會選取 Property 屬性並展開項目，使項目顯示於清單中：</span><span class="sxs-lookup"><span data-stu-id="32ec6-111">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="32ec6-112">若要以更可讀的形式檢視登錄項目，請使用 `Get-ItemProperty`：</span><span class="sxs-lookup"><span data-stu-id="32ec6-112">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="32ec6-113">機碼的 Windows PowerShell 相關屬性都包含首碼 "PS"，例如 **PSPath** 、 **PSParentPath** 、 **PSChildName** 和 **PSProvider** 。</span><span class="sxs-lookup"><span data-stu-id="32ec6-113">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath** , **PSParentPath** , **PSChildName** , and **PSProvider** .</span></span>

<span data-ttu-id="32ec6-114">您可以使用 `*.*` 標記法以參照目前的位置。</span><span class="sxs-lookup"><span data-stu-id="32ec6-114">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="32ec6-115">您可以使用 `Set-Location` 先變更為 **CurrentVersion** 登錄容器：</span><span class="sxs-lookup"><span data-stu-id="32ec6-115">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="32ec6-116">或者，您可以使用內建的 HKLM PSDrive 來搭配 `Set-Location`：</span><span class="sxs-lookup"><span data-stu-id="32ec6-116">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="32ec6-117">接著，您可以使用 `*.*` 標記法來表示目前的位置，以列出屬性而不指定完整路徑：</span><span class="sxs-lookup"><span data-stu-id="32ec6-117">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="32ec6-118">路徑擴充的作用與在檔案系統中一致，因此從這個位置，您可以使用 `Get-ItemProperty -Path ..\Help` 取得 `HKLM:\SOFTWARE\Microsoft\Windows\Help` 的 **ItemProperty** 清單。</span><span class="sxs-lookup"><span data-stu-id="32ec6-118">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="32ec6-119">取得單一登錄項目</span><span class="sxs-lookup"><span data-stu-id="32ec6-119">Getting a Single Registry Entry</span></span>

<span data-ttu-id="32ec6-120">若要抓取登錄機碼中的特定項目，您可以使用數種可行方法之一。</span><span class="sxs-lookup"><span data-stu-id="32ec6-120">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="32ec6-121">此範例會在 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion` 中尋找 **DevicePath** 的值。</span><span class="sxs-lookup"><span data-stu-id="32ec6-121">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="32ec6-122">使用 `Get-ItemProperty` 時，請使用 **Path** 參數來指定機碼的名稱，並使用 **Name** 參數來指定 **DevicePath** 項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="32ec6-122">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="32ec6-123">此命令會傳回標準的 Windows PowerShell 屬性與 **DevicePath** 屬性。</span><span class="sxs-lookup"><span data-stu-id="32ec6-123">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="32ec6-124">雖然 `Get-ItemProperty` 包含 **Filter** 、 **Include** 與 **Exclude** 參數，但您無法使用它們來篩選屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="32ec6-124">Although `Get-ItemProperty` has **Filter** , **Include** , and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="32ec6-125">這些參數指的是登錄機碼 (即項目路徑，而非登錄項目)，即項目屬性。</span><span class="sxs-lookup"><span data-stu-id="32ec6-125">These parameters refer to registry keys, which are item paths and not registry entries, which are item properties.</span></span>

<span data-ttu-id="32ec6-126">另一個選項是使用 Reg.exe 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="32ec6-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="32ec6-127">如需 reg.exe 的說明，請在命令提示字元中輸入 `reg.exe /?`。</span><span class="sxs-lookup"><span data-stu-id="32ec6-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="32ec6-128">若要尋找 DevicePath 項目，請使用 reg.exe，如下列命令所示：</span><span class="sxs-lookup"><span data-stu-id="32ec6-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="32ec6-129">您也可以使用 **WshShell** COM 物件來尋找某些登錄項目，雖然此方法無法處理大型二進位資料或包含 "\\" 等字元的登錄項目名稱)。</span><span class="sxs-lookup"><span data-stu-id="32ec6-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="32ec6-130">使用 \\ 分隔符號將屬性名稱附加至項目路徑：</span><span class="sxs-lookup"><span data-stu-id="32ec6-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="32ec6-131">設定單一登錄項目</span><span class="sxs-lookup"><span data-stu-id="32ec6-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="32ec6-132">若要變更登錄機碼中的特定項目，您可以使用數種可行方法之一。</span><span class="sxs-lookup"><span data-stu-id="32ec6-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="32ec6-133">此範例會修改 `HKEY_CURRENT_USER\Environment` 下的 **Path** 項目。</span><span class="sxs-lookup"><span data-stu-id="32ec6-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="32ec6-134">**Path** 項目指定何處可找到可執行檔。</span><span class="sxs-lookup"><span data-stu-id="32ec6-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="32ec6-135">使用 `Get-ItemProperty` 擷取 **Path** 項目目前的值。</span><span class="sxs-lookup"><span data-stu-id="32ec6-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="32ec6-136">加入新的值，並使用 `;` 來分隔。</span><span class="sxs-lookup"><span data-stu-id="32ec6-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="32ec6-137">使用 `Set-ItemProperty` 搭配指定的機碼、項目名稱與值來修改登錄項目。</span><span class="sxs-lookup"><span data-stu-id="32ec6-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="32ec6-138">雖然 `Set-ItemProperty` 包含 **Filter** 、 **Include** 與 **Exclude** 參數，但您無法使用它們來篩選屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="32ec6-138">Although `Set-ItemProperty` has **Filter** , **Include** , and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="32ec6-139">這些參數指的是登錄機碼 (它們是項目路徑，不是登錄項目)，即項目屬性。</span><span class="sxs-lookup"><span data-stu-id="32ec6-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="32ec6-140">另一個選項是使用 Reg.exe 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="32ec6-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="32ec6-141">如需 reg.exe 的說明，請輸入 **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="32ec6-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="32ec6-142">。</span><span class="sxs-lookup"><span data-stu-id="32ec6-142">at a command prompt.</span></span>

<span data-ttu-id="32ec6-143">下列範例會透過刪除上述範例中加入的路徑來變更 **Path** 條目。</span><span class="sxs-lookup"><span data-stu-id="32ec6-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="32ec6-144">`Get-ItemProperty` 仍然用來擷取目前的值，以避免必須剖析從 `reg query` 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="32ec6-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="32ec6-145">**SubString** 與 **LastIndexOf** 方法用於擷取加入到 **Path** 項目的最後一個路徑。</span><span class="sxs-lookup"><span data-stu-id="32ec6-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="32ec6-146">建立新的登錄項目</span><span class="sxs-lookup"><span data-stu-id="32ec6-146">Creating New Registry Entries</span></span>

<span data-ttu-id="32ec6-147">若要將名為 "PowerShellPath" 的新項目新增至 **CurrentVersion** 機碼，請搭配機碼路徑、項目名稱與項目值使用 `New-ItemProperty`。</span><span class="sxs-lookup"><span data-stu-id="32ec6-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="32ec6-148">對於此範例，我們將接受 Windows PowerShell 變數 `$PSHome` 的值，它儲存 Windows PowerShell 安裝目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="32ec6-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="32ec6-149">您可以使用下列命令將新項目新增至機碼，此命令也會傳回關於新項目的資訊：</span><span class="sxs-lookup"><span data-stu-id="32ec6-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="32ec6-150">**PropertyType** 必須是下表之 **Microsoft.Win32.RegistryValueKind** 列舉成員的名稱：</span><span class="sxs-lookup"><span data-stu-id="32ec6-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="32ec6-151">PropertyType 值</span><span class="sxs-lookup"><span data-stu-id="32ec6-151">PropertyType Value</span></span>|<span data-ttu-id="32ec6-152">意義</span><span class="sxs-lookup"><span data-stu-id="32ec6-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="32ec6-153">Binary</span><span class="sxs-lookup"><span data-stu-id="32ec6-153">Binary</span></span>|<span data-ttu-id="32ec6-154">二進位資料</span><span class="sxs-lookup"><span data-stu-id="32ec6-154">Binary data</span></span>|
|<span data-ttu-id="32ec6-155">DWord</span><span class="sxs-lookup"><span data-stu-id="32ec6-155">DWord</span></span>|<span data-ttu-id="32ec6-156">屬於有效 UInt32 的數字</span><span class="sxs-lookup"><span data-stu-id="32ec6-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="32ec6-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="32ec6-157">ExpandString</span></span>|<span data-ttu-id="32ec6-158">可包含會動態展開之環境變數的字串</span><span class="sxs-lookup"><span data-stu-id="32ec6-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="32ec6-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="32ec6-159">MultiString</span></span>|<span data-ttu-id="32ec6-160">多行字串</span><span class="sxs-lookup"><span data-stu-id="32ec6-160">A multiline string</span></span>|
|<span data-ttu-id="32ec6-161">String</span><span class="sxs-lookup"><span data-stu-id="32ec6-161">String</span></span>|<span data-ttu-id="32ec6-162">任何字串值</span><span class="sxs-lookup"><span data-stu-id="32ec6-162">Any string value</span></span>|
|<span data-ttu-id="32ec6-163">QWord</span><span class="sxs-lookup"><span data-stu-id="32ec6-163">QWord</span></span>|<span data-ttu-id="32ec6-164">8 個位元組的二進位資料</span><span class="sxs-lookup"><span data-stu-id="32ec6-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="32ec6-165">為 **Path** 參數指定值陣列，可以將某個登錄項目新增至多個位置：</span><span class="sxs-lookup"><span data-stu-id="32ec6-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="32ec6-166">您也可以將 **Force** 參數新增至任一 `New-ItemProperty` 命令，以覆寫已存在的登錄項目值。</span><span class="sxs-lookup"><span data-stu-id="32ec6-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="32ec6-167">重新命名登錄項目</span><span class="sxs-lookup"><span data-stu-id="32ec6-167">Renaming Registry Entries</span></span>

<span data-ttu-id="32ec6-168">若要將 **PowerShellPath** 項目重新命名為 "PSHome"，請使用 `Rename-ItemProperty`：</span><span class="sxs-lookup"><span data-stu-id="32ec6-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="32ec6-169">若要顯示重新命名的值，請將 **PassThru** 參數新增至命令。</span><span class="sxs-lookup"><span data-stu-id="32ec6-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="32ec6-170">刪除登錄項目</span><span class="sxs-lookup"><span data-stu-id="32ec6-170">Deleting Registry Entries</span></span>

<span data-ttu-id="32ec6-171">若要刪除 PSHome 與 PowerShellPath 登錄項目，請使用 `Remove-ItemProperty`：</span><span class="sxs-lookup"><span data-stu-id="32ec6-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
