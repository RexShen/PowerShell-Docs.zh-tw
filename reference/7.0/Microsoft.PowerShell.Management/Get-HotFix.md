---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 277dd2678b54c9e708d09f6ca27d82ab9afd4c1c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347613"
---
# <span data-ttu-id="fe8fb-103">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="fe8fb-103">Get-HotFix</span></span>

## <span data-ttu-id="fe8fb-104">概要</span><span class="sxs-lookup"><span data-stu-id="fe8fb-104">SYNOPSIS</span></span>
<span data-ttu-id="fe8fb-105">取得安裝在本機或遠端電腦上的修補程式。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-105">Gets the hotfixes that are installed on local or remote computers.</span></span>

## <span data-ttu-id="fe8fb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fe8fb-106">SYNTAX</span></span>

### <span data-ttu-id="fe8fb-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="fe8fb-107">Default (Default)</span></span>

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### <span data-ttu-id="fe8fb-108">說明</span><span class="sxs-lookup"><span data-stu-id="fe8fb-108">Description</span></span>

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## <span data-ttu-id="fe8fb-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fe8fb-109">DESCRIPTION</span></span>

<span data-ttu-id="fe8fb-110">此 `Get-Hotfix` Cmdlet 會取得本機電腦或指定的遠端電腦上安裝的修補程式或更新。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-110">The `Get-Hotfix` cmdlet gets hotfixes, or updates, that are installed on the local computer or specified remote computers.</span></span> <span data-ttu-id="fe8fb-111">您可以 Windows Update、Microsoft Update、Windows Server Update Services 或手動安裝更新來安裝更新。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-111">The updates can be installed by Windows Update, Microsoft Update, Windows Server Update Services, or manually installed.</span></span>

## <span data-ttu-id="fe8fb-112">範例</span><span class="sxs-lookup"><span data-stu-id="fe8fb-112">EXAMPLES</span></span>

### <span data-ttu-id="fe8fb-113">範例1：取得本機電腦上的所有修補程式</span><span class="sxs-lookup"><span data-stu-id="fe8fb-113">Example 1: Get all hotfixes on the local computer</span></span>

<span data-ttu-id="fe8fb-114">`Get-Hotfix`Cmdlet 會取得本機電腦上安裝的所有修補程式。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-114">The `Get-Hotfix` cmdlet gets all hotfixes installed on the local computer.</span></span>

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### <span data-ttu-id="fe8fb-115">範例2：從以字串篩選的多部電腦取得修補程式</span><span class="sxs-lookup"><span data-stu-id="fe8fb-115">Example 2: Get hotfixes from multiple computers filtered by a string</span></span>

<span data-ttu-id="fe8fb-116">此 `Get-Hotfix` 命令會使用參數來取得在遠端電腦上安裝的修補程式。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-116">The `Get-Hotfix` command uses parameters to get hotfixes installed on remote computers.</span></span> <span data-ttu-id="fe8fb-117">結果會依指定的描述字串進行篩選。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-117">The results are filtered by a specified description string.</span></span>

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

<span data-ttu-id="fe8fb-118">`Get-Hotfix`篩選具有 **Description** 參數的輸出，以及包含星號 **Security** () 萬用字元的字串安全性 `*` 。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-118">`Get-Hotfix` filters the output with the **Description** parameter and the string **Security** that includes the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="fe8fb-119">**ComputerName** 參數包含以逗號分隔的遠端電腦名稱稱字串。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-119">The **ComputerName** parameter includes a comma-separated string of remote computer names.</span></span> <span data-ttu-id="fe8fb-120">**Credential** 參數指定具有存取遠端電腦和執行命令之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-120">The **Credential** parameter specifies a user account that has permission to access the remote computers and run commands.</span></span>

### <span data-ttu-id="fe8fb-121">範例3：確認是否已安裝更新，並將電腦名稱稱寫入檔案</span><span class="sxs-lookup"><span data-stu-id="fe8fb-121">Example 3: Verify if an update is installed and write computer names to a file</span></span>

<span data-ttu-id="fe8fb-122">此範例中的命令會確認是否已安裝特定的更新。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-122">The commands in this example verify whether a particular update installed.</span></span> <span data-ttu-id="fe8fb-123">如果未安裝此更新，則會將電腦名稱稱寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-123">If the update isn't installed, the computer name is written to a text file.</span></span>

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

<span data-ttu-id="fe8fb-124">`$A`變數包含從文字檔取得的電腦名稱稱 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-124">The `$A` variable contains computer names that were obtained by `Get-Content` from a text file.</span></span> <span data-ttu-id="fe8fb-125">中的物件 `$A` 會向下傳送到管線 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-125">The objects in `$A` are sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="fe8fb-126">`if`語句會使用 `Get-Hotfix` Cmdlet 搭配 **Id** 參數和每個電腦名稱稱的特定識別碼。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-126">An `if` statement uses the `Get-Hotfix` cmdlet with the **Id** parameter and a specific Id number for each computer name.</span></span> <span data-ttu-id="fe8fb-127">如果電腦未安裝指定的修正程式識別碼，則 Cmdlet 會將 `Add-Content` 電腦名稱稱寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-127">If a computer doesn't have the specified hotfix Id installed, the `Add-Content` cmdlet writes the computer name to a file.</span></span>

### <span data-ttu-id="fe8fb-128">範例4：在本機電腦上取得最新的修正程式</span><span class="sxs-lookup"><span data-stu-id="fe8fb-128">Example 4: Get the most recent hotfix on the local computer</span></span>

<span data-ttu-id="fe8fb-129">此範例會取得電腦上安裝的最新的修正程式。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-129">This example gets the most recent hotfix installed on a computer.</span></span>

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

<span data-ttu-id="fe8fb-130">`Get-Hotfix` 將物件沿著管線向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-130">`Get-Hotfix` sends the objects down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="fe8fb-131">`Sort-Object` 依遞增順序排序物件，並使用 **Property** 參數來評估每個 **InstalledOn** 日期。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-131">`Sort-Object` sorts objects by ascending order and uses the **Property** parameter to evaluate each **InstalledOn** date.</span></span> <span data-ttu-id="fe8fb-132">陣列標記法會 `[-1]` 選取最近安裝的修正程式。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-132">The array notation `[-1]` selects the most recent installed hotfix.</span></span>

## <span data-ttu-id="fe8fb-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fe8fb-133">PARAMETERS</span></span>

### <span data-ttu-id="fe8fb-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="fe8fb-134">-ComputerName</span></span>

<span data-ttu-id="fe8fb-135">指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-135">Specifies a remote computer.</span></span> <span data-ttu-id="fe8fb-136">輸入 NetBIOS 名稱、網際網路通訊協定 (IP) 位址，或遠端電腦 (FQDN) 的完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-136">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>

<span data-ttu-id="fe8fb-137">如果未指定 **ComputerName** 參數，會 `Get-Hotfix` 在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-137">When the **ComputerName** parameter isn't specified, `Get-Hotfix` runs on the local computer.</span></span>

<span data-ttu-id="fe8fb-138">**ComputerName** 參數不依賴 Windows PowerShell 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-138">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="fe8fb-139">如果您的電腦未設定為執行遠端命令，請使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-139">If your computer isn't configured to run remote commands, use the **ComputerName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fe8fb-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="fe8fb-140">-Credential</span></span>

<span data-ttu-id="fe8fb-141">指定擁有存取電腦和執行命令之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-141">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="fe8fb-142">預設值為目前的使用者</span><span class="sxs-lookup"><span data-stu-id="fe8fb-142">The default is the current user</span></span>

<span data-ttu-id="fe8fb-143">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-143">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="fe8fb-144">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-144">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="fe8fb-145">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-145">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="fe8fb-146">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-146">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe8fb-147">-Description</span><span class="sxs-lookup"><span data-stu-id="fe8fb-147">-Description</span></span>

<span data-ttu-id="fe8fb-148">`Get-HotFix` 使用 **Description** 參數指定修正程式類型。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-148">`Get-HotFix` uses the **Description** parameter to specify hotfix types.</span></span> <span data-ttu-id="fe8fb-149">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-149">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="fe8fb-150">-Id</span><span class="sxs-lookup"><span data-stu-id="fe8fb-150">-Id</span></span>

<span data-ttu-id="fe8fb-151">篩選 `Get-HotFix` 特定修正程式識別碼的結果。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-151">Filters the `Get-HotFix` results for specific hotfix Ids.</span></span> <span data-ttu-id="fe8fb-152">不接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-152">Wildcards aren't accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe8fb-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fe8fb-153">CommonParameters</span></span>

<span data-ttu-id="fe8fb-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fe8fb-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fe8fb-156">輸入</span><span class="sxs-lookup"><span data-stu-id="fe8fb-156">INPUTS</span></span>

### <span data-ttu-id="fe8fb-157">字串</span><span class="sxs-lookup"><span data-stu-id="fe8fb-157">String</span></span>

<span data-ttu-id="fe8fb-158">您可以透過管道將一或多個電腦名稱稱傳送至 Get-修正程式。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-158">You can pipe one or more computer names to Get-HotFix.</span></span>

## <span data-ttu-id="fe8fb-159">輸出</span><span class="sxs-lookup"><span data-stu-id="fe8fb-159">OUTPUTS</span></span>

### <span data-ttu-id="fe8fb-160">System.management.managementobject # root\CIMV2\ Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="fe8fb-160">System.Management.ManagementObject#root\CIMV2\Win32_QuickFixEngineering</span></span>

<span data-ttu-id="fe8fb-161">`Get-HotFix` 傳回物件，代表電腦上的修正程式。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-161">`Get-HotFix` returns objects that represent the hotfixes on the computer.</span></span>

## <span data-ttu-id="fe8fb-162">注意</span><span class="sxs-lookup"><span data-stu-id="fe8fb-162">NOTES</span></span>

<span data-ttu-id="fe8fb-163">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-163">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="fe8fb-164">**Win32_QuickFixEngineering** [WMI 類別](/windows/desktop/WmiSdk/retrieving-a-class)代表一小段全系統更新，通常稱為快速修正工程 (QFE) update，套用至目前的作業系統。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-164">The **Win32_QuickFixEngineering** [WMI class](/windows/desktop/WmiSdk/retrieving-a-class) represents a small system-wide update, commonly referred to as a quick-fix engineering (QFE) update, applied to the current operating system.</span></span> <span data-ttu-id="fe8fb-165">這個類別只會傳回以元件為基礎的服務 (CBS) 所提供的更新。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-165">This class returns only the updates supplied by Component Based Servicing (CBS).</span></span> <span data-ttu-id="fe8fb-166">這些更新不會列在登錄中。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-166">These updates are not listed in the registry.</span></span> <span data-ttu-id="fe8fb-167">**Win32_QuickFixEngineering** 不會傳回 Microsoft WINDOWS INSTALLER (MSI) 或 [Windows Update](https://update.microsoft.com)網站所提供的更新。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-167">Updates supplied by Microsoft Windows Installer (MSI) or the [Windows Update](https://update.microsoft.com) site are not returned by **Win32_QuickFixEngineering**.</span></span> <span data-ttu-id="fe8fb-168">如需詳細資訊，請參閱 [Win32_QuickFixEngineering 類別](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-168">For more information, see [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span></span>

<span data-ttu-id="fe8fb-169">`Get-HotFix`不同的作業系統可能會有不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="fe8fb-169">The `Get-HotFix` output might vary on different operating systems.</span></span>

## <span data-ttu-id="fe8fb-170">相關連結</span><span class="sxs-lookup"><span data-stu-id="fe8fb-170">RELATED LINKS</span></span>

[<span data-ttu-id="fe8fb-171">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="fe8fb-171">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="fe8fb-172">Add-Content</span><span class="sxs-lookup"><span data-stu-id="fe8fb-172">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="fe8fb-173">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="fe8fb-173">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="fe8fb-174">Win32_QuickFixEngineering 類別</span><span class="sxs-lookup"><span data-stu-id="fe8fb-174">Win32_QuickFixEngineering class</span></span>](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
