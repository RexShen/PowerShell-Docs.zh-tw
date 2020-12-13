---
ms.date: 09/12/2016
ms.topic: reference
title: GetProc03 (VB.NET) 範例程式碼
description: GetProc03 (VB.NET) 範例程式碼
ms.openlocfilehash: fc70496178c85e101b380e68aacd64c8d1f350e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355556"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="8f0bd-103">GetProc03 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="8f0bd-103">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="8f0bd-104">下列程式碼顯示 `Get-Process` 可接受管線輸入的 Cmdlet 執行。</span><span class="sxs-lookup"><span data-stu-id="8f0bd-104">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="8f0bd-105">這個實值會定義一個 `Name` 接受管線輸入的參數、根據提供的名稱抓取本機電腦的處理資訊，然後使用 [WriteObject (system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 方法做為傳送物件至管線的輸出機制。</span><span class="sxs-lookup"><span data-stu-id="8f0bd-105">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8f0bd-106">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="8f0bd-106">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
