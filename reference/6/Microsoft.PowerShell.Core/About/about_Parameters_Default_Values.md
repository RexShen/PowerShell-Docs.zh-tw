---
description: 說明如何設定 Cmdlet 參數和 advanced 函數的自訂預設值。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 5/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: 0e19241549b53bac9a57de183f2896985f94d116
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206988"
---
# <a name="about-parameters-default-values"></a><span data-ttu-id="6875d-104">關於參數的預設值</span><span class="sxs-lookup"><span data-stu-id="6875d-104">About Parameters Default Values</span></span>

## <a name="short-description"></a><span data-ttu-id="6875d-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="6875d-105">Short description</span></span>

<span data-ttu-id="6875d-106">說明如何設定 Cmdlet 參數和 advanced 函數的自訂預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-106">Describes how to set custom default values for cmdlet parameters and advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="6875d-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="6875d-107">Long description</span></span>

<span data-ttu-id="6875d-108">`$PSDefaultParameterValues`喜好設定變數可讓您指定任何 Cmdlet 或 advanced 函數的自訂預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-108">The `$PSDefaultParameterValues` preference variable lets you specify custom default values for any cmdlet or advanced function.</span></span> <span data-ttu-id="6875d-109">除非您在命令中指定另一個值，否則 Cmdlet 和 advanced 函數會使用自訂預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-109">Cmdlets and advanced functions use the custom default value unless you specify another value in the command.</span></span>

<span data-ttu-id="6875d-110">Cmdlet 和 advanced 函式的作者會為其參數設定標準預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-110">The authors of cmdlets and advanced functions set standard default values for their parameters.</span></span> <span data-ttu-id="6875d-111">一般而言，標準預設值很有用，但可能不適合所有環境。</span><span class="sxs-lookup"><span data-stu-id="6875d-111">Typically, the standard default values are useful, but they might not be appropriate for all environments.</span></span>

<span data-ttu-id="6875d-112">當您在每次使用命令時，或是當特定的參數值很難記住（例如電子郵件伺服器名稱或專案 GUID）時，這項功能特別有用。</span><span class="sxs-lookup"><span data-stu-id="6875d-112">This feature is especially useful when you must specify the same alternate parameter value nearly every time you use the command or when a particular parameter value is difficult to remember, such as an email server name or project GUID.</span></span>

<span data-ttu-id="6875d-113">如果所需的預設值有不同的預期值，您可以指定腳本區塊，在不同的條件下為參數提供不同的預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-113">If the desired default value varies predictably, you can specify a script block that provides different default values for a parameter under different conditions.</span></span>

<span data-ttu-id="6875d-114">`$PSDefaultParameterValues` 已在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6875d-114">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

## <a name="syntax"></a><span data-ttu-id="6875d-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="6875d-115">Syntax</span></span>

<span data-ttu-id="6875d-116">`$PSDefaultParameterValues`變數是一個雜湊表，可驗證索引鍵的格式是否為 **DefaultParameterDictionary** 的物件類型。</span><span class="sxs-lookup"><span data-stu-id="6875d-116">The `$PSDefaultParameterValues` variable is a hash table that validates the format of keys as an object type of **System.Management.Automation.DefaultParameterDictionary** .</span></span> <span data-ttu-id="6875d-117">雜湊表包含索引 **鍵/值** 組。</span><span class="sxs-lookup"><span data-stu-id="6875d-117">The hash table contains **Key/Value** pairs.</span></span> <span data-ttu-id="6875d-118">索引 **鍵** 的格式為 `CmdletName:ParameterName` 。</span><span class="sxs-lookup"><span data-stu-id="6875d-118">A **Key** is in the format `CmdletName:ParameterName`.</span></span> <span data-ttu-id="6875d-119">**值** 是指派給索引鍵的 **DefaultValue** 或 **ScriptBlock** 。</span><span class="sxs-lookup"><span data-stu-id="6875d-119">A **Value** is the **DefaultValue** or **ScriptBlock** assigned to the key.</span></span>

<span data-ttu-id="6875d-120">喜好設定變數的語法如下所示 `$PSDefaultParameterValues` ：</span><span class="sxs-lookup"><span data-stu-id="6875d-120">The syntax of the `$PSDefaultParameterValues` preference variable is as follows:</span></span>

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

<span data-ttu-id="6875d-121">**CmdletName** 和 **ParameterName** 值中允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6875d-121">Wildcard characters are permitted in the **CmdletName** and **ParameterName** values.</span></span>

<span data-ttu-id="6875d-122">若要設定、變更、新增或移除中的特定索引 **鍵/值** 組 `$PSDefaultParameterValues` ，請使用方法來編輯標準雜湊表。</span><span class="sxs-lookup"><span data-stu-id="6875d-122">To set, change, add, or remove a specific **Key/Value** pair from `$PSDefaultParameterValues`, use the methods to edit a standard hash table.</span></span> <span data-ttu-id="6875d-123">例如， **新增** 和 **移除** 方法。</span><span class="sxs-lookup"><span data-stu-id="6875d-123">For example, the **Add** and **Remove** methods.</span></span> <span data-ttu-id="6875d-124">這些方法不會覆寫雜湊表中的其他值。</span><span class="sxs-lookup"><span data-stu-id="6875d-124">These methods don't overwrite other values in the hash table.</span></span>

<span data-ttu-id="6875d-125">還有另一個不會覆寫現有 `$PSDefaultParameterValues` 雜湊表的語法。</span><span class="sxs-lookup"><span data-stu-id="6875d-125">There's another syntax that doesn't overwrite an existing `$PSDefaultParameterValues` hash table.</span></span> <span data-ttu-id="6875d-126">若要新增或變更特定的索引 **鍵/值** 組，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6875d-126">To add or change a specific **Key/Value** pair, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="6875d-127">**CmdletName** 必須是 Cmdlet 的名稱或使用 **CmdletBinding** 屬性之 advanced 函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6875d-127">The **CmdletName** must be the name of a cmdlet or the name of an advanced function that uses the **CmdletBinding** attribute.</span></span> <span data-ttu-id="6875d-128">您無法使用 `$PSDefaultParameterValues` 來指定腳本或簡單函數的預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-128">You can't use `$PSDefaultParameterValues` to specify default values for scripts or simple functions.</span></span>

<span data-ttu-id="6875d-129">**DefaultValue** 可以是物件或腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="6875d-129">The **DefaultValue** can be an object or a script block.</span></span> <span data-ttu-id="6875d-130">如果此值為腳本區塊，則 PowerShell 會評估腳本區塊，並使用結果做為參數值。</span><span class="sxs-lookup"><span data-stu-id="6875d-130">If the value is a script block, PowerShell evaluates the script block and uses the result as the parameter value.</span></span> <span data-ttu-id="6875d-131">當指定的參數接受腳本區塊值時，請將腳本區塊值括在第二組大括弧中，例如：</span><span class="sxs-lookup"><span data-stu-id="6875d-131">When the specified parameter accepts a script block value, enclose the script block value in a second set of braces, such as:</span></span>

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

<span data-ttu-id="6875d-132">如需詳細資訊，請參閱下列文件：</span><span class="sxs-lookup"><span data-stu-id="6875d-132">For more information, see the following documents:</span></span>

- [<span data-ttu-id="6875d-133">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="6875d-133">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="6875d-134">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="6875d-134">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="6875d-135">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="6875d-135">about_Preference_Variables</span></span>](about_Preference_Variables.md)

## <a name="examples"></a><span data-ttu-id="6875d-136">範例</span><span class="sxs-lookup"><span data-stu-id="6875d-136">Examples</span></span>

### <a name="how-to-set-psdefaultparametervalues"></a><span data-ttu-id="6875d-137">如何設定 \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="6875d-137">How to set \$PSDefaultParameterValues</span></span>

<span data-ttu-id="6875d-138">`$PSDefaultParameterValues` 是喜好設定變數，所以它只存在於設定的會話中。</span><span class="sxs-lookup"><span data-stu-id="6875d-138">`$PSDefaultParameterValues` is a preference variable, so it exists only in the session in which it's set.</span></span> <span data-ttu-id="6875d-139">它沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-139">It has no default value.</span></span>

<span data-ttu-id="6875d-140">若要設定 `$PSDefaultParameterValues` ，請輸入變數名稱和一或多個索引 **鍵/值** 組。</span><span class="sxs-lookup"><span data-stu-id="6875d-140">To set `$PSDefaultParameterValues`, type the variable name and one or more **Key/Value** pairs.</span></span> <span data-ttu-id="6875d-141">如果您執行另一個 `$PSDefaultParameterValues` 命令，則會覆寫現有的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="6875d-141">If you run another `$PSDefaultParameterValues` command, it overwrites the existing hash table.</span></span>

<span data-ttu-id="6875d-142">如需有關如何在不覆寫現有雜湊表值的情況下變更索引 **鍵/值** 組的範例，請參閱 [如何將值加入至 \$ PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) 或 [如何變更 \$ PSDefaultParameterValues 中的值](#how-to-change-values-in-psdefaultparametervalues)。</span><span class="sxs-lookup"><span data-stu-id="6875d-142">For examples about how to change **Key/Value** pairs without overwriting existing hash table values, see [How to add values to \$PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) or [How to change values in \$PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).</span></span>

<span data-ttu-id="6875d-143">若要儲存 `$PSDefaultParameterValues` 未來的會話，請將 `$PSDefaultParameterValues` 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="6875d-143">To save `$PSDefaultParameterValues` for future sessions, add a `$PSDefaultParameterValues` command to your PowerShell profile.</span></span> <span data-ttu-id="6875d-144">如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="6875d-144">For more information, see [about_Profiles](about_Profiles.md).</span></span>

#### <a name="set-a-custom-default-value"></a><span data-ttu-id="6875d-145">設定自訂預設值</span><span class="sxs-lookup"><span data-stu-id="6875d-145">Set a custom default value</span></span>

<span data-ttu-id="6875d-146">索引 **鍵/值** 組會將索引 `Send-MailMessage:SmtpServer` 鍵設定為自訂預設值 **Server123** 。</span><span class="sxs-lookup"><span data-stu-id="6875d-146">The **Key/Value** pair sets the `Send-MailMessage:SmtpServer` key to a custom default value of **Server123** .</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a><span data-ttu-id="6875d-147">設定多個參數的預設值</span><span class="sxs-lookup"><span data-stu-id="6875d-147">Set default values for multiple parameters</span></span>

<span data-ttu-id="6875d-148">若要設定多個參數的預設值，請以分號分隔每個索引 **鍵/值** 組 (`;`) 。</span><span class="sxs-lookup"><span data-stu-id="6875d-148">To set default values for multiple parameters, separate each **Key/Value** pair with a semicolon (`;`).</span></span> <span data-ttu-id="6875d-149">`Send-MailMessage:SmtpServer`和索引 `Get-WinEvent:LogName` 鍵會設定為自訂的預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-149">The `Send-MailMessage:SmtpServer` and `Get-WinEvent:LogName` keys are set to custom default values.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a><span data-ttu-id="6875d-150">使用萬用字元和切換參數</span><span class="sxs-lookup"><span data-stu-id="6875d-150">Use wildcards and switch parameters</span></span>

<span data-ttu-id="6875d-151">Cmdlet 和參數名稱可以包含萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6875d-151">The cmdlet and parameter names can contain wildcard characters.</span></span> <span data-ttu-id="6875d-152">使用 `$True` 和 `$False` 來設定切換參數的值，例如 **Verbose** 。</span><span class="sxs-lookup"><span data-stu-id="6875d-152">Use `$True` and `$False` to set values for switch parameters, such as **Verbose** .</span></span> <span data-ttu-id="6875d-153">一般參數的 **Verbose** 參數會 `$True` 針對所有命令設定為。</span><span class="sxs-lookup"><span data-stu-id="6875d-153">The common parameter's **Verbose** parameter is set to `$True` for all commands.</span></span>

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a><span data-ttu-id="6875d-154">使用預設值的陣列</span><span class="sxs-lookup"><span data-stu-id="6875d-154">Use an array for the default value</span></span>

<span data-ttu-id="6875d-155">如果參數可以接受多個值（陣列），您可以將多個值設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-155">If a parameter can accept multiple values, an array, you can set multiple values as the default values.</span></span> <span data-ttu-id="6875d-156">索引鍵的預設值 `Invoke-Command:ComputerName` 會設定為數組值 **Server01** 和 **Server02** 。</span><span class="sxs-lookup"><span data-stu-id="6875d-156">The default value of the `Invoke-Command:ComputerName` key is set to an array value of **Server01** and **Server02** .</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a><span data-ttu-id="6875d-157">使用腳本區塊</span><span class="sxs-lookup"><span data-stu-id="6875d-157">Use a script block</span></span>

<span data-ttu-id="6875d-158">您可以使用腳本區塊，在不同的條件下為參數指定不同的預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-158">You can use a script block to specify different default values for a parameter under different conditions.</span></span> <span data-ttu-id="6875d-159">PowerShell 會評估腳本區塊，並使用結果作為預設參數值。</span><span class="sxs-lookup"><span data-stu-id="6875d-159">PowerShell evaluates the script block and uses the result as the default parameter value.</span></span>

<span data-ttu-id="6875d-160">將 `Format-Table:AutoSize` 參數切換為預設值 **True** 的索引鍵集。</span><span class="sxs-lookup"><span data-stu-id="6875d-160">The `Format-Table:AutoSize` key sets that switch parameter to a default value of **True** .</span></span> <span data-ttu-id="6875d-161">`If`語句包含 `$host.Name` 必須是 PowerShell 主控台 **ConsoleHost** 的條件。</span><span class="sxs-lookup"><span data-stu-id="6875d-161">The `If` statement contains a condition that the `$host.Name` must be the PowerShell console, **ConsoleHost** .</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

<span data-ttu-id="6875d-162">如果參數接受腳本區塊值，請將腳本區塊括在一組額外的大括弧中。</span><span class="sxs-lookup"><span data-stu-id="6875d-162">If a parameter accepts a script block value, enclose the script block in an extra set of braces.</span></span> <span data-ttu-id="6875d-163">當 PowerShell 評估外部腳本區塊時，結果會是內部腳本區塊，並且會設定為預設參數值。</span><span class="sxs-lookup"><span data-stu-id="6875d-163">When PowerShell evaluates the outer script block, the result is the inner script block, and that is set as the default parameter value.</span></span>

<span data-ttu-id="6875d-164">`Invoke-Command:ScriptBlock`因為腳本區塊是以第二組大括弧括住，所以索引鍵會設定為 **系統事件記錄** 檔的預設值。</span><span class="sxs-lookup"><span data-stu-id="6875d-164">The `Invoke-Command:ScriptBlock` key set to a default value of the **System event log** because the script block is enclosed in a second set of braces.</span></span> <span data-ttu-id="6875d-165">腳本區塊的結果會傳遞至 `Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6875d-165">The result of the script block is passed to the `Invoke-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a><span data-ttu-id="6875d-166">如何取得 \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="6875d-166">How to get \$PSDefaultParameterValues</span></span>

<span data-ttu-id="6875d-167">在 PowerShell 提示字元中輸入，即可顯示雜湊資料表值 `$PSDefaultParameterValues` 。</span><span class="sxs-lookup"><span data-stu-id="6875d-167">The hash table values are displayed by entering `$PSDefaultParameterValues` at the PowerShell prompt.</span></span>

<span data-ttu-id="6875d-168">`$PSDefaultParameterValues`雜湊表會以三個索引 **鍵/值** 組來設定。</span><span class="sxs-lookup"><span data-stu-id="6875d-168">A `$PSDefaultParameterValues` hash table is set with three **Key/Value** pairs.</span></span>
<span data-ttu-id="6875d-169">下列範例會使用此雜湊表，說明如何從加入、變更和移除值 `$PSDefaultParameterValues` 。</span><span class="sxs-lookup"><span data-stu-id="6875d-169">This hash table is used in the following examples that describe how to add, change, and remove values from `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

<span data-ttu-id="6875d-170">若要取得特定索引鍵的值 `CmdletName:ParameterName` ，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6875d-170">To get the value of a specific `CmdletName:ParameterName` key, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

<span data-ttu-id="6875d-171">例如，取得索引鍵的值 `Send-MailMessage:SmtpServer` 。</span><span class="sxs-lookup"><span data-stu-id="6875d-171">For example, to get the value for the `Send-MailMessage:SmtpServer` key.</span></span>

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a><span data-ttu-id="6875d-172">如何將值新增至 \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="6875d-172">How to add values to \$PSDefaultParameterValues</span></span>

<span data-ttu-id="6875d-173">若要將值加入至 `$PSDefaultParameterValues` ，請使用 **add** 方法。</span><span class="sxs-lookup"><span data-stu-id="6875d-173">To add a value to `$PSDefaultParameterValues`, use the **Add** method.</span></span> <span data-ttu-id="6875d-174">加入值並不會影響雜湊表的現有值。</span><span class="sxs-lookup"><span data-stu-id="6875d-174">Adding a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="6875d-175">使用逗號 (`,`) ，將索引 **鍵** 與 **值** 分隔開來。</span><span class="sxs-lookup"><span data-stu-id="6875d-175">Use a comma (`,`) to separate the **Key** from the **Value** .</span></span> <span data-ttu-id="6875d-176">下列語法顯示如何使用的 **Add** 方法 `$PSDefaultParameterValues` 。</span><span class="sxs-lookup"><span data-stu-id="6875d-176">The following syntax shows how to use the **Add** method for `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

<span data-ttu-id="6875d-177">先前範例中建立的雜湊表會以新的索引 **鍵/值** 組進行更新。</span><span class="sxs-lookup"><span data-stu-id="6875d-177">The hash table created in the prior example is updated with a new **Key/Value** pair.</span></span> <span data-ttu-id="6875d-178">**Add** 方法會將 `Get-Process:Name` 金鑰設定為 **PowerShell** 的值。</span><span class="sxs-lookup"><span data-stu-id="6875d-178">The **Add** method sets the `Get-Process:Name` key to the value **PowerShell** .</span></span>

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

<span data-ttu-id="6875d-179">下列語法會完成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="6875d-179">The following syntax accomplishes the same result.</span></span>

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

<span data-ttu-id="6875d-180">`$PSDefaultParameterValues`變數會顯示更新的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="6875d-180">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="6875d-181">`Get-Process:Name`已新增金鑰。</span><span class="sxs-lookup"><span data-stu-id="6875d-181">The `Get-Process:Name` key was added.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a><span data-ttu-id="6875d-182">如何從 PSDefaultParameterValues 中移除值 \$</span><span class="sxs-lookup"><span data-stu-id="6875d-182">How to remove values from \$PSDefaultParameterValues</span></span>

<span data-ttu-id="6875d-183">若要從移除值 `$PSDefaultParameterValues` ，請使用雜湊表的 **移除** 方法。</span><span class="sxs-lookup"><span data-stu-id="6875d-183">To remove a value from `$PSDefaultParameterValues`, use the **Remove** method of hash tables.</span></span> <span data-ttu-id="6875d-184">移除值並不會影響雜湊表的現有值。</span><span class="sxs-lookup"><span data-stu-id="6875d-184">Removing a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="6875d-185">下列語法示範如何在上使用 **Remove** 方法 `$PSDefaultParameterValues` 。</span><span class="sxs-lookup"><span data-stu-id="6875d-185">The following syntax shows how to use the **Remove** method on `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

<span data-ttu-id="6875d-186">在此範例中，會更新在先前範例中建立的雜湊表，以移除索引 **鍵/值** 組。</span><span class="sxs-lookup"><span data-stu-id="6875d-186">In this example, the hash table created in the prior example is updated to remove a **Key/Value** pair.</span></span> <span data-ttu-id="6875d-187">**Remove** 方法會移除索引 `Get-Process:Name` 鍵。</span><span class="sxs-lookup"><span data-stu-id="6875d-187">The **Remove** method removes the `Get-Process:Name` key.</span></span>

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

<span data-ttu-id="6875d-188">`$PSDefaultParameterValues`變數會顯示更新的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="6875d-188">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="6875d-189">已 `Get-Process:Name` 移除索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6875d-189">The `Get-Process:Name` key was removed.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a><span data-ttu-id="6875d-190">如何變更 PSDefaultParameterValues 中的值 \$</span><span class="sxs-lookup"><span data-stu-id="6875d-190">How to change values in \$PSDefaultParameterValues</span></span>

<span data-ttu-id="6875d-191">對特定值所做的變更不會影響現有的雜湊資料表值。</span><span class="sxs-lookup"><span data-stu-id="6875d-191">Changes to a specific value don't affect existing hash table values.</span></span> <span data-ttu-id="6875d-192">若要變更中的特定索引 **鍵/值** 組 `$PSDefaultParameterValues` ，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6875d-192">To change a specific **Key/Value** pair in `$PSDefaultParameterValues`, use the following syntax:</span></span>

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="6875d-193">在此範例中，會更新在先前範例中建立的雜湊表來變更索引 **鍵/值** 組。</span><span class="sxs-lookup"><span data-stu-id="6875d-193">In this example, the hash table created in the prior example is updated to change a **Key/Value** pair.</span></span> <span data-ttu-id="6875d-194">下列命令會將機 `Send-MailMessage:SmtpServer` 碼變更為 **ServerXYZ** 的新值。</span><span class="sxs-lookup"><span data-stu-id="6875d-194">The following command changes the `Send-MailMessage:SmtpServer` key to a new value of **ServerXYZ** .</span></span>

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

<span data-ttu-id="6875d-195">`$PSDefaultParameterValues`變數會顯示更新的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="6875d-195">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="6875d-196">`Send-MailMessage:SmtpServer`金鑰已變更為新的值。</span><span class="sxs-lookup"><span data-stu-id="6875d-196">The `Send-MailMessage:SmtpServer` key was changed to a new value.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a><span data-ttu-id="6875d-197">如何停用和重新啟用 \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="6875d-197">How to disable and re-enable \$PSDefaultParameterValues</span></span>

<span data-ttu-id="6875d-198">您可以暫時停用再重新啟用 `$PSDefaultParameterValues` 。</span><span class="sxs-lookup"><span data-stu-id="6875d-198">You can temporarily disable and then re-enable `$PSDefaultParameterValues`.</span></span>
<span data-ttu-id="6875d-199">`$PSDefaultParameterValues`如果您執行的腳本需要不同的預設參數值，則停用會很有用。</span><span class="sxs-lookup"><span data-stu-id="6875d-199">Disabling `$PSDefaultParameterValues` is useful if you're running scripts that need different default parameter values.</span></span>

<span data-ttu-id="6875d-200">若要停 `$PSDefaultParameterValues` 用，請新增 `Disabled` 值為 **True** 的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6875d-200">To disable `$PSDefaultParameterValues`, add a key of `Disabled` with a value of **True** .</span></span> <span data-ttu-id="6875d-201">中的值 `$PSDefaultParameterValues` 會保持不變，但無效。</span><span class="sxs-lookup"><span data-stu-id="6875d-201">The values in `$PSDefaultParameterValues` are preserved, but aren't effective.</span></span>

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

<span data-ttu-id="6875d-202">下列語法會完成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="6875d-202">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

<span data-ttu-id="6875d-203">`$PSDefaultParameterValues`變數會以索引鍵的值顯示已更新的雜湊資料表 `Disabled` 。</span><span class="sxs-lookup"><span data-stu-id="6875d-203">The `$PSDefaultParameterValues` variable displays the updated hash table with the value for the `Disabled` key.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

<span data-ttu-id="6875d-204">若要重新啟用 `$PSDefaultParameterValues` ，請移除 **已停用** 的金鑰，或將 **停用** 的索引鍵值變更為 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="6875d-204">To re-enable `$PSDefaultParameterValues`, remove the **Disabled** key or change the value of the **Disabled** key to `$False`.</span></span> <span data-ttu-id="6875d-205">先前的值 `$PSDefaultParameterValues` 會再次生效。</span><span class="sxs-lookup"><span data-stu-id="6875d-205">The previous value of `$PSDefaultParameterValues` is effective again.</span></span>

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

<span data-ttu-id="6875d-206">下列語法會完成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="6875d-206">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

<span data-ttu-id="6875d-207">`$PSDefaultParameterValues`變數會顯示更新的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="6875d-207">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="6875d-208">使用 **Remove** 方法時， `Disabled` 會從輸出中移除索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6875d-208">When the **Remove** method is used, the `Disabled` key is removed from the output.</span></span>
<span data-ttu-id="6875d-209">如果替代語法是用來重新啟用的 `$PSDefaultParameterValues` ，則索引 `Disabled` 鍵會顯示為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="6875d-209">If the alternate syntax was used to re-enable `$PSDefaultParameterValues`, the `Disabled` key is displayed as **False** .</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a><span data-ttu-id="6875d-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6875d-210">See also</span></span>

[<span data-ttu-id="6875d-211">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6875d-211">about_CommonParameters</span></span>](https://go.microsoft.com/fwlink/?LinkID=113216)

[<span data-ttu-id="6875d-212">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="6875d-212">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="6875d-213">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="6875d-213">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="6875d-214">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="6875d-214">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="6875d-215">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="6875d-215">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="6875d-216">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="6875d-216">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="6875d-217">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="6875d-217">about_Script_Blocks</span></span>](about_Script_Blocks.md)
