---
title: GetProc02 （VB.NET）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 4ec63ed32bd2906f5b027523aa0f253b51a5d873
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366767"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="8de7b-102">GetProc02 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="8de7b-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="8de7b-103">下列程式碼顯示接受命令列輸入的 `Get-Process` Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="8de7b-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="8de7b-104">請注意，這個執行會定義一個 `Name` 參數以允許命令列輸入，而且它會使用[WriteObject （system.string，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為輸出機制，以便將輸出物件傳送至管線。</span><span class="sxs-lookup"><span data-stu-id="8de7b-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8de7b-105">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="8de7b-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="8de7b-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8de7b-106">See Also</span></span>

[<span data-ttu-id="8de7b-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8de7b-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
