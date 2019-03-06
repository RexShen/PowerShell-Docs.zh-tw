---
title: Runspace01 (C#) 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 59320365c4a35c3d71af10273eb21b1ce01e5c0c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429698"
---
# <a name="runspace01-c-code-sample"></a>Runspace01 (C#) 程式碼範例

如下的程式碼範例中所述的 runspace[建立主控台應用程式，執行指定命令](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e)。 若要這樣做，應用程式會叫用的 runspace，然後再叫用命令。 （請注意，此應用程式未指定 runspace 組態資訊，也不會它明確地建立管線）。 叫用的命令是`Get-Process`cmdlet。

> [!NOTE]
> 您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件此 runspace 的原始程式檔 (runspace01.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)