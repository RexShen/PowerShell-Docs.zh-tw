---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3dca5f922f31690bb78ccc610b4ed44b7423ca47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202715"
---
# <span data-ttu-id="6bdce-103">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="6bdce-103">New-PSRoleCapabilityFile</span></span>

## <span data-ttu-id="6bdce-104">概要</span><span class="sxs-lookup"><span data-stu-id="6bdce-104">SYNOPSIS</span></span>
<span data-ttu-id="6bdce-105">建立檔案，該檔案會定義要透過會話設定公開的一組功能。</span><span class="sxs-lookup"><span data-stu-id="6bdce-105">Creates a file that defines a set of capabilities to be exposed through a session configuration.</span></span>

## <span data-ttu-id="6bdce-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6bdce-106">SYNTAX</span></span>

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="6bdce-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6bdce-107">DESCRIPTION</span></span>

<span data-ttu-id="6bdce-108">此 `New-PSRoleCapabilityFile` Cmdlet 會建立一個檔案，該檔案會定義一組可透過會話設定檔公開的使用者功能。</span><span class="sxs-lookup"><span data-stu-id="6bdce-108">The `New-PSRoleCapabilityFile` cmdlet creates a file that defines a set of user capabilities that can be exposed through session configuration files.</span></span> <span data-ttu-id="6bdce-109">這包括判斷使用者可以使用哪些 Cmdlet、函式和腳本。</span><span class="sxs-lookup"><span data-stu-id="6bdce-109">This includes determining which cmdlets, functions, and scripts are available to users.</span></span> <span data-ttu-id="6bdce-110">功能檔案是人們可讀取的文字檔，其中包含會話設定屬性和值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="6bdce-110">The capability file is a human-readable text file that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="6bdce-111">檔案的副檔名為 .psrc，且可供一個以上的會話設定使用。</span><span class="sxs-lookup"><span data-stu-id="6bdce-111">The file has a .psrc file name extension, and can be used by more than one session configuration.</span></span>

<span data-ttu-id="6bdce-112">的所有參數 `New-PSRoleCapabilityFile` 都是選擇性的，但 **Path** 參數除外，後者會指定檔案的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="6bdce-112">All the parameters of `New-PSRoleCapabilityFile` are optional except for the **Path** parameter, which specifies the file path for the file.</span></span> <span data-ttu-id="6bdce-113">如果您在執行 Cmdlet 時未包含參數，則會話設定檔中的對應索引鍵會被批註化，除非在參數描述中注明。</span><span class="sxs-lookup"><span data-stu-id="6bdce-113">If you do not include a parameter when you run the cmdlet, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span> <span data-ttu-id="6bdce-114">例如，如果您未包含 **AssembliesToLoad** 參數，則會將會話設定檔的該區段標記為批註。</span><span class="sxs-lookup"><span data-stu-id="6bdce-114">For example, if you do not include the **AssembliesToLoad** parameter then that section of the session configuration file is commented out.</span></span>

<span data-ttu-id="6bdce-115">若要在會話設定中使用角色功能檔案，請先將檔案放在有效 PowerShell 模組資料夾的 **RoleCapabilities** 子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6bdce-115">To use the role capability file in a session configuration, first place the file in a **RoleCapabilities** subfolder of a valid PowerShell module folder.</span></span> <span data-ttu-id="6bdce-116">然後，在 PowerShell 會話設定的 [ **RoleDefinitions** ] 欄位中依名稱參考檔案， (. .pssc) 檔。</span><span class="sxs-lookup"><span data-stu-id="6bdce-116">Then reference the file by name in the **RoleDefinitions** field in a PowerShell Session Configuration (.pssc) file.</span></span>

<span data-ttu-id="6bdce-117">此 Cmdlet 是在 Windows PowerShell 5.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6bdce-117">This cmdlet was introduced in Windows PowerShell 5.0.</span></span>

## <span data-ttu-id="6bdce-118">範例</span><span class="sxs-lookup"><span data-stu-id="6bdce-118">EXAMPLES</span></span>

### <span data-ttu-id="6bdce-119">範例1：建立空白角色功能檔案</span><span class="sxs-lookup"><span data-stu-id="6bdce-119">Example 1: Create a blank role capability file</span></span>

<span data-ttu-id="6bdce-120">這個範例會建立新的角色功能檔案，該檔案會使用預設 (空白的) 值。</span><span class="sxs-lookup"><span data-stu-id="6bdce-120">This example creates a new role capability file that uses the default (blank) values.</span></span> <span data-ttu-id="6bdce-121">您稍後可以在文字編輯器中編輯檔案，以變更這些設定。</span><span class="sxs-lookup"><span data-stu-id="6bdce-121">The file can later be edited in a text editor to change these configuration settings.</span></span>

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### <span data-ttu-id="6bdce-122">範例2：建立角色功能檔案，讓使用者重新開機服務和任何 VDI 電腦</span><span class="sxs-lookup"><span data-stu-id="6bdce-122">Example 2: Create a role capability file allowing users to restart services and any VDI computer</span></span>

<span data-ttu-id="6bdce-123">這個範例會建立一個範例角色功能檔案，讓使用者能夠重新開機符合特定名稱模式的服務和電腦。</span><span class="sxs-lookup"><span data-stu-id="6bdce-123">This example creates a sample role capability file that enables users to restart services and computers that match a specific name pattern.</span></span> <span data-ttu-id="6bdce-124">名稱篩選是藉由將 **ValidatePattern** 參數設定為正則運算式來定義 `VDI\d+` 。</span><span class="sxs-lookup"><span data-stu-id="6bdce-124">Name filtering is defined by setting the **ValidatePattern** parameter to the regular expression `VDI\d+`.</span></span>

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## <span data-ttu-id="6bdce-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6bdce-125">PARAMETERS</span></span>

### <span data-ttu-id="6bdce-126">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="6bdce-126">-AliasDefinitions</span></span>

<span data-ttu-id="6bdce-127">將指定的別名新增至使用角色功能檔案的會話。</span><span class="sxs-lookup"><span data-stu-id="6bdce-127">Adds the specified aliases to sessions that use the role capability file.</span></span> <span data-ttu-id="6bdce-128">輸入包含下列索引鍵的雜湊表：</span><span class="sxs-lookup"><span data-stu-id="6bdce-128">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="6bdce-129">Name：</span><span class="sxs-lookup"><span data-stu-id="6bdce-129">Name.</span></span> <span data-ttu-id="6bdce-130">別名的名稱。</span><span class="sxs-lookup"><span data-stu-id="6bdce-130">Name of the alias.</span></span> <span data-ttu-id="6bdce-131">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-131">This key is required.</span></span>
- <span data-ttu-id="6bdce-132">值。</span><span class="sxs-lookup"><span data-stu-id="6bdce-132">Value.</span></span> <span data-ttu-id="6bdce-133">別名代表的命令。</span><span class="sxs-lookup"><span data-stu-id="6bdce-133">The command that the alias represents.</span></span> <span data-ttu-id="6bdce-134">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-134">This key is required.</span></span>
- <span data-ttu-id="6bdce-135">描述</span><span class="sxs-lookup"><span data-stu-id="6bdce-135">Description.</span></span> <span data-ttu-id="6bdce-136">描述別名的文字字串。</span><span class="sxs-lookup"><span data-stu-id="6bdce-136">A text string that describes the alias.</span></span> <span data-ttu-id="6bdce-137">此為選擇性索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-137">This key is optional.</span></span>
- <span data-ttu-id="6bdce-138">選項。</span><span class="sxs-lookup"><span data-stu-id="6bdce-138">Options.</span></span> <span data-ttu-id="6bdce-139">別名選項。</span><span class="sxs-lookup"><span data-stu-id="6bdce-139">Alias options.</span></span> <span data-ttu-id="6bdce-140">此為選擇性索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-140">This key is optional.</span></span> <span data-ttu-id="6bdce-141">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="6bdce-141">The default value is None.</span></span> <span data-ttu-id="6bdce-142">此參數可接受的值為： None、ReadOnly、常數、私用或 AllScope。</span><span class="sxs-lookup"><span data-stu-id="6bdce-142">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="6bdce-143">例如：`@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span><span class="sxs-lookup"><span data-stu-id="6bdce-143">For example: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-144">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="6bdce-144">-AssembliesToLoad</span></span>

<span data-ttu-id="6bdce-145">指定要載入至使用角色功能檔案之會話的元件。</span><span class="sxs-lookup"><span data-stu-id="6bdce-145">Specifies the assemblies to load into the sessions that use the role capability file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-146">-作者</span><span class="sxs-lookup"><span data-stu-id="6bdce-146">-Author</span></span>

<span data-ttu-id="6bdce-147">指定建立角色功能檔案的使用者。</span><span class="sxs-lookup"><span data-stu-id="6bdce-147">Specifies the user that created the role capability file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-148">-公司名稱</span><span class="sxs-lookup"><span data-stu-id="6bdce-148">-CompanyName</span></span>

<span data-ttu-id="6bdce-149">識別建立角色功能檔案的公司。</span><span class="sxs-lookup"><span data-stu-id="6bdce-149">Identifies the company that created the role capability file.</span></span>
<span data-ttu-id="6bdce-150">預設值為 [未知]。</span><span class="sxs-lookup"><span data-stu-id="6bdce-150">The default value is Unknown.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-151">-著作權</span><span class="sxs-lookup"><span data-stu-id="6bdce-151">-Copyright</span></span>

<span data-ttu-id="6bdce-152">指定角色功能檔案的著作權。</span><span class="sxs-lookup"><span data-stu-id="6bdce-152">Specifies a copyright for the role capability file.</span></span> <span data-ttu-id="6bdce-153">如果您省略此參數，則會 `New-PSRoleCapabilityFile` 使用 **Author** 參數的值產生著作權語句。</span><span class="sxs-lookup"><span data-stu-id="6bdce-153">If you omit this parameter, `New-PSRoleCapabilityFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-154">-Description</span><span class="sxs-lookup"><span data-stu-id="6bdce-154">-Description</span></span>

<span data-ttu-id="6bdce-155">指定角色功能檔案的描述。</span><span class="sxs-lookup"><span data-stu-id="6bdce-155">Specifies a description for the role capability file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-156">-EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="6bdce-156">-EnvironmentVariables</span></span>

<span data-ttu-id="6bdce-157">為公開此角色功能檔案的會話指定環境變數。</span><span class="sxs-lookup"><span data-stu-id="6bdce-157">Specifies the environment variables for sessions that expose this role capability file.</span></span> <span data-ttu-id="6bdce-158">輸入雜湊表，其中索引鍵為環境變數名稱，值為環境變數值。</span><span class="sxs-lookup"><span data-stu-id="6bdce-158">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="6bdce-159">例如：`EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span><span class="sxs-lookup"><span data-stu-id="6bdce-159">For example: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-160">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="6bdce-160">-FormatsToProcess</span></span>

<span data-ttu-id="6bdce-161">指定在使用角色功能檔案的會話中執行的格式化檔案 (. .ps1xml) 。</span><span class="sxs-lookup"><span data-stu-id="6bdce-161">Specifies the formatting files (.ps1xml) that run in sessions that use the role capability file.</span></span> <span data-ttu-id="6bdce-162">此參數的值必須是格式化檔案的完整路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="6bdce-162">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-163">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="6bdce-163">-FunctionDefinitions</span></span>

<span data-ttu-id="6bdce-164">將指定的函式加入至公開角色功能的會話。</span><span class="sxs-lookup"><span data-stu-id="6bdce-164">Adds the specified functions to sessions that expose the role capability.</span></span> <span data-ttu-id="6bdce-165">輸入包含下列索引鍵的雜湊表：</span><span class="sxs-lookup"><span data-stu-id="6bdce-165">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="6bdce-166">Name：</span><span class="sxs-lookup"><span data-stu-id="6bdce-166">Name.</span></span> <span data-ttu-id="6bdce-167">函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6bdce-167">Name of the function.</span></span> <span data-ttu-id="6bdce-168">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-168">This key is required.</span></span>
- <span data-ttu-id="6bdce-169">ScriptBlock.</span><span class="sxs-lookup"><span data-stu-id="6bdce-169">ScriptBlock.</span></span> <span data-ttu-id="6bdce-170">函式主體。</span><span class="sxs-lookup"><span data-stu-id="6bdce-170">Function body.</span></span> <span data-ttu-id="6bdce-171">輸入指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="6bdce-171">Enter a script block.</span></span> <span data-ttu-id="6bdce-172">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-172">This key is required.</span></span>
- <span data-ttu-id="6bdce-173">選項。</span><span class="sxs-lookup"><span data-stu-id="6bdce-173">Options.</span></span> <span data-ttu-id="6bdce-174">函式選項。</span><span class="sxs-lookup"><span data-stu-id="6bdce-174">Function options.</span></span> <span data-ttu-id="6bdce-175">此為選擇性索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-175">This key is optional.</span></span> <span data-ttu-id="6bdce-176">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="6bdce-176">The default value is None.</span></span> <span data-ttu-id="6bdce-177">此參數可接受的值包括：無、ReadOnly、常數、私用或 AllScope。</span><span class="sxs-lookup"><span data-stu-id="6bdce-177">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="6bdce-178">例如：</span><span class="sxs-lookup"><span data-stu-id="6bdce-178">For example:</span></span>

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-179">-Guid</span><span class="sxs-lookup"><span data-stu-id="6bdce-179">-Guid</span></span>

<span data-ttu-id="6bdce-180">指定角色功能檔案的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="6bdce-180">Specifies a unique identifier for the role capability file.</span></span> <span data-ttu-id="6bdce-181">如果您省略此參數，則會產生檔案的 `New-PSRoleCapabilityFile` GUID。</span><span class="sxs-lookup"><span data-stu-id="6bdce-181">If you omit this parameter, `New-PSRoleCapabilityFile` generates a GUID for the file.</span></span> <span data-ttu-id="6bdce-182">若要在 PowerShell 中建立新的 GUID，請輸入 `[guid]::NewGuid()` 。</span><span class="sxs-lookup"><span data-stu-id="6bdce-182">To create a new GUID in PowerShell, type `[guid]::NewGuid()`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-183">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="6bdce-183">-ModulesToImport</span></span>

<span data-ttu-id="6bdce-184">指定自動匯入至使用角色功能檔案之會話的模組。</span><span class="sxs-lookup"><span data-stu-id="6bdce-184">Specifies the modules that are automatically imported into sessions that use the role capability file.</span></span> <span data-ttu-id="6bdce-185">根據預設，列出模組中的所有命令都是可見的。</span><span class="sxs-lookup"><span data-stu-id="6bdce-185">By default, all the commands in listed modules are visible.</span></span> <span data-ttu-id="6bdce-186">搭配 **VisibleCmdlets** 或 **VisibleFunctions** 使用時，可以限制指定模組中可見的命令。</span><span class="sxs-lookup"><span data-stu-id="6bdce-186">When used with **VisibleCmdlets** or **VisibleFunctions** , the commands visible from the specified modules can be restricted.</span></span>

<span data-ttu-id="6bdce-187">此參數的值中所使用的每個模組都可以用字串或雜湊表表示。</span><span class="sxs-lookup"><span data-stu-id="6bdce-187">Each module used in the value of this parameter can be represented by a string or by a hash table.</span></span> <span data-ttu-id="6bdce-188">模組字串只包含模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="6bdce-188">A module string consists only of the name of the module.</span></span> <span data-ttu-id="6bdce-189">模組雜湊表可包括 **ModuleName** 、 **ModuleVersion** 和 **GUID** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-189">A module hash table can include **ModuleName** , **ModuleVersion** , and **GUID** keys.</span></span> <span data-ttu-id="6bdce-190">只有 **ModuleName** 索引鍵是必要的。</span><span class="sxs-lookup"><span data-stu-id="6bdce-190">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="6bdce-191">例如，以下的值包含字串和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="6bdce-191">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="6bdce-192">字串或雜湊表以任何順序組成的任何組合都是有效的。</span><span class="sxs-lookup"><span data-stu-id="6bdce-192">Any combination of strings and hash tables, in any order, is valid.</span></span>

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-193">-Path</span><span class="sxs-lookup"><span data-stu-id="6bdce-193">-Path</span></span>

<span data-ttu-id="6bdce-194">指定角色功能檔案的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-194">Specifies the path and filename of the role capability file.</span></span> <span data-ttu-id="6bdce-195">檔案的副檔名必須是 `.psrc` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-195">The file must have a `.psrc` filename extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-196">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="6bdce-196">-ScriptsToProcess</span></span>

<span data-ttu-id="6bdce-197">指定要加入至使用角色功能檔案之會話的腳本。</span><span class="sxs-lookup"><span data-stu-id="6bdce-197">Specifies scripts to add to sessions that use the role capability file.</span></span> <span data-ttu-id="6bdce-198">輸入指令碼的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6bdce-198">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="6bdce-199">此參數的值必須是指令檔名的完整路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="6bdce-199">The value of this parameter must be a full or absolute path of the script file names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-200">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="6bdce-200">-TypesToProcess</span></span>

<span data-ttu-id="6bdce-201">指定要加入至使用角色功能檔案之會話的類型檔案 (. .ps1xml) 。</span><span class="sxs-lookup"><span data-stu-id="6bdce-201">Specifies type files (.ps1xml) to add to sessions that use the role capability file.</span></span> <span data-ttu-id="6bdce-202">輸入類型檔案名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-202">Enter the type filenames.</span></span> <span data-ttu-id="6bdce-203">此參數的值必須是類型檔案名的完整路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="6bdce-203">The value of this parameter must be a full or absolute path of the type filenames.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-204">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="6bdce-204">-VariableDefinitions</span></span>

<span data-ttu-id="6bdce-205">指定要加入至使用角色功能檔案之會話的變數。</span><span class="sxs-lookup"><span data-stu-id="6bdce-205">Specifies variables to add to sessions that use the role capability file.</span></span> <span data-ttu-id="6bdce-206">輸入包含下列索引鍵的雜湊表：</span><span class="sxs-lookup"><span data-stu-id="6bdce-206">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="6bdce-207">Name：</span><span class="sxs-lookup"><span data-stu-id="6bdce-207">Name.</span></span> <span data-ttu-id="6bdce-208">變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6bdce-208">Name of the variable.</span></span> <span data-ttu-id="6bdce-209">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-209">This key is required.</span></span>
- <span data-ttu-id="6bdce-210">值。</span><span class="sxs-lookup"><span data-stu-id="6bdce-210">Value.</span></span> <span data-ttu-id="6bdce-211">變數值。</span><span class="sxs-lookup"><span data-stu-id="6bdce-211">Variable value.</span></span> <span data-ttu-id="6bdce-212">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-212">This key is required.</span></span>
- <span data-ttu-id="6bdce-213">選項。</span><span class="sxs-lookup"><span data-stu-id="6bdce-213">Options.</span></span> <span data-ttu-id="6bdce-214">變數選項。</span><span class="sxs-lookup"><span data-stu-id="6bdce-214">Variable options.</span></span> <span data-ttu-id="6bdce-215">此為選擇性索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6bdce-215">This key is optional.</span></span> <span data-ttu-id="6bdce-216">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="6bdce-216">The default value is None.</span></span> <span data-ttu-id="6bdce-217">此參數可接受的值包括：無、ReadOnly、常數、私用或 AllScope。</span><span class="sxs-lookup"><span data-stu-id="6bdce-217">The acceptable values for this parameter are: are None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="6bdce-218">例如：`@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span><span class="sxs-lookup"><span data-stu-id="6bdce-218">For example: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-219">-Visiblealiase</span><span class="sxs-lookup"><span data-stu-id="6bdce-219">-VisibleAliases</span></span>

<span data-ttu-id="6bdce-220">將會話中的別名限制為此參數的值中指定的別名，以及您在 **AliasDefinition** 參數中定義的任何別名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-220">Limits the aliases in the session to those aliases specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="6bdce-221">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6bdce-221">Wildcard characters are supported.</span></span>
<span data-ttu-id="6bdce-222">根據預設，會話中會顯示所有由 PowerShell 引擎定義的別名，以及模組匯出的所有別名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-222">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="6bdce-223">例如，若要將可用的別名限制為 gm 和 gcm，請使用此語法： `VisibleAliases="gcm", "gp"`</span><span class="sxs-lookup"><span data-stu-id="6bdce-223">For example, to limit the available aliases to gm and gcm use this syntax: `VisibleAliases="gcm", "gp"`</span></span>

<span data-ttu-id="6bdce-224">當角色功能檔案中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-224">When any **Visible** parameter is included in the role capability file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="6bdce-225">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="6bdce-225">-VisibleCmdlets</span></span>

<span data-ttu-id="6bdce-226">將工作階段中的 Cmdlet 限制為此參數的值中指定的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6bdce-226">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="6bdce-227">支援萬用字元和模組限定名稱。</span><span class="sxs-lookup"><span data-stu-id="6bdce-227">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="6bdce-228">根據預設，會話中的模組會在會話中顯示所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6bdce-228">By default, all cmdlets that the modules in the session export are visible in the session.</span></span> <span data-ttu-id="6bdce-229">使用 **SessionType** 和 **ModulesToImport** 參數決定要在工作階段中匯入哪些模組和嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="6bdce-229">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="6bdce-230">如果 **ModulesToImport** 中沒有任何模組公開 Cmdlet，則會 `New-PSRoleCapabilityFile` 嘗試載入適當的模組。</span><span class="sxs-lookup"><span data-stu-id="6bdce-230">If no modules in **ModulesToImport** expose the cmdlet, `New-PSRoleCapabilityFile` tries to load the appropriate module.</span></span>

<span data-ttu-id="6bdce-231">當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-231">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6bdce-232">-了 visibleexternalcommands</span><span class="sxs-lookup"><span data-stu-id="6bdce-232">-VisibleExternalCommands</span></span>

<span data-ttu-id="6bdce-233">將會話中可執行檔外部二進位檔、腳本和命令，限制為此參數的值中指定的二進位檔、腳本和命令。</span><span class="sxs-lookup"><span data-stu-id="6bdce-233">Limits the external binaries, scripts and commands that can be executed in the session to those specified in the value of this parameter.</span></span>

<span data-ttu-id="6bdce-234">依預設，在此會話中不會顯示任何外部命令。</span><span class="sxs-lookup"><span data-stu-id="6bdce-234">By default, no external commands are visible in this session.</span></span>

<span data-ttu-id="6bdce-235">當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-235">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bdce-236">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="6bdce-236">-VisibleFunctions</span></span>

<span data-ttu-id="6bdce-237">將會話中的函式限制為此參數的值中指定的函式，以及您在 **FunctionDefinitions** 參數中定義的任何函數。</span><span class="sxs-lookup"><span data-stu-id="6bdce-237">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinitions** parameter.</span></span> <span data-ttu-id="6bdce-238">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6bdce-238">Wildcard characters are supported.</span></span>

<span data-ttu-id="6bdce-239">依預設，會話中的模組匯出的所有函式都會顯示在該會話中。</span><span class="sxs-lookup"><span data-stu-id="6bdce-239">By default, all functions exported by modules in the session are visible in that session.</span></span> <span data-ttu-id="6bdce-240">您可以使用 **SessionType** 和 **ModulesToImport** 參數來判斷要將哪些模組匯入到會話中。</span><span class="sxs-lookup"><span data-stu-id="6bdce-240">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="6bdce-241">當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-241">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6bdce-242">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="6bdce-242">-VisibleProviders</span></span>

<span data-ttu-id="6bdce-243">將會話中的 PowerShell 提供者限制為此參數的值中指定的提供者。</span><span class="sxs-lookup"><span data-stu-id="6bdce-243">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="6bdce-244">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6bdce-244">Wildcard characters are supported.</span></span>

<span data-ttu-id="6bdce-245">依預設，會話中的模組匯出的所有提供者都會顯示在會話中。</span><span class="sxs-lookup"><span data-stu-id="6bdce-245">By default, all providers exported by a module in the session are visible in the session.</span></span> <span data-ttu-id="6bdce-246">您可以使用 **SessionType** 和 **ModulesToImport** 參數來判斷要將哪些模組匯入到會話中。</span><span class="sxs-lookup"><span data-stu-id="6bdce-246">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="6bdce-247">當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。</span><span class="sxs-lookup"><span data-stu-id="6bdce-247">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="6bdce-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6bdce-248">CommonParameters</span></span>

<span data-ttu-id="6bdce-249">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6bdce-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6bdce-250">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6bdce-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6bdce-251">輸入</span><span class="sxs-lookup"><span data-stu-id="6bdce-251">INPUTS</span></span>

## <span data-ttu-id="6bdce-252">輸出</span><span class="sxs-lookup"><span data-stu-id="6bdce-252">OUTPUTS</span></span>

## <span data-ttu-id="6bdce-253">注意</span><span class="sxs-lookup"><span data-stu-id="6bdce-253">NOTES</span></span>

## <span data-ttu-id="6bdce-254">相關連結</span><span class="sxs-lookup"><span data-stu-id="6bdce-254">RELATED LINKS</span></span>

[<span data-ttu-id="6bdce-255">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="6bdce-255">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="6bdce-256">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="6bdce-256">Get-PSSessionCapability</span></span>](Get-PSSessionCapability.md)
