---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113580
Help Version: 6.2.5.0
Locale: en-US
Module Guid: 29955884-f6a6-49ba-a071-a4dc8842697f
Module Name: ThreadJob
ms.date: 07/09/2019
title: ThreadJob 模組
ms.openlocfilehash: f841465c5db3bcd410bfe663ee6cd20e81700614
ms.sourcegitcommit: 3571b9e87e8881adbf7984cda46a63891039a987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "93201027"
---
# <span data-ttu-id="7411e-102">ThreadJob 模組</span><span class="sxs-lookup"><span data-stu-id="7411e-102">ThreadJob Module</span></span>

## <span data-ttu-id="7411e-103">描述</span><span class="sxs-lookup"><span data-stu-id="7411e-103">Description</span></span>
<span data-ttu-id="7411e-104">此模組會擴充現有的 PowerShell BackgroundJob，以包含以執行緒為基礎的新 **ThreadJob** 工作。</span><span class="sxs-lookup"><span data-stu-id="7411e-104">This module extends the existing PowerShell BackgroundJob to include a new thread based **ThreadJob** job.</span></span> <span data-ttu-id="7411e-105">這是較輕量的解決方案，可用於執行可在現有 PowerShell 作業基礎結構內運作的並行 PowerShell 腳本。</span><span class="sxs-lookup"><span data-stu-id="7411e-105">This is a lighter weight solution for running concurrent PowerShell scripts that works within the existing PowerShell job infrastructure.</span></span>

## <span data-ttu-id="7411e-106">ThreadJob Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7411e-106">ThreadJob Cmdlets</span></span>

### [<span data-ttu-id="7411e-107">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="7411e-107">Start-ThreadJob</span></span>](Start-ThreadJob.md)
<span data-ttu-id="7411e-108">建立與 Cmdlet 類似的背景工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="7411e-108">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>
