---
title: 寫入格式檔案的 PowerShell |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083566"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="478eb-102">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="478eb-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="478eb-103">「 撰寫 PowerShell 格式化檔案 「 適用於命令開發人員撰寫 cmdlet 或函式的輸出至命令列的物件。</span><span class="sxs-lookup"><span data-stu-id="478eb-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="478eb-104">格式檔案會定義 PowerShell 在命令列所顯示的那些物件。</span><span class="sxs-lookup"><span data-stu-id="478eb-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="478eb-105">這份文件概述的格式化檔案，說明您在撰寫這些檔案，這些檔案和參考一節中的 XML 項目所使用的 XML 的範例時應該了解的概念。</span><span class="sxs-lookup"><span data-stu-id="478eb-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="478eb-106">在本節中</span><span class="sxs-lookup"><span data-stu-id="478eb-106">In This Section</span></span>

<span data-ttu-id="478eb-107">[格式檔案概觀](./formatting-file-overview.md)何種格式檔案的說明和格式化檔案，其中包括可以定義在檔案中，可以為.NET 物件定義的格式檢視的不同類型的常見功能的一般元件，簡化的範例中用來定義資料表的檢視表的 xml。</span><span class="sxs-lookup"><span data-stu-id="478eb-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="478eb-108">[格式檔案概念](./formatting-file-concepts.md)包含您可能需要知道建立您自己的格式化檔案時，不同類型的檢視，您可以定義和特殊的元件，這些檢視的這類的資訊。</span><span class="sxs-lookup"><span data-stu-id="478eb-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="478eb-109">[格式檔案的範例](./examples-of-formatting-files.md)的數個格式化的檔案，包括的資料表檢視、 清單檢視中和寬型檢視中，範例以及示範如何定義功能，例如選取項目集，選擇條件的範例提供的 XML 範例和通用控制項。</span><span class="sxs-lookup"><span data-stu-id="478eb-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="478eb-110">[格式化 XML 參考](./format-schema-xml-reference.md)包含參考主題中的格式化檔案中所使用的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="478eb-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
