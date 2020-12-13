---
ms.date: 09/13/2016
ms.topic: reference
title: 建立自訂控制項
description: 建立自訂控制項
ms.openlocfilehash: 78d8cc2970b2b3e493bef25d78404ba1be195bb1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668043"
---
# <a name="creating-custom-controls"></a>建立自訂控制項

自訂控制項是格式化檔案中最具彈性的元件。 不同于定義資料的正式結構（例如資料表）的資料表、清單和寬視圖，自訂控制項可讓您定義個別資料片段的顯示方式。 您可以定義一組通用的自訂控制項，這些控制項可供格式化檔案的所有視圖使用，您可以定義特定視圖可用的自訂控制項，也可以定義一組可供物件群組使用的控制項。

## <a name="custom-control-example"></a>自訂控制項範例

下列範例顯示 Certificates.Format.ps1xml 檔案中定義的自訂控制項。 此自訂控制項是用來分隔顯示在資料表視圖中的 [系統. 管理. Signature](/dotnet/api/System.Management.Automation.Signature) 物件。

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
