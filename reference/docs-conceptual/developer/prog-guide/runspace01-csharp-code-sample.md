---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace01 (C#) 程式碼範例
description: Runspace01 (C#) 程式碼範例
ms.openlocfilehash: e6121c144e1a4c1a1d9460d01119f44ee5835821
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657145"
---
# <a name="runspace01-c-code-sample"></a>Runspace01 (C#) 程式碼範例

以下是 [建立執行指定命令的主控台應用程式](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)中所述之運行空間的程式碼範例。
若要這樣做，應用程式會叫用運行空間，然後再叫用命令。  (請注意，此應用程式不會指定運行時設定資訊，也不會明確建立管線) 。 叫用的命令是 `Get-Process` Cmdlet。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件，下載此執行時間的 c # 原始程式檔 (runspace01.cs) 。
> 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
