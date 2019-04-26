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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066680"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="8aad2-102">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="8aad2-102">Creating Custom Controls</span></span>

<span data-ttu-id="8aad2-103">自訂控制項是最具彈性的格式化檔案元件。</span><span class="sxs-lookup"><span data-stu-id="8aad2-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="8aad2-104">與資料表、 清單和定義正式的資料，例如資料的資料表，結構的寬型檢視不同的是自訂的控制項可讓您定義個別的一段資料的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="8aad2-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="8aad2-105">您可以定義一組常用的自訂控制項所提供的格式化檔案的所有檢視，您可以定義自訂的控制項，且適用於特定的檢視，或您可以定義一組可用於一整組物件的控制項。</span><span class="sxs-lookup"><span data-stu-id="8aad2-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="8aad2-106">自訂控制項範例</span><span class="sxs-lookup"><span data-stu-id="8aad2-106">Custom Control Example</span></span>

<span data-ttu-id="8aad2-107">下列範例顯示 Certificates.Format.ps1xml 檔案中定義的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="8aad2-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="8aad2-108">此自訂控制項用來分隔[System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature)資料表檢視中顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="8aad2-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8aad2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8aad2-109">See Also</span></span>

[<span data-ttu-id="8aad2-110">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="8aad2-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
