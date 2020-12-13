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
# <a name="how-to-add-parameter-information"></a>如何新增參數資訊

本節說明如何新增在 Cmdlet 說明主題的 **PARAMETERS** 區段中顯示的內容。 說明主題的 **parameters** 區段會列出 Cmdlet 的每個參數，並提供每個參數的詳細描述。

[ **參數** ] 區段的內容應該與 [説明] 主題的 [ **語法** ] 區段內容一致。 說明作者必須負責確定 [ **語法** ] 和 [ **參數** ] 節點都包含類似的 XML 元素。

> [!NOTE]
> 如需說明檔的完整觀點，請開啟 `dll-Help.xml` 位於 PowerShell 安裝目錄中的其中一個檔案。 例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。

### <a name="to-add-parameters"></a>若要加入參數

1. 開啟 Cmdlet 說明檔，並找出您所記錄之 Cmdlet 的命令節點。 如果您要新增新的 Cmdlet，您將需要建立新的命令節點。 您的說明檔會包含每個 Cmdlet 的命令節點，您提供的說明內容。 以下是空白的命令節點範例。

    ```xml
    <command:command>
    </command:command>
    ```

1. 在命令節點內，找出 [描述] 節點並加入 [參數] 節點，如下所示。
   只允許一個參數節點，而且應該緊接在語法節點後面。

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

1. 在 [參數] 節點內，為 Cmdlet 的每個參數新增 **參數** 節點，如下所示。

   在此範例中，會針對三個參數加入 **參數** 節點。

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   因為這些是在語法節點中使用的相同 XML 標記，而且在這裡指定的參數必須符合語法節點所指定的參數，所以您可以從語法節點複製參數節點，並將其貼入 [參數] 節點。 不過，請務必只複製一個參數節點的實例，即使參數是在語法中的多個參數集內指定的。

1. 針對每個參數節點設定屬性值，以定義每個參數的特性。 這些屬性包括下列各項：必要、萬用字元、pipelineinput 和位置。

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

1. 針對每個參數節點，加入參數的名稱。 以下是新增至參數節點的參數名稱範例。

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

1. 針對每個 **參數** 節點，加入參數的描述。 以下是新增至 **參數** 節點的參數描述範例。

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

1. 針對每個 **參數** 節點，加入參數的 .net 型別。 參數類型會與參數名稱一起顯示。

   以下是已加入至 **參數** 節點之參數 .net 類型的範例。

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

1. 針對每個 **參數** 節點，加入參數的預設值。 當顯示內容時，會將下列句子新增至參數描述： **DefaultValue** 是預設值。

   以下是將參數預設值新增至 **參數** 節點的範例。

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

1. 針對具有多個值的每個參數，新增可能的值節點。

   以下是可能值節點的範例，其中定義參數的兩個可能值。

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

以下是新增參數時要記住的一些事項。

- 參數的屬性不會顯示在 Cmdlet 說明主題的所有視圖中。 不過，當使用者要求 () 視圖的 **完整** (`Get-Help <cmdletname> -full`) 或 **參數** 時，它們會顯示在下表中的參數描述 `Get-Help <cmdletname> -parameter` 。

- 參數描述是 Cmdlet 說明主題最重要的部分之一。 描述應該是簡短的，也可以是完整的。 此外，請記住，如果參數描述變得太長，例如當兩個參數彼此互動時，您可以在 Cmdlet 說明主題的 NOTES 區段中新增更多內容。

  參數描述提供兩種類型的資訊。

- 使用參數時，Cmdlet 會執行的工作。

- 參數的合法值。

- 因為參數值是以 .NET 物件表示，所以使用者需要這些值的詳細資訊，而不是傳統的命令列說明。 告訴使用者參數設計要接受何種類型的資料，並包含範例。

參數的預設值是在命令列上未指定參數時，所使用的值。 請注意，預設值是選擇性的，某些參數（例如必要的參數）不需要此值。 不過，您應該針對大部分的選擇性參數指定預設值。

預設值可協助使用者瞭解不使用參數的效果。 明確說明預設值，例如「目前的目錄」或「PowerShell 安裝目錄 () 」作為 `$PSHOME` 選擇性路徑。 您也可以撰寫描述預設值的句子，例如用於 **passthru** 參數的下列句子：「如果未指定 passthru，Cmdlet 不會將物件沿著管線向下傳遞」。 此外，因為值的顯示方式與功能變數名稱 **預設值** 相反，所以您不需要在專案中包含「預設值」一詞。

參數的預設值不會顯示在 Cmdlet 說明主題的所有視圖中。 不過，它會顯示在資料表中 (以及當使用者要求整個主題的 **完整** (`Get-Help <cmdletname> -full`) 或 **參數** () 時，) 遵循參數描述的參數屬性 `Get-Help
<cmdletname> -parameter` 。

下列 XML 會顯示 `<dev:defaultValue>` 新增至節點的一對標記 `<command:parameter>` 。
請注意，當指定參數值時，預設值緊接在結尾 `</command:parameterValue>` 標記之後 (，) 或 `</maml:description>` 參數描述的結束記號。 名稱。

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

新增列舉類型的值

如果參數有多個值或列舉類型的值，您可以使用選擇性 \<dev:possibleValues> 節點。 此節點可讓您指定多個值的名稱和描述。

請注意，列舉值的描述不會出現在 Cmdlet 所顯示的任何預設說明視圖中 `Get-Help` ，但其他說明檢視器可能會在其視圖中顯示此內容。

下列 XML 會顯示 `<dev:possibleValues>` 具有兩個指定值的節點。

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
