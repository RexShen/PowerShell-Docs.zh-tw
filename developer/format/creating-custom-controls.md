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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853194"
---
# <a name="creating-custom-controls"></a>建立自訂控制項

自訂控制項是最具彈性的格式化檔案元件。 與資料表、 清單和定義正式的資料，例如資料的資料表，結構的寬型檢視不同的是自訂的控制項可讓您定義個別的一段資料的顯示方式。 您可以定義一組常用的自訂控制項所提供的格式化檔案的所有檢視，您可以定義自訂的控制項，且適用於特定的檢視，或您可以定義一組可用於一整組物件的控制項。

## <a name="custom-control-example"></a>自訂控制項範例

下列範例顯示 Certificates.Format.ps1xml 檔案中定義的自訂控制項。 此自訂控制項用來分隔[System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature)資料表檢視中顯示的物件。

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
