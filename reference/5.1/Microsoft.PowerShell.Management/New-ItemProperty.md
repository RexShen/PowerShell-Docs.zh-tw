---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 2569f4778f54f6cdad22e10cf92e727b73c323e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203592"
---
# <span data-ttu-id="ffb3f-103">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ffb3f-103">New-ItemProperty</span></span>

## <span data-ttu-id="ffb3f-104">概要</span><span class="sxs-lookup"><span data-stu-id="ffb3f-104">SYNOPSIS</span></span>
<span data-ttu-id="ffb3f-105">建立項目的新屬性，並設定其值。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-105">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="ffb3f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ffb3f-106">SYNTAX</span></span>

### <span data-ttu-id="ffb3f-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="ffb3f-107">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="ffb3f-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ffb3f-108">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="ffb3f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ffb3f-109">DESCRIPTION</span></span>

<span data-ttu-id="ffb3f-110">`New-ItemProperty`Cmdlet 會為指定的專案建立新的屬性，並設定其值。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-110">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="ffb3f-111">一般而言，這個 Cmdlet 是用來建立新的登錄值，因為登錄值是登錄機碼項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-111">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="ffb3f-112">這個 Cmdlet 並不會將屬性新增到物件。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-112">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="ffb3f-113">若要將屬性加入至物件的實例，請使用 `Add-Member` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-113">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="ffb3f-114">若要將屬性新增到特定類型的所有物件，請修改 Types.ps1的 xml 檔。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-114">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="ffb3f-115">範例</span><span class="sxs-lookup"><span data-stu-id="ffb3f-115">EXAMPLES</span></span>

### <span data-ttu-id="ffb3f-116">範例1：新增登錄專案</span><span class="sxs-lookup"><span data-stu-id="ffb3f-116">Example 1: Add a registry entry</span></span>

<span data-ttu-id="ffb3f-117">此命令會將新的登錄專案 "NoOfEmployees" 新增至 "HKLM： \ Software hive" 的 "MyCompany" 機碼。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-117">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="ffb3f-118">第一個命令使用 **path** 參數來指定 "MyCompany" 登錄機碼的路徑。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-118">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="ffb3f-119">它會使用 **name** 參數來指定專案的名稱，並使用 **Value** 參數來指定其值。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-119">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="ffb3f-120">第二個命令會使用 `Get-ItemProperty` Cmdlet 來查看新的登錄專案。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-120">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### <span data-ttu-id="ffb3f-121">範例2：將登錄專案新增至機碼</span><span class="sxs-lookup"><span data-stu-id="ffb3f-121">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="ffb3f-122">這個命令會將新登錄項目新增到登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-122">This command adds a new registry entry to a registry key.</span></span> <span data-ttu-id="ffb3f-123">若要指定索引鍵，它會使用管線運算子 (|) ，將代表金鑰的物件傳送至 `New-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-123">To specify the key, it uses a pipeline operator (|) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="ffb3f-124">命令的第一個部分會使用 `Get-Item` Cmdlet 來取得 "MyCompany" 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-124">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span> <span data-ttu-id="ffb3f-125">管線運算子會將命令的結果傳送至 `New-ItemProperty` ，這會將新的登錄專案 ( "NoOfLocations" ) ，並將其值 (3) 新增至 "MyCompany" 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-125">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="ffb3f-126">此命令的運作方式是因為 Windows PowerShell 的參數系結功能會將傳回的 `RegistryKey` 物件路徑 `Get-Item` 與的 **LiteralPath** 參數產生關聯 `New-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-126">This command works because the parameter-binding feature of Windows PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="ffb3f-127">如需詳細資訊，請參閱 [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-127">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="ffb3f-128">範例3：使用 Here-String 在登錄中建立 MultiString 值</span><span class="sxs-lookup"><span data-stu-id="ffb3f-128">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="ffb3f-129">此範例會使用此處的字串來建立 MultiString 值。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-129">This example creates a MultiString value using a Here-String.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### <span data-ttu-id="ffb3f-130">範例4：使用陣列在登錄中建立 MultiString 值</span><span class="sxs-lookup"><span data-stu-id="ffb3f-130">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="ffb3f-131">此範例顯示如何使用值的陣列來建立 `MultiString` 值。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-131">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="ffb3f-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ffb3f-132">PARAMETERS</span></span>

### <span data-ttu-id="ffb3f-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="ffb3f-133">-Credential</span></span>

<span data-ttu-id="ffb3f-134">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-134">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="ffb3f-135">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-135">The default is the current user.</span></span>

<span data-ttu-id="ffb3f-136">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-136">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="ffb3f-137">若您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-137">If you type a user name, you are prompted for a password.</span></span>

> [!NOTE]
> <span data-ttu-id="ffb3f-138">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-138">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="ffb3f-139">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-139">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="ffb3f-140">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ffb3f-140">-Exclude</span></span>

<span data-ttu-id="ffb3f-141">以字串陣列指定此 Cmdlet 從作業中排除的屬性或屬性。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-141">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="ffb3f-142">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-142">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="ffb3f-143">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-143">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="ffb3f-144">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-144">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ffb3f-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="ffb3f-145">-Filter</span></span>

<span data-ttu-id="ffb3f-146">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-146">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="ffb3f-147">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-147">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="ffb3f-148">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-148">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="ffb3f-149">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-149">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="ffb3f-150">-Force</span><span class="sxs-lookup"><span data-stu-id="ffb3f-150">-Force</span></span>

<span data-ttu-id="ffb3f-151">強制 Cmdlet 在使用者無法以其他方式存取的物件上建立屬性。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-151">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="ffb3f-152">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-152">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="ffb3f-153">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-153">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="ffb3f-154">-Include</span><span class="sxs-lookup"><span data-stu-id="ffb3f-154">-Include</span></span>

<span data-ttu-id="ffb3f-155">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-155">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="ffb3f-156">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-156">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="ffb3f-157">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-157">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="ffb3f-158">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-158">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ffb3f-159">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ffb3f-159">-LiteralPath</span></span>

<span data-ttu-id="ffb3f-160">指定屬性之目前位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-160">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="ffb3f-161">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-161">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="ffb3f-162">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-162">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="ffb3f-163">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-163">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="ffb3f-164">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-164">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ffb3f-165">-Name</span><span class="sxs-lookup"><span data-stu-id="ffb3f-165">-Name</span></span>

<span data-ttu-id="ffb3f-166">指定新屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-166">Specifies a name for the new property.</span></span>
<span data-ttu-id="ffb3f-167">如果屬性是登錄項目，這個參數便會指定該項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-167">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ffb3f-168">-Path</span><span class="sxs-lookup"><span data-stu-id="ffb3f-168">-Path</span></span>

<span data-ttu-id="ffb3f-169">指定專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-169">Specifies the path of the item.</span></span>
<span data-ttu-id="ffb3f-170">此參數會識別這個 Cmdlet 要加入新屬性的專案。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-170">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ffb3f-171">-PropertyType</span><span class="sxs-lookup"><span data-stu-id="ffb3f-171">-PropertyType</span></span>

<span data-ttu-id="ffb3f-172">指定此 Cmdlet 所新增的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-172">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="ffb3f-173">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="ffb3f-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ffb3f-174">**字串** ：指定以 null 終止的字串。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-174">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="ffb3f-175">相當於 **REG_SZ** 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-175">Equivalent to **REG_SZ** .</span></span>
- <span data-ttu-id="ffb3f-176">**ExpandString** ：指定以 null 終止的字串，其中包含在抓取值時展開之環境變數的未展開參考。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-176">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="ffb3f-177">相當於 **REG_EXPAND_SZ** 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-177">Equivalent to **REG_EXPAND_SZ** .</span></span>
- <span data-ttu-id="ffb3f-178">**Binary** ：以任何形式指定二進位資料。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-178">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="ffb3f-179">相當於 **REG_BINARY** 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-179">Equivalent to **REG_BINARY** .</span></span>
- <span data-ttu-id="ffb3f-180">**DWord** ：指定32位的二進位數。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-180">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="ffb3f-181">相當於 **REG_DWORD** 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-181">Equivalent to **REG_DWORD** .</span></span>
- <span data-ttu-id="ffb3f-182">**MultiString** ：指定以 null 終止的字串陣列（以兩個 null 字元結束）。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-182">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="ffb3f-183">相當於 **REG_MULTI_SZ** 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-183">Equivalent to **REG_MULTI_SZ** .</span></span>
- <span data-ttu-id="ffb3f-184">**Qword** ：指定64位的二進位數。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-184">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="ffb3f-185">相當於 **REG_QWORD** 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-185">Equivalent to **REG_QWORD** .</span></span>
- <span data-ttu-id="ffb3f-186">**未知** ：表示不支援的登錄資料類型，例如 **REG_RESOURCE_LIST** 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-186">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST** .</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ffb3f-187">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="ffb3f-187">-UseTransaction</span></span>

<span data-ttu-id="ffb3f-188">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-188">Includes the command in the active transaction.</span></span>
<span data-ttu-id="ffb3f-189">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-189">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="ffb3f-190">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-190">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="ffb3f-191">-Value</span><span class="sxs-lookup"><span data-stu-id="ffb3f-191">-Value</span></span>

<span data-ttu-id="ffb3f-192">指定屬性值。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-192">Specifies the property value.</span></span>
<span data-ttu-id="ffb3f-193">如果屬性是登錄項目，這個參數便會指定該項目的值。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-193">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ffb3f-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ffb3f-194">-Confirm</span></span>

<span data-ttu-id="ffb3f-195">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ffb3f-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ffb3f-196">-WhatIf</span></span>

<span data-ttu-id="ffb3f-197">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-197">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ffb3f-198">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ffb3f-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ffb3f-199">CommonParameters</span></span>

<span data-ttu-id="ffb3f-200">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-200">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="ffb3f-201">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-201">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ffb3f-202">輸入</span><span class="sxs-lookup"><span data-stu-id="ffb3f-202">INPUTS</span></span>

### <span data-ttu-id="ffb3f-203">無</span><span class="sxs-lookup"><span data-stu-id="ffb3f-203">None</span></span>

<span data-ttu-id="ffb3f-204">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-204">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ffb3f-205">輸出</span><span class="sxs-lookup"><span data-stu-id="ffb3f-205">OUTPUTS</span></span>

### <span data-ttu-id="ffb3f-206">System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="ffb3f-206">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="ffb3f-207">`New-ItemProperty` 傳回包含新屬性的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-207">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="ffb3f-208">注意</span><span class="sxs-lookup"><span data-stu-id="ffb3f-208">NOTES</span></span>

<span data-ttu-id="ffb3f-209">`New-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-209">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ffb3f-210">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-210">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="ffb3f-211">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="ffb3f-211">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="ffb3f-212">相關連結</span><span class="sxs-lookup"><span data-stu-id="ffb3f-212">RELATED LINKS</span></span>

[<span data-ttu-id="ffb3f-213">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ffb3f-213">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="ffb3f-214">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ffb3f-214">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="ffb3f-215">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ffb3f-215">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="ffb3f-216">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ffb3f-216">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="ffb3f-217">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ffb3f-217">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="ffb3f-218">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ffb3f-218">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="ffb3f-219">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ffb3f-219">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="ffb3f-220">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ffb3f-220">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
