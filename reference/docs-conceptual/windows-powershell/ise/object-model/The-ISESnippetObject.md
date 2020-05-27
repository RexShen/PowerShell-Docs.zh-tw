---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetObject
ms.openlocfilehash: f810e6b26f0ded04be15bdc37f336d7890e29dad
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809574"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="5f9c7-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="5f9c7-103">The ISESnippetObject</span></span>

<span data-ttu-id="5f9c7-104">**ISESnippet** 物件是 Microsoft.PowerShell.Host.ISE.ISESnippet 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f9c7-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="5f9c7-105">`$psISE.CurrentPowerShellTab.Snippets` 集合的成員都是 **ISESnippet** 物件的範例。</span><span class="sxs-lookup"><span data-stu-id="5f9c7-105">The members of the `$psISE.CurrentPowerShellTab.Snippets` collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="5f9c7-106">建立程式碼片段的最簡單方式是使用 [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f9c7-106">The easiest way to create a snippet is to use the [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="5f9c7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5f9c7-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="5f9c7-108">作者</span><span class="sxs-lookup"><span data-stu-id="5f9c7-108">Author</span></span>

<span data-ttu-id="5f9c7-109">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="5f9c7-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5f9c7-110">唯讀屬性，可取得程式碼片段的作者名稱。</span><span class="sxs-lookup"><span data-stu-id="5f9c7-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="5f9c7-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="5f9c7-111">CodeFragment</span></span>

<span data-ttu-id="5f9c7-112">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="5f9c7-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5f9c7-113">唯讀屬性，可取得要插入至編輯器的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="5f9c7-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="5f9c7-114">快速鍵</span><span class="sxs-lookup"><span data-stu-id="5f9c7-114">Shortcut</span></span>

<span data-ttu-id="5f9c7-115">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="5f9c7-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="5f9c7-116">唯讀屬性，可取得功能表項目的 Windows 鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="5f9c7-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="5f9c7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f9c7-117">See Also</span></span>

- [<span data-ttu-id="5f9c7-118">ISESnippetCollection 物件</span><span class="sxs-lookup"><span data-stu-id="5f9c7-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="5f9c7-119">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="5f9c7-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="5f9c7-120">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="5f9c7-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
