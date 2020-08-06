---
title: 'GetProc02 (c # ) 範例程式碼 |Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: d9afa8fff23d99661987c067e8082a9294c12717
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787150"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="e3059-102">GetProc02 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="e3059-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="e3059-103">下列程式碼顯示 `Get-Process` 接受命令列輸入之 Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="e3059-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="e3059-104">請注意，此實 `Name` 作為會定義允許命令列輸入的參數，並使用[WriteObject (system.object，system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為將輸出物件傳送至管線的輸出機制。</span><span class="sxs-lookup"><span data-stu-id="e3059-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e3059-105">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e3059-105">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a><span data-ttu-id="e3059-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3059-106">See Also</span></span>

[<span data-ttu-id="e3059-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e3059-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
