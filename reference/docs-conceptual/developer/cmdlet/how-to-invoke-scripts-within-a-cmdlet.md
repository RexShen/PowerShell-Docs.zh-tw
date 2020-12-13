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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="8ad7c-103">如何在 Cmdlet 內叫用指令碼</span><span class="sxs-lookup"><span data-stu-id="8ad7c-103">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="8ad7c-104">此範例說明如何叫用提供給 Cmdlet 的腳本。</span><span class="sxs-lookup"><span data-stu-id="8ad7c-104">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="8ad7c-105">腳本是由指令程式執行，其結果會以 [system.string 物件的](/dotnet/api/System.Management.Automation.PSObject) 集合形式傳回至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ad7c-105">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="8ad7c-106">若要叫用腳本區塊</span><span class="sxs-lookup"><span data-stu-id="8ad7c-106">To invoke a script block</span></span>

1. <span data-ttu-id="8ad7c-107">此命令會驗證是否已提供腳本區塊給 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ad7c-107">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="8ad7c-108">如果提供了腳本區塊，命令就會使用它所需的參數來叫用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="8ad7c-108">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="8ad7c-109">然後，腳本會逐一查看傳回的 [system.object](/dotnet/api/System.Management.Automation.PSObject) 物件集合，並執行必要的作業。</span><span class="sxs-lookup"><span data-stu-id="8ad7c-109">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8ad7c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ad7c-110">See Also</span></span>

[<span data-ttu-id="8ad7c-111">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8ad7c-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
