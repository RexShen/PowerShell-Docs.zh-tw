---
title: Windows PowerShell 會話狀態 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.openlocfilehash: 7436e3ebd0e099ead81f9fea01a0a2994b982213
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783937"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="b10ee-102">Windows PowerShell 工作階段狀態</span><span class="sxs-lookup"><span data-stu-id="b10ee-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="b10ee-103">會話狀態指的是 Windows PowerShell 會話或模組的目前設定。</span><span class="sxs-lookup"><span data-stu-id="b10ee-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="b10ee-104">Windows PowerShell 會話是一種操作環境，由命令列使用者以互動方式使用，或由主應用程式以程式設計方式使用。</span><span class="sxs-lookup"><span data-stu-id="b10ee-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="b10ee-105">會話的會話狀態稱為「全域會話」狀態。</span><span class="sxs-lookup"><span data-stu-id="b10ee-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="b10ee-106">從開發人員的觀點來看，Windows PowerShell 會話是指主應用程式開啟 Windows PowerShell 執行時間和關閉執行時間時之間的時間。</span><span class="sxs-lookup"><span data-stu-id="b10ee-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="b10ee-107">另一種方式是，會話是在執行時間存在時叫用的 Windows PowerShell 引擎實例的存留期。</span><span class="sxs-lookup"><span data-stu-id="b10ee-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="b10ee-108">模組會話狀態</span><span class="sxs-lookup"><span data-stu-id="b10ee-108">Module Session State</span></span>

<span data-ttu-id="b10ee-109">每當模組或其中一個嵌套模組匯入會話時，就會建立模組會話狀態。</span><span class="sxs-lookup"><span data-stu-id="b10ee-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="b10ee-110">當模組匯出元素（例如 Cmdlet、函式或腳本）時，該專案的參考會加入至會話的全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="b10ee-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="b10ee-111">不過，當元素執行時，它會在模組的會話狀態中執行。</span><span class="sxs-lookup"><span data-stu-id="b10ee-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="b10ee-112">會話狀態資料</span><span class="sxs-lookup"><span data-stu-id="b10ee-112">Session-State Data</span></span>

<span data-ttu-id="b10ee-113">會話狀態資料可以是公用或私用。</span><span class="sxs-lookup"><span data-stu-id="b10ee-113">Session state data can be public or private.</span></span> <span data-ttu-id="b10ee-114">公用資料可供從會話狀態外部呼叫，而私用資料僅供從會話狀態內呼叫。</span><span class="sxs-lookup"><span data-stu-id="b10ee-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="b10ee-115">例如，模組可以具有只能由模組呼叫的私用函式，或只能由已匯出的公用元素在內部進行呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="b10ee-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="b10ee-116">這類似于 .NET Framework 類型的私用和公用成員。</span><span class="sxs-lookup"><span data-stu-id="b10ee-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="b10ee-117">目前 Windows PowerShell 會話的內容中，目前的執行引擎實例會儲存會話狀態資料。</span><span class="sxs-lookup"><span data-stu-id="b10ee-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="b10ee-118">會話狀態資料是由下列專案所組成：</span><span class="sxs-lookup"><span data-stu-id="b10ee-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="b10ee-119">路徑資訊</span><span class="sxs-lookup"><span data-stu-id="b10ee-119">Path information</span></span>

- <span data-ttu-id="b10ee-120">磁片磁碟機資訊</span><span class="sxs-lookup"><span data-stu-id="b10ee-120">Drive information</span></span>

- <span data-ttu-id="b10ee-121">Windows PowerShell 提供者資訊</span><span class="sxs-lookup"><span data-stu-id="b10ee-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="b10ee-122">匯入模組的相關資訊以及模組元素的參考 (例如模組所匯出的 Cmdlet、函式和腳本) 。</span><span class="sxs-lookup"><span data-stu-id="b10ee-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="b10ee-123">這項資訊和這些參考僅適用于全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="b10ee-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="b10ee-124">會話狀態變數資訊</span><span class="sxs-lookup"><span data-stu-id="b10ee-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="b10ee-125">存取 Cmdlet 內的會話狀態資料</span><span class="sxs-lookup"><span data-stu-id="b10ee-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="b10ee-126">Cmdlet 可以透過 Cmdlet 類別的[PSCmdlet. Sessionstate \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)屬性，或直接透過[Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別，來存取會話狀態資料（可能為間接）。</span><span class="sxs-lookup"><span data-stu-id="b10ee-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="b10ee-127">[Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別所提供的屬性可用來調查不同類型的會話狀態資料。</span><span class="sxs-lookup"><span data-stu-id="b10ee-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="b10ee-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b10ee-128">See Also</span></span>

[<span data-ttu-id="b10ee-129">System.web. PSCmdlet. Sessionstate</span><span class="sxs-lookup"><span data-stu-id="b10ee-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="b10ee-130">Sessionstate 嗎？Displayproperty = Fullname</span><span class="sxs-lookup"><span data-stu-id="b10ee-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="b10ee-131">Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b10ee-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="b10ee-132">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b10ee-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="b10ee-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="b10ee-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
