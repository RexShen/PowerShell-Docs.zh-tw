---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用登錄項目
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400940"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="92106-103">使用登錄項目</span><span class="sxs-lookup"><span data-stu-id="92106-103">Working with Registry Entries</span></span>

<span data-ttu-id="92106-104">因為登錄項目是機碼的屬性，所以無法直接瀏覽，在使用時，必須採取稍微不同的方法。</span><span class="sxs-lookup"><span data-stu-id="92106-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="92106-105">列出登錄項目</span><span class="sxs-lookup"><span data-stu-id="92106-105">Listing Registry Entries</span></span>

<span data-ttu-id="92106-106">有許多方法可以檢查登錄項目。</span><span class="sxs-lookup"><span data-stu-id="92106-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="92106-107">最簡單的方法是取得與機碼相關聯的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="92106-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="92106-108">例如，若要查看登錄機碼 **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion** 中的項目名稱，請使用 **Get-Item**。</span><span class="sxs-lookup"><span data-stu-id="92106-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="92106-109">登錄機碼有一個具有一般名稱 "Property" 的屬性，是機碼中之登錄項目的清單。</span><span class="sxs-lookup"><span data-stu-id="92106-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="92106-110">下列命令會選取 Property 屬性並展開項目，使項目顯示於清單中：</span><span class="sxs-lookup"><span data-stu-id="92106-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="92106-111">若要以更多可讀形式檢視登錄項目，請使用 **Get-ItemProperty**：</span><span class="sxs-lookup"><span data-stu-id="92106-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

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

<span data-ttu-id="92106-112">機碼的 Windows PowerShell 相關屬性都包含首碼 "PS"，例如 **PSPath**、**PSParentPath**、**PSChildName** 和 **PSProvider**。</span><span class="sxs-lookup"><span data-stu-id="92106-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="92106-113">您可以使用 "**.**" 標記法以參照目前的位置。</span><span class="sxs-lookup"><span data-stu-id="92106-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="92106-114">您可以先使用 **Set-Location** 來變更為 **CurrentVersion** 登錄容器：</span><span class="sxs-lookup"><span data-stu-id="92106-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="92106-115">或者，您可以使用內建的 HKLM PSDrive 來搭配 **Set-Location**：</span><span class="sxs-lookup"><span data-stu-id="92106-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="92106-116">接著，您可以使用 "**.**" 標記法來表示目前的位置，以列出屬性而不指定完整路徑：</span><span class="sxs-lookup"><span data-stu-id="92106-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="92106-117">路徑擴充的作用與在檔案系統中一致，因此從這個位置，您可以使用 **Get-ItemProperty -Path ..\\Help** 取得 **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** 的 **ItemProperty** 清單。</span><span class="sxs-lookup"><span data-stu-id="92106-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="92106-118">取得單一登錄項目</span><span class="sxs-lookup"><span data-stu-id="92106-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="92106-119">若要抓取登錄機碼中的特定項目，您可以使用數種可行方法之一。</span><span class="sxs-lookup"><span data-stu-id="92106-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="92106-120">這個範例會在 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion** 中尋找 **DevicePath** 的值。</span><span class="sxs-lookup"><span data-stu-id="92106-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="92106-121">使用 **Get-ItemProperty** 時，請使用 **Path** 參數來指定機碼的名稱，並使用 **Name** 參數來指定 **DevicePath** 項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="92106-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="92106-122">此命令會傳回標準的 Windows PowerShell 屬性與 **DevicePath** 屬性。</span><span class="sxs-lookup"><span data-stu-id="92106-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="92106-123">雖然 **Get-ItemProperty** 包含 **Filter**、**Include** 與 **Exclude** 參數，但您無法使用它們來篩選屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="92106-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="92106-124">這些參數指的是登錄機碼 (它們是項目路徑，不是登錄項目)，即項目屬性。</span><span class="sxs-lookup"><span data-stu-id="92106-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="92106-125">另一個選項是使用 Reg.exe 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="92106-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="92106-126">如需 reg.exe 的說明，請輸入 **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="92106-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="92106-127">。</span><span class="sxs-lookup"><span data-stu-id="92106-127">at a command prompt.</span></span> <span data-ttu-id="92106-128">若要尋找 DevicePath 項目，請使用 reg.exe，如下列命令所示：</span><span class="sxs-lookup"><span data-stu-id="92106-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="92106-129">您也可以使用 **WshShell COM** 物件來尋找某些登錄項目，雖然此方法無法處理大型二進位資料或包含 "\\" 等字元的登錄項目名稱)。</span><span class="sxs-lookup"><span data-stu-id="92106-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="92106-130">使用 \\ 分隔符號將屬性名稱附加至項目路徑：</span><span class="sxs-lookup"><span data-stu-id="92106-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="92106-131">建立新的登錄項目</span><span class="sxs-lookup"><span data-stu-id="92106-131">Creating New Registry Entries</span></span>

<span data-ttu-id="92106-132">若要將名為 "PowerShellPath" 的新項目新增至 **CurrentVersion** 機碼，請搭配機碼路徑、項目名稱與項目值使用 **New-ItemProperty**。</span><span class="sxs-lookup"><span data-stu-id="92106-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="92106-133">對於此範例，我們將接受 Windows PowerShell 變數 **$PSHome** 的值，它儲存 Windows PowerShell 安裝目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="92106-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="92106-134">您可以使用下列命令將新項目新增至機碼，此命令也會傳回關於新項目的資訊：</span><span class="sxs-lookup"><span data-stu-id="92106-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="92106-135">**PropertyType** 必須是下表之 **Microsoft.Win32.RegistryValueKind** 列舉成員的名稱：</span><span class="sxs-lookup"><span data-stu-id="92106-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="92106-136">PropertyType 值</span><span class="sxs-lookup"><span data-stu-id="92106-136">PropertyType Value</span></span>|<span data-ttu-id="92106-137">意義</span><span class="sxs-lookup"><span data-stu-id="92106-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="92106-138">Binary</span><span class="sxs-lookup"><span data-stu-id="92106-138">Binary</span></span>|<span data-ttu-id="92106-139">二進位資料</span><span class="sxs-lookup"><span data-stu-id="92106-139">Binary data</span></span>|
|<span data-ttu-id="92106-140">DWord</span><span class="sxs-lookup"><span data-stu-id="92106-140">DWord</span></span>|<span data-ttu-id="92106-141">屬於有效 UInt32 的數字</span><span class="sxs-lookup"><span data-stu-id="92106-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="92106-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="92106-142">ExpandString</span></span>|<span data-ttu-id="92106-143">可包含會動態展開之環境變數的字串</span><span class="sxs-lookup"><span data-stu-id="92106-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="92106-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="92106-144">MultiString</span></span>|<span data-ttu-id="92106-145">多行字串</span><span class="sxs-lookup"><span data-stu-id="92106-145">A multiline string</span></span>|
|<span data-ttu-id="92106-146">String</span><span class="sxs-lookup"><span data-stu-id="92106-146">String</span></span>|<span data-ttu-id="92106-147">任何字串值</span><span class="sxs-lookup"><span data-stu-id="92106-147">Any string value</span></span>|
|<span data-ttu-id="92106-148">QWord</span><span class="sxs-lookup"><span data-stu-id="92106-148">QWord</span></span>|<span data-ttu-id="92106-149">8 個位元組的二進位資料</span><span class="sxs-lookup"><span data-stu-id="92106-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="92106-150">為 **Path** 參數指定值陣列，可以將某個登錄項目新增至多個位置：</span><span class="sxs-lookup"><span data-stu-id="92106-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="92106-151">您也可以將 **Force** 參數新增至任一 **New-ItemProperty** 命令，以覆寫已存在的登錄項目值。</span><span class="sxs-lookup"><span data-stu-id="92106-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="92106-152">重新命名登錄項目</span><span class="sxs-lookup"><span data-stu-id="92106-152">Renaming Registry Entries</span></span>

<span data-ttu-id="92106-153">若要將 **PowerShellPath** 項目重新命名為 "PSHome"，請使用 **Rename-ItemProperty**：</span><span class="sxs-lookup"><span data-stu-id="92106-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="92106-154">若要顯示重新命名的值，請將 **PassThru** 參數新增至命令。</span><span class="sxs-lookup"><span data-stu-id="92106-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="92106-155">刪除登錄項目</span><span class="sxs-lookup"><span data-stu-id="92106-155">Deleting Registry Entries</span></span>

<span data-ttu-id="92106-156">若要刪除 PSHome 與 PowerShellPath 登錄項目，請使用 **Remove-ItemProperty**：</span><span class="sxs-lookup"><span data-stu-id="92106-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```