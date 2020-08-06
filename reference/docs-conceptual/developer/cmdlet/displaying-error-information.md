---
title: 顯示錯誤資訊 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e542110e9c35a74c5d4c112b0a831f7f8ad9242e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774570"
---
# <a name="displaying-error-information"></a><span data-ttu-id="0ac96-102">顯示錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="0ac96-102">Displaying Error Information</span></span>

<span data-ttu-id="0ac96-103">本主題討論使用者可以顯示錯誤資訊的方式。</span><span class="sxs-lookup"><span data-stu-id="0ac96-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="0ac96-104">當您的 Cmdlet 遇到錯誤時，根據預設，錯誤資訊的呈現會類似下列錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="0ac96-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="0ac96-105">不過，使用者可以藉由將變數設定為，依類別來查看錯誤 `$ErrorView` `"CategoryView"` 。</span><span class="sxs-lookup"><span data-stu-id="0ac96-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="0ac96-106">類別目錄檢視會顯示錯誤記錄中的特定資訊，而不是錯誤的任意文字描述。</span><span class="sxs-lookup"><span data-stu-id="0ac96-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="0ac96-107">如果您有很長的錯誤清單要掃描，這個視圖會很有用。</span><span class="sxs-lookup"><span data-stu-id="0ac96-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="0ac96-108">在 [類別目錄] 視圖中，先前的錯誤訊息會顯示如下。</span><span class="sxs-lookup"><span data-stu-id="0ac96-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="0ac96-109">如需錯誤類別目錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="0ac96-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ac96-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ac96-110">See Also</span></span>

[<span data-ttu-id="0ac96-111">Windows PowerShell 錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="0ac96-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="0ac96-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0ac96-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
