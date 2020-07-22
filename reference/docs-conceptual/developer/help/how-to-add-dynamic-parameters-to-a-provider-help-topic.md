---
title: 如何新增動態參數至提供者說明主題
ms.date: 09/13/2016
ms.openlocfilehash: ddf964292ee7bf477767a2ca17c717aef84bad51
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893453"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>如何新增動態參數至提供者說明主題

本節說明如何填入提供者說明主題的**動態參數**一節。

*動態參數*是 Cmdlet 或函式的參數，只有在指定的條件下才可使用。

提供者說明主題中記載的動態參數是在提供者磁片磁碟機中使用 Cmdlet 或函式時，提供者新增至 Cmdlet 或函式的動態參數。

動態參數也可以在提供者的自訂 Cmdlet 說明中記載。 為提供者撰寫提供者說明和自訂 Cmdlet 說明時，請在這兩份檔中包含動態參數檔。

如果提供者未執行任何動態參數，提供者說明主題會包含空的 `DynamicParameters` 元素。

### <a name="to-add-dynamic-parameters"></a>新增動態參數

1. 在檔案中 `<AssemblyName>.dll-help.xml` 的專案內 `providerHelp` ，加入 `DynamicParameters` 元素。 `DynamicParameters`元素應出現在元素之後 `Tasks` 和專案之前 `RelatedLinks` 。

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

   如果提供者未執行任何動態參數， `DynamicParameters` 元素可以是空的。

1. 在專案中， `DynamicParameters` 針對每個動態參數加入 `DynamicParameter` 元素。

   例如：

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

1. 在每個專案中 `DynamicParameter` ，加入 `Name` and `CmdletSupported` 元素。

   - 名稱-指定參數名稱
   - CmdletSupported-指定參數有效的 Cmdlet。 輸入以逗號分隔的 Cmdlet 名稱清單。

   例如，下列 XML 記載 `Encoding` Windows PowerShell FileSystem 提供者新增至 `Add-Content` 、 `Get-Content` 、Cmdlet 的動態參數 `Set-Content` 。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

1. 在每個專案中 `DynamicParameter` ，新增 `Type` 元素。 `Type`元素是元素的容器， `Name` 其中包含動態參數值的 .net 類型。

   例如，下列 XML 顯示動態參數的 .NET 類型 `Encoding` 為[filesystemCmdletproviderencoding parameter sets](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)列舉。

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

1. 加入 `Description` 元素，其中包含動態參數的簡短描述。 撰寫描述時，請使用[如何新增參數資訊](./how-to-add-parameter-information.md)中的所有 Cmdlet 參數所規定的指導方針。

   例如，下列 XML 包含 `Encoding` 動態參數的描述。

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

1. 加入 `PossibleValues` 元素及其子專案。 這些元素一起描述動態參數的值。 此元素是針對列舉值所設計。 如果動態參數未採用值（例如，如果是具有切換參數的案例），或無法列舉值，請加入空的 `PossibleValues` 元素。

   下表列出並描述 `PossibleValues` 元素及其子項目。

   - PossibleValues-此元素是容器。 其子項目如下所述。 將一個 `PossibleValues` 元素新增至每個提供者說明主題。 元素可以是空的。
   - PossibleValue-此元素是容器。 其子項目如下所述。 `PossibleValue`為動態參數的每個值新增一個元素。
   - 值-指定值名稱。
   - Description-此元素包含 `Para` 元素。 元素中的文字 `Para` 描述元素中所命名的值 `Value` 。

   例如，下列 XML 會顯示 `PossibleValue` 動態參數的一個元素 `Encoding` 。

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

下列範例顯示 `DynamicParameters` `Encoding` 動態參數的元素。

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
