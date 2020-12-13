---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04 程式碼範例
description: GetProc04 程式碼範例
ms.openlocfilehash: db94eda2b3aa5fc88a3054df66f54628e1482f56
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659244"
---
# <a name="getproc04-code-samples"></a>GetProc04 程式碼範例

以下是 GetProc04 範例 Cmdlet 的程式碼範例。 此為[新增持續錯誤報告至 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md) 中所描述 `Get-Process` Cmdlet 範例。 `Get-Process`每當在抓取處理常式資訊時擲回無效作業例外狀況時，此 Cmdlet 會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。

> [!NOTE]
> 您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此 Get-Proc Cmdlet 的 c # 原始程式檔 (getprov04.cs) 。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

如需完整的範例程式碼，請參閱下列主題。

|語言|主題|
|--------------|-----------|
|C#|[GetProc04 (C#) 範例程式碼](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 (VB.NET) 範例程式碼](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
