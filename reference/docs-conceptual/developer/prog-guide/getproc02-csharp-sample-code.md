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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360367"
---
# <a name="getproc02-c-sample-code"></a>GetProc02 (C#) 範例程式碼

下列程式碼顯示接受命令列輸入的 `Get-Process` Cmdlet 的執行。 請注意，這個執行會定義一個 `Name` 參數以允許命令列輸入，而且它會使用[WriteObject （system.string，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為輸出機制，以便將輸出物件傳送至管線。

## <a name="code-sample"></a>範例程式碼

[!code-csharp[GetProcessSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
