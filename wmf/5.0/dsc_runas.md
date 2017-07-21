---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 2df24cb3ddf38c34876f023b5cdb41f46638e5ff
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="automatic-runas-support-for-dsc-resources"></a><span data-ttu-id="6e45d-102">DSC 資源的自動 RunAs 支援</span><span class="sxs-lookup"><span data-stu-id="6e45d-102">Automatic RunAs support for DSC Resources</span></span>

<span data-ttu-id="6e45d-103">WMF 5.0 包含在指定認證下執行**任何** DSC 資源的支援，方法是使用屬性 `PsDscRunAsCredential`。</span><span class="sxs-lookup"><span data-stu-id="6e45d-103">WMF 5.0 includes support for running **any** DSC resource under a specified set of credentials by using the property `PsDscRunAsCredential`.</span></span> 

<span data-ttu-id="6e45d-104">如需詳細資訊，請參閱[以使用者認證執行 DSC](https://msdn.microsoft.com/powershell/dsc/runasuser)。</span><span class="sxs-lookup"><span data-stu-id="6e45d-104">For more information, see [Running DSC with user credentials](https://msdn.microsoft.com/powershell/dsc/runasuser).</span></span>

