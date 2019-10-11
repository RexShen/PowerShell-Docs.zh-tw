---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 建置自訂的 Windows PowerShell 預期狀態設定資源
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952845"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="32a62-103">建置自訂的 Windows PowerShell 預期狀態設定資源</span><span class="sxs-lookup"><span data-stu-id="32a62-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="32a62-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="32a62-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="32a62-105">Windows PowerShell 預期狀態設定 (DSC) 有內建資源，可用以設定您的環境。</span><span class="sxs-lookup"><span data-stu-id="32a62-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="32a62-106">本主題提供開發資源概述以及特定資訊和範例的主題連結。</span><span class="sxs-lookup"><span data-stu-id="32a62-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="32a62-107">DSC 資源元件</span><span class="sxs-lookup"><span data-stu-id="32a62-107">DSC resource components</span></span>

<span data-ttu-id="32a62-108">DSC 資源是 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="32a62-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="32a62-109">模組包含資源的結構描述 (可設定的屬性定義) 和實作 (真正執行設定所指定工作的程式碼)。</span><span class="sxs-lookup"><span data-stu-id="32a62-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="32a62-110">DSC 資源結構描述可以在 MOF 檔案中定義，並由指令碼模組執行實作。</span><span class="sxs-lookup"><span data-stu-id="32a62-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="32a62-111">從第 5 版的 PowerShell 類別支援開始，結構描述和實作都可以在類別中定義。</span><span class="sxs-lookup"><span data-stu-id="32a62-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="32a62-112">下列主題會詳細說明如何建立 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="32a62-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="32a62-113">撰寫自訂的 DSC 資源與 MOF</span><span class="sxs-lookup"><span data-stu-id="32a62-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="32a62-114">在 C# 中實作 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="32a62-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="32a62-115">使用 PowerShell 類別撰寫自訂的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="32a62-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="32a62-116">複合資源：將 DSC 設定當成資源使用</span><span class="sxs-lookup"><span data-stu-id="32a62-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* <span data-ttu-id="32a62-117">[使用 [資源設計工具] 工具](authoringResourceMofDesigner.md)</span><span class="sxs-lookup"><span data-stu-id="32a62-117">[Using the Resource Designer tool](authoringResourceMofDesigner.md)</span></span>
