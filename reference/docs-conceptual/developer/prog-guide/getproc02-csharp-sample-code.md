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
# <a name="getproc02-c-sample-code"></a>GetProc02 (C#) 範例程式碼

下列程式碼顯示 `Get-Process` 接受命令列輸入之 Cmdlet 的執行。 請注意，此實 `Name` 作為會定義允許命令列輸入的參數，並使用[WriteObject (system.object，system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為將輸出物件傳送至管線的輸出機制。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
