---
ms.date: 09/12/2016
ms.topic: reference
title: 設定已顯示之資料的格式
description: 設定已顯示之資料的格式
ms.openlocfilehash: 40f6b3b4fa36062ee0bad3f197ad159f571445c8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667856"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="337a3-103">設定已顯示之資料的格式</span><span class="sxs-lookup"><span data-stu-id="337a3-103">Formatting Displayed Data</span></span>

<span data-ttu-id="337a3-104">您可以指定如何顯示清單、表格或寬視野中的個別資料點。</span><span class="sxs-lookup"><span data-stu-id="337a3-104">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="337a3-105">您可以在 `FormatString` 定義您的視圖專案時使用專案，也可以使用專案 `ScriptBlock` 來呼叫 `FormatString` 資料上的方法。</span><span class="sxs-lookup"><span data-stu-id="337a3-105">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="337a3-106">使用格式格式元素</span><span class="sxs-lookup"><span data-stu-id="337a3-106">Using the FormatString Element</span></span>

<span data-ttu-id="337a3-107">在下列範例中， `TotalProcessorTime` [系統](/dotnet/api/System.Diagnostics.Process) 的屬性值是使用格式值元素來格式化。</span><span class="sxs-lookup"><span data-stu-id="337a3-107">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="337a3-108">`TotalProcessorTime`屬性</span><span class="sxs-lookup"><span data-stu-id="337a3-108">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
