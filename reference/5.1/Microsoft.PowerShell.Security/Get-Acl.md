---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: 6b862ad6bada3035551d35d592183db5805b232f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203427"
---
# <span data-ttu-id="eb2d2-103">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="eb2d2-103">Get-Acl</span></span>

## <span data-ttu-id="eb2d2-104">概要</span><span class="sxs-lookup"><span data-stu-id="eb2d2-104">SYNOPSIS</span></span>
<span data-ttu-id="eb2d2-105">取得資源 (例如檔案或登錄機碼) 的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-105">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="eb2d2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eb2d2-106">SYNTAX</span></span>

### <span data-ttu-id="eb2d2-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="eb2d2-107">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="eb2d2-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="eb2d2-108">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="eb2d2-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="eb2d2-109">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="eb2d2-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="eb2d2-110">DESCRIPTION</span></span>

<span data-ttu-id="eb2d2-111">`Get-Acl`Cmdlet 會取得代表檔案或資源安全描述項的物件。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-111">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="eb2d2-112">安全性描述元包含資源的存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-112">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="eb2d2-113">ACL 會指定使用者和使用者群組存取資源所需的權限。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-113">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="eb2d2-114">從 Windows PowerShell 3.0 開始，您可以使用的 **InputObject** 參數 `Get-Acl` 來取得沒有路徑之物件的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-114">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="eb2d2-115">範例</span><span class="sxs-lookup"><span data-stu-id="eb2d2-115">EXAMPLES</span></span>

### <span data-ttu-id="eb2d2-116">範例 1-取得資料夾的 ACL</span><span class="sxs-lookup"><span data-stu-id="eb2d2-116">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="eb2d2-117">這個範例會取得目錄的安全描述項 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-117">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="eb2d2-118">範例 2-使用萬用字元取得資料夾的 ACL</span><span class="sxs-lookup"><span data-stu-id="eb2d2-118">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="eb2d2-119">此範例會取得名稱開頭為之目錄中所有檔案的 PowerShell 路徑和 SDDL `.log` `C:\Windows` `s` 。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-119">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="eb2d2-120">此命令會使用 `Get-Acl` Cmdlet 取得代表每個記錄檔之安全描述項的物件。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-120">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="eb2d2-121">它會使用管線運算子 (`|`) 將結果傳送至 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-121">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="eb2d2-122">命令使用的 **Property** 參數 `Format-List` ，只顯示每個安全描述項物件的 **PsPath** 和 **SDDL** 屬性。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-122">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="eb2d2-123">清單通常會在 PowerShell 中使用，因為資料表中的長值會被截斷。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-123">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="eb2d2-124">**SDDL** 值對系統管理員而言非常有用，因為它們是簡單的文字字串，其中包含安全性描述元中的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-124">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="eb2d2-125">因此，可輕鬆地傳遞和儲存這些值，並在需要時加以剖析。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-125">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="eb2d2-126">範例 3-取得 ACL 的 Audit 專案計數</span><span class="sxs-lookup"><span data-stu-id="eb2d2-126">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="eb2d2-127">這個範例會取得 `.log` 名稱開頭為之目錄中檔案的安全描述項 `C:\Windows` `s` 。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-127">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="eb2d2-128">它使用 **Audit** 參數，取得安全性描述元中 SACL 的稽核記錄。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-128">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="eb2d2-129">然後，它會使用 `ForEach-Object` Cmdlet 來計算與每個檔案相關聯的 audit 記錄數目。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-129">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="eb2d2-130">結果是一個數字清單，代表每個記錄檔的稽核記錄數目。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-130">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="eb2d2-131">範例 4-取得登錄機碼的 ACL</span><span class="sxs-lookup"><span data-stu-id="eb2d2-131">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="eb2d2-132">這個範例會使用 `Get-Acl` Cmdlet 來取得 (登錄) 的控制項子機碼的安全描述項 `HKLM:\SYSTEM\CurrentControlSet\Control` 。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-132">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="eb2d2-133">**Path** 參數會指定 Control 子機碼。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-133">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="eb2d2-134">管線運算子 (`|`) 會將取得的安全描述項傳遞 `Get-Acl` 至 `Format-List` 命令，這會將安全描述項的屬性格式化為清單，使其易於讀取。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-134">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="eb2d2-135">範例 5-使用 **InputObject** 取得 ACL</span><span class="sxs-lookup"><span data-stu-id="eb2d2-135">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="eb2d2-136">此範例使用的 **InputObject** 參數 `Get-Acl` 來取得儲存子系統物件的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-136">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="eb2d2-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="eb2d2-137">PARAMETERS</span></span>

### <span data-ttu-id="eb2d2-138">-Audit</span><span class="sxs-lookup"><span data-stu-id="eb2d2-138">-Audit</span></span>

<span data-ttu-id="eb2d2-139">從系統存取控制清單 (SACL) 取得安全性描述元的稽核資料。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-139">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eb2d2-140">-Exclude</span><span class="sxs-lookup"><span data-stu-id="eb2d2-140">-Exclude</span></span>

<span data-ttu-id="eb2d2-141">省略指定的項目。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-141">Omits the specified items.</span></span> <span data-ttu-id="eb2d2-142">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-142">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="eb2d2-143">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-143">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="eb2d2-144">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-144">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="eb2d2-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="eb2d2-145">-Filter</span></span>

<span data-ttu-id="eb2d2-146">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-146">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="eb2d2-147">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="eb2d2-148">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-148">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="eb2d2-149">篩選比其他參數更有效率，因為提供者會在取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-149">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="eb2d2-150">-Include</span><span class="sxs-lookup"><span data-stu-id="eb2d2-150">-Include</span></span>

<span data-ttu-id="eb2d2-151">只取得指定的項目。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-151">Gets only the specified items.</span></span> <span data-ttu-id="eb2d2-152">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-152">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="eb2d2-153">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-153">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="eb2d2-154">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-154">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="eb2d2-155">-Path</span><span class="sxs-lookup"><span data-stu-id="eb2d2-155">-Path</span></span>

<span data-ttu-id="eb2d2-156">指定資源的路徑。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-156">Specifies the path to a resource.</span></span> <span data-ttu-id="eb2d2-157">`Get-Acl` 取得路徑所指示之資源的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-157">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="eb2d2-158">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-158">Wildcards are permitted.</span></span> <span data-ttu-id="eb2d2-159">如果您省略 **Path** 參數，會 `Get-Acl` 取得目前目錄的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-159">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="eb2d2-160">參數名稱 ("Path") 為選擇性。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-160">The parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="eb2d2-161">-AllCentralAccessPolicies</span><span class="sxs-lookup"><span data-stu-id="eb2d2-161">-AllCentralAccessPolicies</span></span>

<span data-ttu-id="eb2d2-162">取得電腦上啟用的所有集中存取原則的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-162">Gets information about all central access policies that are enabled on the computer.</span></span>

<span data-ttu-id="eb2d2-163">從 Windows Server 2012 開始，系統管理員可以使用 Active Directory 和群組原則為使用者和群組設定集中存取原則。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-163">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="eb2d2-164">如需詳細資訊，請參閱 [動態存取控制：案例總覽](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-164">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="eb2d2-165">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-165">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="eb2d2-166">-InputObject</span><span class="sxs-lookup"><span data-stu-id="eb2d2-166">-InputObject</span></span>

<span data-ttu-id="eb2d2-167">取得指定物件的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-167">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="eb2d2-168">輸入包含物件的變數，或輸入可取得物件的命令。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-168">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="eb2d2-169">您無法使用管線將路徑以外的物件傳送至 `Get-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-169">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="eb2d2-170">請改為在命令中明確地使用 **InputObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-170">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="eb2d2-171">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-171">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eb2d2-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="eb2d2-172">-LiteralPath</span></span>

<span data-ttu-id="eb2d2-173">指定資源的路徑。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-173">Specifies the path to a resource.</span></span> <span data-ttu-id="eb2d2-174">與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-174">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="eb2d2-175">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="eb2d2-176">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="eb2d2-177">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="eb2d2-178">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-178">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="eb2d2-179">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="eb2d2-179">-UseTransaction</span></span>

<span data-ttu-id="eb2d2-180">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-180">Includes the command in the active transaction.</span></span>
<span data-ttu-id="eb2d2-181">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-181">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="eb2d2-182">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-182">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="eb2d2-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eb2d2-183">CommonParameters</span></span>

<span data-ttu-id="eb2d2-184">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eb2d2-185">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eb2d2-186">輸入</span><span class="sxs-lookup"><span data-stu-id="eb2d2-186">INPUTS</span></span>

### <span data-ttu-id="eb2d2-187">System.String</span><span class="sxs-lookup"><span data-stu-id="eb2d2-187">System.String</span></span>

<span data-ttu-id="eb2d2-188">您可以使用管線將包含路徑的字串傳送至 `Get-Acl` 。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-188">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="eb2d2-189">輸出</span><span class="sxs-lookup"><span data-stu-id="eb2d2-189">OUTPUTS</span></span>

### <span data-ttu-id="eb2d2-190">AccessControl. System.security.accesscontrol.filesecurity，AccessControl. System.security.accesscontrol.directorysecurity，AccessControl. RegistrySecurity.。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-190">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="eb2d2-191">`Get-Acl` 傳回物件，代表它取得的 Acl。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-191">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="eb2d2-192">物件類型取決於 ACL 類型。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-192">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="eb2d2-193">注意</span><span class="sxs-lookup"><span data-stu-id="eb2d2-193">NOTES</span></span>

<span data-ttu-id="eb2d2-194">依預設，會 `Get-Acl` 顯示資源 (的 PowerShell 路徑 `<provider>::<resource-path>`) 、資源的擁有者，以及「存取」，這是在資源的任意存取控制清單中) 存取控制專案的清單 (陣列 (DACL) 。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-194">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="eb2d2-195">DACL 清單是由資源擁有者所控制。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-195">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="eb2d2-196">當您將結果格式化為清單時， `Get-Acl | Format-List` 除了路徑、擁有者及存取清單之外， () ，PowerShell 還會顯示下列屬性和屬性值：</span><span class="sxs-lookup"><span data-stu-id="eb2d2-196">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="eb2d2-197">**Group** ：擁有者的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-197">**Group** : The security group of the owner.</span></span>
- <span data-ttu-id="eb2d2-198">**Audit** ：系統存取控制清單 (SACL) 中的項目清單 (陣列)。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-198">**Audit** :  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="eb2d2-199">SACL 會指定 Windows 為其產生稽核記錄的存取嘗試類型。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-199">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="eb2d2-200">**Sddl** ：在單一文字字串中，以 Security Descriptor Definition Language 格式顯示的資源安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-200">**Sddl** : The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="eb2d2-201">PowerShell 會使用安全描述項的 **GetSddlForm** 方法來取得此資料。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-201">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="eb2d2-202">因為 `Get-Acl` 檔案系統和登錄提供者支援，所以您可以使用 `Get-Acl` 來查看檔案系統物件（例如檔案和目錄）與登錄物件（例如登錄機碼和專案）的 ACL。</span><span class="sxs-lookup"><span data-stu-id="eb2d2-202">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="eb2d2-203">相關連結</span><span class="sxs-lookup"><span data-stu-id="eb2d2-203">RELATED LINKS</span></span>

[<span data-ttu-id="eb2d2-204">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="eb2d2-204">Set-Acl</span></span>](Set-Acl.md)
