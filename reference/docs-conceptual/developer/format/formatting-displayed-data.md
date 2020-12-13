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
# <a name="formatting-displayed-data"></a>設定已顯示之資料的格式

您可以指定如何顯示清單、表格或寬視野中的個別資料點。 您可以在 `FormatString` 定義您的視圖專案時使用專案，也可以使用專案 `ScriptBlock` 來呼叫 `FormatString` 資料上的方法。

## <a name="using-the-formatstring-element"></a>使用格式格式元素

在下列範例中， `TotalProcessorTime` [系統](/dotnet/api/System.Diagnostics.Process) 的屬性值是使用格式值元素來格式化。 `TotalProcessorTime`屬性

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
