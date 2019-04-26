---
title: 語法的註解型說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083207"
---
# <a name="syntax-of-comment-based-help"></a>註解型說明的語法

本章節描述註解型說明的語法。

## <a name="syntax-diagram"></a>語法圖

 註解型說明的語法如下所示：

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>語法描述

 以一系列的註解寫入註解型說明。 每一行的註解之前，您可以輸入註解符號 （#），或者您可以使用 「\<#"和"#>"符號，可建立註解區塊。 註解區塊中的所有行會都解譯成註解。

 關鍵字所定義的註解型說明每個區段和每個關鍵字加句點 （.）。 關鍵字可以按照任何順序出現。 關鍵字名稱不區分大小寫。

 註解區塊必須包含至少一個的 help 關鍵字。 某些關鍵字，例如範例中，可以多次出現相同的註解區塊中。 每個關鍵字的說明內容的關鍵字後開始列上，並可以跨越多行。

 所有註解型說明主題中的行必須是連續的。 如果註解型說明主題後面的註解不是 [說明] 主題的一部分，必須有至少一個空白行，最後一個非說明註解線條之間開頭的註解型說明。

 例如，包含下列的註解型說明主題。說明關鍵字和其值，也就是函式或指令碼的描述。

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```