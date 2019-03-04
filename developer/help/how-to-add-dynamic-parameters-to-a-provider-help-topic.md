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
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859874"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>如何新增動態參數至提供者說明主題

本節說明如何以填入**動態參數**區段的提供者說明主題。

*動態參數*是 cmdlet 的參數或函式，可只在指定的條件。

提供者說明主題中所述的動態參數是動態參數提供者磁碟機中使用的 cmdlet 或函式時，提供者新增至 cmdlet 或函式。

動態參數也有記載在 提供者的自訂 cmdlet 說明。 當撰寫提供者的提供者說明和自訂的 cmdlet 說明，包含動態參數文件中兩份文件。 如需有關自訂的 cmdlet 說明的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 自訂 Cmdlet 說明的提供者](./writing-custom-cmdlet-help-for-windows-powershell-providers.md)。

如果提供者未實作任何動態參數，提供者的 [說明] 主題包含空`DynamicParameters`項目。

### <a name="to-add-dynamic-parameters"></a>若要新增的動態參數

1. 在  *AssemblyName*.dll help.xml 檔案，內`providerHelp`項目，新增`DynamicParameters`項目。 `DynamicParameters`後的項目應該會出現`Tasks`項目和前面`RelatedLinks`項目。

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

   如果提供者未實作任何動態參數，`DynamicParameters`項目可以是空白。

2. 內`DynamicParameters`項目，每個動態參數，新增`DynamicParameter`項目。

   例如：

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. 在每個`DynamicParameter`項目，新增`Name`和`CmdletSupported`項目。

   |元素名稱|描述|
   |------------------|-----------------|
   |名稱|指定參數名稱。|
   |CmdletSupported|指定的 cmdlet 參數無效。 輸入 cmdlet 名稱的逗號分隔清單。|

   例如，下列的 XML 文件`Encoding`Windows PowerShell FileSystem 提供者新增到的動態參數`Add-Content`， `Get-Content`， `Set-Content` cmdlet。

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. 在每個`DynamicParameter`項目，新增`Type`項目。 `Type`項目是容器`Name`所在的.NET 類型的動態參數值的項目。

   例如，下列 XML 顯示的.NET 類型`Encoding`動態參數是[Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)列舉型別。

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

5. 新增`Description`元素，其中包含的動態參數的簡短描述。 當您在撰寫描述，使用中的所有 cmdlet 參數所都規定的指導方針[如何新增參數資訊](./how-to-add-parameter-information.md)。

   比方說，下列 XML 會包含描述`Encoding`動態參數。

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

6. 新增`PossibleValues`項目和其子項目。 在一起，這些元素會說明動態參數的值。 這個項目被設計用於列舉的值。 如果動態參數不接受的值，這類案例，並切換參數，或無法列舉的值，加入空白`PossibleValues`項目。

   下表列出並描述`PossibleValues`項目和其子項目。

   |元素名稱|描述|
   |------------------|-----------------|
   |PossibleValues|這個項目是一個容器。 其子項目如下所述。 加入一個`PossibleValues`每個提供者說明主題的項目。 項目可以是空的。|
   |PossibleValue|這個項目是一個容器。 其子項目如下所述。 加入一個`PossibleValue`動態參數的每個值的項目。|
   |值|指定值的名稱。|
   |描述|這個項目包含`Para`項目。 中的文字`Para`項目會描述出現在值`Value`項目。|

   例如，下列 XML 會顯示其中一個`PossibleValue`項目`Encoding`動態參數。

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

下列範例所示`DynamicParameters`項目`Encoding`動態參數。

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