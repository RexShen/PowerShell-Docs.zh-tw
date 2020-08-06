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
# <a name="formatting-displayed-data"></a>設定已顯示之資料的格式

您可以指定如何顯示清單、資料表或寬視圖中的個別資料點。 `FormatString`定義您的視圖專案時，您可以使用元素，也可以使用專案 `ScriptBlock` 來呼叫 `FormatString` 資料上的方法。

## <a name="using-the-formatstring-element"></a>使用格式字串元素

在下列範例中， `TotalProcessorTime` 會使用格式字串元素來格式化[system.webserver](/dotnet/api/System.Diagnostics.Process)物件的屬性值。 `TotalProcessorTime`屬性

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
