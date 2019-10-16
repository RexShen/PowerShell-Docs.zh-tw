---
title: 顯示錯誤資訊 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369967"
---
# <a name="displaying-error-information"></a><span data-ttu-id="3429e-102">顯示錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="3429e-102">Displaying Error Information</span></span>

<span data-ttu-id="3429e-103">本主題討論使用者可以顯示錯誤資訊的方式。</span><span class="sxs-lookup"><span data-stu-id="3429e-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="3429e-104">當您的 Cmdlet 遇到錯誤時，根據預設，錯誤資訊的呈現會類似下列錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="3429e-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="3429e-105">不過，使用者可以藉由將 `$ErrorView` 變數設定為 `"CategoryView"`，依分類來查看錯誤。</span><span class="sxs-lookup"><span data-stu-id="3429e-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="3429e-106">類別目錄檢視會顯示錯誤記錄中的特定資訊，而不是錯誤的任意文字描述。</span><span class="sxs-lookup"><span data-stu-id="3429e-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="3429e-107">如果您有很長的錯誤清單要掃描，這個視圖會很有用。</span><span class="sxs-lookup"><span data-stu-id="3429e-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="3429e-108">在 [類別目錄] 視圖中，先前的錯誤訊息會顯示如下。</span><span class="sxs-lookup"><span data-stu-id="3429e-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="3429e-109">如需錯誤類別目錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="3429e-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3429e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3429e-110">See Also</span></span>

[<span data-ttu-id="3429e-111">Windows PowerShell 錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="3429e-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="3429e-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3429e-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
