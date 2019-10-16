---
title: GetProc02 （C#）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 5989b1e7030375b1bacdd9b82c25c1a8288fd637
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360367"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="e45aa-102">GetProc02 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="e45aa-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="e45aa-103">下列程式碼顯示可接受命令列輸入的 `Get-Process` Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="e45aa-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="e45aa-104">請注意，此實值會定義 `Name` 參數，以允許命令列輸入，並使用[WriteObject （system.string，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為將輸出物件傳送至管線的輸出機制。</span><span class="sxs-lookup"><span data-stu-id="e45aa-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e45aa-105">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e45aa-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="e45aa-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e45aa-106">See Also</span></span>

[<span data-ttu-id="e45aa-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e45aa-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
