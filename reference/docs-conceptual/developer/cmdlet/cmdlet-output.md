---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 輸出
description: Cmdlet 輸出
ms.openlocfilehash: 37606e57d9dff3ed9fa25b2b99eb07efa0147127
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653258"
---
# <a name="cmdlet-output"></a><span data-ttu-id="5293d-103">Cmdlet 輸出</span><span class="sxs-lookup"><span data-stu-id="5293d-103">Cmdlet Output</span></span>

<span data-ttu-id="5293d-104">本節討論 Cmdlet 輸出的類型，以及 Cmdlet 可呼叫來產生輸出的方法，例如錯誤訊息和物件。</span><span class="sxs-lookup"><span data-stu-id="5293d-104">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="5293d-105">本節也會說明如何定義您的 Cmdlet 所傳回的 .NET Framework 類型，以及這些物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="5293d-105">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5293d-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="5293d-106">In This Section</span></span>

<span data-ttu-id="5293d-107">[Cmdlet 輸出的類型](./types-of-cmdlet-output.md) 描述 Cmdlet 可以產生的類型和輸出，以及 Cmdlet 呼叫來產生輸出的方法。</span><span class="sxs-lookup"><span data-stu-id="5293d-107">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="5293d-108">[Cmdlet 錯誤報表](./cmdlet-error-reporting.md) 討論 Cmdlet 錯誤報表，這是 Cmdlet 輸出的子集。</span><span class="sxs-lookup"><span data-stu-id="5293d-108">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="5293d-109">[擴充輸出物件](./extending-output-objects.md) 討論如何使用類型檔案 ( .ps1xml) 來擴充 Cmdlet、函式和腳本所傳回的 .NET Framework 物件。</span><span class="sxs-lookup"><span data-stu-id="5293d-109">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="5293d-110">[PowerShell 格式設定檔](../format/powershell-formatting-files.md) 案描述格式化檔案 ( # B0 xml) 檔案，這些檔案會定義 Windows PowerShell 中特定 .NET Framework 物件集的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="5293d-110">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="5293d-111">[自訂格式設定檔](./custom-formatting-files.md) 案說明如何建立您自己的自訂格式檔案，以覆寫預設顯示格式或定義您自己的命令所傳回的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="5293d-111">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="5293d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5293d-112">See Also</span></span>

[<span data-ttu-id="5293d-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5293d-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
