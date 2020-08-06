---
title: 'Runspace01 (c # ) 程式碼範例 |Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 418162731b4a98989642e1c61c655fdb0f002698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787049"
---
# <a name="runspace01-c-code-sample"></a>Runspace01 (C#) 程式碼範例

以下是[建立主控台應用程式（可執行指定的命令](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)）中所述之運行空間的程式碼範例。
若要這樣做，應用程式會叫用運行空間，然後叫用命令。  (請注意，此應用程式不會指定執行空間設定資訊，也不會明確地建立管線) 。 所叫用的命令是 `Get-Process` Cmdlet。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，為此執行時間下載 c # 原始程式檔 (runspace01.cs) 。
> 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
