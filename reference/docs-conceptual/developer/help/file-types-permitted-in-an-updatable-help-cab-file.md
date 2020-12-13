---
ms.date: 03/22/2012
ms.topic: reference
title: 可更新的說明 CAB 檔案中允許的檔案類型
description: 可更新的說明 CAB 檔案中允許的檔案類型
ms.openlocfilehash: bb69b8b89a9a3a5c8c00059ec404a4d41a5db9a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654745"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="91386-103">可更新的說明 CAB 檔案中允許的檔案類型</span><span class="sxs-lookup"><span data-stu-id="91386-103">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="91386-104">未壓縮的 CAB 檔案內容預設限制為 1 GB。</span><span class="sxs-lookup"><span data-stu-id="91386-104">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="91386-105">若要略過此限制，使用者必須使用 Update-help **參數和** [get-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) [Cmdlet。](/powershell/module/Microsoft.PowerShell.Core/Save-Help)</span><span class="sxs-lookup"><span data-stu-id="91386-105">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="91386-106">為了確保從網際網路下載說明檔的安全性，可更新的說明封包檔只能包含以下所列的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="91386-106">To assure the security of help files that are downloaded from the internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="91386-107">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet 會針對說明主題架構驗證所有檔案。</span><span class="sxs-lookup"><span data-stu-id="91386-107">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="91386-108">如果 `Update-Help` Cmdlet 遇到無效或不是允許的類型的檔案，則不會安裝不正確檔案，也不會在使用者電腦上的 CAB 中停止安裝檔案。</span><span class="sxs-lookup"><span data-stu-id="91386-108">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="91386-109">Cmdlet 的 XML 型說明主題。</span><span class="sxs-lookup"><span data-stu-id="91386-109">XML-based help topics for cmdlets.</span></span>
- <span data-ttu-id="91386-110">腳本和函式的 XML 型說明主題。</span><span class="sxs-lookup"><span data-stu-id="91386-110">XML-based help topics for scripts and functions.</span></span>
- <span data-ttu-id="91386-111">PowerShell 提供者的 XML 型說明主題。</span><span class="sxs-lookup"><span data-stu-id="91386-111">XML-based help topics for PowerShell providers.</span></span>
- <span data-ttu-id="91386-112">以文字為基礎的說明主題，例如「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="91386-112">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="91386-113">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)會在解壓縮 cab 時驗證 cab 內容。</span><span class="sxs-lookup"><span data-stu-id="91386-113">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="91386-114">如果 `Update-Help` 在可更新的說明 CAB 檔案中找到不符合規範的檔案類型，它會產生終止錯誤並停止作業。</span><span class="sxs-lookup"><span data-stu-id="91386-114">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="91386-115">它不會從 CAB 安裝任何說明檔，即使是符合規範的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="91386-115">It does not install any help files from the CAB, even those of compliant file types.</span></span>
