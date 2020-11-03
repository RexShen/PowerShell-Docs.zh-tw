---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203996"
---
# <span data-ttu-id="ba20e-103">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba20e-103">Get-ItemProperty</span></span>

## <span data-ttu-id="ba20e-104">概要</span><span class="sxs-lookup"><span data-stu-id="ba20e-104">SYNOPSIS</span></span>
<span data-ttu-id="ba20e-105">取得指定項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba20e-105">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="ba20e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ba20e-106">SYNTAX</span></span>

### <span data-ttu-id="ba20e-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="ba20e-107">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="ba20e-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ba20e-108">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="ba20e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ba20e-109">DESCRIPTION</span></span>

<span data-ttu-id="ba20e-110">`Get-ItemProperty`Cmdlet 會取得指定專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba20e-110">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="ba20e-111">例如，您可以使用這個 Cmdlet 取得檔案物件的 LastAccessTime 屬性值。</span><span class="sxs-lookup"><span data-stu-id="ba20e-111">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span>
<span data-ttu-id="ba20e-112">您也可以使用這個 Cmdlet 來查看登錄專案和其值。</span><span class="sxs-lookup"><span data-stu-id="ba20e-112">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="ba20e-113">範例</span><span class="sxs-lookup"><span data-stu-id="ba20e-113">EXAMPLES</span></span>

### <span data-ttu-id="ba20e-114">範例1：取得特定目錄的相關資訊</span><span class="sxs-lookup"><span data-stu-id="ba20e-114">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="ba20e-115">此命令會取得 "C：\Windows" 目錄的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ba20e-115">This command gets information about the "C:\Windows" directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="ba20e-116">範例2：取得特定檔案的屬性</span><span class="sxs-lookup"><span data-stu-id="ba20e-116">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="ba20e-117">此命令會取得 "C:\Test\Weather.xls" 檔案的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba20e-117">This command gets the properties of the "C:\Test\Weather.xls" file.</span></span>
<span data-ttu-id="ba20e-118">結果會透過管道傳送至 `Format-List` Cmdlet，以將輸出顯示為清單。</span><span class="sxs-lookup"><span data-stu-id="ba20e-118">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="ba20e-119">範例3：顯示登錄子機碼中登錄專案的值名稱和資料</span><span class="sxs-lookup"><span data-stu-id="ba20e-119">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="ba20e-120">此命令顯示 "CurrentVersion" 登錄子機碼中包含之每個登錄專案的值名稱和資料。</span><span class="sxs-lookup"><span data-stu-id="ba20e-120">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="ba20e-121">請注意，此命令會要求將名為的 PowerShell 磁片磁碟機 `HKLM:` 對應至登錄的 "HKEY_LOCAL_MACHINE" hive。</span><span class="sxs-lookup"><span data-stu-id="ba20e-121">Note that the command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
<span data-ttu-id="ba20e-122">具有該名稱和對應的磁片磁碟機預設可在 PowerShell 中使用。</span><span class="sxs-lookup"><span data-stu-id="ba20e-122">A drive with that name and mapping is available in PowerShell by default.</span></span>
<span data-ttu-id="ba20e-123">或者，您可以使用下列替代路徑 (開頭為提供者名稱，後面是兩個冒號) 來指定此登錄子機碼的路徑：</span><span class="sxs-lookup"><span data-stu-id="ba20e-123">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>

<span data-ttu-id="ba20e-124">"Registry：： HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion"。</span><span class="sxs-lookup"><span data-stu-id="ba20e-124">"Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion".</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### <span data-ttu-id="ba20e-125">範例4：取得登錄子機碼中登錄專案的值名稱和資料</span><span class="sxs-lookup"><span data-stu-id="ba20e-125">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="ba20e-126">此命令會取得 "CurrentVersion" 登錄子機碼中 "ProgramFilesDir" 登錄專案的值名稱和資料。</span><span class="sxs-lookup"><span data-stu-id="ba20e-126">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="ba20e-127">命令使用 **Path** 參數指定子機碼和 Name 參數，以指定專案的值名稱。</span><span class="sxs-lookup"><span data-stu-id="ba20e-127">The command uses the **Path** parameter to specify the subkey and the Name parameter to specify the value name of the entry.</span></span>

<span data-ttu-id="ba20e-128">此命令會使用反向刻度或抑音符 \` 號 () （PowerShell 接續字元）來繼續第二行的命令。</span><span class="sxs-lookup"><span data-stu-id="ba20e-128">The command uses a back tick or grave accent (\`), the PowerShell continuation character, to continue the command on the second line.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="ba20e-129">範例5：取得登錄機碼中登錄專案的值名稱和資料</span><span class="sxs-lookup"><span data-stu-id="ba20e-129">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="ba20e-130">此命令會取得 "PowerShellEngine" 登錄機碼中登錄專案的值名稱和資料。</span><span class="sxs-lookup"><span data-stu-id="ba20e-130">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span>
<span data-ttu-id="ba20e-131">結果顯示在下列範例輸出中。</span><span class="sxs-lookup"><span data-stu-id="ba20e-131">The results are shown in the following sample output.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

### <span data-ttu-id="ba20e-132">範例6：取得、格式化及顯示登錄值和資料的結果</span><span class="sxs-lookup"><span data-stu-id="ba20e-132">Example 6: Get, format, and display the results of registry values and data</span></span>

<span data-ttu-id="ba20e-133">此範例顯示如何格式化 `Get-ItemProperty` 清單中命令的輸出，讓您輕鬆查看登錄值和資料，並讓您輕鬆地解讀結果。</span><span class="sxs-lookup"><span data-stu-id="ba20e-133">This example shows how to format the output of a `Get-ItemProperty` command in a list to make it easy to see the registry values and data and to make it easy to interpret the results.</span></span>

<span data-ttu-id="ba20e-134">第一個命令會使用 `Get-ItemProperty` Cmdlet 取得 **Microsoft PowerShell** 子機碼中的登錄專案。</span><span class="sxs-lookup"><span data-stu-id="ba20e-134">The first command uses the `Get-ItemProperty` cmdlet to get the registry entries in the **Microsoft.PowerShell** subkey.</span></span>
<span data-ttu-id="ba20e-135">此子機碼會儲存 PowerShell 預設 shell 的選項。</span><span class="sxs-lookup"><span data-stu-id="ba20e-135">This subkey stores options for the default shell for PowerShell.</span></span>
<span data-ttu-id="ba20e-136">結果顯示在下列範例輸出中。</span><span class="sxs-lookup"><span data-stu-id="ba20e-136">The results are shown in the following sample output.</span></span>

<span data-ttu-id="ba20e-137">輸出顯示有兩個登錄專案： "Path" 和 "ExecutionPolicy"。</span><span class="sxs-lookup"><span data-stu-id="ba20e-137">The output shows that there are two registry entries, "Path" and "ExecutionPolicy".</span></span>
<span data-ttu-id="ba20e-138">當登錄機碼包含的項目少於五個時，預設會顯示在表格中，但在清單中檢視通常更容易。</span><span class="sxs-lookup"><span data-stu-id="ba20e-138">When a registry key contains fewer than five entries, by default it is displayed in a table, but it is often easier to view in a list.</span></span>

<span data-ttu-id="ba20e-139">第二個命令使用相同的 `Get-ItemProperty` 命令。</span><span class="sxs-lookup"><span data-stu-id="ba20e-139">The second command uses the same `Get-ItemProperty` command.</span></span>
<span data-ttu-id="ba20e-140">不過，這次命令會使用管線運算子 (`|`) 將命令的結果傳送至 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba20e-140">However, this time, the command uses a pipeline operator (`|`) to send the results of the command to the `Format-List` cmdlet.</span></span>
<span data-ttu-id="ba20e-141">此 `Format-List` 命令會使用值為 ' \* ' 的 Property 參數 (所有) 來顯示清單中物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="ba20e-141">The `Format-List` command uses the Property parameter with a value of '\*' (all) to display all of the properties of the objects in a list.</span></span>
<span data-ttu-id="ba20e-142">結果顯示在下列範例輸出中。</span><span class="sxs-lookup"><span data-stu-id="ba20e-142">The results are shown in the following sample output.</span></span>

<span data-ttu-id="ba20e-143">產生的顯示會顯示 "Path" 和 "ExecutionPolicy" 登錄專案，以及數個較不熟悉的登錄機碼物件屬性。</span><span class="sxs-lookup"><span data-stu-id="ba20e-143">The resulting display shows the "Path" and "ExecutionPolicy" registry entries, along with several less familiar properties of the registry key object.</span></span>
<span data-ttu-id="ba20e-144">其他以 PS 開頭的屬性是 PowerShell 自訂物件的屬性，例如代表登錄機碼的物件。</span><span class="sxs-lookup"><span data-stu-id="ba20e-144">The other properties, prefixed with PS, are properties of PowerShell custom objects, such as the objects that represent the registry keys.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## <span data-ttu-id="ba20e-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ba20e-145">PARAMETERS</span></span>

### <span data-ttu-id="ba20e-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="ba20e-146">-Credential</span></span>

<span data-ttu-id="ba20e-147">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ba20e-147">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="ba20e-148">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="ba20e-148">The default is the current user.</span></span>

<span data-ttu-id="ba20e-149">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="ba20e-149">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="ba20e-150">若您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="ba20e-150">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="ba20e-151">與 Windows PowerShell 一起安裝的任何提供者皆不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="ba20e-151">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="ba20e-152">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ba20e-152">-Exclude</span></span>

<span data-ttu-id="ba20e-153">以字串陣列指定此 Cmdlet 在作業中排除的項目。</span><span class="sxs-lookup"><span data-stu-id="ba20e-153">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="ba20e-154">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ba20e-154">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="ba20e-155">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="ba20e-155">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="ba20e-156">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ba20e-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ba20e-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="ba20e-157">-Filter</span></span>

<span data-ttu-id="ba20e-158">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="ba20e-158">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="ba20e-159">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ba20e-159">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="ba20e-160">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="ba20e-160">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="ba20e-161">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="ba20e-161">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="ba20e-162">-Include</span><span class="sxs-lookup"><span data-stu-id="ba20e-162">-Include</span></span>

<span data-ttu-id="ba20e-163">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="ba20e-163">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="ba20e-164">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="ba20e-164">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="ba20e-165">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="ba20e-165">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="ba20e-166">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ba20e-166">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ba20e-167">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ba20e-167">-LiteralPath</span></span>

<span data-ttu-id="ba20e-168">指定屬性之目前位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="ba20e-168">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="ba20e-169">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="ba20e-169">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="ba20e-170">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ba20e-170">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="ba20e-171">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="ba20e-171">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="ba20e-172">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="ba20e-172">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="ba20e-173">-Name</span><span class="sxs-lookup"><span data-stu-id="ba20e-173">-Name</span></span>

<span data-ttu-id="ba20e-174">指定要抓取之一或多個屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="ba20e-174">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba20e-175">-Path</span><span class="sxs-lookup"><span data-stu-id="ba20e-175">-Path</span></span>

<span data-ttu-id="ba20e-176">指定一或多個項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="ba20e-176">Specifies the path to the item or items.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ba20e-177">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="ba20e-177">-UseTransaction</span></span>

<span data-ttu-id="ba20e-178">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="ba20e-178">Includes the command in the active transaction.</span></span>
<span data-ttu-id="ba20e-179">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="ba20e-179">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="ba20e-180">如需詳細資訊，請參閱＜將命令加入使用中交易＞。</span><span class="sxs-lookup"><span data-stu-id="ba20e-180">For more information, see Includes the command in the active transaction.</span></span>
<span data-ttu-id="ba20e-181">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="ba20e-181">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="ba20e-182">如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="ba20e-182">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="ba20e-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ba20e-183">CommonParameters</span></span>

<span data-ttu-id="ba20e-184">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="ba20e-184">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="ba20e-185">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="ba20e-185">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ba20e-186">輸入</span><span class="sxs-lookup"><span data-stu-id="ba20e-186">INPUTS</span></span>

### <span data-ttu-id="ba20e-187">System.String</span><span class="sxs-lookup"><span data-stu-id="ba20e-187">System.String</span></span>

<span data-ttu-id="ba20e-188">您可以使用管線將包含路徑的字串傳送至 `Get-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="ba20e-188">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="ba20e-189">輸出</span><span class="sxs-lookup"><span data-stu-id="ba20e-189">OUTPUTS</span></span>

### <span data-ttu-id="ba20e-190">System.Boolean、System.String、System.DateTime</span><span class="sxs-lookup"><span data-stu-id="ba20e-190">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="ba20e-191">`Get-ItemProperty` 針對它取得的每個專案屬性，各傳回一個物件。</span><span class="sxs-lookup"><span data-stu-id="ba20e-191">`Get-ItemProperty` returns an object for each item property that it gets.</span></span>
<span data-ttu-id="ba20e-192">物件類型取決於所抓取的物件。</span><span class="sxs-lookup"><span data-stu-id="ba20e-192">The object type depends on the object that is retrieved.</span></span>
<span data-ttu-id="ba20e-193">例如，在檔案系統磁碟機中，它可能會傳回檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba20e-193">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="ba20e-194">注意</span><span class="sxs-lookup"><span data-stu-id="ba20e-194">NOTES</span></span>

<span data-ttu-id="ba20e-195">此 `Get-ItemProperty` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="ba20e-195">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ba20e-196">若要列出會話中可用的提供者，請輸入 " `Get-PSProvider` "。</span><span class="sxs-lookup"><span data-stu-id="ba20e-196">To list the providers available in your session, type "`Get-PSProvider`".</span></span> <span data-ttu-id="ba20e-197">如需詳細資訊，請參閱 about_Providers。</span><span class="sxs-lookup"><span data-stu-id="ba20e-197">For more information, see about_Providers.</span></span>

## <span data-ttu-id="ba20e-198">相關連結</span><span class="sxs-lookup"><span data-stu-id="ba20e-198">RELATED LINKS</span></span>

[<span data-ttu-id="ba20e-199">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba20e-199">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="ba20e-200">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba20e-200">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="ba20e-201">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba20e-201">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="ba20e-202">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba20e-202">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="ba20e-203">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba20e-203">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="ba20e-204">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba20e-204">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="ba20e-205">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="ba20e-205">Set-ItemProperty</span></span>](Set-ItemProperty.md)
