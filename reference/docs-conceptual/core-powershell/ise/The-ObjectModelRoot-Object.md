---
ms.date: 2017-08-25
keywords: powershell,cmdlet
title: "ObjectModelRoot 物件"
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="0f576-103">ObjectModelRoot 物件</span><span class="sxs-lookup"><span data-stu-id="0f576-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="0f576-104">**$psISE** 物件 (Windows PowerShell® 整合式指令碼環境中 (ISE) 的主要根物件) 是 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0f576-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="0f576-105">本主題描述 **ObjectModelRoot** 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f576-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="0f576-106">[內容]</span><span class="sxs-lookup"><span data-stu-id="0f576-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="0f576-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="0f576-107">CurrentFile</span></span>

> <span data-ttu-id="0f576-108">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="0f576-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="0f576-109">唯讀屬性，可取得目前具有焦點之主機物件相關聯的檔案。</span><span class="sxs-lookup"><span data-stu-id="0f576-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="0f576-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="0f576-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="0f576-111">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="0f576-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0f576-112">唯讀屬性，可取得具有焦點的 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0f576-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="0f576-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="0f576-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="0f576-114">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="0f576-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0f576-115">唯讀屬性，可取得目前顯示於編輯器底部水平工具窗格的 Windows PowerShell ISE 附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="0f576-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="0f576-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="0f576-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="0f576-117">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="0f576-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="0f576-118">唯讀屬性，可取得目前顯示於編輯器右邊垂直工具窗格的 Windows PowerShell ISE 附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="0f576-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="0f576-119">選項</span><span class="sxs-lookup"><span data-stu-id="0f576-119">Options</span></span>

> <span data-ttu-id="0f576-120">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="0f576-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="0f576-121">唯讀屬性，取得可變更 Windows PowerShell ISE 中之設定的各種選項。</span><span class="sxs-lookup"><span data-stu-id="0f576-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="0f576-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="0f576-122">PowerShellTabs</span></span>

> <span data-ttu-id="0f576-123">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="0f576-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="0f576-124">唯讀屬性，可取得 Windows PowerShell ISE 中開啟的 PowerShell 索引標籤集合。</span><span class="sxs-lookup"><span data-stu-id="0f576-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="0f576-125">根據預設，這個物件包含一個 PowerShell 索引標籤。不過，您可以使用指令碼，或使用 Windows PowerShell ISE 中的功能表，新增多個 PowerShell 索引標籤到此物件中。</span><span class="sxs-lookup"><span data-stu-id="0f576-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f576-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f576-126">See Also</span></span>

- [<span data-ttu-id="0f576-127">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="0f576-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="0f576-128">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="0f576-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="0f576-129">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="0f576-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
