---
title: 格式化顯示的資料 |Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: 97d23b3079b2779e518b6b6d2f2ac0c5e9d1f3a3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781506"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="e2863-102">設定已顯示之資料的格式</span><span class="sxs-lookup"><span data-stu-id="e2863-102">Formatting Displayed Data</span></span>

<span data-ttu-id="e2863-103">您可以指定如何顯示清單、資料表或寬視圖中的個別資料點。</span><span class="sxs-lookup"><span data-stu-id="e2863-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="e2863-104">`FormatString`定義您的視圖專案時，您可以使用元素，也可以使用專案 `ScriptBlock` 來呼叫 `FormatString` 資料上的方法。</span><span class="sxs-lookup"><span data-stu-id="e2863-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="e2863-105">使用格式字串元素</span><span class="sxs-lookup"><span data-stu-id="e2863-105">Using the FormatString Element</span></span>

<span data-ttu-id="e2863-106">在下列範例中， `TotalProcessorTime` 會使用格式字串元素來格式化[system.webserver](/dotnet/api/System.Diagnostics.Process)物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="e2863-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="e2863-107">`TotalProcessorTime`屬性</span><span class="sxs-lookup"><span data-stu-id="e2863-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
