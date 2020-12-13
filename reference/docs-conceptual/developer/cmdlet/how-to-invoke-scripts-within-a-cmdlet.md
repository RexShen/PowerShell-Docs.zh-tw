---
ms.date: 09/13/2016
ms.topic: reference
title: 如何在 Cmdlet 內叫用指令碼
description: 如何在 Cmdlet 內叫用指令碼
ms.openlocfilehash: f4a43a1e1240854e57deac5721e1e070c1a45a51
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667023"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>如何在 Cmdlet 內叫用指令碼

此範例說明如何叫用提供給 Cmdlet 的腳本。 腳本是由指令程式執行，其結果會以 [system.string 物件的](/dotnet/api/System.Management.Automation.PSObject) 集合形式傳回至 Cmdlet。

## <a name="to-invoke-a-script-block"></a>若要叫用腳本區塊

1. 此命令會驗證是否已提供腳本區塊給 Cmdlet。 如果提供了腳本區塊，命令就會使用它所需的參數來叫用腳本區塊。

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. 然後，腳本會逐一查看傳回的 [system.object](/dotnet/api/System.Management.Automation.PSObject) 物件集合，並執行必要的作業。

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
