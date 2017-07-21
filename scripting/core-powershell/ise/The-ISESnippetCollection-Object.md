---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISESnippetCollection 物件"
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="a8046-103">ISESnippetCollection 物件</span><span class="sxs-lookup"><span data-stu-id="a8046-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="a8046-104">**ISESnippetCollection** 物件是 **ISESnippet** 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="a8046-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="a8046-105">與 **PowerShellTab** 物件相關聯的檔案集合是這個類別的成員。</span><span class="sxs-lookup"><span data-stu-id="a8046-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="a8046-106">**$psISE.CurrentPowerShellTab.Files** 集合即為一例。</span><span class="sxs-lookup"><span data-stu-id="a8046-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="a8046-107">方法</span><span class="sxs-lookup"><span data-stu-id="a8046-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="a8046-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="a8046-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="a8046-109">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="a8046-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="a8046-110">載入 .snippets.ps1xml 檔案，其中包含使用者定義的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="a8046-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="a8046-111">建立程式碼片段的最簡單方式是使用 New-IseSnippet Cmdlet，自動將它們儲存於您的設定檔資料夾中，如此一來，每當您啟動 Windows PowerShell ISE 時就會自動載入它們。</span><span class="sxs-lookup"><span data-stu-id="a8046-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="a8046-112">**FilePathName** - .snippets.ps1xml 檔案的路徑和檔案名稱，其中包含程式碼片段定義。</span><span class="sxs-lookup"><span data-stu-id="a8046-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="a8046-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8046-113">See Also</span></span>
- [<span data-ttu-id="a8046-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="a8046-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="a8046-115">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="a8046-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="a8046-116">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="a8046-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="a8046-117">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="a8046-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
