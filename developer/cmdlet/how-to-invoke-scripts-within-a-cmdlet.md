---
title: 如何叫用 Cmdlet 中的指令碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067870"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>如何在 Cmdlet 內叫用指令碼

此範例示範如何叫用的指令碼，提供給 cmdlet。 指令程式，所執行的指令碼和其結果的集合傳回 cmdlet [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)物件。

## <a name="to-invoke-a-script-block"></a>若要叫用指令碼區塊

1. 此命令會驗證指令碼區塊已提供給此 cmdlet。 如果提供的指令碼區塊，此命令會叫用指令碼區塊，以及其所需的參數。

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

2. 然後，指令碼，將透過傳回的集合會逐一查看[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)物件，並執行必要的作業。

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
