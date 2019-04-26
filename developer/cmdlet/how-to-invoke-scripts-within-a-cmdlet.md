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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="ae1e2-102">如何在 Cmdlet 內叫用指令碼</span><span class="sxs-lookup"><span data-stu-id="ae1e2-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="ae1e2-103">此範例示範如何叫用的指令碼，提供給 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae1e2-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="ae1e2-104">指令程式，所執行的指令碼和其結果的集合傳回 cmdlet [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)物件。</span><span class="sxs-lookup"><span data-stu-id="ae1e2-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="ae1e2-105">若要叫用指令碼區塊</span><span class="sxs-lookup"><span data-stu-id="ae1e2-105">To invoke a script block</span></span>

1. <span data-ttu-id="ae1e2-106">此命令會驗證指令碼區塊已提供給此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae1e2-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="ae1e2-107">如果提供的指令碼區塊，此命令會叫用指令碼區塊，以及其所需的參數。</span><span class="sxs-lookup"><span data-stu-id="ae1e2-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="ae1e2-108">然後，指令碼，將透過傳回的集合會逐一查看[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)物件，並執行必要的作業。</span><span class="sxs-lookup"><span data-stu-id="ae1e2-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ae1e2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae1e2-109">See Also</span></span>

[<span data-ttu-id="ae1e2-110">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae1e2-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
