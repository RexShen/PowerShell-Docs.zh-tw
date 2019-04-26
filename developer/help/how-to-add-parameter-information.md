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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083360"
---
# <a name="how-to-add-parameter-information"></a>如何新增參數資訊

本節說明如何新增會顯示 cmdlet 說明主題的參數區段中的內容。 [說明] 主題的 PARAMETERS 區段會列出每個 cmdlet 的參數，並提供每個參數的詳細的描述。

參數區段的內容應該是一致的語法 」 一節說明主題的內容。 它負責說明作者，以確定語法和參數 節點包含類似的 XML 項目。

> [!NOTE]
> 說明檔案，開啟其中一個 dll Help.xml 檔案位於 Windows PowerShell 安裝目錄的完整檢視。 比方說，Microsoft.PowerShell.Commands.Management.dll Help.xml 檔案會包含內容的數個 Windows PowerShell cmdlet。

### <a name="to-add-parameters"></a>若要加入參數

1. 開啟的 cmdlet 說明檔，並找出您所記載的 cmdlet 的命令 節點。 如果您要新增新的 cmdlet，您必須建立新的 [命令] 節點。 說明檔會包含您要提供的說明內容的每個 cmdlet 的命令節點。 以下是空白的命令節點的範例。

    ```xml
    <command:command>
    </command:command>
    ```

2. 在 [命令] 節點中，找出 [描述] 節點，並將 [參數] 節點，如下所示。 將允許只有一個參數 節點，而它應該緊接語法節點。

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. 在 [參數] 節點中，請新增 cmdlet 的每個參數的參數節點，如下所示。

   在此範例中，針對三個參數加入的參數節點。

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   因為這些都是相同的 XML 標記，它會在語法節點，而且因為此處指定的參數必須符合指定的語法節點的參數，您可以複製語法節點中的參數節點，並將其貼到 [參數] 節點。 不過，請務必複製的參數節點只有一個執行個體，即使參數中指定多個參數是設定在語法中。

4. 針對每個參數 節點中，設定屬性值定義每個參數的特性。 這些屬性包括下列： 有需要，萬用字元、 pipelineinput 和位置。

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

5. 針對每個參數 節點中，新增參數的名稱。 以下是範例參數名稱加入至參數的節點。

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. 針對每個參數 節點中，新增參數的描述。 以下是新增至 [參數] 節點的參數描述的範例。

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

7. 針對每個參數 節點中，新增參數的.NET Framework 型別。 參數類型會顯示與參數名稱。

   以下是參數的.NET Framework 型別新增至 [參數] 節點的範例。

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

8. 針對每個參數 節點中，新增參數的預設值。 顯示內容時，下列句子被新增參數描述：預設值為 「 DefaultValue 」。

   以下是範例的參數預設值加入至參數的節點。

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

9. 每個參數有多個值，將 可能的值節點。

   以下是範例定義兩個可能的值，參數可能的值節點的

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

以下是要加入參數時，必須記住的一些事項。

- 參數的屬性不會顯示在所有檢視中的 cmdlet 說明主題。 不過，它們會顯示在下列參數的描述，當使用者要求完整的資料表 (Get-help \<cmdletname >-完整) 或參數 (Get-help \<cmdletname >-參數) 主題的檢視。

- 參數描述是其中一個最重要的組件的 cmdlet 說明主題。 描述應為簡短，以及完整。 此外，請記住，是否參數描述變得太長，例如當兩個參數的互動方式，您可以新增更多的內容中的 cmdlet 說明主題的附註 區段。

  參數描述會提供兩種類型的資訊。

- Cmdlet 的功能時使用的參數。

- 哪些合法的值為參數。

- 參數值會表示為.NET Framework 物件，因為使用者如需有關這些值不像傳統的命令列說明。 告訴使用者的接受，旨在參數的資料類型，並包括範例。

如果未在命令列上指定的參數會使用值為參數的預設值。 請注意，預設值是選擇性的而且不需要某些參數，例如必要的參數。 不過，您應該指定大部分的選擇性參數的預設值。

預設值可協助使用者了解如何不使用此參數的效果。 描述非常具體來說，例如 「 目前的目錄 」 或 「 Windows PowerShell 安裝目錄 ($pshome) 」 的選擇性路徑的預設值。 您也可以撰寫描述預設值，例如用於下列句子的句子`PassThru`參數：「 如果未指定 PassThru，cmdlet 未通過物件沿著管線向下的。 」  此外，因為相反的欄位名稱會顯示值"**預設值**」，您不需要的項目中包含 「 預設值 」 一詞。

參數的預設值不會顯示在所有檢視中的 cmdlet 說明主題。 不過，它會顯示在下列參數的描述，當使用者要求完整的資料表 （以及參數屬性） (Get-help \<cmdletname >-full) 或參數 (Get-help \<cmdletname >-參數) 檢視主題。

下列 XML 會顯示一組`<dev:defaultValue>`加入至標記`<command:parameter>`節點。 請注意，預設值會遵循關閉之後緊接著`</command:parameterValue>`標記 （當指定的參數值） 或關閉`</maml:description>`標記的參數描述。 名稱。

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

新增列舉型別值

如果參數有多個值或值的列舉型別，您可以使用選擇性\<dev:possibleValues > 節點。 此節點可讓您指定的名稱和描述多個值。

請注意，列舉值的描述不會出現在任何預設值所顯示的說明檢視`Get-Help`cmdlet，但其他的說明檢視器可能會在其檢視中顯示此內容。

下列 XML 會說明`<dev:possibleValues>`節點與兩個指定的值。

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