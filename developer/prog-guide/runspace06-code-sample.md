---
title: RunSpace06 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: b6fdad90f7339e941d77646936b1b5952cd65500
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734925"
---
# <a name="runspace06-code-sample"></a>RunSpace06 程式碼範例

以下是原始程式碼，Runspace06 範例中所述[設定使用 Windows PowerShell 嵌入式管理單元的 Runspace](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)。 此範例應用程式會建立 runspace，根據 Windows PowerShell 嵌入式管理單元，然後用來執行管線，使用單一命令。 若要這樣做，應用程式會建立 runspace 的組態資訊、 建立 runspace，使用單一命令，會建立管線，然後執行管線。

> [!NOTE]
> 您可以下載C#使用的 Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件的原始程式檔 (runspace06.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)