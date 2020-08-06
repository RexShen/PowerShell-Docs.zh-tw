---
title: 建立自訂控制項 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c36fa9b778e01501a3c88f735cdefdfbb04411a0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786113"
---
# <a name="creating-custom-controls"></a>建立自訂控制項

自訂控制項是格式檔案中最具彈性的元件。 不同于定義正式資料結構（例如資料資料表）的資料表、清單和寬型視圖，自訂控制項可讓您定義個別資料片段的顯示方式。 您可以定義一組常用的自訂控制項，以供格式檔案的所有視圖使用，您可以定義可用於特定視圖的自訂控制項，也可以定義一組可用於物件群組的控制項。

## <a name="custom-control-example"></a>自訂控制項範例

下列範例顯示在 Certificates.Format.ps1xml 檔案中定義的自訂控制項。 這個自訂控制項是用來分隔在資料表視圖中顯示的[system.web. Signature](/dotnet/api/System.Management.Automation.Signature)物件。

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
