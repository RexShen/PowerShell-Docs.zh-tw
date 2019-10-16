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
# <a name="formatting-displayed-data"></a>設定已顯示之資料的格式

您可以指定如何顯示清單、資料表或寬視圖中的個別資料點。 定義您的視圖專案時，您可以使用 `FormatString` 元素，也可以使用 `ScriptBlock` 元素來呼叫資料上的 `FormatString` 方法。

## <a name="using-the-formatstring-element"></a>使用格式字串元素

在下列範例中，會使用格式字串元素來格式化[system.web](/dotnet/api/System.Diagnostics.Process)物件的 `TotalProcessorTime` 屬性值。 `TotalProcessorTime` 屬性

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



