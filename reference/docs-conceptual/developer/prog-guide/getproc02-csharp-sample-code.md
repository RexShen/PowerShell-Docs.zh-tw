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
# <a name="getproc02-c-sample-code"></a>GetProc02 (C#) 範例程式碼

下列程式碼顯示 `Get-Process` 可接受命令列輸入的 Cmdlet 執行。 請注意，此實值會定義 `Name` 允許命令列輸入的參數，並使用 [WriteObject (system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 方法作為輸出機制，以將輸出物件傳送到管線。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
