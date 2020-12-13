---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc01 (C#) 程式碼範例
description: GetProc01 (C#) 程式碼範例
ms.openlocfilehash: 79509ff12afb32c907058f4ddb0c707f3823857a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654489"
---
# <a name="getproc01-c-sample-code"></a>GetProc01 (C#) 程式碼範例

下列程式碼顯示 GetProc01 範例 Cmdlet 的執行。 請注意，透過將進程抓取的實際工作保留給 [system.diagnostics.process.getprocesses *](/dotnet/api/System.Diagnostics.Process.GetProcesses) 方法，即可簡化此 Cmdlet。

> [!NOTE]
> 您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此 Get-Proc Cmdlet 的 c # 原始程式檔 (getproc01.cs) 。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
