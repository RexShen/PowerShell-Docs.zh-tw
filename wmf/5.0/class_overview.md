---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 5919a68c87ae8827a1b97befc653bb74713f33fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085774"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="91d0c-102">使用 PowerShell 類別建立自訂類型</span><span class="sxs-lookup"><span data-stu-id="91d0c-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="91d0c-103">我們使用類似其他物件導向程式設計語言的正式語法和語意，改善了 PowerShell 語言對類別和其他使用者定義類型的定義。</span><span class="sxs-lookup"><span data-stu-id="91d0c-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="91d0c-104">目標是要讓開發人員和 IT 專業人員能夠掌握更多面向的 PowerShell 使用案例、簡化 PowerShell 成品的開發 (例如 DSC 資源)，並擴大管理介面的涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="91d0c-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="91d0c-105">本版的支援案例</span><span class="sxs-lookup"><span data-stu-id="91d0c-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="91d0c-106">使用 PowerShell 語言定義 DSC 資源及其相關聯類型</span><span class="sxs-lookup"><span data-stu-id="91d0c-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="91d0c-107">使用熟悉的物件導向程式設計建構，例如類別、屬性、方法等等，在 PowerShell 中定義自訂的類型。</span><span class="sxs-lookup"><span data-stu-id="91d0c-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="91d0c-108">具有 PowerShell 類別和類別基底 DSC 資源的繼承支援</span><span class="sxs-lookup"><span data-stu-id="91d0c-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="91d0c-109">使用 PowerShell 語言偵錯類型</span><span class="sxs-lookup"><span data-stu-id="91d0c-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="91d0c-110">使用正式的機制在正確的層級產生和處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="91d0c-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
