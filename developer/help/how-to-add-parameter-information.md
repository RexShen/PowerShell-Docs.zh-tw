---
title: 如何新增參數資訊 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863324"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="9c980-102">如何新增參數資訊</span><span class="sxs-lookup"><span data-stu-id="9c980-102">How to Add Parameter Information</span></span>

<span data-ttu-id="9c980-103">本節說明如何新增會顯示 cmdlet 說明主題的參數區段中的內容。</span><span class="sxs-lookup"><span data-stu-id="9c980-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="9c980-104">[說明] 主題的 PARAMETERS 區段會列出每個 cmdlet 的參數，並提供每個參數的詳細的描述。</span><span class="sxs-lookup"><span data-stu-id="9c980-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="9c980-105">參數區段的內容應該是一致的語法 」 一節說明主題的內容。</span><span class="sxs-lookup"><span data-stu-id="9c980-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="9c980-106">它負責說明作者，以確定語法和參數 節點包含類似的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="9c980-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="9c980-107">說明檔案，開啟其中一個 dll Help.xml 檔案位於 Windows PowerShell 安裝目錄的完整檢視。</span><span class="sxs-lookup"><span data-stu-id="9c980-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="9c980-108">比方說，Microsoft.PowerShell.Commands.Management.dll Help.xml 檔案會包含內容的數個 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c980-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="9c980-109">若要加入參數</span><span class="sxs-lookup"><span data-stu-id="9c980-109">To Add Parameters</span></span>

1. <span data-ttu-id="9c980-110">開啟的 cmdlet 說明檔，並找出您所記載的 cmdlet 的命令 節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="9c980-111">如果您要新增新的 cmdlet，您必須建立新的 [命令] 節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="9c980-112">說明檔會包含您要提供的說明內容的每個 cmdlet 的命令節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="9c980-113">以下是空白的命令節點的範例。</span><span class="sxs-lookup"><span data-stu-id="9c980-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="9c980-114">在 [命令] 節點中，找出 [描述] 節點，並將 [參數] 節點，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9c980-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="9c980-115">將允許只有一個參數 節點，而它應該緊接語法節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="9c980-116">在 [參數] 節點中，請新增 cmdlet 的每個參數的參數節點，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9c980-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="9c980-117">在此範例中，針對三個參數加入的參數節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="9c980-118">因為這些都是相同的 XML 標記，它會在語法節點，而且因為此處指定的參數必須符合指定的語法節點的參數，您可以複製語法節點中的參數節點，並將其貼到 [參數] 節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="9c980-119">不過，請務必複製的參數節點只有一個執行個體，即使參數中指定多個參數是設定在語法中。</span><span class="sxs-lookup"><span data-stu-id="9c980-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="9c980-120">針對每個參數 節點中，設定屬性值定義每個參數的特性。</span><span class="sxs-lookup"><span data-stu-id="9c980-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="9c980-121">這些屬性包括下列： 有需要，萬用字元、 pipelineinput 和位置。</span><span class="sxs-lookup"><span data-stu-id="9c980-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. <span data-ttu-id="9c980-122">針對每個參數 節點中，新增參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c980-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="9c980-123">以下是範例參數名稱加入至參數的節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="9c980-124">針對每個參數 節點中，新增參數的描述。</span><span class="sxs-lookup"><span data-stu-id="9c980-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="9c980-125">以下是新增至 [參數] 節點的參數描述的範例。</span><span class="sxs-lookup"><span data-stu-id="9c980-125">Here is an example of the parameter description added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. <span data-ttu-id="9c980-126">針對每個參數 節點中，新增參數的.NET Framework 型別。</span><span class="sxs-lookup"><span data-stu-id="9c980-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="9c980-127">參數類型會顯示與參數名稱。</span><span class="sxs-lookup"><span data-stu-id="9c980-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="9c980-128">以下是參數的.NET Framework 型別新增至 [參數] 節點的範例。</span><span class="sxs-lookup"><span data-stu-id="9c980-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. <span data-ttu-id="9c980-129">針對每個參數 節點中，新增參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="9c980-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="9c980-130">顯示內容時，下列句子被新增參數描述：預設值為 「 DefaultValue 」。</span><span class="sxs-lookup"><span data-stu-id="9c980-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="9c980-131">以下是範例的參數預設值加入至參數的節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. <span data-ttu-id="9c980-132">每個參數有多個值，將 可能的值節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="9c980-133">以下是範例定義兩個可能的值，參數可能的值節點的</span><span class="sxs-lookup"><span data-stu-id="9c980-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="9c980-134">以下是要加入參數時，必須記住的一些事項。</span><span class="sxs-lookup"><span data-stu-id="9c980-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="9c980-135">參數的屬性不會顯示在所有檢視中的 cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="9c980-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="9c980-136">不過，它們會顯示在下列參數的描述，當使用者要求完整的資料表 (Get-help \<cmdletname >-完整) 或參數 (Get-help \<cmdletname >-參數) 主題的檢視。</span><span class="sxs-lookup"><span data-stu-id="9c980-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="9c980-137">參數描述是其中一個最重要的組件的 cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="9c980-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="9c980-138">描述應為簡短，以及完整。</span><span class="sxs-lookup"><span data-stu-id="9c980-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="9c980-139">此外，請記住，是否參數描述變得太長，例如當兩個參數的互動方式，您可以新增更多的內容中的 cmdlet 說明主題的附註 區段。</span><span class="sxs-lookup"><span data-stu-id="9c980-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="9c980-140">參數描述會提供兩種類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="9c980-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="9c980-141">Cmdlet 的功能時使用的參數。</span><span class="sxs-lookup"><span data-stu-id="9c980-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="9c980-142">哪些合法的值為參數。</span><span class="sxs-lookup"><span data-stu-id="9c980-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="9c980-143">參數值會表示為.NET Framework 物件，因為使用者如需有關這些值不像傳統的命令列說明。</span><span class="sxs-lookup"><span data-stu-id="9c980-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="9c980-144">告訴使用者的接受，旨在參數的資料類型，並包括範例。</span><span class="sxs-lookup"><span data-stu-id="9c980-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="9c980-145">如果未在命令列上指定的參數會使用值為參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="9c980-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="9c980-146">請注意，預設值是選擇性的而且不需要某些參數，例如必要的參數。</span><span class="sxs-lookup"><span data-stu-id="9c980-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="9c980-147">不過，您應該指定大部分的選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="9c980-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="9c980-148">預設值可協助使用者了解如何不使用此參數的效果。</span><span class="sxs-lookup"><span data-stu-id="9c980-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="9c980-149">描述非常具體來說，例如 「 目前的目錄 」 或 「 Windows PowerShell 安裝目錄 ($pshome) 」 的選擇性路徑的預設值。</span><span class="sxs-lookup"><span data-stu-id="9c980-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="9c980-150">您也可以撰寫描述預設值，例如用於下列句子的句子`PassThru`參數：「 如果未指定 PassThru，cmdlet 未通過物件沿著管線向下的。 」</span><span class="sxs-lookup"><span data-stu-id="9c980-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="9c980-151">此外，因為相反的欄位名稱會顯示值"**預設值**」，您不需要的項目中包含 「 預設值 」 一詞。</span><span class="sxs-lookup"><span data-stu-id="9c980-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="9c980-152">參數的預設值不會顯示在所有檢視中的 cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="9c980-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="9c980-153">不過，它會顯示在下列參數的描述，當使用者要求完整的資料表 （以及參數屬性） (Get-help \<cmdletname >-full) 或參數 (Get-help \<cmdletname >-參數) 檢視主題。</span><span class="sxs-lookup"><span data-stu-id="9c980-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="9c980-154">下列 XML 會顯示一組`<dev:defaultValue>`加入至標記`<command:parameter>`節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="9c980-155">請注意，預設值會遵循關閉之後緊接著`</command:parameterValue>`標記 （當指定的參數值） 或關閉`</maml:description>`標記的參數描述。</span><span class="sxs-lookup"><span data-stu-id="9c980-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="9c980-156">名稱。</span><span class="sxs-lookup"><span data-stu-id="9c980-156">name.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

<span data-ttu-id="9c980-157">新增列舉型別值</span><span class="sxs-lookup"><span data-stu-id="9c980-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="9c980-158">如果參數有多個值或值的列舉型別，您可以使用選擇性\<dev:possibleValues > 節點。</span><span class="sxs-lookup"><span data-stu-id="9c980-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="9c980-159">此節點可讓您指定的名稱和描述多個值。</span><span class="sxs-lookup"><span data-stu-id="9c980-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="9c980-160">請注意，列舉值的描述不會出現在任何預設值所顯示的說明檢視`Get-Help`cmdlet，但其他的說明檢視器可能會在其檢視中顯示此內容。</span><span class="sxs-lookup"><span data-stu-id="9c980-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="9c980-161">下列 XML 會說明`<dev:possibleValues>`節點與兩個指定的值。</span><span class="sxs-lookup"><span data-stu-id="9c980-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```