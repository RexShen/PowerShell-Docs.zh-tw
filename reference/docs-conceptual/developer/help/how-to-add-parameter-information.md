---
ms.date: 09/12/2016
ms.topic: reference
title: 如何新增參數資訊
description: 如何新增參數資訊
ms.openlocfilehash: 8f4fc46ef256a77b058df4ba506124f80732cb39
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92663051"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="a4e05-103">如何新增參數資訊</span><span class="sxs-lookup"><span data-stu-id="a4e05-103">How to Add Parameter Information</span></span>

<span data-ttu-id="a4e05-104">本節說明如何新增在 Cmdlet 說明主題的 **PARAMETERS** 區段中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="a4e05-104">This section describes how to add content that is displayed in the **PARAMETERS** section of the cmdlet Help topic.</span></span> <span data-ttu-id="a4e05-105">說明主題的 **parameters** 區段會列出 Cmdlet 的每個參數，並提供每個參數的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="a4e05-105">The **PARAMETERS** section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="a4e05-106">[ **參數** ] 區段的內容應該與 [説明] 主題的 [ **語法** ] 區段內容一致。</span><span class="sxs-lookup"><span data-stu-id="a4e05-106">The content of the **PARAMETERS** section should be consistent with the content of the **SYNTAX** section of the Help topic.</span></span> <span data-ttu-id="a4e05-107">說明作者必須負責確定 [ **語法** ] 和 [ **參數** ] 節點都包含類似的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="a4e05-107">It is the responsibility of the Help author to make sure that both the **Syntax** and **Parameters** node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="a4e05-108">如需說明檔的完整觀點，請開啟 `dll-Help.xml` 位於 PowerShell 安裝目錄中的其中一個檔案。</span><span class="sxs-lookup"><span data-stu-id="a4e05-108">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="a4e05-109">例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。</span><span class="sxs-lookup"><span data-stu-id="a4e05-109">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="a4e05-110">若要加入參數</span><span class="sxs-lookup"><span data-stu-id="a4e05-110">To Add Parameters</span></span>

1. <span data-ttu-id="a4e05-111">開啟 Cmdlet 說明檔，並找出您所記錄之 Cmdlet 的命令節點。</span><span class="sxs-lookup"><span data-stu-id="a4e05-111">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="a4e05-112">如果您要新增新的 Cmdlet，您將需要建立新的命令節點。</span><span class="sxs-lookup"><span data-stu-id="a4e05-112">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="a4e05-113">您的說明檔會包含每個 Cmdlet 的命令節點，您提供的說明內容。</span><span class="sxs-lookup"><span data-stu-id="a4e05-113">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="a4e05-114">以下是空白的命令節點範例。</span><span class="sxs-lookup"><span data-stu-id="a4e05-114">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

1. <span data-ttu-id="a4e05-115">在命令節點內，找出 [描述] 節點並加入 [參數] 節點，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a4e05-115">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span>
   <span data-ttu-id="a4e05-116">只允許一個參數節點，而且應該緊接在語法節點後面。</span><span class="sxs-lookup"><span data-stu-id="a4e05-116">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

1. <span data-ttu-id="a4e05-117">在 [參數] 節點內，為 Cmdlet 的每個參數新增 **參數** 節點，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a4e05-117">Within the Parameters node, add a **Parameter** node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="a4e05-118">在此範例中，會針對三個參數加入 **參數** 節點。</span><span class="sxs-lookup"><span data-stu-id="a4e05-118">In this example, a **Parameter** node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="a4e05-119">因為這些是在語法節點中使用的相同 XML 標記，而且在這裡指定的參數必須符合語法節點所指定的參數，所以您可以從語法節點複製參數節點，並將其貼入 [參數] 節點。</span><span class="sxs-lookup"><span data-stu-id="a4e05-119">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="a4e05-120">不過，請務必只複製一個參數節點的實例，即使參數是在語法中的多個參數集內指定的。</span><span class="sxs-lookup"><span data-stu-id="a4e05-120">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

1. <span data-ttu-id="a4e05-121">針對每個參數節點設定屬性值，以定義每個參數的特性。</span><span class="sxs-lookup"><span data-stu-id="a4e05-121">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="a4e05-122">這些屬性包括下列各項：必要、萬用字元、pipelineinput 和位置。</span><span class="sxs-lookup"><span data-stu-id="a4e05-122">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

1. <span data-ttu-id="a4e05-123">針對每個參數節點，加入參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4e05-123">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="a4e05-124">以下是新增至參數節點的參數名稱範例。</span><span class="sxs-lookup"><span data-stu-id="a4e05-124">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

1. <span data-ttu-id="a4e05-125">針對每個 **參數** 節點，加入參數的描述。</span><span class="sxs-lookup"><span data-stu-id="a4e05-125">For each **Parameter** node, add the description of the parameter.</span></span> <span data-ttu-id="a4e05-126">以下是新增至 **參數** 節點的參數描述範例。</span><span class="sxs-lookup"><span data-stu-id="a4e05-126">Here is an example of the parameter description added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="a4e05-127">針對每個 **參數** 節點，加入參數的 .net 型別。</span><span class="sxs-lookup"><span data-stu-id="a4e05-127">For each **Parameter** node, add the .NET type of the parameter.</span></span> <span data-ttu-id="a4e05-128">參數類型會與參數名稱一起顯示。</span><span class="sxs-lookup"><span data-stu-id="a4e05-128">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="a4e05-129">以下是已加入至 **參數** 節點之參數 .net 類型的範例。</span><span class="sxs-lookup"><span data-stu-id="a4e05-129">Here is an example of the parameter .NET type added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="a4e05-130">針對每個 **參數** 節點，加入參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="a4e05-130">For each **Parameter** node, add the default value of the parameter.</span></span> <span data-ttu-id="a4e05-131">當顯示內容時，會將下列句子新增至參數描述： **DefaultValue** 是預設值。</span><span class="sxs-lookup"><span data-stu-id="a4e05-131">The following sentence is added to the parameter description when the content is displayed: **DefaultValue** is the default.</span></span>

   <span data-ttu-id="a4e05-132">以下是將參數預設值新增至 **參數** 節點的範例。</span><span class="sxs-lookup"><span data-stu-id="a4e05-132">Here is an example of the parameter default value is added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="a4e05-133">針對具有多個值的每個參數，新增可能的值節點。</span><span class="sxs-lookup"><span data-stu-id="a4e05-133">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="a4e05-134">以下是可能值節點的範例，其中定義參數的兩個可能值。</span><span class="sxs-lookup"><span data-stu-id="a4e05-134">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="a4e05-135">以下是新增參數時要記住的一些事項。</span><span class="sxs-lookup"><span data-stu-id="a4e05-135">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="a4e05-136">參數的屬性不會顯示在 Cmdlet 說明主題的所有視圖中。</span><span class="sxs-lookup"><span data-stu-id="a4e05-136">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="a4e05-137">不過，當使用者要求 () 視圖的 **完整** (`Get-Help <cmdletname> -full`) 或 **參數** 時，它們會顯示在下表中的參數描述 `Get-Help <cmdletname> -parameter` 。</span><span class="sxs-lookup"><span data-stu-id="a4e05-137">However, they are displayed in a table following the parameter description when the user asks for the **Full** (`Get-Help <cmdletname> -full`) or **Parameter** (`Get-Help <cmdletname> -parameter`) view of the topic.</span></span>

- <span data-ttu-id="a4e05-138">參數描述是 Cmdlet 說明主題最重要的部分之一。</span><span class="sxs-lookup"><span data-stu-id="a4e05-138">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="a4e05-139">描述應該是簡短的，也可以是完整的。</span><span class="sxs-lookup"><span data-stu-id="a4e05-139">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="a4e05-140">此外，請記住，如果參數描述變得太長，例如當兩個參數彼此互動時，您可以在 Cmdlet 說明主題的 NOTES 區段中新增更多內容。</span><span class="sxs-lookup"><span data-stu-id="a4e05-140">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="a4e05-141">參數描述提供兩種類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="a4e05-141">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="a4e05-142">使用參數時，Cmdlet 會執行的工作。</span><span class="sxs-lookup"><span data-stu-id="a4e05-142">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="a4e05-143">參數的合法值。</span><span class="sxs-lookup"><span data-stu-id="a4e05-143">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="a4e05-144">因為參數值是以 .NET 物件表示，所以使用者需要這些值的詳細資訊，而不是傳統的命令列說明。</span><span class="sxs-lookup"><span data-stu-id="a4e05-144">Because the parameter values are expressed as .NET objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="a4e05-145">告訴使用者參數設計要接受何種類型的資料，並包含範例。</span><span class="sxs-lookup"><span data-stu-id="a4e05-145">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="a4e05-146">參數的預設值是在命令列上未指定參數時，所使用的值。</span><span class="sxs-lookup"><span data-stu-id="a4e05-146">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="a4e05-147">請注意，預設值是選擇性的，某些參數（例如必要的參數）不需要此值。</span><span class="sxs-lookup"><span data-stu-id="a4e05-147">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="a4e05-148">不過，您應該針對大部分的選擇性參數指定預設值。</span><span class="sxs-lookup"><span data-stu-id="a4e05-148">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="a4e05-149">預設值可協助使用者瞭解不使用參數的效果。</span><span class="sxs-lookup"><span data-stu-id="a4e05-149">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="a4e05-150">明確說明預設值，例如「目前的目錄」或「PowerShell 安裝目錄 () 」作為 `$PSHOME` 選擇性路徑。</span><span class="sxs-lookup"><span data-stu-id="a4e05-150">Describe the default value very specifically, such as the "Current directory" or the "PowerShell installation directory (`$PSHOME`)" for an optional path.</span></span> <span data-ttu-id="a4e05-151">您也可以撰寫描述預設值的句子，例如用於 **passthru** 參數的下列句子：「如果未指定 passthru，Cmdlet 不會將物件沿著管線向下傳遞」。</span><span class="sxs-lookup"><span data-stu-id="a4e05-151">You can also write a sentence that describes the default, such as the following sentence used for the **PassThru** parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span> <span data-ttu-id="a4e05-152">此外，因為值的顯示方式與功能變數名稱 **預設值** 相反，所以您不需要在專案中包含「預設值」一詞。</span><span class="sxs-lookup"><span data-stu-id="a4e05-152">Also, because the value is displayed opposite the field name **Default value**, you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="a4e05-153">參數的預設值不會顯示在 Cmdlet 說明主題的所有視圖中。</span><span class="sxs-lookup"><span data-stu-id="a4e05-153">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="a4e05-154">不過，它會顯示在資料表中 (以及當使用者要求整個主題的 **完整** (`Get-Help <cmdletname> -full`) 或 **參數** () 時，) 遵循參數描述的參數屬性 `Get-Help
<cmdletname> -parameter` 。</span><span class="sxs-lookup"><span data-stu-id="a4e05-154">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the **Full** (`Get-Help <cmdletname> -full`) or **Parameter** (`Get-Help
<cmdletname> -parameter`) view of the topic.</span></span>

<span data-ttu-id="a4e05-155">下列 XML 會顯示 `<dev:defaultValue>` 新增至節點的一對標記 `<command:parameter>` 。</span><span class="sxs-lookup"><span data-stu-id="a4e05-155">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span>
<span data-ttu-id="a4e05-156">請注意，當指定參數值時，預設值緊接在結尾 `</command:parameterValue>` 標記之後 (，) 或 `</maml:description>` 參數描述的結束記號。</span><span class="sxs-lookup"><span data-stu-id="a4e05-156">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="a4e05-157">名稱。</span><span class="sxs-lookup"><span data-stu-id="a4e05-157">name.</span></span>

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

<span data-ttu-id="a4e05-158">新增列舉類型的值</span><span class="sxs-lookup"><span data-stu-id="a4e05-158">Add Values for Enumerated Types</span></span>

<span data-ttu-id="a4e05-159">如果參數有多個值或列舉類型的值，您可以使用選擇性 \<dev:possibleValues> 節點。</span><span class="sxs-lookup"><span data-stu-id="a4e05-159">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="a4e05-160">此節點可讓您指定多個值的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="a4e05-160">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="a4e05-161">請注意，列舉值的描述不會出現在 Cmdlet 所顯示的任何預設說明視圖中 `Get-Help` ，但其他說明檢視器可能會在其視圖中顯示此內容。</span><span class="sxs-lookup"><span data-stu-id="a4e05-161">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="a4e05-162">下列 XML 會顯示 `<dev:possibleValues>` 具有兩個指定值的節點。</span><span class="sxs-lookup"><span data-stu-id="a4e05-162">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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
