---
title: 建立自訂控制項 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363377"
---
# <a name="creating-custom-controls"></a>建立自訂控制項

自訂控制項是格式檔案中最具彈性的元件。 不同于定義正式資料結構（例如資料資料表）的資料表、清單和寬型視圖，自訂控制項可讓您定義個別資料片段的顯示方式。 您可以定義一組常用的自訂控制項，以供格式檔案的所有視圖使用，您可以定義可用於特定視圖的自訂控制項，也可以定義一組可用於物件群組的控制項。

## <a name="custom-control-example"></a>自訂控制項範例

下列範例顯示在 types.ps1xml 檔案中定義的自訂控制項。 這個自訂控制項是用來分隔在資料表視圖中顯示的[system.web. Signature](/dotnet/api/System.Management.Automation.Signature)物件。

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

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
