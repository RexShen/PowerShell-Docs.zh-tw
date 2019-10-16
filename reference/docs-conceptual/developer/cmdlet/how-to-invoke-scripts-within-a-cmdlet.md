---
title: 如何在 Cmdlet 內叫用腳本 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364407"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="4575d-102">如何在 Cmdlet 內叫用指令碼</span><span class="sxs-lookup"><span data-stu-id="4575d-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="4575d-103">這個範例示範如何叫用提供給 Cmdlet 的腳本。</span><span class="sxs-lookup"><span data-stu-id="4575d-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="4575d-104">此腳本是由指令程式執行，其結果會以[系統管理](/dotnet/api/System.Management.Automation.PSObject)物件的集合形式傳回至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4575d-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="4575d-105">若要叫用腳本區塊</span><span class="sxs-lookup"><span data-stu-id="4575d-105">To invoke a script block</span></span>

1. <span data-ttu-id="4575d-106">命令會確認腳本區塊是否已提供給 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4575d-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="4575d-107">如果已提供腳本區塊，此命令會以其所需的參數叫用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="4575d-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="4575d-108">然後，腳本會逐一查看所傳回的[系統管理](/dotnet/api/System.Management.Automation.PSObject)物件集合，並執行必要的作業。</span><span class="sxs-lookup"><span data-stu-id="4575d-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4575d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4575d-109">See Also</span></span>

[<span data-ttu-id="4575d-110">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4575d-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
