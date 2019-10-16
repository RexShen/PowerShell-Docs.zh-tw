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
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="ebb4e-102">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ebb4e-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="ebb4e-103">「撰寫 PowerShell 格式檔案」適用于正在寫入 Cmdlet 或函式的命令開發人員，這些指令程式會將物件輸出至命令列。</span><span class="sxs-lookup"><span data-stu-id="ebb4e-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="ebb4e-104">格式化檔案會定義 PowerShell 如何在命令列顯示這些物件。</span><span class="sxs-lookup"><span data-stu-id="ebb4e-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="ebb4e-105">本檔提供格式化檔案的總覽，說明您在撰寫這些檔案時應該瞭解的概念、這些檔案中使用的 XML 範例，以及 XML 元素的參考區段。</span><span class="sxs-lookup"><span data-stu-id="ebb4e-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ebb4e-106">在本節中</span><span class="sxs-lookup"><span data-stu-id="ebb4e-106">In This Section</span></span>

<span data-ttu-id="ebb4e-107">[格式化檔案總覽](./formatting-file-overview.md)描述什麼是格式檔案，以及格式化檔案的一般元件，包括可以在檔案中定義的一般功能、可針對 .NET 物件定義的不同格式 views 類型，以及用來定義資料表 v 的簡單 XML 範例。檢視 i）.</span><span class="sxs-lookup"><span data-stu-id="ebb4e-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="ebb4e-108">[格式化檔案概念](./formatting-file-concepts.md)包含您在建立自己的格式化檔案時可能需要知道的資訊，例如您可以定義的不同檢視類型，以及這些視圖的特殊元件。</span><span class="sxs-lookup"><span data-stu-id="ebb4e-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="ebb4e-109">[格式檔案的範例](./examples-of-formatting-files.md)提供數個格式檔案的 XML 範例，包括資料表視圖、清單視圖和寬視圖的範例，以及示範如何定義功能的範例，例如選取範圍、選取條件和通用控制項。</span><span class="sxs-lookup"><span data-stu-id="ebb4e-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="ebb4e-110">[格式 XML 參考](./format-schema-xml-reference.md)包含用於格式化檔案之 XML 元素的參考主題。</span><span class="sxs-lookup"><span data-stu-id="ebb4e-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
