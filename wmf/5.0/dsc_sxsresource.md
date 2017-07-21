---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="4897e-102">DSC 資源的並行模組版本管理支援</span><span class="sxs-lookup"><span data-stu-id="4897e-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="4897e-103">包含 DSC 資源的模組可以並行安裝，且 DSC 設定可以使用安裝於系統上的特定資源版本。</span><span class="sxs-lookup"><span data-stu-id="4897e-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="4897e-104">如需詳細資訊，請參閱[使用多個版本的資源](https://msdn.microsoft.com/powershell/dsc/sxsresource)。</span><span class="sxs-lookup"><span data-stu-id="4897e-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="4897e-105">已知問題</span><span class="sxs-lookup"><span data-stu-id="4897e-105">Known issues</span></span>

<span data-ttu-id="4897e-106">下列為此版本中已知的並行安裝問題︰</span><span class="sxs-lookup"><span data-stu-id="4897e-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="4897e-107">不支援在相同設定中使用兩個不同的 DSC 資源版本。</span><span class="sxs-lookup"><span data-stu-id="4897e-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>

