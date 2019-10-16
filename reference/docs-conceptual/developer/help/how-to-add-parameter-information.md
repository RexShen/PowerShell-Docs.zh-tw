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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361227"
---
# <a name="how-to-add-parameter-information"></a>如何新增參數資訊

本節說明如何新增在 Cmdlet 說明主題的 PARAMETERS 區段中所顯示的內容。 說明主題的 PARAMETERS 區段會列出 Cmdlet 的每個參數，並提供每個參數的詳細描述。

[參數] 區段的內容應該與說明主題的 [語法] 區段內容一致。 說明作者必須負責確保 [語法] 和 [參數] 節點包含類似的 XML 元素。

> [!NOTE]
> 如需說明檔的完整視圖，請開啟位於 Windows PowerShell 安裝目錄中的其中一個 dll-Help 檔案。 例如，dll-Help 檔案包含數個 Windows PowerShell 指令程式的內容（content）。

### <a name="to-add-parameters"></a>若要加入參數

1. 開啟 Cmdlet 說明檔，並找出您所記錄之 Cmdlet 的命令節點。 如果您要新增新的 Cmdlet，您將需要建立新的命令節點。 您的說明檔會針對您提供說明內容的每個 Cmdlet，各包含一個命令節點。 以下是空白命令節點的範例。

    ```xml
    <command:command>
    </command:command>
    ```

2. 在 [命令] 節點中，找出 [描述] 節點並新增 [參數] 節點，如下所示。 只允許一個參數節點，而且應該緊接在語法節點後面。

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. 在 [參數] 節點中，為 Cmdlet 的每個參數新增參數節點，如下所示。

   在此範例中，會加入三個參數的參數節點。

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   因為這些是語法節點中所使用的相同 XML 標記，而且在此處指定的參數必須符合語法節點所指定的參數，所以您可以從語法節點複製參數節點，並將它們貼入 [參數] 節點。 不過，請務必只複製一個參數節點的實例，即使在語法的多個參數集中指定了參數也一樣。

4. 針對每個參數節點，設定屬性值，以定義每個參數的特性。 這些屬性包括下列各項： required、通配、pipelineinput 和 position。

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

5. 針對每個參數節點，新增參數的名稱。 以下是將參數名稱新增至參數節點的範例。

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. 針對每個參數節點，新增參數的描述。 以下是將參數描述新增至參數節點的範例。

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

7. 針對每個參數節點，新增參數的 .NET Framework 類型。 參數類型會與參數名稱一起顯示。

   以下是將參數加入至參數節點 .NET Framework 類型的範例。

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

8. 針對每個參數節點，新增參數的預設值。 顯示內容時，會將下列句子加入至參數描述： "DefaultValue" 是預設值。

   以下是將參數預設值新增至參數節點的範例。

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

9. 針對每個具有多個值的參數，新增 [可能的值] 節點。

   以下是可能值節點的範例，其定義參數的兩個可能值。

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

以下是新增參數時要記住的一些事項。

- 參數的屬性不會顯示在 Cmdlet 說明主題的所有視圖中。 不過，當使用者要求完整（Get-help \<Cmdletname >-Full）或主題的參數（Get-help \<Cmdletname >-參數）時，它們會顯示在參數描述後面的表格中。

- 參數描述是 Cmdlet 說明主題其中一個最重要的部分。 描述應該是簡短的，也應該是完整的。 此外，請記住，如果參數描述變得太長，例如兩個參數彼此互動時，您可以在 Cmdlet 說明主題的附注區段中新增更多內容。

  參數描述提供兩種類型的資訊。

- 使用參數時，Cmdlet 會執行的工作。

- 參數的合法值。

- 因為參數值會表示為 .NET Framework 物件，所以使用者需要這些值的詳細資訊，而不是傳統命令列說明中的。 告知使用者參數設計要接受的資料類型，並包含範例。

參數的預設值是在命令列上未指定參數時所使用的值。 請注意，預設值是選擇性的，而某些參數（例如必要的參數）則不需要。 不過，您應該為大部分的選擇性參數指定預設值。

預設值可協助使用者瞭解不使用參數的效果。 明確描述預設值，例如「目前目錄」或選擇性路徑的「Windows PowerShell 安裝目錄（$pshome）」。 您也可以撰寫描述預設值的句子，例如用於 `PassThru` 參數的下列句子：「如果未指定 PassThru，Cmdlet 就不會將物件沿著管線向下傳遞」。  此外，因為此值會與功能變數名稱「**預設值**」相反地顯示，所以您不需要在專案中包含「預設值」一詞。

此參數的預設值不會顯示在 Cmdlet 說明主題的所有 views 中。 不過，當使用者要求完整（Get-help \<Cmdletname >-Full）或主題的參數（Get-help \<Cmdletname >-parameter）時，它會在參數描述之後，顯示在資料表中（連同參數屬性）。

下列 XML 顯示已新增至 `<command:parameter>` 節點的一對 `<dev:defaultValue>` 標記。 請注意，預設值會緊接在結尾 `</command:parameterValue>` 標記之後（指定參數值時），或是參數描述的結尾 `</maml:description>` 標記後面。 檔案名.

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

如果參數有多個值或列舉類型的值，您可以使用選擇性的 @no__t 0dev： possibleValues > 節點。 此節點可讓您指定多個值的名稱和描述。

請注意，列舉值的描述不會出現在 `Get-Help` Cmdlet 所顯示的任何預設說明視圖中，但其他說明檢視器可能會在其視圖中顯示此內容。

下列 XML 顯示已指定兩個值的 @no__t 0 節點。

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