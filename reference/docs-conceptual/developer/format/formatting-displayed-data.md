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
ms.openlocfilehash: 9f3a3176ae16ac7c014cadce6b4e856f9bd3b5da
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560384"
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
