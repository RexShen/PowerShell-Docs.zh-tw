---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 工作階段狀態
description: Windows PowerShell 工作階段狀態
ms.openlocfilehash: 51de92f1f392f708cf49c7ccb4a6808fd628076c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668128"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="b3310-103">Windows PowerShell 工作階段狀態</span><span class="sxs-lookup"><span data-stu-id="b3310-103">Windows PowerShell Session State</span></span>

<span data-ttu-id="b3310-104">會話狀態是指 Windows PowerShell 會話或模組的目前設定。</span><span class="sxs-lookup"><span data-stu-id="b3310-104">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="b3310-105">Windows PowerShell 會話是由命令列使用者以互動方式或由主應用程式以程式設計方式使用的操作環境。</span><span class="sxs-lookup"><span data-stu-id="b3310-105">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="b3310-106">會話的會話狀態稱為全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="b3310-106">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="b3310-107">從開發人員的觀點來看，Windows PowerShell 會話是指主應用程式開啟 Windows PowerShell 的執行時間與關閉該執行時間之間的時間。</span><span class="sxs-lookup"><span data-stu-id="b3310-107">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="b3310-108">另一種方式是，會話是在執行時間存在時所叫用的 Windows PowerShell 引擎實例的存留期。</span><span class="sxs-lookup"><span data-stu-id="b3310-108">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="b3310-109">模組會話狀態</span><span class="sxs-lookup"><span data-stu-id="b3310-109">Module Session State</span></span>

<span data-ttu-id="b3310-110">每當模組或其中一個的嵌套模組匯入會話時，就會建立模組會話狀態。</span><span class="sxs-lookup"><span data-stu-id="b3310-110">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="b3310-111">當模組匯出元素（例如 Cmdlet、函式或腳本）時，會將該元素的參考加入會話的全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="b3310-111">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="b3310-112">不過，當元素執行時，它會在模組的會話狀態中執行。</span><span class="sxs-lookup"><span data-stu-id="b3310-112">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="b3310-113">Session-State 資料</span><span class="sxs-lookup"><span data-stu-id="b3310-113">Session-State Data</span></span>

<span data-ttu-id="b3310-114">會話狀態資料可以是公用或私用。</span><span class="sxs-lookup"><span data-stu-id="b3310-114">Session state data can be public or private.</span></span> <span data-ttu-id="b3310-115">公用資料可供來自會話狀態之外的呼叫，而私用資料僅供來自會話狀態內的呼叫使用。</span><span class="sxs-lookup"><span data-stu-id="b3310-115">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="b3310-116">例如，模組可以有私用函式只能由模組呼叫，或只能由已匯出的公用元素在內部呼叫。</span><span class="sxs-lookup"><span data-stu-id="b3310-116">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="b3310-117">這類似于 .NET Framework 類型的私用和公共成員。</span><span class="sxs-lookup"><span data-stu-id="b3310-117">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="b3310-118">會話狀態資料會由目前的執行引擎實例儲存在目前 Windows PowerShell 會話的內容中。</span><span class="sxs-lookup"><span data-stu-id="b3310-118">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="b3310-119">會話狀態資料包含下列專案：</span><span class="sxs-lookup"><span data-stu-id="b3310-119">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="b3310-120">路徑資訊</span><span class="sxs-lookup"><span data-stu-id="b3310-120">Path information</span></span>

- <span data-ttu-id="b3310-121">磁片磁碟機資訊</span><span class="sxs-lookup"><span data-stu-id="b3310-121">Drive information</span></span>

- <span data-ttu-id="b3310-122">Windows PowerShell 提供者資訊</span><span class="sxs-lookup"><span data-stu-id="b3310-122">Windows PowerShell provider information</span></span>

- <span data-ttu-id="b3310-123">匯入模組的相關資訊，以及模組元素的參考 (例如模組所匯出的 Cmdlet、函式和腳本) 。</span><span class="sxs-lookup"><span data-stu-id="b3310-123">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="b3310-124">此資訊和這些參考僅適用于全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="b3310-124">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="b3310-125">會話狀態變數資訊</span><span class="sxs-lookup"><span data-stu-id="b3310-125">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="b3310-126">存取 Cmdlet 內的 Session-State 資料</span><span class="sxs-lookup"><span data-stu-id="b3310-126">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="b3310-127">Cmdlet 可以透過 Cmdlet 類別的 [PSCmdlet. Sessionstate \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) 屬性間接存取會話狀態資料，或直接透過 [Sessionstate](/dotnet/api/System.Management.Automation.SessionState) 類別來存取會話狀態資料。</span><span class="sxs-lookup"><span data-stu-id="b3310-127">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="b3310-128">[Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別所提供的屬性可用來調查不同類型的會話狀態資料。</span><span class="sxs-lookup"><span data-stu-id="b3310-128">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3310-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3310-129">See Also</span></span>

[<span data-ttu-id="b3310-130">PSCmdlet. Sessionstate。</span><span class="sxs-lookup"><span data-stu-id="b3310-130">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="b3310-131">Sessionstate 嗎？Displayproperty = Fullname</span><span class="sxs-lookup"><span data-stu-id="b3310-131">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="b3310-132">Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3310-132">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="b3310-133">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3310-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="b3310-134">Windows PowerShell 殼層 SDK</span><span class="sxs-lookup"><span data-stu-id="b3310-134">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
