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
ms.openlocfilehash: b9ccca75c2d9126e84a7f486ffe803042a742b62
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565555"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="a6d4f-102">如何新增參數資訊</span><span class="sxs-lookup"><span data-stu-id="a6d4f-102">How to Add Parameter Information</span></span>

<span data-ttu-id="a6d4f-103">本節說明如何新增在 Cmdlet 說明主題的 PARAMETERS 區段中所顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="a6d4f-104">說明主題的 PARAMETERS 區段會列出 Cmdlet 的每個參數，並提供每個參數的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="a6d4f-105">[參數] 區段的內容應該與說明主題的 [語法] 區段內容一致。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="a6d4f-106">說明作者必須負責確保 [語法] 和 [參數] 節點包含類似的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="a6d4f-107">如需說明檔的完整視圖，請開啟位於 Windows PowerShell 安裝目錄中的其中一個 dll-Help 檔案。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="a6d4f-108">例如，dll-Help 檔案包含數個 Windows PowerShell 指令程式的內容（content）。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="a6d4f-109">若要加入參數</span><span class="sxs-lookup"><span data-stu-id="a6d4f-109">To Add Parameters</span></span>

1. <span data-ttu-id="a6d4f-110">開啟 Cmdlet 說明檔，並找出您所記錄之 Cmdlet 的命令節點。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="a6d4f-111">如果您要新增新的 Cmdlet，您將需要建立新的命令節點。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="a6d4f-112">您的說明檔會針對您提供說明內容的每個 Cmdlet，各包含一個命令節點。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="a6d4f-113">以下是空白命令節點的範例。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="a6d4f-114">在 [命令] 節點中，找出 [描述] 節點並新增 [參數] 節點，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="a6d4f-115">只允許一個參數節點，而且應該緊接在語法節點後面。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="a6d4f-116">在 [參數] 節點中，為 Cmdlet 的每個參數新增參數節點，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="a6d4f-117">在此範例中，會加入三個參數的參數節點。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="a6d4f-118">因為這些是語法節點中所使用的相同 XML 標記，而且在此處指定的參數必須符合語法節點所指定的參數，所以您可以從語法節點複製參數節點，並將它們貼入 [參數] 節點。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="a6d4f-119">不過，請務必只複製一個參數節點的實例，即使在語法的多個參數集中指定了參數也一樣。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="a6d4f-120">針對每個參數節點，設定屬性值，以定義每個參數的特性。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="a6d4f-121">這些屬性包括下列各項： required、通配、pipelineinput 和 position。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

5. <span data-ttu-id="a6d4f-122">針對每個參數節點，新增參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="a6d4f-123">以下是將參數名稱新增至參數節點的範例。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="a6d4f-124">針對每個參數節點，新增參數的描述。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="a6d4f-125">以下是將參數描述新增至參數節點的範例。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-125">Here is an example of the parameter description added to the Parameter node.</span></span>

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

7. <span data-ttu-id="a6d4f-126">針對每個參數節點，新增參數的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="a6d4f-127">參數類型會與參數名稱一起顯示。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="a6d4f-128">以下是將參數加入至參數節點 .NET Framework 類型的範例。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

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

8. <span data-ttu-id="a6d4f-129">針對每個參數節點，新增參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="a6d4f-130">顯示內容時，會將下列句子加入至參數描述： "DefaultValue" 是預設值。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="a6d4f-131">以下是將參數預設值新增至參數節點的範例。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

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

9. <span data-ttu-id="a6d4f-132">針對每個具有多個值的參數，新增 [可能的值] 節點。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="a6d4f-133">以下是可能值節點的範例，其定義參數的兩個可能值。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

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

<span data-ttu-id="a6d4f-134">以下是新增參數時要記住的一些事項。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="a6d4f-135">參數的屬性不會顯示在 Cmdlet 說明主題的所有視圖中。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="a6d4f-136">不過，當使用者要求完整（Get-help \< Cmdletname>-Full）或主題的參數（get-help \< Cmdletname> 參數）時，會依照參數描述，將它們顯示在資料表中。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="a6d4f-137">參數描述是 Cmdlet 說明主題其中一個最重要的部分。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="a6d4f-138">描述應該是簡短的，也應該是完整的。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="a6d4f-139">此外，請記住，如果參數描述變得太長，例如兩個參數彼此互動時，您可以在 Cmdlet 說明主題的附注區段中新增更多內容。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="a6d4f-140">參數描述提供兩種類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="a6d4f-141">使用參數時，Cmdlet 會執行的工作。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="a6d4f-142">參數的合法值。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="a6d4f-143">因為參數值會表示為 .NET Framework 物件，所以使用者需要這些值的詳細資訊，而不是傳統命令列說明中的。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="a6d4f-144">告知使用者參數設計要接受的資料類型，並包含範例。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="a6d4f-145">參數的預設值是在命令列上未指定參數時所使用的值。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="a6d4f-146">請注意，預設值是選擇性的，而某些參數（例如必要的參數）則不需要。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="a6d4f-147">不過，您應該為大部分的選擇性參數指定預設值。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="a6d4f-148">預設值可協助使用者瞭解不使用參數的效果。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="a6d4f-149">明確描述預設值，例如「目前目錄」或選擇性路徑的「Windows PowerShell 安裝目錄（$pshome）」。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="a6d4f-150">您也可以撰寫描述預設值的句子，例如用於參數的下列句子 `PassThru` ：「如果未指定 PassThru，Cmdlet 就不會將物件沿著管線向下傳遞」。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="a6d4f-151">此外，因為此值會與功能變數名稱「**預設值**」相反地顯示，所以您不需要在專案中包含「預設值」一詞。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="a6d4f-152">此參數的預設值不會顯示在 Cmdlet 說明主題的所有 views 中。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="a6d4f-153">不過，當使用者要求主題的完整（Get-help \< Cmdletname>-Full）或 parameter （get-help \< Cmdletname>-parameter）時，它會在參數描述之後，顯示在資料表中（連同參數屬性）。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="a6d4f-154">下列 XML 會顯示一對 `<dev:defaultValue>` 加入至節點的標記 `<command:parameter>` 。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="a6d4f-155">請注意，預設值緊接在結束記號之後 `</command:parameterValue>` （指定參數值時）或 `</maml:description>` 參數描述的結束記號後面。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="a6d4f-156">名稱。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-156">name.</span></span>

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

<span data-ttu-id="a6d4f-157">新增列舉類型的值</span><span class="sxs-lookup"><span data-stu-id="a6d4f-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="a6d4f-158">如果參數有多個值或列舉類型的值，您可以使用選擇性的 \< dev： possibleValues> 節點。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="a6d4f-159">此節點可讓您指定多個值的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="a6d4f-160">請注意，列舉值的描述並不會出現在 Cmdlet 所顯示的任何預設說明視圖中 `Get-Help` ，但其他協助檢視器可能會在其視圖中顯示此內容。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="a6d4f-161">下列 XML 顯示已 `<dev:possibleValues>` 指定兩個值的節點。</span><span class="sxs-lookup"><span data-stu-id="a6d4f-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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
