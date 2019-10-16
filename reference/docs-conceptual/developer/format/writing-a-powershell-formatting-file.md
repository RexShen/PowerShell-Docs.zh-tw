---
title: 撰寫 PowerShell 格式檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361407"
---
# <a name="writing-a-powershell-formatting-file"></a>撰寫 PowerShell 格式設定檔案

「撰寫 PowerShell 格式檔案」適用于正在寫入 Cmdlet 或函式的命令開發人員，這些指令程式會將物件輸出至命令列。 格式化檔案會定義 PowerShell 如何在命令列顯示這些物件。 本檔提供格式化檔案的總覽，說明您在撰寫這些檔案時應該瞭解的概念、這些檔案中使用的 XML 範例，以及 XML 元素的參考區段。

## <a name="in-this-section"></a>在本節中

[格式化檔案總覽](./formatting-file-overview.md)描述什麼是格式檔案，以及格式化檔案的一般元件，包括可以在檔案中定義的一般功能、可針對 .NET 物件定義的不同格式 views 類型，以及用來定義資料表 v 的簡單 XML 範例。檢視 i）.

[格式化檔案概念](./formatting-file-concepts.md)包含您在建立自己的格式化檔案時可能需要知道的資訊，例如您可以定義的不同檢視類型，以及這些視圖的特殊元件。

[格式檔案的範例](./examples-of-formatting-files.md)提供數個格式檔案的 XML 範例，包括資料表視圖、清單視圖和寬視圖的範例，以及示範如何定義功能的範例，例如選取範圍、選取條件和通用控制項。

[格式 XML 參考](./format-schema-xml-reference.md)包含用於格式化檔案之 XML 元素的參考主題。
