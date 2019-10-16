---
title: GetProc03 （VB.NET）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360307"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="c092f-102">GetProc03 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="c092f-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="c092f-103">下列程式碼顯示可接受管線輸入的 @no__t 0 Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="c092f-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="c092f-104">此實作為定義 `Name` 參數，可接受管線輸入、根據提供的名稱從本機電腦上抓取進程資訊，然後使用[WriteObject （system.object，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為輸出將物件傳送至管線的機制。</span><span class="sxs-lookup"><span data-stu-id="c092f-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c092f-105">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="c092f-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
