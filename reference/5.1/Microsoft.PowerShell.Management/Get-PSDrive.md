---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: 7a37857d9a4fb9eb18869ef78dc0ac19dc26367f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203992"
---
# <span data-ttu-id="ad09a-103">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ad09a-103">Get-PSDrive</span></span>

## <span data-ttu-id="ad09a-104">概要</span><span class="sxs-lookup"><span data-stu-id="ad09a-104">SYNOPSIS</span></span>
<span data-ttu-id="ad09a-105">取得目前工作階段中的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-105">Gets drives in the current session.</span></span>

## <span data-ttu-id="ad09a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ad09a-106">SYNTAX</span></span>

### <span data-ttu-id="ad09a-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="ad09a-107">Name (Default)</span></span>

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="ad09a-108">LiteralName</span><span class="sxs-lookup"><span data-stu-id="ad09a-108">LiteralName</span></span>

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="ad09a-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ad09a-109">DESCRIPTION</span></span>

<span data-ttu-id="ad09a-110">`Get-PSDrive`Cmdlet 會取得目前會話中的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-110">The `Get-PSDrive` cmdlet gets the drives in the current session.</span></span> <span data-ttu-id="ad09a-111">您可以取得工作階段中的特定磁碟機或所有磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-111">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="ad09a-112">此 Cmdlet 會取得下列類型的磁片磁碟機：</span><span class="sxs-lookup"><span data-stu-id="ad09a-112">This cmdlet gets the following types of drives:</span></span>

- <span data-ttu-id="ad09a-113">電腦上的 Windows 邏輯磁碟機，包括對應至網路共用的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-113">Windows logical drives on the computer, including drives mapped to network shares.</span></span>
- <span data-ttu-id="ad09a-114">PowerShell 提供者所公開的磁片磁碟機 (例如 Certificate：、Function：和 Alias：磁片磁碟機) 和 Windows PowerShell 登錄提供者所公開的 HKLM：和 HKCU：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-114">Drives exposed by PowerShell providers (such as the Certificate:, Function:, and Alias: drives) and the HKLM: and HKCU: drives that are exposed by the Windows PowerShell Registry provider.</span></span>
- <span data-ttu-id="ad09a-115">工作階段指定的暫時性磁碟機，以及您使用 New-PSDrive Cmdlet 建立的永久連線網路磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-115">Session-specified temporary drives and persistent mapped network drives that you create by using the New-PSDrive cmdlet.</span></span>

<span data-ttu-id="ad09a-116">從 Windows PowerShell 3.0 開始，此 Cmdlet 的 **保存** 參數 `New-PSDrive` 可以建立儲存在本機電腦上且可在其他會話中使用的對應網路磁碟機機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-116">Beginning in Windows PowerShell 3.0, the **Persist** parameter of the `New-PSDrive` cmdlet can create mapped network drives that are saved on the local computer and are available in other sessions.</span></span> <span data-ttu-id="ad09a-117">如需詳細資訊，請參閱 New-PSDrive。</span><span class="sxs-lookup"><span data-stu-id="ad09a-117">For more information, see New-PSDrive.</span></span>

<span data-ttu-id="ad09a-118">此外，從 Windows PowerShell 3.0 開始，當外接式磁碟機連接到電腦時，Windows PowerShell 便會自動將代表新磁碟機的 PSDrive 新增到檔案系統。</span><span class="sxs-lookup"><span data-stu-id="ad09a-118">Also, beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, Windows PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="ad09a-119">您不需要重新啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ad09a-119">You do not need to restart Windows PowerShell.</span></span> <span data-ttu-id="ad09a-120">同樣地，當外接式磁碟機已從電腦中斷連接時，Windows PowerShell 也會自動刪除代表已移除之磁碟機的 PSDrive 。</span><span class="sxs-lookup"><span data-stu-id="ad09a-120">Similarly, when an external drive is disconnected from the computer, Windows PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="ad09a-121">範例</span><span class="sxs-lookup"><span data-stu-id="ad09a-121">EXAMPLES</span></span>

### <span data-ttu-id="ad09a-122">範例1：取得目前會話中的磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="ad09a-122">Example 1: Get drives in the current session</span></span>

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

<span data-ttu-id="ad09a-123">這個命令會取得目前工作階段中的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-123">This command gets the drives in the current session.</span></span>

<span data-ttu-id="ad09a-124">輸出顯示硬碟 (C： ) 、CD-ROM 光碟機 (D： ) ，以及 Windows PowerShell 提供者所公開的磁片磁碟機 (Alias：、Cert：、Env：、Function：、HKCU：、HKLM：和 Variable： ) 。</span><span class="sxs-lookup"><span data-stu-id="ad09a-124">The output shows the hard drive (C:), CD-ROM drive (D:), and the drives exposed by the Windows PowerShell providers (Alias:, Cert:, Env:, Function:, HKCU:, HKLM:, and Variable:).</span></span>

### <span data-ttu-id="ad09a-125">範例2：取得電腦上的磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="ad09a-125">Example 2: Get a drive on the computer</span></span>

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

<span data-ttu-id="ad09a-126">這個命令會取得電腦上的 D: 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-126">This command gets the D: drive on the computer.</span></span> <span data-ttu-id="ad09a-127">請注意，命令中的磁碟機代號後面不接冒號。</span><span class="sxs-lookup"><span data-stu-id="ad09a-127">Note that the drive letter in the command is not followed by a colon.</span></span>

### <span data-ttu-id="ad09a-128">範例3：取得 Windows PowerShell 檔案系統提供者所支援的所有磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="ad09a-128">Example 3: Get all the drives that are supported by the Windows PowerShell file system provider</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

<span data-ttu-id="ad09a-129">這個命令會取得 Windows PowerShell FileSystem 提供者所支援的全部磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-129">This command gets all of the drives that are supported by the Windows PowerShell FileSystem provider.</span></span> <span data-ttu-id="ad09a-130">這包括固定式磁碟機、邏輯磁碟分割、連線的網路磁碟機，以及您使用 New-PSDrive Cmdlet 建立的暫時性磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-130">This includes fixed drives, logical partitions, mapped network drives, and temporary drives that you create by using the New-PSDrive cmdlet.</span></span>

### <span data-ttu-id="ad09a-131">範例4：檢查磁片磁碟機是否使用 Windows PowerShell 磁片磁碟機名稱</span><span class="sxs-lookup"><span data-stu-id="ad09a-131">Example 4: Check to see if a drive is in use as a Windows PowerShell drive name</span></span>

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

<span data-ttu-id="ad09a-132">這個命令會檢查 X 磁碟機是否已被用來做為 Windows PowerShell 磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="ad09a-132">This command checks to see whether the X drive is already in use as a Windows PowerShell drive name.</span></span>
<span data-ttu-id="ad09a-133">如果不是，此命令會使用指令程式 `New-PSDrive` 來建立與 HKLM： \ SOFTWARE 登錄機碼對應的暫存磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-133">If it is not, the command uses the `New-PSDrive` cmdlet to create a temporary drive that is mapped to the HKLM:\SOFTWARE registry key.</span></span>

### <span data-ttu-id="ad09a-134">範例5：比較檔案類型的系統磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="ad09a-134">Example 5: Compare the types of files system drives</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

<span data-ttu-id="ad09a-135">此範例會將顯示的檔案系統磁片磁碟機類型， `Get-PSDrive` 與使用其他方法顯示的檔案系統磁片磁碟機類型進行比較。</span><span class="sxs-lookup"><span data-stu-id="ad09a-135">This example compares the types of file system drives that are displayed by `Get-PSDrive` to those displayed by using other methods.</span></span> <span data-ttu-id="ad09a-136">此範例示範在 Windows PowerShell 中顯示磁片磁碟機的不同方式，並顯示使用 New-PSDrive Cmdlet 所建立的會話特定磁片磁碟機只能在 Windows PowerShell 中存取。</span><span class="sxs-lookup"><span data-stu-id="ad09a-136">This example demonstrates different ways to display drives in Windows PowerShell, and it shows that session-specific drives created by using the New-PSDrive cmdlet are accessible only in Windows PowerShell.</span></span>

<span data-ttu-id="ad09a-137">第一個命令會使用 `Get-PSDrive` 來取得會話中的所有檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-137">The first command uses `Get-PSDrive` to get all of the file system drives in the session.</span></span> <span data-ttu-id="ad09a-138">這包括固定磁片磁碟機 (C：和 D： ) 、使用的 **保存** 參數所建立的對應網路磁碟機 (G： ) `New-PSDrive` ，以及使用 `New-PSDrive` 不含 **保存** 參數的來建立的 PowerShell 磁片磁碟機 (T： ) 。</span><span class="sxs-lookup"><span data-stu-id="ad09a-138">This includes the fixed drives (C: and D:), a mapped network drive (G:) that was created by using the **Persist** parameter of `New-PSDrive`, and a PowerShell drive (T:) that was created by using `New-PSDrive` without the **Persist** parameter.</span></span>

<span data-ttu-id="ad09a-139">**Net use** 命令會顯示 Windows 連線的網路磁碟機機，在此情況下，它只會顯示 G 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-139">The **net use** command displays Windows mapped network drives, in this case it displays only the G drive.</span></span> <span data-ttu-id="ad09a-140">它不會顯示所建立的 X：磁片磁碟機 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="ad09a-140">It does not display the X: drive that was created by `New-PSDrive`.</span></span> <span data-ttu-id="ad09a-141">它會顯示 G：磁片磁碟機也會對應到 \\ \\ 音樂 \\ GratefulDead。</span><span class="sxs-lookup"><span data-stu-id="ad09a-141">It shows that the G: drive is also mapped to \\\\Music\\GratefulDead.</span></span>

<span data-ttu-id="ad09a-142">第三個命令使用 Microsoft .NET Framework **System.IO.DriveInfo** 類別的 **GetDrives** 方法。</span><span class="sxs-lookup"><span data-stu-id="ad09a-142">The third command uses the **GetDrives** method of the Microsoft .NET Framework **System.IO.DriveInfo** class.</span></span> <span data-ttu-id="ad09a-143">此命令會取得 Windows 檔案系統磁片磁碟機（包括磁片磁碟機 G：），但不會取得所建立的磁片磁碟機 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="ad09a-143">This command gets the Windows file system drives, including drive G:, but it does not get the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="ad09a-144">第四個命令會使用 `Get-CimInstance` Cmdlet 來取得 **Win32_LogicalDisk** 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="ad09a-144">The fourth command uses the `Get-CimInstance` cmdlet to get the instances of the **Win32_LogicalDisk** class.</span></span> <span data-ttu-id="ad09a-145">它會傳回：、C：、D：、E：和 G：磁片磁碟機，但不會傳回所建立的磁片磁碟機 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="ad09a-145">It returns the A:, C:, D:, E:, and G: drives, but not the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="ad09a-146">最後一個命令會使用 `Get-CimInstance` Cmdlet 來顯示 **Win32_NetworkConnection** 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="ad09a-146">The last command uses the `Get-CimInstance` cmdlet to display the instances of the **Win32_NetworkConnection** class.</span></span> <span data-ttu-id="ad09a-147">就像 **net use** 一樣，它只會傳回所建立的持續性 G：磁片磁碟機 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="ad09a-147">Like **net use** , it returns only the persistent G: drive created by `New-PSDrive`.</span></span>

## <span data-ttu-id="ad09a-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ad09a-148">PARAMETERS</span></span>

### <span data-ttu-id="ad09a-149">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="ad09a-149">-LiteralName</span></span>

<span data-ttu-id="ad09a-150">指定磁碟機的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad09a-150">Specifies the name of the drive.</span></span>

<span data-ttu-id="ad09a-151">**LiteralName** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="ad09a-151">The value of **LiteralName** is used exactly as it is typed.</span></span> <span data-ttu-id="ad09a-152">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ad09a-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ad09a-153">如果名稱包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="ad09a-153">If the name includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ad09a-154">單引號告知 Windows PowerShell 不要將任何字元視為逸出序列。</span><span class="sxs-lookup"><span data-stu-id="ad09a-154">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ad09a-155">-Name</span><span class="sxs-lookup"><span data-stu-id="ad09a-155">-Name</span></span>

<span data-ttu-id="ad09a-156">以字串陣列指定此 Cmdlet 在作業中取得的磁片磁碟機名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="ad09a-156">Specifies, as a string array, the name or name of drives that this cmdlet gets in the operation.</span></span>
<span data-ttu-id="ad09a-157">請輸入不含冒號 (:) 的磁碟機名稱或代號。</span><span class="sxs-lookup"><span data-stu-id="ad09a-157">Type the drive name or letter without a colon (:).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ad09a-158">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="ad09a-158">-PSProvider</span></span>

<span data-ttu-id="ad09a-159">將 Windows PowerShell 提供者指定為字串陣列。</span><span class="sxs-lookup"><span data-stu-id="ad09a-159">Specifies, as a string array, the Windows PowerShell provider.</span></span> <span data-ttu-id="ad09a-160">此 Cmdlet 只會取得這個提供者所支援的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-160">This cmdlet gets only the drives supported by this provider.</span></span> <span data-ttu-id="ad09a-161">請輸入提供者的名稱，例如 FileSystem、Registry 或 Certificate。</span><span class="sxs-lookup"><span data-stu-id="ad09a-161">Type the name of a provider, such as FileSystem, Registry, or Certificate.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ad09a-162">-Scope</span><span class="sxs-lookup"><span data-stu-id="ad09a-162">-Scope</span></span>

<span data-ttu-id="ad09a-163">指定此 Cmdlet 取得磁片磁碟機的範圍。</span><span class="sxs-lookup"><span data-stu-id="ad09a-163">Specifies the scope in which this cmdlet gets the drives.</span></span>

<span data-ttu-id="ad09a-164">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="ad09a-164">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ad09a-165">全球</span><span class="sxs-lookup"><span data-stu-id="ad09a-165">Global</span></span>
- <span data-ttu-id="ad09a-166">本機</span><span class="sxs-lookup"><span data-stu-id="ad09a-166">Local</span></span>
- <span data-ttu-id="ad09a-167">指令碼</span><span class="sxs-lookup"><span data-stu-id="ad09a-167">Script</span></span>
- <span data-ttu-id="ad09a-168">相對於目前範圍的數位 (0 至範圍數目，0為目前範圍，1為其父) 。</span><span class="sxs-lookup"><span data-stu-id="ad09a-168">a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span> <span data-ttu-id="ad09a-169">"Local" 為預設值。</span><span class="sxs-lookup"><span data-stu-id="ad09a-169">"Local" is the default.</span></span>

<span data-ttu-id="ad09a-170">如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="ad09a-170">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ad09a-171">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="ad09a-171">-UseTransaction</span></span>

<span data-ttu-id="ad09a-172">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="ad09a-172">Includes the command in the active transaction.</span></span> <span data-ttu-id="ad09a-173">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="ad09a-173">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="ad09a-174">如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="ad09a-174">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad09a-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ad09a-175">CommonParameters</span></span>

<span data-ttu-id="ad09a-176">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ad09a-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ad09a-177">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ad09a-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ad09a-178">輸入</span><span class="sxs-lookup"><span data-stu-id="ad09a-178">INPUTS</span></span>

### <span data-ttu-id="ad09a-179">無</span><span class="sxs-lookup"><span data-stu-id="ad09a-179">None</span></span>

<span data-ttu-id="ad09a-180">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad09a-180">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="ad09a-181">輸出</span><span class="sxs-lookup"><span data-stu-id="ad09a-181">OUTPUTS</span></span>

### <span data-ttu-id="ad09a-182">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="ad09a-182">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="ad09a-183">此 Cmdlet 會傳回代表會話中磁片磁碟機的物件。</span><span class="sxs-lookup"><span data-stu-id="ad09a-183">This cmdlet returns objects that represent the drives in the session.</span></span>

## <span data-ttu-id="ad09a-184">注意</span><span class="sxs-lookup"><span data-stu-id="ad09a-184">NOTES</span></span>

* <span data-ttu-id="ad09a-185">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="ad09a-185">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ad09a-186">若要列出會話中可用的提供者，請使用 `Get-PSProvider` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad09a-186">To list the providers available in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="ad09a-187">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="ad09a-187">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
* <span data-ttu-id="ad09a-188">使用 New-PSDrive Cmdlet 的 **Persist** 參數來建立的連線網路磁碟機是使用者帳戶特定的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="ad09a-188">Mapped network drives that are created by using the **Persist** parameter of the New-PSDrive cmdlet are specific to a user account.</span></span> <span data-ttu-id="ad09a-189">您在使用 [以系統管理員身分執行] 選項啟動的會話中建立的對應網路磁碟機機，或使用其他使用者的認證來啟動的會話，不會顯示在不含明確認證或使用目前使用者的認證啟動的會話中。</span><span class="sxs-lookup"><span data-stu-id="ad09a-189">Mapped network drives that you create in sessions that are started with the Run as administrator option or with the credentials of another user are not visible in sessions that are started without explicit credentials or with the credentials of the current user.</span></span>

## <span data-ttu-id="ad09a-190">相關連結</span><span class="sxs-lookup"><span data-stu-id="ad09a-190">RELATED LINKS</span></span>

[<span data-ttu-id="ad09a-191">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ad09a-191">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="ad09a-192">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="ad09a-192">Remove-PSDrive</span></span>](Remove-PSDrive.md)

[<span data-ttu-id="ad09a-193">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="ad09a-193">Get-PSProvider</span></span>](Get-PSProvider.md)
