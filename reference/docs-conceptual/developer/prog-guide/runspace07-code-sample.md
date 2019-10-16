---
title: RunSpace07 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: ab68f96372f20a435217702c7f3ebde3de633919
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360147"
---
# <a name="runspace07-code-sample"></a>RunSpace07 程式碼範例

以下是[建立可將命令新增至管線的主控台應用程式](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)中所述之 Runspace07 範例的原始程式碼。 這個範例應用程式會建立一個運行時、建立管線、將兩個命令新增至管線，然後執行管線。 新增至管線的命令為 `Get-Process` 和 @no__t 1 Cmdlet。

> [!NOTE]
> 您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載原始程式檔（runspace07.cs）。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[Runspace07.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
