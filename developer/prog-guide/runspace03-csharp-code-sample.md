---
title: RunSpace03 (C#) 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429902"
---
# <a name="runspace03-c-code-sample"></a>RunSpace03 (C#) 程式碼範例

以下是C#中所述的主控台應用程式的原始程式碼[建立主控台應用程式，執行指定指令碼](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68)。 這個範例會使用[System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行的指令碼，擷取處理資訊，請使用傳遞至指令碼的程序名稱的清單。 它會顯示如何將輸入的物件傳遞至指令碼以及如何擷取錯誤物件，以及輸出物件。

> [!NOTE]
> 您可以下載C#此範例使用的 Microsoft Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件的原始程式檔 (runspace03.cs)。 如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。

## <a name="code-sample"></a>程式碼範例

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)