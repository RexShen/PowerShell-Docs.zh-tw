---
title: GetProc04 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b90b7e96c1454e57df93863b526758f25d9be690
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771952"
---
# <a name="getproc04-code-samples"></a>GetProc04 程式碼範例

以下是 GetProc04 範例 Cmdlet 的程式碼範例。 這是 `Get-Process` [將非終止錯誤報表新增至您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 Cmdlet 範例。 `Get-Process`每當在抓取進程資訊時，擲回不正確作業例外狀況時，此 Cmdlet 會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，為這個 getprov04.cs) 下載 c # 原始程式檔 (。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
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
