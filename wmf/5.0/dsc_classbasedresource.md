---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058109"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="692e7-102">以類別為基礎的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="692e7-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="692e7-103">以類別定義 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="692e7-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="692e7-104">根據意見反應，我們讓撰寫以類別為基礎的 DSC 資源更簡單且更容易了解。</span><span class="sxs-lookup"><span data-stu-id="692e7-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="692e7-105">以類別為基礎的 DSC 資源和 Cmdlet DSC 資源提供者之間的主要差異如下︰</span><span class="sxs-lookup"><span data-stu-id="692e7-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="692e7-106">不需要結構描述的 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="692e7-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="692e7-107">不需要模組資料夾中的 **DSCResource** 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="692e7-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="692e7-108">PowerShell 模組檔案可以包含多個 DSC 資源類別。</span><span class="sxs-lookup"><span data-stu-id="692e7-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="692e7-109">如需詳細資訊，請參閱[使用 PowerShell 類別撰寫自訂 DSC 資源](https://msdn.microsoft.com/powershell/dsc/authoringresource)。</span><span class="sxs-lookup"><span data-stu-id="692e7-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
