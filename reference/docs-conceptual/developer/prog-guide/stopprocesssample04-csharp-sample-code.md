---
title: StopProcessSample04 （C#）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 778ce1a2-e16d-4af5-b15b-77ca4326bdc4
caps.latest.revision: 5
ms.openlocfilehash: 52c0cedf237d05e874780d08887f91a87bf13ffd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366457"
---
# <a name="stopprocesssample04-c-sample-code"></a>StopProcessSample04 (C#) 範例程式碼

以下是 StopProc04 範例C# Cmdlet 的完整範例程式碼。 這是[將參數集新增至 Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)中所述的 `Stop-Process` Cmdlet 的程式碼。 @No__t-0 Cmdlet 是設計用來停止使用 Get-Proc Cmdlet 抓取的進程（如[建立您的第一個 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)所述）。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個停止程式 Cmdlet 的（stopprocesssample04.cs）原始程式檔。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L11-L435 "StopProcessSample04.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
