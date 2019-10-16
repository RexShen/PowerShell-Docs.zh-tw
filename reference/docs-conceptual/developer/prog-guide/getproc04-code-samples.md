---
title: GetProc04 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360317"
---
# <a name="getproc04-code-samples"></a>GetProc04 程式碼範例

以下是 GetProc04 範例 Cmdlet 的程式碼範例。 這是[將非終止錯誤報表新增至您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 `Get-Process` Cmdlet 範例。 當抓取程式資訊時，如果擲回不正確作業例外狀況，此 `Get-Process` Cmdlet 會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個 getprov04.cs 的原始程式檔（）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。

如需完整的範例程式碼，請參閱下列主題。

|Language|主題|
|--------------|-----------|
|C#|[GetProc04 （C#）範例程式碼](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 （VB.NET）範例程式碼](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)