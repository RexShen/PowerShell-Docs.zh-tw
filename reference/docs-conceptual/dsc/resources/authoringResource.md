---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: 建置自訂的 Windows PowerShell 預期狀態設定資源
description: 此文章提供開發資源的概觀，以及具有特定資訊與範例之文章的連結。
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656400"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="be856-104">建置自訂的 Windows PowerShell 預期狀態設定資源</span><span class="sxs-lookup"><span data-stu-id="be856-104">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="be856-105">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="be856-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="be856-106">Windows PowerShell 預期狀態設定 (DSC) 有內建資源，可用以設定您的環境。</span><span class="sxs-lookup"><span data-stu-id="be856-106">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="be856-107">此文章提供開發資源的概觀，以及具有特定資訊與範例之文章的連結。</span><span class="sxs-lookup"><span data-stu-id="be856-107">This article provides an overview of developing resources and links to articles with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="be856-108">DSC 資源元件</span><span class="sxs-lookup"><span data-stu-id="be856-108">DSC resource components</span></span>

<span data-ttu-id="be856-109">DSC 資源是 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="be856-109">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="be856-110">模組包含資源的結構描述 (可設定的屬性定義) 和實作 (真正執行設定所指定工作的程式碼)。</span><span class="sxs-lookup"><span data-stu-id="be856-110">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="be856-111">DSC 資源結構描述可以在 MOF 檔案中定義，並由指令碼模組執行實作。</span><span class="sxs-lookup"><span data-stu-id="be856-111">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="be856-112">從第 5 版的 PowerShell 類別支援開始，結構描述和實作都可以在類別中定義。</span><span class="sxs-lookup"><span data-stu-id="be856-112">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="be856-113">下列文章詳細說明如何建立 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="be856-113">The following articles describe in more detail how to create DSC resources.</span></span>

- [<span data-ttu-id="be856-114">撰寫自訂的 DSC 資源與 MOF</span><span class="sxs-lookup"><span data-stu-id="be856-114">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="be856-115">在 C# 中實作 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="be856-115">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
- [<span data-ttu-id="be856-116">使用 PowerShell 類別撰寫自訂的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="be856-116">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="be856-117">複合資源：把 DSC 設定當做資源使用</span><span class="sxs-lookup"><span data-stu-id="be856-117">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
- <span data-ttu-id="be856-118">[使用 [資源設計工具] 工具](authoringResourceMofDesigner.md)</span><span class="sxs-lookup"><span data-stu-id="be856-118">[Using the Resource Designer tool](authoringResourceMofDesigner.md)</span></span>
