---
title: Cmdlet 輸出 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1362f4cd-4e05-4ace-ade6-7128da8ad86c
caps.latest.revision: 10
ms.openlocfilehash: 4c6aacd49b0a87bca6806ba5f08a1b4d48a90959
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068550"
---
# <a name="cmdlet-output"></a><span data-ttu-id="ab7ac-102">Cmdlet 輸出</span><span class="sxs-lookup"><span data-stu-id="ab7ac-102">Cmdlet Output</span></span>

<span data-ttu-id="ab7ac-103">本節討論的各種 cmdlet 的輸出和指令程式可以呼叫來產生輸出，例如錯誤訊息和物件的方法。</span><span class="sxs-lookup"><span data-stu-id="ab7ac-103">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="ab7ac-104">本節也說明如何定義您的 cmdlet 所傳回的.NET Framework 型別，以及這些物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="ab7ac-104">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ab7ac-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="ab7ac-105">In This Section</span></span>

<span data-ttu-id="ab7ac-106">[類型的 Cmdlet 輸出](./types-of-cmdlet-output.md)描述類型以及 cmdlet 可以產生的輸出，以及 cmdlet 呼叫來產生輸出的方法。</span><span class="sxs-lookup"><span data-stu-id="ab7ac-106">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="ab7ac-107">[指令程式錯誤報告](./cmdlet-error-reporting.md)討論 cmdlet 錯誤報告功能，cmdlet 輸出的子集。</span><span class="sxs-lookup"><span data-stu-id="ab7ac-107">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="ab7ac-108">[擴充輸出物件](./extending-output-objects.md)討論如何使用擴充.NET Framework 物件所傳回的類型檔案 (.ps1xml) 的 cmdlet、 函數和指令碼。</span><span class="sxs-lookup"><span data-stu-id="ab7ac-108">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="ab7ac-109">[PowerShell 格式化檔案](../format/powershell-formatting-files.md)描述的格式檔案 (。 format.ps1xml) 檔案會定義預設顯示的一組特定的 Windows PowerShell 中的.NET Framework 物件。</span><span class="sxs-lookup"><span data-stu-id="ab7ac-109">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="ab7ac-110">[自訂格式的檔案](./custom-formatting-files.md)描述如何建立您自己自訂的格式檔案以覆寫預設顯示格式，或定義物件的顯示由您自己的命令。</span><span class="sxs-lookup"><span data-stu-id="ab7ac-110">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab7ac-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab7ac-111">See Also</span></span>

[<span data-ttu-id="ab7ac-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab7ac-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
