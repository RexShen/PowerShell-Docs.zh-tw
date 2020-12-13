---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace07 程式碼範例
description: RunSpace07 程式碼範例
ms.openlocfilehash: 6e8c9f48a6e9c5a642ecf93bca8a85003b3cfbf8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647394"
---
# <a name="runspace07-code-sample"></a>RunSpace07 程式碼範例

以下是 [建立可將命令新增至管線的主控台應用程式](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e)中所述之 Runspace07 範例的原始程式碼。
這個範例應用程式會建立一個運行空間、建立管線、將兩個命令新增至管線，然後執行管線。 新增至管線的命令為 `Get-Process` 和 `Measure-Object` Cmdlet。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件， (runspace07.cs) 下載 c # 原始程式檔。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
