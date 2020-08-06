---
title: Cmdlet 輸出 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7697db01c8c4d1c831202c07256559bf638aeaef
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784430"
---
# <a name="cmdlet-output"></a><span data-ttu-id="36214-102">Cmdlet 輸出</span><span class="sxs-lookup"><span data-stu-id="36214-102">Cmdlet Output</span></span>

<span data-ttu-id="36214-103">本節討論 Cmdlet 輸出的類型，以及 Cmdlet 可以呼叫來產生輸出（例如錯誤訊息和物件）的方法。</span><span class="sxs-lookup"><span data-stu-id="36214-103">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="36214-104">本節也會說明如何定義 Cmdlet 所傳回的 .NET Framework 類型，以及這些物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="36214-104">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="36214-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="36214-105">In This Section</span></span>

<span data-ttu-id="36214-106">[Cmdlet 輸出的類型](./types-of-cmdlet-output.md)描述 Cmdlet 可以產生的類型和輸出，以及 Cmdlet 呼叫來產生輸出的方法。</span><span class="sxs-lookup"><span data-stu-id="36214-106">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="36214-107">[Cmdlet 錯誤報表](./cmdlet-error-reporting.md)討論 Cmdlet 錯誤報表，這是 Cmdlet 輸出的子集。</span><span class="sxs-lookup"><span data-stu-id="36214-107">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="36214-108">[擴充輸出物件](./extending-output-objects.md)討論如何使用類型 files (. types.ps1xml) 來擴充 Cmdlet、函式和腳本所傳回的 .NET Framework 物件。</span><span class="sxs-lookup"><span data-stu-id="36214-108">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="36214-109">[PowerShell 格式化](../format/powershell-formatting-files.md)檔案描述格式檔案 ( # B0 xml) 檔案，這些檔案會在 Windows PowerShell 中定義一組特定 .NET Framework 物件的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="36214-109">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="36214-110">[自訂格式](./custom-formatting-files.md)檔案描述如何建立您自己的自訂格式檔案，以覆寫預設的顯示格式，或定義您自己的命令所傳回的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="36214-110">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="36214-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36214-111">See Also</span></span>

[<span data-ttu-id="36214-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="36214-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
