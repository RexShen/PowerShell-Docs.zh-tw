---
title: GetProc04 Code Samples | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081660"
---
# <a name="getproc04-code-samples"></a>GetProc04 程式碼範例

以下是 GetProc04 cmdlet 範例的程式碼範例。 這是`Get-Process`cmdlet 的範例中所述[新增非終止錯誤報告，您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)。 這`Get-Process`cmdlet 會呼叫[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)時擷取程序資訊時擲回無效作業例外狀況的方法。

> [!NOTE]
> 您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov04.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。

完整的範例程式碼，請參閱下列主題。

|Language|主題|
|--------------|-----------|
|C#|[GetProc04 (C#) Sample Code](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 (VB.NET) Sample Code](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)