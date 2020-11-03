---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: b9a2386b41ec4d64200283a5cd3b802d254b5475
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204928"
---
# <span data-ttu-id="ba4a9-103">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba4a9-103">Set-ItemProperty</span></span>

## <span data-ttu-id="ba4a9-104">概要</span><span class="sxs-lookup"><span data-stu-id="ba4a9-104">SYNOPSIS</span></span>
<span data-ttu-id="ba4a9-105">建立或變更項目屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-105">Creates or changes the value of a property of an item.</span></span>

## <span data-ttu-id="ba4a9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ba4a9-106">SYNTAX</span></span>

### <span data-ttu-id="ba4a9-107">propertyValuePathSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="ba4a9-107">propertyValuePathSet (Default)</span></span>

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### <span data-ttu-id="ba4a9-108">propertyPSObjectPathSet</span><span class="sxs-lookup"><span data-stu-id="ba4a9-108">propertyPSObjectPathSet</span></span>

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### <span data-ttu-id="ba4a9-109">propertyValueLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="ba4a9-109">propertyValueLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### <span data-ttu-id="ba4a9-110">propertyPSObjectLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="ba4a9-110">propertyPSObjectLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

## <span data-ttu-id="ba4a9-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ba4a9-111">DESCRIPTION</span></span>

<span data-ttu-id="ba4a9-112">`Set-ItemProperty`Cmdlet 會變更指定專案的屬性值。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-112">The `Set-ItemProperty` cmdlet changes the value of the property of the specified item.</span></span>
<span data-ttu-id="ba4a9-113">您可以使用此 Cmdlet 來建立或變更項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-113">You can use the cmdlet to establish or change the properties of items.</span></span>
<span data-ttu-id="ba4a9-114">例如，您可以使用將 `Set-ItemProperty` file 物件的 **IsReadOnly** 屬性值設定為 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-114">For example, you can use `Set-ItemProperty` to set the value of the **IsReadOnly** property of a file object to `$True`.</span></span>

<span data-ttu-id="ba4a9-115">您也可以使用 `Set-ItemProperty` 來建立及變更登錄值和資料。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-115">You also use `Set-ItemProperty` to create and change registry values and data.</span></span>
<span data-ttu-id="ba4a9-116">例如，您可以將新登錄項目新增到機碼並建立或變更其值。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-116">For example, you can add a new registry entry to a key and establish or change its value.</span></span>

## <span data-ttu-id="ba4a9-117">範例</span><span class="sxs-lookup"><span data-stu-id="ba4a9-117">EXAMPLES</span></span>

### <span data-ttu-id="ba4a9-118">範例1：設定檔案的屬性</span><span class="sxs-lookup"><span data-stu-id="ba4a9-118">Example 1: Set a property of a file</span></span>

<span data-ttu-id="ba4a9-119">此命令會將 "final.doc" 檔案的 **IsReadOnly** 屬性值設定為 "true"。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-119">This command sets the value of the **IsReadOnly** property of the "final.doc" file to "true".</span></span>
<span data-ttu-id="ba4a9-120">它會使用 **路徑** 來指定檔案、指定屬性名稱的 **名稱** ，以及指定新值的 **值** 參數。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-120">It uses **Path** to specify the file, **Name** to specify the name of the property, and the **Value** parameter to specify the new value.</span></span>

<span data-ttu-id="ba4a9-121">檔案是 **FileInfo** 物件，而 **IsReadOnly** 只是它的其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-121">The file is a **System.IO.FileInfo** object and **IsReadOnly** is just one of its properties.</span></span>
<span data-ttu-id="ba4a9-122">若要查看所有屬性，請輸入 `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-122">To see all of the properties, type `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property`.</span></span>

<span data-ttu-id="ba4a9-123">`$true`自動變數代表值 "TRUE"。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-123">The `$true` automatic variable represents a value of "TRUE".</span></span>
<span data-ttu-id="ba4a9-124">如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-124">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### <span data-ttu-id="ba4a9-125">範例2：建立登錄專案和值</span><span class="sxs-lookup"><span data-stu-id="ba4a9-125">Example 2: Create a registry entry and value</span></span>

<span data-ttu-id="ba4a9-126">此範例示範如何使用 `Set-ItemProperty` 建立新的登錄專案，並將值指派給專案。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-126">This example shows how to use `Set-ItemProperty` to create a new registry entry and to assign a value to the entry.</span></span> <span data-ttu-id="ba4a9-127">它會在機碼中的 "ContosoCompany" 機碼中建立 "NoOfEmployees" 專案 `HKLM\Software` ，並將其值設定為823。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-127">It creates the "NoOfEmployees" entry in the "ContosoCompany" key in `HKLM\Software` key and sets its value to 823.</span></span>

<span data-ttu-id="ba4a9-128">由於登錄專案被視為登錄機碼的屬性，也就是用 `Set-ItemProperty` 來建立登錄專案，以及建立和變更其值的專案。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-128">Because registry entries are considered to be properties of the registry keys, which are items, you use `Set-ItemProperty` to create registry entries, and to establish and change their values.</span></span>

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823
```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

<span data-ttu-id="ba4a9-129">第一個命令會建立登錄專案。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-129">The first command creates the registry entry.</span></span>
<span data-ttu-id="ba4a9-130">它會使用 **path** 來指定 `HKLM:` 磁片磁碟機的路徑和 "software\mycompany 機" 機碼。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-130">It uses **Path** to specify the path of the `HKLM:` drive and the "Software\MyCompany" key.</span></span>
<span data-ttu-id="ba4a9-131">命令使用 **Name** 來指定專案名稱和 **值** ，以指定值。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-131">The command uses **Name** to specify the entry name and **Value** to specify a value.</span></span>

<span data-ttu-id="ba4a9-132">第二個命令會使用 `Get-ItemProperty` Cmdlet 來查看新的登錄專案。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-132">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>
<span data-ttu-id="ba4a9-133">如果您使用 `Get-Item` 或 `Get-ChildItem` Cmdlet，這些專案就不會出現，因為它們是索引鍵的屬性，而不是專案或子專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-133">If you use the `Get-Item` or `Get-ChildItem` cmdlets, the entries do not appear because they are properties of a key, not items or child items.</span></span>

<span data-ttu-id="ba4a9-134">第三個命令會將 **NoOfEmployees** 專案的值變更為824。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-134">The third command changes the value of the **NoOfEmployees** entry to 824.</span></span>

<span data-ttu-id="ba4a9-135">您也可以使用 `New-ItemProperty` Cmdlet 來建立登錄專案及其值，然後使用 `Set-ItemProperty` 來變更值。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-135">You can also use the `New-ItemProperty` cmdlet to create the registry entry and its value and then use `Set-ItemProperty` to change the value.</span></span>

<span data-ttu-id="ba4a9-136">如需磁片磁碟機的詳細資訊 `HKLM:` ，請輸入 `Get-Help Get-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-136">For more information about the `HKLM:` drive, type `Get-Help Get-PSDrive`.</span></span>
<span data-ttu-id="ba4a9-137">如需有關如何使用 PowerShell 來管理登錄的詳細資訊，請輸入 `Get-Help Registry` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-137">For more information about how to use PowerShell to manage the registry, type `Get-Help Registry`.</span></span>

### <span data-ttu-id="ba4a9-138">範例3：使用管線修改專案</span><span class="sxs-lookup"><span data-stu-id="ba4a9-138">Example 3: Modify an item by using the pipeline</span></span>

<span data-ttu-id="ba4a9-139">這些命令示範如何使用管線運算子 () 將 `|` 專案傳送至其中 `Set-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-139">These commands show how to use a pipeline operator (`|`) to send an item to `Set-ItemProperty`.</span></span>

<span data-ttu-id="ba4a9-140">命令的第一個部分會使用 `Get-ChildItem` 來取得代表 "Weekly.txt" 檔案的物件。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-140">The first part of the command uses `Get-ChildItem` to get an object that represents the "Weekly.txt" file.</span></span> <span data-ttu-id="ba4a9-141">此命令會使用管線運算子將檔案物件傳送至 `Set-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-141">The command uses a pipeline operator to send the file object to `Set-ItemProperty`.</span></span>
<span data-ttu-id="ba4a9-142">`Set-ItemProperty`命令使用 **Name** 和 **Value** 參數指定屬性及其新值。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-142">The `Set-ItemProperty` command uses the **Name** and **Value** parameters to specify the property and its new value.</span></span>

<span data-ttu-id="ba4a9-143">此命令相當於使用 **InputObject** 參數來指定取得的物件 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-143">This command is equivalent to using the **InputObject** parameter to specify the object that `Get-ChildItem` gets.</span></span>

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## <span data-ttu-id="ba4a9-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ba4a9-144">PARAMETERS</span></span>

### <span data-ttu-id="ba4a9-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="ba4a9-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="ba4a9-146">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="ba4a9-147">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ba4a9-148">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ba4a9-148">-Exclude</span></span>

<span data-ttu-id="ba4a9-149">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-149">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="ba4a9-150">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-150">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="ba4a9-151">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-151">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="ba4a9-152">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-152">Wildcard characters are permitted.</span></span> <span data-ttu-id="ba4a9-153">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-153">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="ba4a9-154">-Filter</span><span class="sxs-lookup"><span data-stu-id="ba4a9-154">-Filter</span></span>

<span data-ttu-id="ba4a9-155">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-155">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="ba4a9-156">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-156">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="ba4a9-157">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-157">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="ba4a9-158">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-158">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="ba4a9-159">-Force</span><span class="sxs-lookup"><span data-stu-id="ba4a9-159">-Force</span></span>

<span data-ttu-id="ba4a9-160">強制 Cmdlet 在使用者無法以其他方式存取的專案上設定屬性。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-160">Forces the cmdlet to set a property on items that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="ba4a9-161">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-161">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="ba4a9-162">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-162">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="ba4a9-163">-Include</span><span class="sxs-lookup"><span data-stu-id="ba4a9-163">-Include</span></span>

<span data-ttu-id="ba4a9-164">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-164">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="ba4a9-165">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-165">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="ba4a9-166">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-166">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="ba4a9-167">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-167">Wildcard characters are permitted.</span></span> <span data-ttu-id="ba4a9-168">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-168">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="ba4a9-169">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ba4a9-169">-InputObject</span></span>

<span data-ttu-id="ba4a9-170">指定具有此 Cmdlet 所變更屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-170">Specifies the object that has the properties that this cmdlet changes.</span></span>
<span data-ttu-id="ba4a9-171">輸入包含物件的變數，或輸入可取得物件的命令。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-171">Enter a variable that contains the object or a command that gets the object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ba4a9-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ba4a9-172">-LiteralPath</span></span>

<span data-ttu-id="ba4a9-173">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-173">Specifies a path to one or more locations.</span></span> <span data-ttu-id="ba4a9-174">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-174">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="ba4a9-175">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ba4a9-176">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ba4a9-177">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="ba4a9-178">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-178">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyPSObjectLiteralPathSet, propertyValueLiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ba4a9-179">-Name</span><span class="sxs-lookup"><span data-stu-id="ba4a9-179">-Name</span></span>

<span data-ttu-id="ba4a9-180">指定屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-180">Specifies the name of the property.</span></span>

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ba4a9-181">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ba4a9-181">-PassThru</span></span>

<span data-ttu-id="ba4a9-182">傳回代表項目屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-182">Returns an object that represents the item property.</span></span>
<span data-ttu-id="ba4a9-183">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-183">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ba4a9-184">-Path</span><span class="sxs-lookup"><span data-stu-id="ba4a9-184">-Path</span></span>

<span data-ttu-id="ba4a9-185">使用要修改的屬性，指定專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-185">Specifies the path of the items with the property to modify.</span></span>
<span data-ttu-id="ba4a9-186">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-186">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ba4a9-187">-Type</span><span class="sxs-lookup"><span data-stu-id="ba4a9-187">-Type</span></span>

<span data-ttu-id="ba4a9-188">**類型** 是登錄提供者新增至 Cmdlet 的動態參數 `Set-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-188">**Type** is a dynamic parameter that the Registry provider adds to the `Set-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="ba4a9-189">這個參數只能在登錄磁片磁碟機中運作。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-189">This parameter only works in the registry drives.</span></span>

<span data-ttu-id="ba4a9-190">指定此 Cmdlet 所新增的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-190">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="ba4a9-191">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="ba4a9-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ba4a9-192">**字串** ：指定以 null 終止的字串。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-192">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="ba4a9-193">相當於 **REG_SZ** 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-193">Equivalent to **REG_SZ** .</span></span>
- <span data-ttu-id="ba4a9-194">**ExpandString** ：指定以 null 終止的字串，其中包含在抓取值時展開之環境變數的未展開參考。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-194">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="ba4a9-195">相當於 **REG_EXPAND_SZ** 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-195">Equivalent to **REG_EXPAND_SZ** .</span></span>
- <span data-ttu-id="ba4a9-196">**Binary** ：以任何形式指定二進位資料。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-196">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="ba4a9-197">相當於 **REG_BINARY** 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-197">Equivalent to **REG_BINARY** .</span></span>
- <span data-ttu-id="ba4a9-198">**DWord** ：指定32位的二進位數。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-198">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="ba4a9-199">相當於 **REG_DWORD** 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-199">Equivalent to **REG_DWORD** .</span></span>
- <span data-ttu-id="ba4a9-200">**MultiString** ：指定以 null 終止的字串陣列（以兩個 null 字元結束）。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-200">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="ba4a9-201">相當於 **REG_MULTI_SZ** 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-201">Equivalent to **REG_MULTI_SZ** .</span></span>
- <span data-ttu-id="ba4a9-202">**Qword** ：指定64位的二進位數。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-202">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="ba4a9-203">相當於 **REG_QWORD** 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-203">Equivalent to **REG_QWORD** .</span></span>
- <span data-ttu-id="ba4a9-204">**未知** ：表示不支援的登錄資料類型，例如 **REG_RESOURCE_LIST** 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-204">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST** .</span></span>

```yaml
Type: Microsoft.Win32.RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ba4a9-205">-Value</span><span class="sxs-lookup"><span data-stu-id="ba4a9-205">-Value</span></span>

<span data-ttu-id="ba4a9-206">指定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-206">Specifies the value of the property.</span></span>

```yaml
Type: System.Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ba4a9-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ba4a9-207">-Confirm</span></span>

<span data-ttu-id="ba4a9-208">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-208">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba4a9-209">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ba4a9-209">-WhatIf</span></span>

<span data-ttu-id="ba4a9-210">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-210">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ba4a9-211">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-211">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba4a9-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ba4a9-212">CommonParameters</span></span>

<span data-ttu-id="ba4a9-213">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-213">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="ba4a9-214">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-214">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ba4a9-215">輸入</span><span class="sxs-lookup"><span data-stu-id="ba4a9-215">INPUTS</span></span>

### <span data-ttu-id="ba4a9-216">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="ba4a9-216">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="ba4a9-217">您可以透過管道將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-217">You can pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="ba4a9-218">輸出</span><span class="sxs-lookup"><span data-stu-id="ba4a9-218">OUTPUTS</span></span>

### <span data-ttu-id="ba4a9-219">None，System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="ba4a9-219">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="ba4a9-220">如果您指定 **PassThru** 參數，此 Cmdlet 會產生代表已變更之專案及其新屬性值的 **PSCustomObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-220">This cmdlet generates a **PSCustomObject** object that represents the item that was changed and its new property value, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="ba4a9-221">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-221">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ba4a9-222">注意</span><span class="sxs-lookup"><span data-stu-id="ba4a9-222">NOTES</span></span>

<span data-ttu-id="ba4a9-223">`Set-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-223">`Set-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ba4a9-224">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-224">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="ba4a9-225">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="ba4a9-225">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="ba4a9-226">相關連結</span><span class="sxs-lookup"><span data-stu-id="ba4a9-226">RELATED LINKS</span></span>

[<span data-ttu-id="ba4a9-227">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba4a9-227">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="ba4a9-228">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba4a9-228">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="ba4a9-229">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba4a9-229">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="ba4a9-230">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba4a9-230">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="ba4a9-231">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba4a9-231">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="ba4a9-232">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba4a9-232">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="ba4a9-233">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba4a9-233">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="ba4a9-234">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ba4a9-234">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
