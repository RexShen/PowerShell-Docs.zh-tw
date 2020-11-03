---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
Locale: en-US
Module Guid: 0e7b895d-2fec-43f7-8cae-11e8d16f6e40
Module Name: ThreadJob
ms.date: 07/09/2019
title: ThreadJob 模組
ms.openlocfilehash: 4a6abe107ac041f0ce5fa3e5d776bb0ac352685c
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205720"
---
# <span data-ttu-id="15d21-102">ThreadJob 模組</span><span class="sxs-lookup"><span data-stu-id="15d21-102">ThreadJob Module</span></span>

## <span data-ttu-id="15d21-103">Description</span><span class="sxs-lookup"><span data-stu-id="15d21-103">Description</span></span>
<span data-ttu-id="15d21-104">此模組會擴充現有的 PowerShell BackgroundJob，以包含以執行緒為基礎的新 **ThreadJob** 工作。</span><span class="sxs-lookup"><span data-stu-id="15d21-104">This module extends the existing PowerShell BackgroundJob to include a new thread based **ThreadJob** job.</span></span> <span data-ttu-id="15d21-105">這是較輕量的解決方案，可用於執行可在現有 PowerShell 作業基礎結構內運作的並行 PowerShell 腳本。</span><span class="sxs-lookup"><span data-stu-id="15d21-105">This is a lighter weight solution for running concurrent PowerShell scripts that works within the existing PowerShell job infrastructure.</span></span>

## <span data-ttu-id="15d21-106">ThreadJob Cmdlet</span><span class="sxs-lookup"><span data-stu-id="15d21-106">ThreadJob Cmdlets</span></span>

### [<span data-ttu-id="15d21-107">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="15d21-107">Start-ThreadJob</span></span>](Start-ThreadJob.md)
<span data-ttu-id="15d21-108">建立與 Cmdlet 類似的背景工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="15d21-108">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>
