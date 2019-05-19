---
title: 如何將 Cmdlet 說明主題中的語法 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855141"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="9517e-102">如何新增語法至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="9517e-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="9517e-103">您開始撰寫程式碼的 XML 語法圖表中的 cmdlet 說明檔之前，請閱讀本節以取得清楚類型，您必須提供的資料，例如參數屬性和語法圖表中顯示該資料的方式了解...</span><span class="sxs-lookup"><span data-stu-id="9517e-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="9517e-104">參數屬性</span><span class="sxs-lookup"><span data-stu-id="9517e-104">Parameter Attributes</span></span>

- <span data-ttu-id="9517e-105">必要</span><span class="sxs-lookup"><span data-stu-id="9517e-105">Required</span></span>

  - <span data-ttu-id="9517e-106">如果為 true，參數必須出現在使用參數集的所有命令。</span><span class="sxs-lookup"><span data-stu-id="9517e-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="9517e-107">如果為 false，參數是選擇性的所有命令的參數集。</span><span class="sxs-lookup"><span data-stu-id="9517e-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="9517e-108">位置</span><span class="sxs-lookup"><span data-stu-id="9517e-108">Position</span></span>

  - <span data-ttu-id="9517e-109">如果名稱，參數名稱為必要。</span><span class="sxs-lookup"><span data-stu-id="9517e-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="9517e-110">如果位置，參數名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="9517e-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="9517e-111">省略時，參數值必須在命令中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="9517e-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="9517e-112">例如，如果值為位置 ="1"的參數值必須是第一個或唯一未命名的命令中的參數值。</span><span class="sxs-lookup"><span data-stu-id="9517e-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="9517e-113">管線輸入</span><span class="sxs-lookup"><span data-stu-id="9517e-113">Pipeline Input</span></span>

  - <span data-ttu-id="9517e-114">如果為 true (ByValue)，您可以使用管線傳送輸入至參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="9517e-115">輸入是相關聯 （「 繫結至"） 與即使屬性名稱和物件型別不符合預期的類型參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="9517e-116">Windows PowerShell 中？參數繫結元件，嘗試將輸入轉換成正確的型別，並讓命令失敗，無法將類型轉換時，才而不同。</span><span class="sxs-lookup"><span data-stu-id="9517e-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="9517e-117">參數集合中的只有一個參數可以傳值產生關聯。</span><span class="sxs-lookup"><span data-stu-id="9517e-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="9517e-118">如果為 true (ByPropertyName)，您可以使用管線傳送輸入至參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="9517e-119">不過，輸入是屬性的與參數相關聯的參數名稱相符的輸入物件名稱時，才。</span><span class="sxs-lookup"><span data-stu-id="9517e-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="9517e-120">比方說，如果參數名稱為`Path`，物件具有名為路徑的屬性時，才傳送至 cmdlet 的物件都是與該參數相關聯。</span><span class="sxs-lookup"><span data-stu-id="9517e-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="9517e-121">如果您可以透過管道傳送至參數的輸入屬性名稱或值為 true （ByValue、 ByPropertyName）。</span><span class="sxs-lookup"><span data-stu-id="9517e-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="9517e-122">參數集合中的只有一個參數可以傳值產生關聯。</span><span class="sxs-lookup"><span data-stu-id="9517e-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="9517e-123">如果為 false，您無法使用管線傳送輸入至這個參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="9517e-124">萬用字元</span><span class="sxs-lookup"><span data-stu-id="9517e-124">Globbing</span></span>

  - <span data-ttu-id="9517e-125">如果為 true，使用者輸入參數值的文字可以包含萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9517e-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="9517e-126">如果為 false，使用者輸入參數值的文字不能包含萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9517e-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="9517e-127">參數值屬性</span><span class="sxs-lookup"><span data-stu-id="9517e-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="9517e-128">必要</span><span class="sxs-lookup"><span data-stu-id="9517e-128">Required</span></span>

  - <span data-ttu-id="9517e-129">如果為 true，只要在命令中使用的參數必須使用指定的值。</span><span class="sxs-lookup"><span data-stu-id="9517e-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="9517e-130">如果為 false，參數值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="9517e-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="9517e-131">一般而言，值是選擇性，它是其中一個的數個有效的值是參數，例如在列舉型別時，才。</span><span class="sxs-lookup"><span data-stu-id="9517e-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="9517e-132">必要的參數值的屬性與不同參數的必要的屬性。</span><span class="sxs-lookup"><span data-stu-id="9517e-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="9517e-133">參數的必要的屬性表示是否參數 （和其值） 必須包含叫用 cmdlet 時。</span><span class="sxs-lookup"><span data-stu-id="9517e-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="9517e-134">相較之下，已在命令中包含參數時，才可以使用的參數值的必要的屬性。</span><span class="sxs-lookup"><span data-stu-id="9517e-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="9517e-135">指出是否必須搭配參數使用該特定的值。</span><span class="sxs-lookup"><span data-stu-id="9517e-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="9517e-136">一般而言，是預留位置的參數值是必要值，並屬於常值的參數值不是必要的因為它們可能會與參數搭配使用的數個值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="9517e-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="9517e-137">正在蒐集的語法資訊</span><span class="sxs-lookup"><span data-stu-id="9517e-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="9517e-138">Cmdlet 名稱的開頭。</span><span class="sxs-lookup"><span data-stu-id="9517e-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="9517e-139">列出所有 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="9517e-140">輸入以連字號 （也稱為 「 虛線 」 或 「 負號"(ASCII 45) 在每個參數名稱之前。</span><span class="sxs-lookup"><span data-stu-id="9517e-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="9517e-141">參數分成 （某些 cmdlet 可能會有只有一個參數設定） 的參數集。</span><span class="sxs-lookup"><span data-stu-id="9517e-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="9517e-142">在此範例中取得科技 cmdlet 有兩個參數集。</span><span class="sxs-lookup"><span data-stu-id="9517e-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="9517e-143">開始使用的 cmdlet 名稱設定每個參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="9517e-144">列出的預設參數集的第一次。</span><span class="sxs-lookup"><span data-stu-id="9517e-144">List the default parameter set first.</span></span> <span data-ttu-id="9517e-145">在 cmdlet 類別所指定的預設參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="9517e-146">每個參數集，其唯一參數先列出，除非有必須第一個出現的位置參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="9517e-147">在上述範例中，名稱和識別碼的參數都是兩個參數集的唯一參數 （每個參數集必須是唯一的參數集的一個參數）。</span><span class="sxs-lookup"><span data-stu-id="9517e-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="9517e-148">這可讓使用者更輕鬆地識別所需的參數提供哪些參數集。</span><span class="sxs-lookup"><span data-stu-id="9517e-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="9517e-149">列出的順序，它們應該會出現在命令中的參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="9517e-150">如果順序並不重要，放在一起，列出相關的參數，或先列出最常使用的參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="9517e-151">請務必如果 cmdlet 支援 ShouldProcess 時，請列出 WhatIf 和 Confirm 參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="9517e-152">待辦事項清單 （例如 Verbose、 Debug 和 ErrorAction） 語法圖表中的一般參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="9517e-153">`Get-Help` Cmdlet 會顯示 [說明] 主題時，將新增您該資訊。</span><span class="sxs-lookup"><span data-stu-id="9517e-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="9517e-154">新增參數的值。</span><span class="sxs-lookup"><span data-stu-id="9517e-154">Add the parameter values.</span></span> <span data-ttu-id="9517e-155">在 Windows PowerShell？，參數值都由它們的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="9517e-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="9517e-156">不過，在型別名稱可以縮寫，例如"string"的 System.String。</span><span class="sxs-lookup"><span data-stu-id="9517e-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="9517e-157">只要它們的意義明確，例如"string"的 System.String 和 System.Int32 的 「 int 」，將類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="9517e-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="9517e-158">列出所有值的列舉型別，例如在先前的範例中，可以設定為 「 基本 」 或 「 進階 」-型別參數。</span><span class="sxs-lookup"><span data-stu-id="9517e-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="9517e-159">切換參數，例如-在上述範例中的清單，並沒有值。</span><span class="sxs-lookup"><span data-stu-id="9517e-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="9517e-160">角括號加入預留位置，相較於是常值的參數值的參數值。</span><span class="sxs-lookup"><span data-stu-id="9517e-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="9517e-161">將選擇性參數，而且其值括在方括號中。</span><span class="sxs-lookup"><span data-stu-id="9517e-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="9517e-162">方括號括住選擇性參數名稱 （適用於位置的參數）。</span><span class="sxs-lookup"><span data-stu-id="9517e-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="9517e-163">要包含在命令中沒有參數的位置，例如在下列範例中，名稱參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="9517e-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="9517e-164">如果參數值可以包含多個值，例如在 Name 參數，名稱的清單加入 方括號後面的參數值的配對。</span><span class="sxs-lookup"><span data-stu-id="9517e-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="9517e-165">如果使用者可以選擇從參數或參數值，型別參數，例如將選擇括在大括號，並使用 exclusive OR symbol(;) 隔開。</span><span class="sxs-lookup"><span data-stu-id="9517e-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="9517e-166">如果參數值必須使用特定的格式，例如引號或大括號，請在語法中顯示的格式。</span><span class="sxs-lookup"><span data-stu-id="9517e-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="9517e-167">撰寫程式碼的語法圖 XML</span><span class="sxs-lookup"><span data-stu-id="9517e-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="9517e-168">XML 的語法節點開始，[描述] 節點，以結束後立即\</maml:description > 標記。</span><span class="sxs-lookup"><span data-stu-id="9517e-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="9517e-169">如需收集的語法圖表中使用的資料，請參閱[蒐集的語法資訊](#gathering-syntax-information)。</span><span class="sxs-lookup"><span data-stu-id="9517e-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="9517e-170">新增的語法節點</span><span class="sxs-lookup"><span data-stu-id="9517e-170">Adding a Syntax Node</span></span>

<span data-ttu-id="9517e-171">顯示 cmdlet 說明主題中的語法圖表就會產生從 XML 的語法節點中的資料。</span><span class="sxs-lookup"><span data-stu-id="9517e-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="9517e-172">語法節點住一組，如果\<命令語法： > 標記。</span><span class="sxs-lookup"><span data-stu-id="9517e-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="9517e-173">使用一組括住此指令程式的每個參數集\<命令： syntaxitem > 標記。</span><span class="sxs-lookup"><span data-stu-id="9517e-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="9517e-174">數目沒有限制\<命令： syntaxitem > 您可以新增的標記。</span><span class="sxs-lookup"><span data-stu-id="9517e-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="9517e-175">下列範例示範具有兩個參數集的語法項目節點的語法節點。</span><span class="sxs-lookup"><span data-stu-id="9517e-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="9517e-176">將資料加入至參數的 Cmdlet 名稱設定</span><span class="sxs-lookup"><span data-stu-id="9517e-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="9517e-177">此 cmdlet 的每個參數集的語法項目節點中指定。</span><span class="sxs-lookup"><span data-stu-id="9517e-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="9517e-178">每個語法項目節點開始的一組\<maml:name > 包含的 cmdlet 名稱的標籤。</span><span class="sxs-lookup"><span data-stu-id="9517e-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="9517e-179">下列範例包含具有兩個參數集的語法項目節點的語法節點。</span><span class="sxs-lookup"><span data-stu-id="9517e-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="9517e-180">加入參數</span><span class="sxs-lookup"><span data-stu-id="9517e-180">Adding Parameters</span></span>

<span data-ttu-id="9517e-181">加入的語法項目節點的每個參數指定一組\<命令： 參數 > 標記。</span><span class="sxs-lookup"><span data-stu-id="9517e-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="9517e-182">您需要一對\<命令： 參數 > 針對每個集合中包含參數，除了一般參數所提供的 Windows PowerShell 的參數標記？。</span><span class="sxs-lookup"><span data-stu-id="9517e-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="9517e-183">屬性的開頭\<命令： 參數 > 標記可讓您決定參數語法圖表中顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="9517e-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="9517e-184">在 參數屬性的資訊，請參閱[參數屬性](#parameter-attributes)。</span><span class="sxs-lookup"><span data-stu-id="9517e-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="9517e-185">\<命令： 參數 > 標記支援子項目\<maml:description > 永遠不會顯示其內容。</span><span class="sxs-lookup"><span data-stu-id="9517e-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="9517e-186">參數描述指定之 xml 的 [參數] 節點中。</span><span class="sxs-lookup"><span data-stu-id="9517e-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="9517e-187">若要避免不一致的語法項目中的資訊 bodes 和 [參數] 節點中，省略 (\<maml:description >，或保持空白。</span><span class="sxs-lookup"><span data-stu-id="9517e-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="9517e-188">下列範例包含具有兩個參數設定為參數的語法項目節點。</span><span class="sxs-lookup"><span data-stu-id="9517e-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
