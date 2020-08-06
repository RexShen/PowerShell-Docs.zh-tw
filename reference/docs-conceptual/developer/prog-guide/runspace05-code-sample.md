---
title: RunSpace05 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 31a73f965a6e38dceec740a2f7d4adead3e2a3f9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784736"
---
# <a name="runspace05-code-sample"></a>RunSpace05 程式碼範例

以下是[使用 RunspaceConfiguration 設定運行空間](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)中所述 Runspace05 範例的原始程式碼。
這個範例示範如何建立執行時間設定資訊、建立執行時間、使用單一命令建立管線，然後執行管線。 執行的命令是 `Get-Process` Cmdlet。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組， (runspace05.cs) 下載 c # 原始程式檔。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
