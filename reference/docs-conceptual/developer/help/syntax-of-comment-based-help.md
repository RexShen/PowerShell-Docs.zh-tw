---
title: 以批註為基礎之說明的語法 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: da74c674c704794d8648dcdf9ba0a1617decba9b
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560605"
---
# <a name="syntax-of-comment-based-help"></a>註解型說明的語法

本節說明以批註為基礎之說明的語法。

## <a name="syntax-diagram"></a>語法圖表

 以批註為基礎的說明語法如下所示：

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

 以批註為基礎的說明會以一系列的批註來撰寫。 您可以在每一行批註之前輸入批註符號（#），也可以使用 " \< #" 和 "# >" 符號來建立批註區塊。 批註區塊中的所有行都會轉譯為批註。

 以批註為基礎的說明的每個區段都是由關鍵字所定義，而且每個關鍵字前面會加上點（.）。 關鍵字可以依任何順序出現。 關鍵字名稱不區分大小寫。

 批註區塊必須包含至少一個 help 關鍵字。 某些關鍵字（例如）可能會在相同的批註區塊中出現多次。 每個關鍵字的說明內容都是在關鍵字後面的一行開始，而且可以跨越多行。

 以批註為基礎的說明主題中的所有行都必須是連續的。 如果以批註為基礎的說明主題遵循不屬於說明主題的批註，則最後一個非說明批註行和批註式說明開頭必須至少有一個空白行。

 例如，下列以批註為基礎的說明主題包含。Description 關鍵字及其值，這是函數或腳本的描述。

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
