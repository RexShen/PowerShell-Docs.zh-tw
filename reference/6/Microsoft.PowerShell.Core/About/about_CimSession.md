---
description: 描述 **CimSession** 物件，以及 CIM 會話與 PowerShell 會話之間的差異。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_cimsession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CimSession
ms.openlocfilehash: f5080b593295343a812b68e1bc993048c0ce28ca
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207172"
---
# <a name="about-cimsession"></a><span data-ttu-id="fa4c2-104">關於 CimSession</span><span class="sxs-lookup"><span data-stu-id="fa4c2-104">About CimSession</span></span>

## <a name="short-description"></a><span data-ttu-id="fa4c2-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="fa4c2-105">Short description</span></span>
<span data-ttu-id="fa4c2-106">描述 **CimSession** 物件，以及 CIM 會話與 PowerShell 會話之間的差異。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-106">Describes a **CimSession** object and the difference between CIM sessions and PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="fa4c2-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="fa4c2-107">Long description</span></span>

<span data-ttu-id="fa4c2-108">通用訊息模型 (CIM) 會話是代表本機電腦或遠端電腦之連接的用戶端物件。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-108">A Common Information Model (CIM) session is a client-side object that represents a connection to a local computer or a remote computer.</span></span> <span data-ttu-id="fa4c2-109">您可以使用 CIM 會話來替代 (Pssession) 的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-109">You can use CIM sessions as an alternative to PowerShell sessions (PSSessions).</span></span> <span data-ttu-id="fa4c2-110">這兩種方法都有其優點。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-110">Both approaches have advantages.</span></span>

<span data-ttu-id="fa4c2-111">您可以使用指令 `New-CimSession` 程式來建立 CIM 會話，其中包含連線的相關資訊，例如電腦名稱稱、連接所使用的通訊協定、會話識別碼和實例識別碼。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-111">You can use the `New-CimSession` cmdlet to create a CIM session that contains information about a connection, such as computer name, the protocol used for the connection, session ID, and instance ID.</span></span>

<span data-ttu-id="fa4c2-112">在您建立 **CimSession** 物件來指定建立連線所需的資訊之後，PowerShell 就無法立即建立連接。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-112">After you create a **CimSession** object that specifies information required to establish a connection, PowerShell does not establish the connection immediately.</span></span> <span data-ttu-id="fa4c2-113">當 Cmdlet 使用 CIM 會話時，PowerShell 會連接到指定的電腦，然後當 Cmdlet 完成時，PowerShell 就會終止連線。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-113">When a cmdlet uses the CIM session, PowerShell connects to the specified computer, and then, when the cmdlet finishes, PowerShell terminates the connection.</span></span>

<span data-ttu-id="fa4c2-114">如果您建立 **PSSession** 而不是使用 CIM 會話，則 PowerShell 會驗證連接設定，然後建立並維護連接。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-114">If you create a **PSSession** instead of using a CIM session, PowerShell validates connection settings, and then establishes and maintains the connection.</span></span> <span data-ttu-id="fa4c2-115">如果您使用 CIM 會話，則在需要時 PowerShell 不會開啟網路連接。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-115">If you use CIM sessions, PowerShell does not open a network connection until needed.</span></span> <span data-ttu-id="fa4c2-116">如需 PowerShell 會話的詳細資訊，請參閱 [about_PSSessions](about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-116">For more information about PowerShell sessions, see [about_PSSessions](about_PSSessions.md).</span></span>

## <a name="when-to-use-a-cim-session"></a><span data-ttu-id="fa4c2-117">使用 CIM 會話的時機</span><span class="sxs-lookup"><span data-stu-id="fa4c2-117">When to use a CIM session</span></span>

<span data-ttu-id="fa4c2-118">只有搭配 Windows Management Instrumentation (WMI) 提供者或 CIM over WS-Man 接受 CIM 會話的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-118">Only cmdlets that work with a Windows Management Instrumentation (WMI) provider or CIM over WS-Man accept CIM sessions.</span></span> <span data-ttu-id="fa4c2-119">若為其他 Cmdlet，請使用 **pssession** 。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-119">For other cmdlets, use **PSSessions** .</span></span>

<span data-ttu-id="fa4c2-120">當您使用 CIM 會話時，PowerShell 會在本機用戶端上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-120">When you use a CIM session, PowerShell runs the cmdlet on the local client.</span></span> <span data-ttu-id="fa4c2-121">它會使用 CIM 會話連接至 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-121">It connects to the WMI provider using the CIM session.</span></span> <span data-ttu-id="fa4c2-122">目的電腦不需要 PowerShell，甚至是任何版本的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-122">The target computer does not require PowerShell, or even any version of the Windows operating system.</span></span>

<span data-ttu-id="fa4c2-123">相反地，Cmdlet 會使用在目的電腦上執行的 **PSSession** 執行。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-123">In contrast, a cmdlet run using a **PSSession** runs on the target computer.</span></span>
<span data-ttu-id="fa4c2-124">目標系統上需要有 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-124">It requires PowerShell on the target system.</span></span> <span data-ttu-id="fa4c2-125">此外，此 Cmdlet 會將資料傳送回本機電腦。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-125">Furthermore, the cmdlet sends data back to the local computer.</span></span> <span data-ttu-id="fa4c2-126">PowerShell 會管理透過連線傳送的資料，並將大小保持在 Windows 遠端管理 (WinRM) 所設定的限制內。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-126">PowerShell manages the data sent over the connection, and keeps the size within the limits set by Windows Remote Management (WinRM).</span></span> <span data-ttu-id="fa4c2-127">CIM 會話不會強加 WinRM 限制。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-127">CIM sessions do not impose the WinRM limits.</span></span>

## <a name="using-cdxml-cmdlets"></a><span data-ttu-id="fa4c2-128">使用 CDXML Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fa4c2-128">Using CDXML cmdlets</span></span>

<span data-ttu-id="fa4c2-129">以 CIM 為基礎的 Cmdlet 定義 XML (CDXML) Cmdlet 可以撰寫成使用任何 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-129">CIM-based Cmdlet Definition XML (CDXML) cmdlets can be written to use any WMI Provider.</span></span> <span data-ttu-id="fa4c2-130">所有 WMI 提供者都會使用 **CimSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-130">All WMI providers use **CimSession** objects.</span></span> <span data-ttu-id="fa4c2-131">如需 CDXML 的詳細資訊，請參閱 [cdxml 定義和詞彙](/previous-versions/windows/desktop/wmi_v2/cdxml-overview)。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-131">For more information about CDXML, see [CDXML definition and terms](/previous-versions/windows/desktop/wmi_v2/cdxml-overview).</span></span>

<span data-ttu-id="fa4c2-132">CDXML Cmdlet 具有可採用 **CimSession** 物件陣列的自動 **CimSession** 參數。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-132">CDXML cmdlets have an automatic **CimSession** parameter that can take an array of **CimSession** objects.</span></span> <span data-ttu-id="fa4c2-133">根據預設，PowerShell 會將並行 CIM 連接數目限制為15。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-133">By default, PowerShell limits number of concurrent CIM Connections to 15.</span></span> <span data-ttu-id="fa4c2-134">這項限制可由執行 **ThrottleLimit** 的 CDXML Cmdlet 覆寫。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-134">This limit can be overridden by CDXML cmdlets that implement the **ThrottleLimit** .</span></span> <span data-ttu-id="fa4c2-135">若要瞭解 **ThrottleLimit** ，請參閱個別的 Cmdlet 檔。</span><span class="sxs-lookup"><span data-stu-id="fa4c2-135">See the individual cmdlet documentation to understand the **ThrottleLimit** .</span></span>

## <a name="see-also"></a><span data-ttu-id="fa4c2-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa4c2-136">SEE ALSO</span></span>

[<span data-ttu-id="fa4c2-137">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="fa4c2-137">New-CimSession</span></span>](xref:CimCmdlets.New-CimSession)

[<span data-ttu-id="fa4c2-138">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="fa4c2-138">about_PSSessions</span></span>](about_PSSessions.md)
