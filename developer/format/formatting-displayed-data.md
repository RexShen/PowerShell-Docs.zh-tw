---
title: 格式化顯示的資料 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065660"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="e223e-102">設定已顯示之資料的格式</span><span class="sxs-lookup"><span data-stu-id="e223e-102">Formatting Displayed Data</span></span>

<span data-ttu-id="e223e-103">您可以指定您的清單、 資料表或寬型檢視中的個別資料點的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="e223e-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="e223e-104">您可以使用`FormatString`元素定義的檢視，或您的項目時可使用`ScriptBlock`呼叫的項目`FormatString`資料的方法。</span><span class="sxs-lookup"><span data-stu-id="e223e-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="e223e-105">使用 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="e223e-105">Using the FormatString Element</span></span>

<span data-ttu-id="e223e-106">在下列範例中值的`TotalProcessorTime`的屬性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件的格式使用 FormatString 元素。</span><span class="sxs-lookup"><span data-stu-id="e223e-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="e223e-107">`TotalProcessorTime`屬性</span><span class="sxs-lookup"><span data-stu-id="e223e-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



