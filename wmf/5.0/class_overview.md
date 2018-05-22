---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: dfc171f9a3471f8fe7801283dd4a9b06860781a2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="1ed32-102">使用 PowerShell 類別建立自訂類型</span><span class="sxs-lookup"><span data-stu-id="1ed32-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="1ed32-103">我們使用類似其他物件導向程式設計語言的正式語法和語意，改善了 PowerShell 語言對類別和其他使用者定義類型的定義。</span><span class="sxs-lookup"><span data-stu-id="1ed32-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="1ed32-104">目標是要讓開發人員和 IT 專業人員能夠掌握更多面向的 PowerShell 使用案例、簡化 PowerShell 成品的開發 (例如 DSC 資源)，並擴大管理介面的涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="1ed32-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="1ed32-105">本版的支援案例</span><span class="sxs-lookup"><span data-stu-id="1ed32-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="1ed32-106">使用 PowerShell 語言定義 DSC 資源及其相關聯類型</span><span class="sxs-lookup"><span data-stu-id="1ed32-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="1ed32-107">使用熟悉的物件導向程式設計建構，例如類別、屬性、方法等等，在 PowerShell 中定義自訂的類型。</span><span class="sxs-lookup"><span data-stu-id="1ed32-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="1ed32-108">具有 PowerShell 類別和類別基底 DSC 資源的繼承支援</span><span class="sxs-lookup"><span data-stu-id="1ed32-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="1ed32-109">使用 PowerShell 語言偵錯類型</span><span class="sxs-lookup"><span data-stu-id="1ed32-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="1ed32-110">使用正式的機制在正確的層級產生和處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="1ed32-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
