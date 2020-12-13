---
ms.date: 09/12/2016
ms.topic: reference
title: 如何新增語法至 Cmdlet 說明主題
description: 如何新增語法至 Cmdlet 說明主題
ms.openlocfilehash: bcc037d22051c162cd0f70702da17afe7ed9c01a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659070"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="72527-103">如何新增語法至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="72527-103">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="72527-104">在您開始撰寫 Cmdlet 說明檔中語法圖表的 XML 程式碼之前，請閱讀本節以清楚瞭解您需要提供的資料類型，例如參數屬性，以及該資料如何顯示在語法圖表中。</span><span class="sxs-lookup"><span data-stu-id="72527-104">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="72527-105">參數屬性</span><span class="sxs-lookup"><span data-stu-id="72527-105">Parameter Attributes</span></span>

- <span data-ttu-id="72527-106">必要</span><span class="sxs-lookup"><span data-stu-id="72527-106">Required</span></span>
  - <span data-ttu-id="72527-107">若為 true，則參數必須出現在所有使用參數集的命令中。</span><span class="sxs-lookup"><span data-stu-id="72527-107">If true, the parameter must appear in all commands that use the parameter set.</span></span>
  - <span data-ttu-id="72527-108">如果為 false，則參數在使用參數集的所有命令中都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="72527-108">If false, the parameter is optional in all commands that use the parameter set.</span></span>
- <span data-ttu-id="72527-109">位置</span><span class="sxs-lookup"><span data-stu-id="72527-109">Position</span></span>
  - <span data-ttu-id="72527-110">如果已命名，則需要參數名稱。</span><span class="sxs-lookup"><span data-stu-id="72527-110">If named, the parameter name is required.</span></span>
  - <span data-ttu-id="72527-111">如果是位置，則參數名稱為選擇性。</span><span class="sxs-lookup"><span data-stu-id="72527-111">If positional, the parameter name is optional.</span></span> <span data-ttu-id="72527-112">當省略時，參數值必須在命令中的指定位置。</span><span class="sxs-lookup"><span data-stu-id="72527-112">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="72527-113">例如，如果值為 position = "1"，則參數值必須是命令中的第一個或唯一未命名的參數值。</span><span class="sxs-lookup"><span data-stu-id="72527-113">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>
- <span data-ttu-id="72527-114">管線輸入</span><span class="sxs-lookup"><span data-stu-id="72527-114">Pipeline Input</span></span>
  - <span data-ttu-id="72527-115">如果為 true (ByValue) ，您可以透過管線將輸入傳送至參數。</span><span class="sxs-lookup"><span data-stu-id="72527-115">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="72527-116">輸入與 ( 「系結至」 ) 參數相關聯，即使屬性名稱和物件類型不符合預期的類型也是一樣。</span><span class="sxs-lookup"><span data-stu-id="72527-116">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span>
    <span data-ttu-id="72527-117">PowerShell 參數系結元件會嘗試將輸入轉換成正確的類型，而且只有在無法轉換類型時，才會使命令失效。</span><span class="sxs-lookup"><span data-stu-id="72527-117">The PowerShell parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="72527-118">參數集中只能有一個參數以傳值方式來建立關聯。</span><span class="sxs-lookup"><span data-stu-id="72527-118">Only one parameter in a parameter set can be associated by value.</span></span>
  - <span data-ttu-id="72527-119">如果為 true (ByPropertyName) ，您可以透過管線將輸入傳送至參數。</span><span class="sxs-lookup"><span data-stu-id="72527-119">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="72527-120">不過，只有當參數名稱符合輸入物件的屬性名稱時，輸入才會與參數建立關聯。</span><span class="sxs-lookup"><span data-stu-id="72527-120">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="72527-121">例如，如果參數名稱為，則 `Path` 只有當物件具有名為 path 的屬性時，才會將傳送至 Cmdlet 的物件與該參數產生關聯。</span><span class="sxs-lookup"><span data-stu-id="72527-121">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>
  - <span data-ttu-id="72527-122">如果為 true (ByValue，ByPropertyName) ，您可以透過屬性名稱或依值將輸入輸送至參數。</span><span class="sxs-lookup"><span data-stu-id="72527-122">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="72527-123">參數集中只能有一個參數以傳值方式來建立關聯。</span><span class="sxs-lookup"><span data-stu-id="72527-123">Only one parameter in a parameter set can be associated by value.</span></span>
  - <span data-ttu-id="72527-124">如果為 false，則無法將輸入傳送至此參數。</span><span class="sxs-lookup"><span data-stu-id="72527-124">If false, you cannot pipe input to this parameter.</span></span>
- <span data-ttu-id="72527-125">萬用字元</span><span class="sxs-lookup"><span data-stu-id="72527-125">Globbing</span></span>
  - <span data-ttu-id="72527-126">若為 true，使用者為參數值輸入的文字可以包含萬用字元。</span><span class="sxs-lookup"><span data-stu-id="72527-126">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>
  - <span data-ttu-id="72527-127">如果為 false，則表示使用者為參數值輸入的文字不能包含萬用字元。</span><span class="sxs-lookup"><span data-stu-id="72527-127">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="72527-128">參數值屬性</span><span class="sxs-lookup"><span data-stu-id="72527-128">Parameter Value Attributes</span></span>

- <span data-ttu-id="72527-129">必要</span><span class="sxs-lookup"><span data-stu-id="72527-129">Required</span></span>
  - <span data-ttu-id="72527-130">若為 true，則在命令中使用參數時，必須使用指定的值。</span><span class="sxs-lookup"><span data-stu-id="72527-130">If true, the specified value must be used whenever using the parameter in a command.</span></span>
  - <span data-ttu-id="72527-131">如果為 false，則參數值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="72527-131">If false, the parameter value is optional.</span></span> <span data-ttu-id="72527-132">一般來說，只有當值是參數的數個有效值之一時（例如在列舉型別中），值才是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="72527-132">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="72527-133">參數值的 **必要** 屬性與參數的 **必要** 屬性不同。</span><span class="sxs-lookup"><span data-stu-id="72527-133">The **Required** attribute of a parameter value is different from the **Required** attribute of a parameter.</span></span>

<span data-ttu-id="72527-134">參數的必要屬性會指出叫用 Cmdlet 時，是否必須包含參數 (和其值) 。</span><span class="sxs-lookup"><span data-stu-id="72527-134">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="72527-135">相反地，只有當命令中包含參數時，才會使用參數值的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="72527-135">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="72527-136">它會指出該特定值是否必須與參數搭配使用。</span><span class="sxs-lookup"><span data-stu-id="72527-136">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="72527-137">通常，需要預留位置的參數值和不需要常值的參數值，因為這些值是可能與參數搭配使用的數個值之一。</span><span class="sxs-lookup"><span data-stu-id="72527-137">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="72527-138">正在搜集語法資訊</span><span class="sxs-lookup"><span data-stu-id="72527-138">Gathering Syntax Information</span></span>

1. <span data-ttu-id="72527-139">從 Cmdlet 名稱開始。</span><span class="sxs-lookup"><span data-stu-id="72527-139">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

1. <span data-ttu-id="72527-140">列出 Cmdlet 的所有參數。</span><span class="sxs-lookup"><span data-stu-id="72527-140">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="72527-141">輸入連字號 (`-`)  (ASCII 45) 在每個參數名稱之前。</span><span class="sxs-lookup"><span data-stu-id="72527-141">Type a hyphen (`-`) (ASCII 45) before each parameter name.</span></span>
   <span data-ttu-id="72527-142">將參數分隔為參數集 (某些 Cmdlet 只能有一個參數集) 。</span><span class="sxs-lookup"><span data-stu-id="72527-142">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="72527-143">在此範例中，Get-Tech Cmdlet 有兩個參數集。</span><span class="sxs-lookup"><span data-stu-id="72527-143">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="72527-144">使用 Cmdlet 名稱啟動每個參數集。</span><span class="sxs-lookup"><span data-stu-id="72527-144">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="72527-145">先列出預設參數集。</span><span class="sxs-lookup"><span data-stu-id="72527-145">List the default parameter set first.</span></span> <span data-ttu-id="72527-146">預設參數是由 Cmdlet 類別指定。</span><span class="sxs-lookup"><span data-stu-id="72527-146">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="72527-147">針對每個參數集，先列出其唯一參數，除非有必須先出現的位置參數。</span><span class="sxs-lookup"><span data-stu-id="72527-147">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="72527-148">在上述範例中，Name 和 ID 參數是兩個參數集的唯一參數 (每個參數集都必須有一個對該參數集) 唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="72527-148">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="72527-149">這可讓使用者更輕鬆地識別需要為參數集提供的參數。</span><span class="sxs-lookup"><span data-stu-id="72527-149">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="72527-150">依命令出現的順序列出參數。</span><span class="sxs-lookup"><span data-stu-id="72527-150">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="72527-151">如果順序不重要，請將相關參數一起列出，或先列出最常使用的參數。</span><span class="sxs-lookup"><span data-stu-id="72527-151">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="72527-152">如果 Cmdlet 支援 ShouldProcess，請務必列出 WhatIf 和 Confirm 參數。</span><span class="sxs-lookup"><span data-stu-id="72527-152">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="72527-153">請勿在您的語法圖表中列出 (的一般參數，例如 Verbose、Debug 和 ErrorAction) 。</span><span class="sxs-lookup"><span data-stu-id="72527-153">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="72527-154">`Get-Help`當您顯示說明主題時，此 Cmdlet 會為您新增該資訊。</span><span class="sxs-lookup"><span data-stu-id="72527-154">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

1. <span data-ttu-id="72527-155">新增參數值。</span><span class="sxs-lookup"><span data-stu-id="72527-155">Add the parameter values.</span></span> <span data-ttu-id="72527-156">在 PowerShell 中，參數值會以其 .NET 類型表示。</span><span class="sxs-lookup"><span data-stu-id="72527-156">In PowerShell, parameter values are represented by their .NET type.</span></span>
   <span data-ttu-id="72527-157">不過，類型名稱可以縮寫，例如 system.string 的 "string"。</span><span class="sxs-lookup"><span data-stu-id="72527-157">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="72527-158">縮寫類型，只要其意義很清楚，例如 system.string 的 **字串** 和 int 的 **int** **。**</span><span class="sxs-lookup"><span data-stu-id="72527-158">Abbreviate types as long as their meaning is clear, such as **string** for **System.String** and **int** for **System.Int32**.</span></span>

   <span data-ttu-id="72527-159">列出列舉的所有值，例如 `-type` 上一個範例中的參數，可以設定為 **basic** 或 **advanced**。</span><span class="sxs-lookup"><span data-stu-id="72527-159">List all values of enumerations, such as the `-type` parameter in the previous example, which can be set to **basic** or **advanced**.</span></span>

   <span data-ttu-id="72527-160">切換參數（例如 `-list` 在先前的範例中）沒有值。</span><span class="sxs-lookup"><span data-stu-id="72527-160">Switch parameters, such as `-list` in the previous example, do not have values.</span></span>

1. <span data-ttu-id="72527-161">在與常值參數值相較之下，將角括弧加入為預留位置的參數值。</span><span class="sxs-lookup"><span data-stu-id="72527-161">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

1. <span data-ttu-id="72527-162">以方括弧括住選擇性參數及其數值。</span><span class="sxs-lookup"><span data-stu-id="72527-162">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. <span data-ttu-id="72527-163">以方括弧括住) 位置參數的選擇性參數名稱 (。</span><span class="sxs-lookup"><span data-stu-id="72527-163">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="72527-164">在命令中不需要包含位置的參數名稱，例如下列範例中的 Name 參數。</span><span class="sxs-lookup"><span data-stu-id="72527-164">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. <span data-ttu-id="72527-165">如果參數值可以包含多個值，例如 Name 參數中的名稱清單，請在參數值後面加上一對方括弧。</span><span class="sxs-lookup"><span data-stu-id="72527-165">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

1. <span data-ttu-id="72527-166">如果使用者可以從參數或參數值（例如類型參數）中選擇，請以大括弧括住這些選項，並使用排除符號或符號 (; ) 。</span><span class="sxs-lookup"><span data-stu-id="72527-166">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

1. <span data-ttu-id="72527-167">如果參數值必須使用特定的格式，例如引號或括弧，請在語法中顯示格式。</span><span class="sxs-lookup"><span data-stu-id="72527-167">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="72527-168">撰寫語法圖表 XML 程式碼</span><span class="sxs-lookup"><span data-stu-id="72527-168">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="72527-169">XML 的語法節點會緊接在描述節點之後，以 `</maml:description>` 標記結尾。</span><span class="sxs-lookup"><span data-stu-id="72527-169">The syntax node of the XML begins immediately after the description node, which ends with the `</maml:description>` tag.</span></span> <span data-ttu-id="72527-170">如需有關收集語法圖表中所使用之資料的詳細資訊，請參閱 [收集語法資訊](#gathering-syntax-information)。</span><span class="sxs-lookup"><span data-stu-id="72527-170">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="72527-171">新增語法節點</span><span class="sxs-lookup"><span data-stu-id="72527-171">Adding a Syntax Node</span></span>

<span data-ttu-id="72527-172">Cmdlet 說明主題中顯示的語法圖表是從 XML 的語法節點中的資料所產生。</span><span class="sxs-lookup"><span data-stu-id="72527-172">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="72527-173">語法節點會在標記中包含成對的 `<command:syntax>` 。</span><span class="sxs-lookup"><span data-stu-id="72527-173">The syntax node is enclosed in a pair if `<command:syntax>` tags.</span></span> <span data-ttu-id="72527-174">將 Cmdlet 的每個參數集加上成對的 `<command:syntaxitem>` 標記。</span><span class="sxs-lookup"><span data-stu-id="72527-174">With each parameter set of the cmdlet enclosed in a pair of `<command:syntaxitem>` tags.</span></span> <span data-ttu-id="72527-175">您可以新增的標記數目沒有任何限制 `<command:syntaxitem>` 。</span><span class="sxs-lookup"><span data-stu-id="72527-175">There is no limit to the number of `<command:syntaxitem>` tags that you can add.</span></span>

<span data-ttu-id="72527-176">下列範例顯示具有兩個參數集之語法專案節點的語法節點。</span><span class="sxs-lookup"><span data-stu-id="72527-176">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="72527-177">將 Cmdlet 名稱新增至參數集資料</span><span class="sxs-lookup"><span data-stu-id="72527-177">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="72527-178">Cmdlet 的每個參數集都是在語法專案節點中指定。</span><span class="sxs-lookup"><span data-stu-id="72527-178">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="72527-179">每個語法專案節點的開頭都是一組 `<maml:name>` 包含 Cmdlet 名稱的標記。</span><span class="sxs-lookup"><span data-stu-id="72527-179">Each syntax item node begins with a pair of `<maml:name>` tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="72527-180">下列範例包含語法節點，其具有兩個參數集的語法專案節點。</span><span class="sxs-lookup"><span data-stu-id="72527-180">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a><span data-ttu-id="72527-181">加入參數</span><span class="sxs-lookup"><span data-stu-id="72527-181">Adding Parameters</span></span>

<span data-ttu-id="72527-182">每個加入至語法專案節點的參數都是在一對標記內指定的 `<command:parameter>` 。</span><span class="sxs-lookup"><span data-stu-id="72527-182">Each parameter added to the syntax item node is specified within a pair of `<command:parameter>` tags.</span></span> <span data-ttu-id="72527-183">`<command:parameter>`參數集中包含的每個參數都需要一組標記，但 PowerShell 提供的一般參數除外。</span><span class="sxs-lookup"><span data-stu-id="72527-183">You need a pair of `<command:parameter>` tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by PowerShell.</span></span>

<span data-ttu-id="72527-184">開頭標記的屬性 `<command:parameter>` 會決定參數如何出現在語法圖表中。</span><span class="sxs-lookup"><span data-stu-id="72527-184">The attributes of the opening `<command:parameter>` tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="72527-185">如需參數屬性的詳細資訊，請參閱 [參數屬性](#parameter-attributes)。</span><span class="sxs-lookup"><span data-stu-id="72527-185">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="72527-186">此 `<command:parameter>` 標記支援 `<maml:description>` 內容永遠不會顯示的子項目。</span><span class="sxs-lookup"><span data-stu-id="72527-186">The `<command:parameter>` tag supports a child element `<maml:description>` whose content is never displayed.</span></span> <span data-ttu-id="72527-187">參數描述是在 XML 的參數節點中指定。</span><span class="sxs-lookup"><span data-stu-id="72527-187">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="72527-188">若要避免語法專案指日可待和參數節點中資訊之間的不一致，請省略 (`<maml:description>` 或將其保留空白。</span><span class="sxs-lookup"><span data-stu-id="72527-188">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (`<maml:description>` or leave it empty.</span></span>

<span data-ttu-id="72527-189">下列範例包含具有兩個參數之參數集的語法專案節點。</span><span class="sxs-lookup"><span data-stu-id="72527-189">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
