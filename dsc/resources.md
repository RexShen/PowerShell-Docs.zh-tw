---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 資源
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219805"
---
# <a name="dsc-resources"></a><span data-ttu-id="23573-103">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="23573-103">DSC Resources</span></span>

><span data-ttu-id="23573-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="23573-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="23573-105">預期狀態設定 (DSC) 資源提供 DSC 設定的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="23573-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="23573-106">資源會公開可以設定的屬性 (結構描述)，而且這些屬性包含本機設定管理員 (LCM) 稱之為「make it so (讓它變成這樣)」的 PowerShell 指令碼函式。</span><span class="sxs-lookup"><span data-stu-id="23573-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="23573-107">資源可以建立某些物件的模型，像檔案一樣平常或如 IIS 伺服器設定一樣專用。</span><span class="sxs-lookup"><span data-stu-id="23573-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="23573-108">類似資源的群組會併入 DSC 模組，將所有必要的檔案組織到可攜式結構中，而且包含中繼資料以識別資源的原訂用法。</span><span class="sxs-lookup"><span data-stu-id="23573-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="23573-109">下列主題會說明 DSC 資源：</span><span class="sxs-lookup"><span data-stu-id="23573-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="23573-110">內建 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="23573-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="23573-111">建置自訂的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="23573-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="23573-112">Linux 的內建 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="23573-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)