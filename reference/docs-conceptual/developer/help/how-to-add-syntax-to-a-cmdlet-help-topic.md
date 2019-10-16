---
title: 如何將語法新增至 Cmdlet 說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361207"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="3e709-102">如何新增語法至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="3e709-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="3e709-103">在您開始為 Cmdlet 說明檔中的語法圖表撰寫 XML 的程式碼之前，請先閱讀本節，以清楚瞭解您需要提供的資料類型，例如參數屬性，以及該資料在語法圖表中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="3e709-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="3e709-104">參數屬性</span><span class="sxs-lookup"><span data-stu-id="3e709-104">Parameter Attributes</span></span>

- <span data-ttu-id="3e709-105">必要</span><span class="sxs-lookup"><span data-stu-id="3e709-105">Required</span></span>

  - <span data-ttu-id="3e709-106">如果為 true，則參數必須出現在所有使用參數集的命令中。</span><span class="sxs-lookup"><span data-stu-id="3e709-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="3e709-107">如果為 false，則在使用參數集的所有命令中，參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="3e709-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="3e709-108">移動</span><span class="sxs-lookup"><span data-stu-id="3e709-108">Position</span></span>

  - <span data-ttu-id="3e709-109">如果命名為，則需要參數名稱。</span><span class="sxs-lookup"><span data-stu-id="3e709-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="3e709-110">如果是位置，參數名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="3e709-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="3e709-111">省略時，參數值必須在命令中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="3e709-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="3e709-112">例如，如果值是 position = "1"，則參數值必須是命令中的第一個或唯一未命名的參數值。</span><span class="sxs-lookup"><span data-stu-id="3e709-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="3e709-113">管線輸入</span><span class="sxs-lookup"><span data-stu-id="3e709-113">Pipeline Input</span></span>

  - <span data-ttu-id="3e709-114">如果為 true （ByValue），您可以透過管道傳送輸入至參數。</span><span class="sxs-lookup"><span data-stu-id="3e709-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="3e709-115">即使屬性名稱和物件類型不符合預期的類型，輸入也會與（「系結至」）參數相關聯。</span><span class="sxs-lookup"><span data-stu-id="3e709-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="3e709-116">Windows PowerShell？參數系結元件會嘗試將輸入轉換成正確的型別，只有在無法轉換型別時，才會使命令失效。</span><span class="sxs-lookup"><span data-stu-id="3e709-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="3e709-117">參數集中只有一個參數可以透過 value 來關聯。</span><span class="sxs-lookup"><span data-stu-id="3e709-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="3e709-118">如果為 true （ByPropertyName），您可以透過管道傳送輸入至參數。</span><span class="sxs-lookup"><span data-stu-id="3e709-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="3e709-119">不過，只有當參數名稱符合輸入物件的屬性名稱時，輸入才會與參數相關聯。</span><span class="sxs-lookup"><span data-stu-id="3e709-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="3e709-120">例如，如果參數名稱是 `Path`，則只有當物件具有名為 path 的屬性時，才會將輸送至 Cmdlet 的物件與該參數相關聯。</span><span class="sxs-lookup"><span data-stu-id="3e709-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="3e709-121">如果為 true （ByValue，ByPropertyName），您可以透過屬性名稱或以傳值方式將輸入傳送至參數。</span><span class="sxs-lookup"><span data-stu-id="3e709-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="3e709-122">參數集中只有一個參數可以透過 value 來關聯。</span><span class="sxs-lookup"><span data-stu-id="3e709-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="3e709-123">如果為 false，則表示您無法透過管道傳送輸入至此參數。</span><span class="sxs-lookup"><span data-stu-id="3e709-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="3e709-124">通配</span><span class="sxs-lookup"><span data-stu-id="3e709-124">Globbing</span></span>

  - <span data-ttu-id="3e709-125">若為 true，使用者為參數值輸入的文字可以包含萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3e709-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="3e709-126">如果為 false，則使用者為參數值輸入的文字不能包含萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3e709-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="3e709-127">參數值屬性</span><span class="sxs-lookup"><span data-stu-id="3e709-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="3e709-128">必要</span><span class="sxs-lookup"><span data-stu-id="3e709-128">Required</span></span>

  - <span data-ttu-id="3e709-129">若為 true，則在命令中使用參數時，必須使用指定的值。</span><span class="sxs-lookup"><span data-stu-id="3e709-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="3e709-130">如果為 false，則表示參數值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="3e709-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="3e709-131">一般來說，只有當值是參數的數個有效值之一時（例如列舉型別），才會是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="3e709-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="3e709-132">參數值的必要屬性與參數的必要屬性不同。</span><span class="sxs-lookup"><span data-stu-id="3e709-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="3e709-133">參數的必要屬性會指出叫用 Cmdlet 時，是否必須包含參數（和其值）。</span><span class="sxs-lookup"><span data-stu-id="3e709-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="3e709-134">相較之下，只有在命令中包含參數時，才會使用參數值的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3e709-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="3e709-135">它會指出該特定值是否必須與參數搭配使用。</span><span class="sxs-lookup"><span data-stu-id="3e709-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="3e709-136">通常是預留位置的參數值，而且不需要常值的參數值，因為它們是可能與參數搭配使用的數個值之一。</span><span class="sxs-lookup"><span data-stu-id="3e709-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="3e709-137">正在搜集語法資訊</span><span class="sxs-lookup"><span data-stu-id="3e709-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="3e709-138">從 Cmdlet 名稱開始。</span><span class="sxs-lookup"><span data-stu-id="3e709-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="3e709-139">列出 Cmdlet 的所有參數。</span><span class="sxs-lookup"><span data-stu-id="3e709-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="3e709-140">在每個參數名稱之前輸入破折號（也稱為「破折號」或「減號」（ASCII 45））。</span><span class="sxs-lookup"><span data-stu-id="3e709-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="3e709-141">將參數分隔成參數集（某些 Cmdlet 只能有一個參數集）。</span><span class="sxs-lookup"><span data-stu-id="3e709-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="3e709-142">在此範例中，取得-Tech Cmdlet 有兩個參數集。</span><span class="sxs-lookup"><span data-stu-id="3e709-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="3e709-143">使用 Cmdlet 名稱啟動每個參數集。</span><span class="sxs-lookup"><span data-stu-id="3e709-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="3e709-144">請先列出預設參數集。</span><span class="sxs-lookup"><span data-stu-id="3e709-144">List the default parameter set first.</span></span> <span data-ttu-id="3e709-145">預設參數是由 Cmdlet 類別所指定。</span><span class="sxs-lookup"><span data-stu-id="3e709-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="3e709-146">針對每個參數集，先列出其唯一的參數，除非有位置參數必須先出現。</span><span class="sxs-lookup"><span data-stu-id="3e709-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="3e709-147">在上述範例中，Name 和 ID 參數是這兩個參數集的唯一參數（每個參數集都必須有一個參數，而此參數集是唯一的）。</span><span class="sxs-lookup"><span data-stu-id="3e709-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="3e709-148">這可讓使用者更輕鬆地識別需要提供給參數集的參數。</span><span class="sxs-lookup"><span data-stu-id="3e709-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="3e709-149">以命令中應該出現的順序列出參數。</span><span class="sxs-lookup"><span data-stu-id="3e709-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="3e709-150">如果順序不重要，請將相關的參數列出在一起，或先列出最常使用的參數。</span><span class="sxs-lookup"><span data-stu-id="3e709-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="3e709-151">如果 Cmdlet 支援 ShouldProcess，請務必列出 WhatIf 和 Confirm 參數。</span><span class="sxs-lookup"><span data-stu-id="3e709-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="3e709-152">請勿在您的語法圖表中列出一般參數（例如 Verbose、Debug 和 ErrorAction）。</span><span class="sxs-lookup"><span data-stu-id="3e709-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="3e709-153">當您顯示說明主題時，`Get-Help` Cmdlet 會為您新增該資訊。</span><span class="sxs-lookup"><span data-stu-id="3e709-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="3e709-154">新增參數值。</span><span class="sxs-lookup"><span data-stu-id="3e709-154">Add the parameter values.</span></span> <span data-ttu-id="3e709-155">在 Windows PowerShell 中，參數值是以其 .NET 類型來表示。</span><span class="sxs-lookup"><span data-stu-id="3e709-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="3e709-156">不過，型別名稱可以是縮寫，例如 system.string 的 "string"。</span><span class="sxs-lookup"><span data-stu-id="3e709-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="3e709-157">縮寫類型（只要其意義很清楚），例如 "string" 代表 System.string，而 "int" 則適用于 System.object。</span><span class="sxs-lookup"><span data-stu-id="3e709-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="3e709-158">列出列舉的所有值，例如上一個範例中的-type 參數，可以設定為 "basic" 或 "advanced"。</span><span class="sxs-lookup"><span data-stu-id="3e709-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="3e709-159">Switch 參數（如前一個範例中的-list）沒有值。</span><span class="sxs-lookup"><span data-stu-id="3e709-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="3e709-160">將角括弧加入為預留位置的參數值（相較于常值的參數值）。</span><span class="sxs-lookup"><span data-stu-id="3e709-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="3e709-161">以方括弧括住選擇性參數和其 missing 值。</span><span class="sxs-lookup"><span data-stu-id="3e709-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="3e709-162">以方括弧括住選擇性參數名稱（適用于位置參數）。</span><span class="sxs-lookup"><span data-stu-id="3e709-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="3e709-163">位置的參數名稱（例如下列範例中的 Name 參數）不需要包含在命令中。</span><span class="sxs-lookup"><span data-stu-id="3e709-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="3e709-164">如果參數值可以包含多個值（例如 Name 參數中的名稱清單），請在參數值後面加上一對方括弧。</span><span class="sxs-lookup"><span data-stu-id="3e709-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="3e709-165">如果使用者可以從參數或參數值中選擇，例如類型參數，請以大括弧括住選擇，並以獨佔或符號（;) 分隔。</span><span class="sxs-lookup"><span data-stu-id="3e709-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="3e709-166">如果參數值必須使用特定格式，例如引號或括弧，請在語法中顯示格式。</span><span class="sxs-lookup"><span data-stu-id="3e709-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="3e709-167">編碼語法圖表 XML</span><span class="sxs-lookup"><span data-stu-id="3e709-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="3e709-168">XML 的語法節點會緊接在 description 節點後面，結尾為 \</maml： description > 標記。</span><span class="sxs-lookup"><span data-stu-id="3e709-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="3e709-169">如需有關收集語法圖表中所用資料的詳細資訊，請參閱[收集語法資訊](#gathering-syntax-information)。</span><span class="sxs-lookup"><span data-stu-id="3e709-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="3e709-170">加入語法節點</span><span class="sxs-lookup"><span data-stu-id="3e709-170">Adding a Syntax Node</span></span>

<span data-ttu-id="3e709-171">Cmdlet 說明主題中顯示的語法圖表是從 XML 的語法節點中的資料產生。</span><span class="sxs-lookup"><span data-stu-id="3e709-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="3e709-172">如果 @no__t 0command：語法 > 標記，語法節點會括在配對中。</span><span class="sxs-lookup"><span data-stu-id="3e709-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="3e709-173">將 Cmdlet 的每個參數集放在一對 \<command： syntaxitem > 標記中。</span><span class="sxs-lookup"><span data-stu-id="3e709-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="3e709-174">您可以新增的 @no__t 0command： syntaxitem > 標記數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="3e709-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="3e709-175">下列範例顯示語法節點，其中包含兩個參數集的語法專案節點。</span><span class="sxs-lookup"><span data-stu-id="3e709-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="3e709-176">將 Cmdlet 名稱新增至參數集資料</span><span class="sxs-lookup"><span data-stu-id="3e709-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="3e709-177">Cmdlet 的每個參數集都指定于語法專案節點中。</span><span class="sxs-lookup"><span data-stu-id="3e709-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="3e709-178">每個語法專案節點的開頭都是一對 \<maml： name > 標記，其中包含 Cmdlet 的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e709-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="3e709-179">下列範例包含語法節點，其中包含兩個參數集的語法專案節點。</span><span class="sxs-lookup"><span data-stu-id="3e709-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="3e709-180">加入參數</span><span class="sxs-lookup"><span data-stu-id="3e709-180">Adding Parameters</span></span>

<span data-ttu-id="3e709-181">加入至語法專案節點的每個參數都是在一對 \<command：參數 > 標記中指定。</span><span class="sxs-lookup"><span data-stu-id="3e709-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="3e709-182">針對參數集內所包含的每個參數，您都需要一對 @no__t 0command：參數 > 標記，但 Windows PowerShell 所提供的一般參數除外？。</span><span class="sxs-lookup"><span data-stu-id="3e709-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="3e709-183">開啟的 @no__t 0command： parameter > 標記的屬性會決定參數如何出現在語法圖表中。</span><span class="sxs-lookup"><span data-stu-id="3e709-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="3e709-184">如需參數屬性的詳細資訊，請參閱[參數屬性](#parameter-attributes)。</span><span class="sxs-lookup"><span data-stu-id="3e709-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="3e709-185">@No__t-0command： parameter > 標記支援 \<maml： description > 內容永遠不會顯示的子項目。</span><span class="sxs-lookup"><span data-stu-id="3e709-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="3e709-186">參數描述是在 XML 的參數節點中指定。</span><span class="sxs-lookup"><span data-stu-id="3e709-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="3e709-187">若要避免語法專案指日可待和參數節點中的資訊不一致，請省略（\<maml： description > 或將其保留空白。</span><span class="sxs-lookup"><span data-stu-id="3e709-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="3e709-188">下列範例包含具有兩個參數之參數集的語法專案節點。</span><span class="sxs-lookup"><span data-stu-id="3e709-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
