---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="b63a5-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="b63a5-103">The ISESnippetObject</span></span>
  <span data-ttu-id="b63a5-104">**ISESnippet** 物件是 Microsoft.PowerShell.Host.ISE.ISESnippet 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b63a5-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="b63a5-105">**$psISE.CurrentPowerShellTab.Snippets** 集合的成員都是 **ISESnippet** 物件的範例。</span><span class="sxs-lookup"><span data-stu-id="b63a5-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="b63a5-106">建立程式碼片段的最簡單方式是使用 [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b63a5-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="b63a5-107">[內容]</span><span class="sxs-lookup"><span data-stu-id="b63a5-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="b63a5-108">作者</span><span class="sxs-lookup"><span data-stu-id="b63a5-108">Author</span></span>
  <span data-ttu-id="b63a5-109">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b63a5-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b63a5-110">唯讀屬性，可取得程式碼片段的作者名稱。</span><span class="sxs-lookup"><span data-stu-id="b63a5-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="b63a5-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="b63a5-111">CodeFragment</span></span>
  <span data-ttu-id="b63a5-112">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b63a5-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b63a5-113">唯讀屬性，可取得要插入至編輯器的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="b63a5-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="b63a5-114">捷徑</span><span class="sxs-lookup"><span data-stu-id="b63a5-114">Shortcut</span></span>
  <span data-ttu-id="b63a5-115">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b63a5-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="b63a5-116">唯讀屬性，可取得功能表項目的 Windows 鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="b63a5-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="b63a5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b63a5-117">See Also</span></span>
- [<span data-ttu-id="b63a5-118">ISESnippetCollection 物件</span><span class="sxs-lookup"><span data-stu-id="b63a5-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="b63a5-119">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="b63a5-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="b63a5-120">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="b63a5-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="b63a5-121">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="b63a5-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
