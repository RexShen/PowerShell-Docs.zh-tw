---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc03 (C#) 範例程式碼
description: GetProc03 (C#) 範例程式碼
ms.openlocfilehash: c81ba04b2b335f4ce992c6b3ed2f019cf6d7d20f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355573"
---
# <a name="getproc03-c-sample-code"></a>GetProc03 (C#) 範例程式碼

下列程式碼顯示 `Get-Process` 可接受管線輸入的 Cmdlet 執行。 這個實值會定義一個 `Name` 接受管線輸入的參數、根據提供的名稱抓取本機電腦的處理資訊，然後使用 [WriteObject (system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 方法做為傳送物件至管線的輸出機制。

> [!NOTE]
> 您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此 Get-Proc Cmdlet 的 c # 原始程式檔 (getprov03.cs) 。 如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
