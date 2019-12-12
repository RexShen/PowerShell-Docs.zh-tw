---
title: RunSpace05 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 979403376c5e694b686aaf77a2cb787d765cb883
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417938"
---
# <a name="runspace05-code-sample"></a>RunSpace05 程式碼範例

以下是[使用 RunspaceConfiguration 設定運行空間](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)中所述 Runspace05 範例的原始程式碼。 這個範例示範如何建立執行時間設定資訊、建立執行時間、使用單一命令建立管線，然後執行管線。 執行的命令是 `Get-Process` Cmdlet。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載原始程式檔（runspace05.cs）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。

## <a name="code-sample"></a>範例程式碼

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
