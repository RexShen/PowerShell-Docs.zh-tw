---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="d168b-102">以類別為基礎的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="d168b-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="d168b-103">以類別定義 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="d168b-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="d168b-104">根據意見反應，我們讓撰寫以類別為基礎的 DSC 資源更簡單且更容易了解。</span><span class="sxs-lookup"><span data-stu-id="d168b-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="d168b-105">以類別為基礎的 DSC 資源和 Cmdlet DSC 資源提供者之間的主要差異如下︰</span><span class="sxs-lookup"><span data-stu-id="d168b-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="d168b-106">不需要結構描述的 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="d168b-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="d168b-107">不需要模組資料夾中的 **DSCResource** 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="d168b-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="d168b-108">PowerShell 模組檔案可以包含多個 DSC 資源類別。</span><span class="sxs-lookup"><span data-stu-id="d168b-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="d168b-109">如需詳細資訊，請參閱[使用 PowerShell 類別撰寫自訂 DSC 資源](https://msdn.microsoft.com/powershell/dsc/authoringresource)。</span><span class="sxs-lookup"><span data-stu-id="d168b-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

