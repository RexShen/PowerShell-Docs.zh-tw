---
title: GetProc03 (VB.NET) 範例程式碼 |Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: ad8a7b13d30b77acdaa2f5365b9b2da02aaeedce
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771918"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="d3e49-102">GetProc03 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="d3e49-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="d3e49-103">下列程式碼顯示 `Get-Process` 可接受管線輸入的 Cmdlet 的執行方式。</span><span class="sxs-lookup"><span data-stu-id="d3e49-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="d3e49-104">這個實作為定義 `Name` 參數，它會接受管線輸入、根據提供的名稱從本機電腦抓取進程資訊，然後使用[WriteObject (system.object，system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為將物件傳送至管線的輸出機制。</span><span class="sxs-lookup"><span data-stu-id="d3e49-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d3e49-105">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d3e49-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
