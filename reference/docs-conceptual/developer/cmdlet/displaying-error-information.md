---
ms.date: 09/13/2016
ms.topic: reference
title: 顯示錯誤資訊
description: 顯示錯誤資訊
ms.openlocfilehash: 37a3adb91d0e616a5c7f27bcab866f8da139f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653050"
---
# <a name="displaying-error-information"></a><span data-ttu-id="7e1c8-103">顯示錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="7e1c8-103">Displaying Error Information</span></span>

<span data-ttu-id="7e1c8-104">本主題討論使用者可以顯示錯誤資訊的方式。</span><span class="sxs-lookup"><span data-stu-id="7e1c8-104">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="7e1c8-105">當您的 Cmdlet 遇到錯誤時，錯誤資訊的呈現方式預設會類似下列錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="7e1c8-105">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="7e1c8-106">不過，使用者可以藉由將變數設定為，以依分類來查看錯誤 `$ErrorView` `"CategoryView"` 。</span><span class="sxs-lookup"><span data-stu-id="7e1c8-106">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="7e1c8-107">類別目錄檢視會顯示錯誤記錄中的特定資訊，而不是錯誤的任意文字描述。</span><span class="sxs-lookup"><span data-stu-id="7e1c8-107">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="7e1c8-108">如果您有一長串要掃描的錯誤，此視圖會很有用。</span><span class="sxs-lookup"><span data-stu-id="7e1c8-108">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="7e1c8-109">在類別目錄檢視中，先前的錯誤訊息會顯示如下。</span><span class="sxs-lookup"><span data-stu-id="7e1c8-109">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="7e1c8-110">如需有關錯誤類別的詳細資訊，請參閱 [Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="7e1c8-110">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e1c8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e1c8-111">See Also</span></span>

[<span data-ttu-id="7e1c8-112">Windows PowerShell 錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="7e1c8-112">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="7e1c8-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7e1c8-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
