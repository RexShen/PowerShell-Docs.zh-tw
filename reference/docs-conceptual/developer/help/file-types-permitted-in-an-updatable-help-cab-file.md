---
title: 可更新的說明 CAB 檔案中允許的檔案類型
ms.date: 03/22/2012
ms.openlocfilehash: 2a8e97edf8daaed915ea1a3e04565d996a2e15fd
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893130"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="df3a4-102">可更新的說明 CAB 檔案中允許的檔案類型</span><span class="sxs-lookup"><span data-stu-id="df3a4-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="df3a4-103">未壓縮的 CAB 檔案內容預設限制為 1 GB。</span><span class="sxs-lookup"><span data-stu-id="df3a4-103">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="df3a4-104">若要略過這項限制，使用者必須使用[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 的**Force**參數。</span><span class="sxs-lookup"><span data-stu-id="df3a4-104">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="df3a4-105">若要確保從網際網路下載之說明檔的安全性，可更新的說明 CAB 檔案只能包含以下所列的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="df3a4-105">To assure the security of help files that are downloaded from the internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="df3a4-106">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet 會根據說明主題架構來驗證所有檔案。</span><span class="sxs-lookup"><span data-stu-id="df3a4-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="df3a4-107">如果 `Update-Help` Cmdlet 遇到無效或不是允許類型的檔案，則不會安裝不正確檔案，而且會在使用者的電腦上停止從 CAB 安裝檔案。</span><span class="sxs-lookup"><span data-stu-id="df3a4-107">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="df3a4-108">Cmdlet 的 XML 為基礎說明主題。</span><span class="sxs-lookup"><span data-stu-id="df3a4-108">XML-based help topics for cmdlets.</span></span>
- <span data-ttu-id="df3a4-109">腳本和函式的 XML 為基礎的說明主題。</span><span class="sxs-lookup"><span data-stu-id="df3a4-109">XML-based help topics for scripts and functions.</span></span>
- <span data-ttu-id="df3a4-110">PowerShell 提供者的 XML 型說明主題。</span><span class="sxs-lookup"><span data-stu-id="df3a4-110">XML-based help topics for PowerShell providers.</span></span>
- <span data-ttu-id="df3a4-111">以文字為基礎的說明主題，例如關於主題。</span><span class="sxs-lookup"><span data-stu-id="df3a4-111">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="df3a4-112">當解壓縮 CAB 時， [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)會驗證 cab 內容。</span><span class="sxs-lookup"><span data-stu-id="df3a4-112">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="df3a4-113">如果 `Update-Help` 在可更新的說明 CAB 檔案中找到不符合規範的檔案類型，它會產生終止錯誤，並停止作業。</span><span class="sxs-lookup"><span data-stu-id="df3a4-113">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="df3a4-114">它不會從 CAB 安裝任何說明檔，即使是符合規範的檔案類型也一樣。</span><span class="sxs-lookup"><span data-stu-id="df3a4-114">It does not install any help files from the CAB, even those of compliant file types.</span></span>
