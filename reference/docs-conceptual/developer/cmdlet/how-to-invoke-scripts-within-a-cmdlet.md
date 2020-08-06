---
title: 如何在 Cmdlet 內叫用腳本 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 248ad7e2e35fe53682836d094a391023007fa0b7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784124"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>如何在 Cmdlet 內叫用指令碼

這個範例示範如何叫用提供給 Cmdlet 的腳本。 此腳本是由指令程式執行，其結果會以[系統管理](/dotnet/api/System.Management.Automation.PSObject)物件的集合形式傳回至 Cmdlet。

## <a name="to-invoke-a-script-block"></a>若要叫用腳本區塊

1. 命令會確認腳本區塊是否已提供給 Cmdlet。 如果已提供腳本區塊，此命令會以其所需的參數叫用腳本區塊。

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

2. 然後，腳本會逐一查看所傳回的[系統管理](/dotnet/api/System.Management.Automation.PSObject)物件集合，並執行必要的作業。

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
