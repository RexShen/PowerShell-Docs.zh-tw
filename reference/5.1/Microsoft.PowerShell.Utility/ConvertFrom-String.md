---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206184"
---
# <span data-ttu-id="e1f45-103">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="e1f45-103">ConvertFrom-String</span></span>

## <span data-ttu-id="e1f45-104">概要</span><span class="sxs-lookup"><span data-stu-id="e1f45-104">SYNOPSIS</span></span>
<span data-ttu-id="e1f45-105">從字串內容中解壓縮和剖析結構化屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f45-105">Extracts and parses structured properties from string content.</span></span>

## <span data-ttu-id="e1f45-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1f45-106">SYNTAX</span></span>

### <span data-ttu-id="e1f45-107">ByDelimiter (預設) </span><span class="sxs-lookup"><span data-stu-id="e1f45-107">ByDelimiter (Default)</span></span>

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="e1f45-108">TemplateParsing</span><span class="sxs-lookup"><span data-stu-id="e1f45-108">TemplateParsing</span></span>

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="e1f45-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e1f45-109">DESCRIPTION</span></span>

<span data-ttu-id="e1f45-110">**Convertfrom-string-String** Cmdlet 會從字串內容中解壓縮和剖析結構化屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f45-110">The **ConvertFrom-String** cmdlet extracts and parses structured properties from string content.</span></span>
<span data-ttu-id="e1f45-111">此 Cmdlet 會藉由剖析傳統文字資料流程中的文字來產生物件。</span><span class="sxs-lookup"><span data-stu-id="e1f45-111">This cmdlet generates an object by parsing text from a traditional text stream.</span></span>
<span data-ttu-id="e1f45-112">針對管線中的每個字串，此 Cmdlet 會依分隔符號或剖析運算式來分割輸入，然後將屬性名稱指派給每個產生的分割元素。</span><span class="sxs-lookup"><span data-stu-id="e1f45-112">For each string in the pipeline, the cmdlet splits the input by either a delimiter or a parse expression, and then assigns property names to each of the resulting split elements.</span></span>
<span data-ttu-id="e1f45-113">您可以提供這些屬性名稱;如果不這麼做，系統會自動為您產生它們。</span><span class="sxs-lookup"><span data-stu-id="e1f45-113">You can provide these property names; if you do not, they are automatically generated for you.</span></span>

<span data-ttu-id="e1f45-114">Cmdlet 的預設參數集（ **ByDelimiter** ）會完全在正則運算式分隔符號上進行分割。</span><span class="sxs-lookup"><span data-stu-id="e1f45-114">The cmdlet's default parameter set, **ByDelimiter** , splits exactly on the regular expression delimiter.</span></span>
<span data-ttu-id="e1f45-115">當 Cmdlet 執行時，它不會執行引號比對或分隔符號的轉義 `Import-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-115">It does not perform quote matching or delimiter escaping as the `Import-Csv` cmdlet does.</span></span>

<span data-ttu-id="e1f45-116">Cmdlet 的替代參數集 **TemplateParsing** 會從正則運算式所捕捉的群組產生元素。</span><span class="sxs-lookup"><span data-stu-id="e1f45-116">The cmdlet's alternate parameter set, **TemplateParsing** , generates elements from the groups that are captured by a regular expression.</span></span> <span data-ttu-id="e1f45-117">如需正則運算式的詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="e1f45-117">For more information on regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

<span data-ttu-id="e1f45-118">這個 Cmdlet 支援兩種模式：基本分隔剖析和自動產生的範例驅動剖析。</span><span class="sxs-lookup"><span data-stu-id="e1f45-118">This cmdlet supports two modes: basic delimited parsing, and automatically-generated, example-driven parsing.</span></span>

<span data-ttu-id="e1f45-119">根據預設，分隔的剖析將輸入從空白字元位置分割，並將屬性名稱指派給產生的群組。</span><span class="sxs-lookup"><span data-stu-id="e1f45-119">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="e1f45-120">您可以使用管線將 `ConvertFrom-String` 結果傳送至其中一個 Cmdlet 來自訂分隔符號 `Format-*` ，也可以使用 **分隔符號** 參數。</span><span class="sxs-lookup"><span data-stu-id="e1f45-120">You can customize the delimiter by piping the `ConvertFrom-String` results into one of the `Format-*` cmdlets, or you can use the **Delimiter** parameter.</span></span>

<span data-ttu-id="e1f45-121">此 Cmdlet 也支援根據 [FlashExtract、Microsoft research 的研究工作](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/)，自動產生的範例驅動剖析。</span><span class="sxs-lookup"><span data-stu-id="e1f45-121">The cmdlet also supports automatically-generated, example-driven parsing based on the [FlashExtract, research work by Microsoft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).</span></span>

## <span data-ttu-id="e1f45-122">範例</span><span class="sxs-lookup"><span data-stu-id="e1f45-122">EXAMPLES</span></span>

### <span data-ttu-id="e1f45-123">範例1：產生具有預設屬性名稱的物件</span><span class="sxs-lookup"><span data-stu-id="e1f45-123">Example 1: Generate an object with default property names</span></span>

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

<span data-ttu-id="e1f45-124">此命令會產生具有預設屬性名稱 **P1** 和 **P2** 的物件。</span><span class="sxs-lookup"><span data-stu-id="e1f45-124">This command generates an object with default property names, **P1** and **P2** .</span></span>

### <span data-ttu-id="e1f45-125">範例1A：瞭解產生的物件</span><span class="sxs-lookup"><span data-stu-id="e1f45-125">Example 1A: Get to know the generated object</span></span>

<span data-ttu-id="e1f45-126">此命令會產生一個具有 **P1** 、 **P2** 、屬性的物件。根據預設，這兩個屬性都是 **字串** 類型。</span><span class="sxs-lookup"><span data-stu-id="e1f45-126">This command generates one object with properties **P1** , **P2** ; both properties are of **String** type, by default.</span></span>

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### <span data-ttu-id="e1f45-127">範例2：使用分隔符號產生具有預設屬性名稱的物件</span><span class="sxs-lookup"><span data-stu-id="e1f45-127">Example 2: Generate an object with default property names using a delimiter</span></span>

<span data-ttu-id="e1f45-128">此命令會使用反斜線 () 作為分隔符號，產生具有網域和使用者名稱的物件 `\` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-128">This command generates an object with a domain and username using the backslash (`\`) as the delimiter.</span></span> <span data-ttu-id="e1f45-129">使用正則運算式時，必須以另一個反斜線來換用反斜線字元。</span><span class="sxs-lookup"><span data-stu-id="e1f45-129">The backslash character must be escaped with another backslash when using regular expressions.</span></span>

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### <span data-ttu-id="e1f45-130">範例3：產生包含兩個命名屬性的物件</span><span class="sxs-lookup"><span data-stu-id="e1f45-130">Example 3: Generate an object that contains two named properties</span></span>

<span data-ttu-id="e1f45-131">下列範例會從 Windows 主機檔案專案建立物件。</span><span class="sxs-lookup"><span data-stu-id="e1f45-131">The following example creates objects from Windows hosts file entries.</span></span>

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

<span data-ttu-id="e1f45-132">Cmdlet 會將 `Get-Content` Windows 主機檔案的內容儲存在中 `$content` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-132">The `Get-Content` cmdlet stores the content of a Windows hosts file in `$content`.</span></span> <span data-ttu-id="e1f45-133">第二個命令會使用符合 () 開頭之任何一行的正則運算式，移除主機檔案開頭的任何批註 `#` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-133">The second command removes any comments at the beginning of the hosts file using a regular expression that matches any line that does not start with (`#`).</span></span> <span data-ttu-id="e1f45-134">最後一個命令會將剩餘的文字轉換成具有 **伺服器** 和 **IP** 屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="e1f45-134">The last command converts the remaining text into objects with **Server** and **IP** properties.</span></span>

### <span data-ttu-id="e1f45-135">範例4：使用運算式作為 TemplateContent 參數的值，將結果儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="e1f45-135">Example 4: Use an expression as the value of the TemplateContent parameter, save the results in a variable.</span></span>

<span data-ttu-id="e1f45-136">此命令會使用運算式做為 **TemplateContent** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="e1f45-136">This command uses an expression as the value of the **TemplateContent** parameter.</span></span>
<span data-ttu-id="e1f45-137">為了簡單起見，運算式會儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="e1f45-137">The expression is saved in a variable for simplicity.</span></span>
<span data-ttu-id="e1f45-138">Windows PowerShell 瞭解管線上所使用的字串 `ConvertFrom-String` 有三個屬性：</span><span class="sxs-lookup"><span data-stu-id="e1f45-138">Windows PowerShell understands now that the string that is used on the pipeline to `ConvertFrom-String` has three properties:</span></span>

- <span data-ttu-id="e1f45-139">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e1f45-139">**Name**</span></span>
- <span data-ttu-id="e1f45-140">**電話**</span><span class="sxs-lookup"><span data-stu-id="e1f45-140">**phone**</span></span>
- <span data-ttu-id="e1f45-141">**age**</span><span class="sxs-lookup"><span data-stu-id="e1f45-141">**age**</span></span>

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

<span data-ttu-id="e1f45-142">輸入中的每一行都是由樣本相符專案來評估。</span><span class="sxs-lookup"><span data-stu-id="e1f45-142">Each line in the input is evaluated by the sample matches.</span></span> <span data-ttu-id="e1f45-143">如果行符合模式中提供的範例，則會將值解壓縮並傳遞至輸出變數。</span><span class="sxs-lookup"><span data-stu-id="e1f45-143">If the line matches the examples given in the pattern, values are extracted and passed to the output variable.</span></span>

<span data-ttu-id="e1f45-144">範例資料 `$template` 提供兩種不同的電話格式：</span><span class="sxs-lookup"><span data-stu-id="e1f45-144">The sample data, `$template`, provides two different phone formats:</span></span>

- `425-123-6789`
- `(206) 987-4321`

<span data-ttu-id="e1f45-145">範例資料也提供兩種不同的年齡格式：</span><span class="sxs-lookup"><span data-stu-id="e1f45-145">The sample data also provides two different age formats:</span></span>

- `6`
- `12`

<span data-ttu-id="e1f45-146">這表示將無法辨識像這樣的電話 `(206) 987 4321` ，因為沒有任何符合該模式的範例資料，因為沒有連字號。</span><span class="sxs-lookup"><span data-stu-id="e1f45-146">This implies that phones like `(206) 987 4321` will not be recognized, because there's no sample data that matches that pattern because there are no hyphens.</span></span>

### <span data-ttu-id="e1f45-147">範例5：對產生的屬性指定資料類型</span><span class="sxs-lookup"><span data-stu-id="e1f45-147">Example 5: Specifying data types to the generated properties</span></span>

<span data-ttu-id="e1f45-148">這是上述範例4的相同範例。</span><span class="sxs-lookup"><span data-stu-id="e1f45-148">This is the same example as Example 4, above.</span></span>
<span data-ttu-id="e1f45-149">差別在於模式字串包含每個所需屬性的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e1f45-149">The difference is that the pattern string includes a data type for each desired property.</span></span>

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

<span data-ttu-id="e1f45-150">此 `Get-Member` Cmdlet 會用來顯示 **age** 屬性為整數。</span><span class="sxs-lookup"><span data-stu-id="e1f45-150">The `Get-Member` cmdlet is used to show that the **age** property is an integer.</span></span>

## <span data-ttu-id="e1f45-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1f45-151">PARAMETERS</span></span>

### <span data-ttu-id="e1f45-152">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="e1f45-152">-Delimiter</span></span>

<span data-ttu-id="e1f45-153">指定識別元素之間界限的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="e1f45-153">Specifies a regular expression that identifies the boundary between elements.</span></span>
<span data-ttu-id="e1f45-154">分割所建立的專案會成為所產生之物件中的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f45-154">Elements that are created by the split become properties in the resulting object.</span></span>
<span data-ttu-id="e1f45-155">分隔符號最後會用於呼叫類型的 **Split** 方法 `[System.Text.RegularExpressions.RegularExpression]` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-155">The delimiter is ultimately used in a call to the **Split** method of the type `[System.Text.RegularExpressions.RegularExpression]`.</span></span>

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f45-156">-IncludeExtent</span><span class="sxs-lookup"><span data-stu-id="e1f45-156">-IncludeExtent</span></span>

<span data-ttu-id="e1f45-157">指出此 Cmdlet 包含預設會移除的範圍文字屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f45-157">Indicates that this cmdlet includes an extent text property that is removed by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f45-158">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e1f45-158">-InputObject</span></span>

<span data-ttu-id="e1f45-159">指定從管線接收的字串，或包含字串物件的變數。</span><span class="sxs-lookup"><span data-stu-id="e1f45-159">Specifies strings received from the pipeline, or a variable that contains a string object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e1f45-160">-之 propertynames</span><span class="sxs-lookup"><span data-stu-id="e1f45-160">-PropertyNames</span></span>

<span data-ttu-id="e1f45-161">指定要在產生的物件中指派分割值之屬性名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1f45-161">Specifies an array of property names to which to assign split values in the resulting object.</span></span>
<span data-ttu-id="e1f45-162">您分割或剖析的每一行文字都會產生代表屬性值的元素。</span><span class="sxs-lookup"><span data-stu-id="e1f45-162">Every line of text that you split or parse generates elements that represent property values.</span></span>
<span data-ttu-id="e1f45-163">如果專案是 capture 群組的結果，而且該 capture 群組的名稱為 (例如 `(?<name>)` 或 `(?'name')` ) ，則該 capture 群組的名稱會指派給屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f45-163">If the element is the result of a capture group, and that capture group is named (for example, `(?<name>)` or `(?'name')` ), then the name of that capture group is assigned to the property.</span></span>

<span data-ttu-id="e1f45-164">如果您在 **PropertyName** 陣列中提供任何元素，這些名稱會指派給尚未命名的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f45-164">If you provide any elements in the **PropertyName** array, those names are assigned to properties that have not yet been named.</span></span>

<span data-ttu-id="e1f45-165">如果您提供的屬性名稱比欄位更多，則 PowerShell 會忽略額外的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e1f45-165">If you provide more property names than there are fields, PowerShell ignores the extra property names.</span></span> <span data-ttu-id="e1f45-166">如果您未指定足夠的屬性名稱來命名所有欄位，則 PowerShell 會自動將數值屬性名稱指派給任何未命名的屬性： **P1** 、 **P2** 等等。</span><span class="sxs-lookup"><span data-stu-id="e1f45-166">If you do not specify enough property names to name all fields, PowerShell automatically assigns numerical property names to any properties that are not named: **P1** , **P2** , etc.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f45-167">-TemplateContent</span><span class="sxs-lookup"><span data-stu-id="e1f45-167">-TemplateContent</span></span>

<span data-ttu-id="e1f45-168">指定運算式或儲存為變數的運算式，以描述此 Cmdlet 指派字串的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f45-168">Specifies an expression, or an expression saved as a variable, that describes the properties to which this cmdlet assigns strings.</span></span> <span data-ttu-id="e1f45-169">範本欄位規格的語法如下： `{[optional-typecast]<name>:<example-value>}` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-169">The syntax of a template field specification is the following: `{[optional-typecast]<name>:<example-value>}`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f45-170">-TemplateFile</span><span class="sxs-lookup"><span data-stu-id="e1f45-170">-TemplateFile</span></span>

<span data-ttu-id="e1f45-171">以陣列的形式指定檔案，其中包含所要剖析之字串的範本。</span><span class="sxs-lookup"><span data-stu-id="e1f45-171">Specifies a file, as an array, that contains a template for the desired parsing of the string.</span></span>
<span data-ttu-id="e1f45-172">在範本檔案中，屬性和其值會以括弧括住，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e1f45-172">In the template file, properties and their values are enclosed in brackets, as shown below.</span></span>
<span data-ttu-id="e1f45-173">如果屬性（例如 **Name** 屬性和其相關聯的其他屬性）出現多次，您可以 () 加入星號， `*` 表示這會產生多筆記錄。</span><span class="sxs-lookup"><span data-stu-id="e1f45-173">If a property, such as the **Name** property and its associated other properties, appears multiple times, you can add an asterisk (`*`) to indicate that this results in multiple records.</span></span> <span data-ttu-id="e1f45-174">這可避免將多個屬性解壓縮成單一記錄。</span><span class="sxs-lookup"><span data-stu-id="e1f45-174">This avoids extracting multiple properties into a single record.</span></span>

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f45-175">-UpdateTemplate</span><span class="sxs-lookup"><span data-stu-id="e1f45-175">-UpdateTemplate</span></span>

<span data-ttu-id="e1f45-176">指出此 Cmdlet 會將學習演算法的結果儲存到範本檔案中的批註。</span><span class="sxs-lookup"><span data-stu-id="e1f45-176">Indicates that this cmdlet saves the results of a learning algorithm into a comment in the template file.</span></span>
<span data-ttu-id="e1f45-177">這可讓演算法學習程式更快。</span><span class="sxs-lookup"><span data-stu-id="e1f45-177">This makes the algorithm learning process faster.</span></span>
<span data-ttu-id="e1f45-178">若要使用此參數，您也必須使用 **TemplateFile** 參數指定範本檔案。</span><span class="sxs-lookup"><span data-stu-id="e1f45-178">To use this parameter, you must also specify a template file with the **TemplateFile** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f45-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1f45-179">CommonParameters</span></span>

<span data-ttu-id="e1f45-180">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="e1f45-180">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="e1f45-181">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="e1f45-181">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e1f45-182">輸入</span><span class="sxs-lookup"><span data-stu-id="e1f45-182">INPUTS</span></span>

### <span data-ttu-id="e1f45-183">System.String</span><span class="sxs-lookup"><span data-stu-id="e1f45-183">System.String</span></span>

## <span data-ttu-id="e1f45-184">輸出</span><span class="sxs-lookup"><span data-stu-id="e1f45-184">OUTPUTS</span></span>

## <span data-ttu-id="e1f45-185">注意</span><span class="sxs-lookup"><span data-stu-id="e1f45-185">NOTES</span></span>

## <span data-ttu-id="e1f45-186">相關連結</span><span class="sxs-lookup"><span data-stu-id="e1f45-186">RELATED LINKS</span></span>

[<span data-ttu-id="e1f45-187">Convertfrom-string-字串：以範例為基礎的文字剖析</span><span class="sxs-lookup"><span data-stu-id="e1f45-187">ConvertFrom-String: Example-based text parsing</span></span>](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[<span data-ttu-id="e1f45-188">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="e1f45-188">ConvertFrom-StringData</span></span>](ConvertFrom-StringData.md)

[<span data-ttu-id="e1f45-189">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="e1f45-189">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="e1f45-190">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="e1f45-190">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)
