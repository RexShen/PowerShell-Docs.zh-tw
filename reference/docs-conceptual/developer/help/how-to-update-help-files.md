---
ms.date: 09/12/2016
ms.topic: reference
title: 如何更新說明檔
description: 如何更新說明檔
ms.openlocfilehash: 19bf501cf91b1eb5dabb334c2179953590b40232
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649591"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="445c7-103">如何更新說明檔</span><span class="sxs-lookup"><span data-stu-id="445c7-103">How to Update Help Files</span></span>

<span data-ttu-id="445c7-104">本主題說明如何更新支援「可更新的說明」之模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="445c7-104">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="445c7-105">正在更新說明檔</span><span class="sxs-lookup"><span data-stu-id="445c7-105">Updating Help Files</span></span>

<span data-ttu-id="445c7-106">更新說明檔的原因有很多，例如更正錯誤、闡明概念、回答常見問題、新增檔案，或新增更好的範例。</span><span class="sxs-lookup"><span data-stu-id="445c7-106">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="445c7-107">若要更新說明檔：</span><span class="sxs-lookup"><span data-stu-id="445c7-107">To update a help file:</span></span>

1. <span data-ttu-id="445c7-108">變更檔案。</span><span class="sxs-lookup"><span data-stu-id="445c7-108">Change the files.</span></span>
1. <span data-ttu-id="445c7-109">將檔案轉譯為其他 UI 文化特性。</span><span class="sxs-lookup"><span data-stu-id="445c7-109">Translate the files into other UI cultures.</span></span>
1. <span data-ttu-id="445c7-110">針對每個 UI 文化特性中的模組，收集所有說明檔 (新的、已變更和未變更的) 。</span><span class="sxs-lookup"><span data-stu-id="445c7-110">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>
1. <span data-ttu-id="445c7-111">針對 XML 架構驗證檔案。</span><span class="sxs-lookup"><span data-stu-id="445c7-111">Validate the files against the XML schema.</span></span>
1. <span data-ttu-id="445c7-112">重建每個 UI 文化特性的 CAB 檔案。</span><span class="sxs-lookup"><span data-stu-id="445c7-112">Rebuild the CAB files for each UI culture.</span></span>
1. <span data-ttu-id="445c7-113">在 HelpInfo XML 檔案中，為每個 UI 文化特性遞增 CAB 檔案的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="445c7-113">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>
1. <span data-ttu-id="445c7-114">將新的 CAB 檔案上傳至 HelpInfo XML 檔案中 **HelpContentUri** 元素的值所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="445c7-114">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="445c7-115">以新的 CAB 檔案取代舊的封包檔。</span><span class="sxs-lookup"><span data-stu-id="445c7-115">Replace the older CAB files with the new CAB files.</span></span>
1. <span data-ttu-id="445c7-116">將更新的 HelpInfo XML 檔案上傳至模組資訊清單中 **HelpInfoUri** 索引鍵所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="445c7-116">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="445c7-117">以新的檔案取代舊版的 HelpInfo XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="445c7-117">Replace the older HelpInfo XML file with the new file.</span></span>
