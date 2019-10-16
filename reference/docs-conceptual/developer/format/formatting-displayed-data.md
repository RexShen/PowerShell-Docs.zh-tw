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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363697"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="5bbcd-102">設定已顯示之資料的格式</span><span class="sxs-lookup"><span data-stu-id="5bbcd-102">Formatting Displayed Data</span></span>

<span data-ttu-id="5bbcd-103">您可以指定如何顯示清單、資料表或寬視圖中的個別資料點。</span><span class="sxs-lookup"><span data-stu-id="5bbcd-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="5bbcd-104">定義您的視圖專案時，您可以使用 `FormatString` 元素，也可以使用 `ScriptBlock` 元素來呼叫資料上的 `FormatString` 方法。</span><span class="sxs-lookup"><span data-stu-id="5bbcd-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="5bbcd-105">使用格式字串元素</span><span class="sxs-lookup"><span data-stu-id="5bbcd-105">Using the FormatString Element</span></span>

<span data-ttu-id="5bbcd-106">在下列範例中，會使用格式字串元素來格式化[system.web](/dotnet/api/System.Diagnostics.Process)物件的 `TotalProcessorTime` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="5bbcd-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="5bbcd-107">`TotalProcessorTime` 屬性</span><span class="sxs-lookup"><span data-stu-id="5bbcd-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



