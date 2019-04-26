---
title: Windows PowerShell 工作階段狀態 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066969"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="e1865-102">Windows PowerShell 工作階段狀態</span><span class="sxs-lookup"><span data-stu-id="e1865-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="e1865-103">工作階段狀態指的是 Windows PowerShell 工作階段或模組的目前組態。</span><span class="sxs-lookup"><span data-stu-id="e1865-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="e1865-104">Windows PowerShell 工作階段是以互動方式或使用的命令列的使用者以程式設計方式的主應用程式的操作環境。</span><span class="sxs-lookup"><span data-stu-id="e1865-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="e1865-105">工作階段的工作階段狀態被指全域工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="e1865-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="e1865-106">開發人員的觀點而言，Windows PowerShell 工作階段是指當主應用程式會開啟 Windows PowerShell runspace 與它在關閉 runspace 時之間的時間。</span><span class="sxs-lookup"><span data-stu-id="e1865-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="e1865-107">工作階段探討另一種方式，是在 runspace 存在時，會叫用的 Windows PowerShell 引擎的執行個體的存留期。</span><span class="sxs-lookup"><span data-stu-id="e1865-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="e1865-108">模組工作階段狀態</span><span class="sxs-lookup"><span data-stu-id="e1865-108">Module Session State</span></span>

<span data-ttu-id="e1865-109">每當模組或其中一個其巢狀模組匯入工作階段，會建立模組工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="e1865-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="e1865-110">當模組匯出的項目，例如 cmdlet、 函數或指令碼時，該元素的參考會加入工作階段的全域工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="e1865-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="e1865-111">不過，當執行項目時，它就是模組的工作階段狀態內執行。</span><span class="sxs-lookup"><span data-stu-id="e1865-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="e1865-112">工作階段狀態資料</span><span class="sxs-lookup"><span data-stu-id="e1865-112">Session-State Data</span></span>

<span data-ttu-id="e1865-113">工作階段狀態資料可以是公用或私用。</span><span class="sxs-lookup"><span data-stu-id="e1865-113">Session state data can be public or private.</span></span> <span data-ttu-id="e1865-114">私用資料可供使用才能內的工作階段狀態的呼叫時，就可從外部工作階段狀態的呼叫公用的資料。</span><span class="sxs-lookup"><span data-stu-id="e1865-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="e1865-115">例如，模組可以有可以只由模組或只在內部呼叫的私用函式的已匯出的公用項目。</span><span class="sxs-lookup"><span data-stu-id="e1865-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="e1865-116">這是類似於.NET Framework 型別的 private 和 public 成員。</span><span class="sxs-lookup"><span data-stu-id="e1865-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="e1865-117">工作階段狀態資料會儲存目前的 Windows PowerShell 工作階段的內容中執行引擎的目前執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1865-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="e1865-118">工作階段狀態資料是由下列項目所組成：</span><span class="sxs-lookup"><span data-stu-id="e1865-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="e1865-119">路徑資訊</span><span class="sxs-lookup"><span data-stu-id="e1865-119">Path information</span></span>

- <span data-ttu-id="e1865-120">磁碟機資訊</span><span class="sxs-lookup"><span data-stu-id="e1865-120">Drive information</span></span>

- <span data-ttu-id="e1865-121">Windows PowerShell 提供者資訊</span><span class="sxs-lookup"><span data-stu-id="e1865-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="e1865-122">匯入的模組和模組所匯出的模組項目 （例如 cmdlet、 函數和指令碼） 的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="e1865-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="e1865-123">這項資訊，這些參考會只有全域工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="e1865-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="e1865-124">工作階段狀態變數的資訊</span><span class="sxs-lookup"><span data-stu-id="e1865-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="e1865-125">工作階段狀態中存取資料的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e1865-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="e1865-126">指令程式可以存取工作階段狀態資料，可能是間接透過[System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)屬性，在 cmdlet 類別或直接透過[System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別。</span><span class="sxs-lookup"><span data-stu-id="e1865-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="e1865-127">[System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState)類別提供可用來調查工作階段狀態資料的不同類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1865-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1865-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1865-128">See Also</span></span>

[<span data-ttu-id="e1865-129">System.Management.Automation.PSCmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="e1865-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="e1865-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="e1865-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="e1865-131">Windows PowerShell Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e1865-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="e1865-132">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e1865-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="e1865-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="e1865-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
