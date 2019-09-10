---
title: 如何將動態參數新增至提供者說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848109"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>如何新增動態參數至提供者說明主題

本節說明如何填入提供者說明主題的**動態參數**一節。

*動態參數*是 Cmdlet 或函式的參數，只有在指定的條件下才可使用。

提供者說明主題中記載的動態參數是在提供者磁片磁碟機中使用 Cmdlet 或函式時，提供者新增至 Cmdlet 或函式的動態參數。

動態參數也可以在提供者的自訂 Cmdlet 說明中記載。 為提供者撰寫提供者說明和自訂 Cmdlet 說明時，請在這兩份檔中包含動態參數檔。

如果提供者未執行任何動態參數，提供者說明主題會包含空`DynamicParameters`的元素。

### <a name="to-add-dynamic-parameters"></a>新增動態參數

1. 在 dll-help .xml `providerHelp` *檔案的專案*中，新增`DynamicParameters`專案。 元素應出現在`Tasks`元素之後和專案之前`RelatedLinks`。 `DynamicParameters`

   例如：

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   如果提供者未執行任何動態參數，元素可以`DynamicParameters`是空的。

2. 在專案中，針對每個動態參數`DynamicParameter`加入元素。 `DynamicParameters`

   例如：

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. 在每`DynamicParameter`個專案中， `Name`加入`CmdletSupported` and 元素。

   |元素名稱|描述|
   |------------------|-----------------|
   |名稱|指定參數名稱。|
   |CmdletSupported|指定參數有效的 Cmdlet。 輸入以逗號分隔的 Cmdlet 名稱清單。|

   例如，下列 XML 記載 Windows PowerShell FileSystem `Encoding`提供者新增`Add-Content`至、 `Get-Content`、 `Set-Content` Cmdlet 的動態參數。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. 在每`DynamicParameter`個專案中， `Type`新增元素。 元素是`Name`元素的容器，其中包含動態參數值的 .net 類型。 `Type`

   例如，下列 XML 會顯示`Encoding`動態參數的 .net 型別為[filesystemCmdletproviderencoding parameter sets](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)列舉的。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. `Description`加入元素，其中包含動態參數的簡短描述。 撰寫描述時，請使用[如何新增參數資訊](./how-to-add-parameter-information.md)中的所有 Cmdlet 參數所規定的指導方針。

   例如，下列 XML 包含`Encoding`動態參數的描述。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. `PossibleValues`加入元素及其子專案。 這些元素一起描述動態參數的值。 此元素是針對列舉值所設計。 如果動態參數未採用值（例如，如果是具有切換參數的案例），或無法列舉值，請加入空`PossibleValues`的元素。

   下表列出並描述`PossibleValues`元素及其子項目。

   |元素名稱|描述|
   |------------------|-----------------|
   |PossibleValues|此元素是容器。 其子項目如下所述。 將一個`PossibleValues`元素新增至每個提供者說明主題。 元素可以是空的。|
   |PossibleValue|此元素是容器。 其子項目如下所述。 為動態`PossibleValue`參數的每個值新增一個元素。|
   |值|指定值名稱。|
   |描述|此元素包含`Para`元素。 `Para`元素中的文字描述`Value`元素中所命名的值。|

   例如，下列 XML 會顯示`PossibleValue` `Encoding`動態參數的一個元素。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>範例

下列範例顯示`Encoding`動態參數`DynamicParameters`的元素。

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```