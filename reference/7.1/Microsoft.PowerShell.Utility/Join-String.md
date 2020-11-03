---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: 8f4dc173ff95476c4e2cb91e24d30afdd8a31697
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202755"
---
# <span data-ttu-id="ef77e-102">Join-String</span><span class="sxs-lookup"><span data-stu-id="ef77e-102">Join-String</span></span>

## <span data-ttu-id="ef77e-103">概要</span><span class="sxs-lookup"><span data-stu-id="ef77e-103">SYNOPSIS</span></span>
<span data-ttu-id="ef77e-104">將管線中的物件合併成單一字串。</span><span class="sxs-lookup"><span data-stu-id="ef77e-104">Combines objects from the pipeline into a single string.</span></span>

## <span data-ttu-id="ef77e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ef77e-105">SYNTAX</span></span>

### <span data-ttu-id="ef77e-106">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="ef77e-106">Default (Default)</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### <span data-ttu-id="ef77e-107">SingleQuote</span><span class="sxs-lookup"><span data-stu-id="ef77e-107">SingleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="ef77e-108">DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="ef77e-108">DoubleQuote</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="ef77e-109">格式</span><span class="sxs-lookup"><span data-stu-id="ef77e-109">Format</span></span>

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="ef77e-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ef77e-110">DESCRIPTION</span></span>

<span data-ttu-id="ef77e-111">此 `Join-String` Cmdlet 會將管線物件中的文字聯結或合併成單一字串。</span><span class="sxs-lookup"><span data-stu-id="ef77e-111">The `Join-String` cmdlet joins, or combines, text from pipeline objects into a single string.</span></span>

<span data-ttu-id="ef77e-112">如果未指定任何參數，則會將管線物件轉換成字串，並使用預設分隔符號聯結 `$OFS` 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-112">If no parameters are specified, the pipeline objects are converted to a string and joined with the default separator `$OFS`.</span></span>

<span data-ttu-id="ef77e-113">藉由指定屬性名稱，屬性的值會轉換成字串，並加入字串。</span><span class="sxs-lookup"><span data-stu-id="ef77e-113">By specifying a property name, the property's value is converted to a string and joined into a string.</span></span>

<span data-ttu-id="ef77e-114">您可以使用腳本區塊，而不是屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ef77e-114">Instead of a property name, a script block can be used.</span></span> <span data-ttu-id="ef77e-115">腳本區塊的結果會在聯結之前轉換成字串，以形成結果。</span><span class="sxs-lookup"><span data-stu-id="ef77e-115">The script block's result is converted to a string before it's joined to form the result.</span></span> <span data-ttu-id="ef77e-116">它可以合併物件屬性的文字，或是轉換成字串的物件結果。</span><span class="sxs-lookup"><span data-stu-id="ef77e-116">It can either combine the text of an object's property or the result of the object that was converted to a string.</span></span>

<span data-ttu-id="ef77e-117">此 Cmdlet 是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="ef77e-117">This cmdlet was introduced in PowerShell 6.2.</span></span>

## <span data-ttu-id="ef77e-118">範例</span><span class="sxs-lookup"><span data-stu-id="ef77e-118">EXAMPLES</span></span>

### <span data-ttu-id="ef77e-119">範例1：聯結目錄名稱</span><span class="sxs-lookup"><span data-stu-id="ef77e-119">Example 1: Join directory names</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="ef77e-120">此範例會聯結目錄名稱、將輸出包裝在雙引號中，並以逗號和空格分隔目錄名稱 (`, `) 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-120">This example joins directory names, wraps the output in double-quotes, and separates the directory names with a comma and space (`, `).</span></span> <span data-ttu-id="ef77e-121">輸出是字串物件。</span><span class="sxs-lookup"><span data-stu-id="ef77e-121">The output is a string object.</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

<span data-ttu-id="ef77e-122">`Get-ChildItem` 使用 **Directory** 參數取得磁片磁碟機的所有目錄名稱 `C:\` 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-122">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="ef77e-123">物件會向下傳送到管線 `Join-String` 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-123">The objects are sent down the pipeline to `Join-String`.</span></span> <span data-ttu-id="ef77e-124">**Property** 參數會指定目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="ef77e-124">The **Property** parameter specifies the directory names.</span></span> <span data-ttu-id="ef77e-125">**DoubleQuote** 參數會以雙引號括住目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="ef77e-125">The **DoubleQuote** parameter wraps the directory names with double-quote marks.</span></span>
<span data-ttu-id="ef77e-126">**分隔符號** 參數指定使用逗號和空格 (`, `) 來分隔目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="ef77e-126">The **Separator** parameter specifies to use a comma and space (`, `) to separate the directory names.</span></span>

<span data-ttu-id="ef77e-127">這些 `Get-ChildItem` 物件是 **DirectoryInfo** ，並 `Join-String` 將物件轉換為 **system.string** 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-127">The `Get-ChildItem` objects are **System.IO.DirectoryInfo** and `Join-String` converts the objects to **System.String** .</span></span>

### <span data-ttu-id="ef77e-128">範例2：使用屬性子字串聯結目錄名稱</span><span class="sxs-lookup"><span data-stu-id="ef77e-128">Example 2: Use a property substring to join directory names</span></span>

<span data-ttu-id="ef77e-129">這個範例會使用 substring 方法來取得前四個字母的目錄名稱、以單引號括住輸出，然後以分號分隔目錄名稱 (`;`) 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-129">This example uses a substring method to get the first four letters of directory names, wraps the output in single-quotes, and separates the directory names with a semicolon (`;`).</span></span>

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

<span data-ttu-id="ef77e-130">`Get-ChildItem` 使用 **Directory** 參數取得磁片磁碟機的所有目錄名稱 `C:\` 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-130">`Get-ChildItem` uses the **Directory** parameter to get all the directory names for the `C:\` drive.</span></span>
<span data-ttu-id="ef77e-131">物件會向下傳送到管線 `Join-String` 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-131">The objects are sent down the pipeline to `Join-String`.</span></span>

<span data-ttu-id="ef77e-132">**屬性** 參數腳本區塊會使用自動變數 (`$_`) 來指定每個物件的 **名稱** 屬性子字串。</span><span class="sxs-lookup"><span data-stu-id="ef77e-132">The **Property** parameter script block uses automatic variable (`$_`) to specify each object's **Name** property substring.</span></span> <span data-ttu-id="ef77e-133">子字串會取得每個目錄名稱的前四個字母。</span><span class="sxs-lookup"><span data-stu-id="ef77e-133">The substring gets the first four letters of each directory name.</span></span> <span data-ttu-id="ef77e-134">子字串指定字元開始和結束位置。</span><span class="sxs-lookup"><span data-stu-id="ef77e-134">The substring specifies the character start and end positions.</span></span> <span data-ttu-id="ef77e-135">**SingleQuote** 參數會以單引號括住目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="ef77e-135">The **SingleQuote** parameter wraps the directory names with single-quote marks.</span></span> <span data-ttu-id="ef77e-136">**分隔符號** 參數指定使用分號 (`;`) 來分隔目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="ef77e-136">The **Separator** parameter specifies to use a semicolon (`;`) to separate the directory names.</span></span>

<span data-ttu-id="ef77e-137">如需自動變數和子字串的詳細資訊，請參閱 [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) 和 [Substring](/dotnet/api/system.string.substring)。</span><span class="sxs-lookup"><span data-stu-id="ef77e-137">For more information about automatic variables and substrings, see [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) and [Substring](/dotnet/api/system.string.substring).</span></span>

### <span data-ttu-id="ef77e-138">範例3：在個別行上顯示聯結輸出</span><span class="sxs-lookup"><span data-stu-id="ef77e-138">Example 3: Display join output on a separate line</span></span>

<span data-ttu-id="ef77e-139">此範例會在個別的行上將服務名稱與每個服務聯結，並以索引標籤進行縮排。</span><span class="sxs-lookup"><span data-stu-id="ef77e-139">This example joins service names with each service on a separate line and indented by a tab.</span></span>

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

<span data-ttu-id="ef77e-140">`Get-Service` 使用 **Name** 參數搭配來指定以開頭的服務 `se*` 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-140">`Get-Service` uses the **Name** parameter with to specify services that begin with `se*`.</span></span> <span data-ttu-id="ef77e-141">星號 (`*`) 是任何字元的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ef77e-141">The asterisk (`*`) is a wildcard for any character.</span></span>

<span data-ttu-id="ef77e-142">物件會向下傳送至 `Join-String` 使用 **Property** 參數來指定服務名稱的管線。</span><span class="sxs-lookup"><span data-stu-id="ef77e-142">The objects are sent down the pipeline to `Join-String` that uses the **Property** parameter to specify the service names.</span></span> <span data-ttu-id="ef77e-143">**分隔符號** 參數指定三個特殊字元，代表換行字元 (`` `r ``) 、新行 (`` `n ``) 和 tab (`` `t ``) 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-143">The **Separator** parameter specifies three special characters that represent a carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span> <span data-ttu-id="ef77e-144">**OutputPrefix** 會插入標籤 **服務：** 在輸出的第一行前面加上新行和索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ef77e-144">The **OutputPrefix** inserts a label **Services:** with a new line and tab before the first line of output.</span></span>

<span data-ttu-id="ef77e-145">如需特殊字元的詳細資訊，請參閱 [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)。</span><span class="sxs-lookup"><span data-stu-id="ef77e-145">For more information about special characters, see [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).</span></span>

### <span data-ttu-id="ef77e-146">範例4：從物件建立類別定義</span><span class="sxs-lookup"><span data-stu-id="ef77e-146">Example 4: Create a class definition from an object</span></span>

<span data-ttu-id="ef77e-147">此範例會使用現有的物件作為範本，以產生 PowerShell 類別定義。</span><span class="sxs-lookup"><span data-stu-id="ef77e-147">This example generates a PowerShell class definition using an existing object as a template.</span></span>

<span data-ttu-id="ef77e-148">這個程式碼範例會使用展開來縮減行長度，並提高可讀性。</span><span class="sxs-lookup"><span data-stu-id="ef77e-148">This code sample uses splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="ef77e-149">如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="ef77e-149">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## <span data-ttu-id="ef77e-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ef77e-150">PARAMETERS</span></span>

### <span data-ttu-id="ef77e-151">-DoubleQuote</span><span class="sxs-lookup"><span data-stu-id="ef77e-151">-DoubleQuote</span></span>

<span data-ttu-id="ef77e-152">以雙引號括住每個管線物件的字串值。</span><span class="sxs-lookup"><span data-stu-id="ef77e-152">Wraps the string value of each pipeline object in double-quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef77e-153">-格式格式</span><span class="sxs-lookup"><span data-stu-id="ef77e-153">-FormatString</span></span>

<span data-ttu-id="ef77e-154">格式字串，指定每個專案的格式化方式。</span><span class="sxs-lookup"><span data-stu-id="ef77e-154">A format string that specifies how each item should be formatted.</span></span>

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef77e-155">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ef77e-155">-InputObject</span></span>

<span data-ttu-id="ef77e-156">指定要加入的文字。</span><span class="sxs-lookup"><span data-stu-id="ef77e-156">Specifies the text to be joined.</span></span> <span data-ttu-id="ef77e-157">輸入包含文字的變數，或輸入可取得要加入字串之物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="ef77e-157">Enter a variable that contains the text, or type a command or expression that gets the objects to join into strings.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ef77e-158">-OutputPrefix</span><span class="sxs-lookup"><span data-stu-id="ef77e-158">-OutputPrefix</span></span>

<span data-ttu-id="ef77e-159">在輸出字串之前插入的文字。</span><span class="sxs-lookup"><span data-stu-id="ef77e-159">Text that's inserted before the output string.</span></span> <span data-ttu-id="ef77e-160">字串可以包含特殊字元，例如， `` `r `` 換行字元 () 、換行 (`` `n ``) 和 tab (`` `t ``) 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-160">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef77e-161">-OutputSuffix</span><span class="sxs-lookup"><span data-stu-id="ef77e-161">-OutputSuffix</span></span>

<span data-ttu-id="ef77e-162">附加至輸出字串的文字。</span><span class="sxs-lookup"><span data-stu-id="ef77e-162">Text that's appended to the output string.</span></span> <span data-ttu-id="ef77e-163">字串可以包含特殊字元，例如， `` `r `` 換行字元 () 、換行 (`` `n ``) 和 tab (`` `t ``) 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-163">The string can contain special characters such as carriage return (`` `r ``), newline (`` `n ``), and tab (`` `t ``).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef77e-164">-Property</span><span class="sxs-lookup"><span data-stu-id="ef77e-164">-Property</span></span>

<span data-ttu-id="ef77e-165">將管線物件投射為文字的屬性或屬性運算式的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef77e-165">The name of a property, or a property expression, that will project the pipeline object to text.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef77e-166">-Separator</span><span class="sxs-lookup"><span data-stu-id="ef77e-166">-Separator</span></span>

<span data-ttu-id="ef77e-167">在每個管線物件的文字之間插入的文字或字元，例如逗號或分號。</span><span class="sxs-lookup"><span data-stu-id="ef77e-167">Text or characters such as a comma or semicolon that's inserted between the text for each pipeline object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef77e-168">-SingleQuote</span><span class="sxs-lookup"><span data-stu-id="ef77e-168">-SingleQuote</span></span>

<span data-ttu-id="ef77e-169">以單引號括住每個管線物件的字串值。</span><span class="sxs-lookup"><span data-stu-id="ef77e-169">Wraps the string value of each pipeline object in single quotes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef77e-170">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="ef77e-170">-UseCulture</span></span>

<span data-ttu-id="ef77e-171">使用目前文化特性的清單分隔字元做為專案分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ef77e-171">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="ef77e-172">若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="ef77e-172">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="ef77e-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef77e-173">CommonParameters</span></span>

<span data-ttu-id="ef77e-174">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ef77e-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef77e-175">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ef77e-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef77e-176">輸入</span><span class="sxs-lookup"><span data-stu-id="ef77e-176">INPUTS</span></span>

### <span data-ttu-id="ef77e-177">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="ef77e-177">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="ef77e-178">輸出</span><span class="sxs-lookup"><span data-stu-id="ef77e-178">OUTPUTS</span></span>

### <span data-ttu-id="ef77e-179">System.String</span><span class="sxs-lookup"><span data-stu-id="ef77e-179">System.String</span></span>

## <span data-ttu-id="ef77e-180">注意</span><span class="sxs-lookup"><span data-stu-id="ef77e-180">NOTES</span></span>

## <span data-ttu-id="ef77e-181">相關連結</span><span class="sxs-lookup"><span data-stu-id="ef77e-181">RELATED LINKS</span></span>

[<span data-ttu-id="ef77e-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="ef77e-182">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="ef77e-183">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="ef77e-183">about_Special_Characters</span></span>](..//microsoft.powershell.core/about/about_special_characters.md)

[<span data-ttu-id="ef77e-184">子</span><span class="sxs-lookup"><span data-stu-id="ef77e-184">Substring</span></span>](/dotnet/api/system.string.substring)

