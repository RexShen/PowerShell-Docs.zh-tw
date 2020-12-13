---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02 (C#) 範例程式碼
description: GetProc02 (C#) 範例程式碼
ms.openlocfilehash: 17fd0d0c0829ed21ef955fd2e62e9ee089d62190
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355607"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="8c973-103">GetProc02 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="8c973-103">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="8c973-104">下列程式碼顯示 `Get-Process` 可接受命令列輸入的 Cmdlet 執行。</span><span class="sxs-lookup"><span data-stu-id="8c973-104">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="8c973-105">請注意，此實值會定義 `Name` 允許命令列輸入的參數，並使用 [WriteObject (system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 方法作為輸出機制，以將輸出物件傳送到管線。</span><span class="sxs-lookup"><span data-stu-id="8c973-105">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8c973-106">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="8c973-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a><span data-ttu-id="8c973-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c973-107">See Also</span></span>

[<span data-ttu-id="8c973-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8c973-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
