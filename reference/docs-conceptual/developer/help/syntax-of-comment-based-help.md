---
ms.date: 09/12/2016
ms.topic: reference
title: 註解型說明的語法
description: 註解型說明的語法
ms.openlocfilehash: 3866f25b40fc970e8d219af6f423b7a25f5b875c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659507"
---
# <a name="syntax-of-comment-based-help"></a>註解型說明的語法

本節說明以批註為基礎的說明語法。

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

 以批註為基礎的說明會以一系列的批註撰寫。 您可以在 `#` 每一行批註之前輸入批註符號 () ，也可以使用 `<#` 和 `#>` 符號來建立批註區塊。 批註區塊內的所有行都會轉譯為批註。

 批註型說明的每個區段都是由關鍵字定義，而每個關鍵字的前面會加上點 (`.`) 。 關鍵字可以依任何順序出現。 關鍵字名稱不區分大小寫。

 批註區塊必須至少包含一個 help 關鍵字。 某些關鍵字（例如 **EXAMPLE**）可以出現在相同批註區塊中的多次。 每個關鍵字的說明內容都是在關鍵字後面的那一行開始，而且可以橫跨多行。

 以批註為基礎的說明主題中的所有程式列都必須是連續的。 如果以批註為基礎的說明主題遵循的批註不在說明主題中，則最後一個非說明批註行和批註式說明的開頭至少必須有一個空白行。

 例如，下列以批註為基礎的說明主題包含。Description 關鍵字及其值，也就是函數或腳本的描述。

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
