---
ms.date: 12/31/2019
title: ISESnippetCollection 物件
description: ISESnippetCollection 物件是 ISESnippet 物件的集合。 與 PowerShellTab 物件相關聯的檔案集合是這個類別的成員。
ms.openlocfilehash: e6170ddf72d5ead840aa3015d4de1dcb21dbfeff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655984"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="03040-104">ISESnippetCollection 物件</span><span class="sxs-lookup"><span data-stu-id="03040-104">The ISESnippetCollection Object</span></span>

<span data-ttu-id="03040-105">**ISESnippetCollection** 物件是 **ISESnippet** 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="03040-105">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="03040-106">與 **PowerShellTab** 物件相關聯的檔案集合是這個類別的成員。</span><span class="sxs-lookup"><span data-stu-id="03040-106">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="03040-107">例如，`$psISE.CurrentPowerShellTab.Files` 集合。</span><span class="sxs-lookup"><span data-stu-id="03040-107">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="03040-108">方法</span><span class="sxs-lookup"><span data-stu-id="03040-108">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="03040-109">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="03040-109">Load\( FilePathName \)</span></span>

<span data-ttu-id="03040-110">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="03040-110">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="03040-111">載入 `.snippets.ps1xml` 檔案，其中包含使用者定義的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="03040-111">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="03040-112">建立程式碼片段的最簡單方式是使用 `New-IseSnippet` Cmdlet，自動將它們儲存於您的設定檔資料夾中，如此一來，每當您啟動 Windows PowerShell ISE 時就會載入它們。</span><span class="sxs-lookup"><span data-stu-id="03040-112">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="03040-113">**FilePathName** - .snippets.ps1xml 檔案的路徑和檔案名稱，其中包含程式碼片段定義。</span><span class="sxs-lookup"><span data-stu-id="03040-113">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="03040-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03040-114">See Also</span></span>

- [<span data-ttu-id="03040-115">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="03040-115">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="03040-116">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="03040-116">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="03040-117">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="03040-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
