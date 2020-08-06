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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="3909d-102">如何在 Cmdlet 內叫用指令碼</span><span class="sxs-lookup"><span data-stu-id="3909d-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="3909d-103">這個範例示範如何叫用提供給 Cmdlet 的腳本。</span><span class="sxs-lookup"><span data-stu-id="3909d-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="3909d-104">此腳本是由指令程式執行，其結果會以[系統管理](/dotnet/api/System.Management.Automation.PSObject)物件的集合形式傳回至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3909d-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="3909d-105">若要叫用腳本區塊</span><span class="sxs-lookup"><span data-stu-id="3909d-105">To invoke a script block</span></span>

1. <span data-ttu-id="3909d-106">命令會確認腳本區塊是否已提供給 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3909d-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="3909d-107">如果已提供腳本區塊，此命令會以其所需的參數叫用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="3909d-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="3909d-108">然後，腳本會逐一查看所傳回的[系統管理](/dotnet/api/System.Management.Automation.PSObject)物件集合，並執行必要的作業。</span><span class="sxs-lookup"><span data-stu-id="3909d-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3909d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3909d-109">See Also</span></span>

[<span data-ttu-id="3909d-110">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3909d-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
