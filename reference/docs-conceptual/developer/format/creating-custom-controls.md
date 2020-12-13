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
# <a name="creating-custom-controls"></a><span data-ttu-id="03244-103">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="03244-103">Creating Custom Controls</span></span>

<span data-ttu-id="03244-104">自訂控制項是格式化檔案中最具彈性的元件。</span><span class="sxs-lookup"><span data-stu-id="03244-104">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="03244-105">不同于定義資料的正式結構（例如資料表）的資料表、清單和寬視圖，自訂控制項可讓您定義個別資料片段的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="03244-105">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="03244-106">您可以定義一組通用的自訂控制項，這些控制項可供格式化檔案的所有視圖使用，您可以定義特定視圖可用的自訂控制項，也可以定義一組可供物件群組使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="03244-106">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="03244-107">自訂控制項範例</span><span class="sxs-lookup"><span data-stu-id="03244-107">Custom Control Example</span></span>

<span data-ttu-id="03244-108">下列範例顯示 Certificates.Format.ps1xml 檔案中定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="03244-108">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="03244-109">此自訂控制項是用來分隔顯示在資料表視圖中的 [系統. 管理. Signature](/dotnet/api/System.Management.Automation.Signature) 物件。</span><span class="sxs-lookup"><span data-stu-id="03244-109">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="03244-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03244-110">See Also</span></span>

[<span data-ttu-id="03244-111">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="03244-111">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
