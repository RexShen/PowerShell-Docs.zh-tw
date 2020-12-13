---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace05 程式碼範例
description: RunSpace05 程式碼範例
ms.openlocfilehash: f128e09522bdb05cba2c160bce4944c829a5c108
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654203"
---
# <a name="runspace05-code-sample"></a>RunSpace05 程式碼範例

以下是 [使用 RunspaceConfiguration 設定運行空間](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)中所述之 Runspace05 範例的原始程式碼。
此範例說明如何建立執行時間設定資訊、建立執行時間、使用單一命令建立管線，然後執行管線。 執行的命令是 `Get-Process` Cmdlet。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件， (runspace05.cs) 下載 c # 原始程式檔。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
