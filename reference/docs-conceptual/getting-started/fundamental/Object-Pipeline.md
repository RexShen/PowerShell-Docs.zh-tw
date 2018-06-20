---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 物件管線
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 6102ec6e8fbf38fdc2bc5fa9c583244ef639dec8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
ms.locfileid: "30948205"
---
# <a name="object-pipeline"></a><span data-ttu-id="036c6-103">物件管線</span><span class="sxs-lookup"><span data-stu-id="036c6-103">Object Pipeline</span></span>
<span data-ttu-id="036c6-104">管線就像是一系列連接的管道區段。</span><span class="sxs-lookup"><span data-stu-id="036c6-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="036c6-105">沿著管線移動的項目會通過每個區段。</span><span class="sxs-lookup"><span data-stu-id="036c6-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="036c6-106">若要在 Windows PowerShell 中建立管線，您可以將命令與管道運算子 "|" 連接在一起。</span><span class="sxs-lookup"><span data-stu-id="036c6-106">To create a pipeline in Windows PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="036c6-107">每個命令的輸出可作為下一個命令的輸入。</span><span class="sxs-lookup"><span data-stu-id="036c6-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="036c6-108">管線可說是用於命令列介面中最重要的概念。</span><span class="sxs-lookup"><span data-stu-id="036c6-108">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="036c6-109">管線若使用得宜，不僅可以減輕輸入複雜命令所涉及的工作，也可以讓您更輕鬆地查看命令中的工作流程。</span><span class="sxs-lookup"><span data-stu-id="036c6-109">Properly used, pipelines not only reduce the effort involved in entering complex commands, but also make it easier to see the flow of work in the commands.</span></span> <span data-ttu-id="036c6-110">管線的相關實用特性在於，由於它們會在每個項目上分開運作，因此您不需要根據管線中將有零個、一個或多個項目對其進行修改。</span><span class="sxs-lookup"><span data-stu-id="036c6-110">A related useful characteristic of pipelines is that because they operate on each item separately, you do not have to modify them based on whether you will have zero, one, or many items in the pipeline.</span></span> <span data-ttu-id="036c6-111">此外，管線中的每個命令 (稱為管線項目) 通常會將其輸出逐項目傳遞至管線中的下一個命令。</span><span class="sxs-lookup"><span data-stu-id="036c6-111">Furthermore, each command in a pipeline (called a pipeline element) usually passes its output to the next command in the pipeline item-by-item.</span></span> <span data-ttu-id="036c6-112">這通常會減少複雜命令的資源需求，讓您立即開始取得輸出。</span><span class="sxs-lookup"><span data-stu-id="036c6-112">This usually reduces the resource demand of complex commands and allows you to begin getting the output immediately.</span></span>

<span data-ttu-id="036c6-113">在本章中，我們將說明 Windows PowerShell 管線與最熱門殼層管線的不同之處，接著示範您可以用來協助控制管線輸出及查看管線運作方式的一些基本工具。</span><span class="sxs-lookup"><span data-stu-id="036c6-113">In this chapter, we will describe how the Windows PowerShell pipeline differs from the pipelines of most popular shells, and then demonstrate some basic tools that you can use to help control pipeline output and also to see how the pipeline operates.</span></span>