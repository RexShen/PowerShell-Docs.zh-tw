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
# <a name="formatting-displayed-data"></a>設定已顯示之資料的格式

您可以指定您的清單、 資料表或寬型檢視中的個別資料點的顯示方式。 您可以使用`FormatString`元素定義的檢視，或您的項目時可使用`ScriptBlock`呼叫的項目`FormatString`資料的方法。

## <a name="using-the-formatstring-element"></a>使用 FormatString 元素

在下列範例中值的`TotalProcessorTime`的屬性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件的格式使用 FormatString 元素。 `TotalProcessorTime`屬性

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



