---
description: Windows Management Instrumentation (WMI) 使用通用訊息模型 (CIM) 來代表系統、應用程式、網路、裝置，以及現代企業的其他可管理元件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207891"
---
# <a name="about-wmi"></a><span data-ttu-id="08e4d-104">關於 WMI</span><span class="sxs-lookup"><span data-stu-id="08e4d-104">About WMI</span></span>

## <a name="short-description"></a><span data-ttu-id="08e4d-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="08e4d-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="08e4d-106">Windows Management Instrumentation (WMI) 使用通用訊息模型 (CIM) 來代表系統、應用程式、網路、裝置，以及現代企業的其他可管理元件。</span><span class="sxs-lookup"><span data-stu-id="08e4d-106">Windows Management Instrumentation (WMI) uses the Common Information Model (CIM) to represent systems, applications, networks, devices, and other manageable components of the modern enterprise.</span></span>

## <a name="long-description"></a><span data-ttu-id="08e4d-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="08e4d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="08e4d-108">Windows Management Instrumentation (WMI) 是 Microsoft 的 Web-Based Enterprise Management (WBEM) （業界標準）實行。</span><span class="sxs-lookup"><span data-stu-id="08e4d-108">Windows Management Instrumentation (WMI) is Microsoft's implementation of Web-Based Enterprise Management (WBEM), the industry standard.</span></span>

<span data-ttu-id="08e4d-109">傳統 WMI 使用 DCOM 與網路裝置通訊，以管理遠端系統。</span><span class="sxs-lookup"><span data-stu-id="08e4d-109">Classic WMI uses DCOM to communicate with networked devices to manage remote systems.</span></span> <span data-ttu-id="08e4d-110">Windows PowerShell 3.0 引進了 CIM 提供者模型，此模型會使用 WinRM 來移除 DCOM 的相依性。</span><span class="sxs-lookup"><span data-stu-id="08e4d-110">Windows PowerShell 3.0 introduces a CIM provider model that uses WinRM to remove the dependency on DCOM.</span></span> <span data-ttu-id="08e4d-111">這個 CIM 提供者模型也會使用新的 WMI 提供者 Api，讓開發人員以機器碼撰寫 Windows PowerShell Cmdlet (C \+ \+) 。</span><span class="sxs-lookup"><span data-stu-id="08e4d-111">This CIM provider model also uses new WMI provider APIs that enable developers to write Windows PowerShell cmdlets in native code (C\+\+).</span></span>

<span data-ttu-id="08e4d-112">請勿混淆 WMI 提供者與 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="08e4d-112">Do not confuse WMI providers with Windows PowerShell providers.</span></span> <span data-ttu-id="08e4d-113">許多 Windows 功能都有相關聯的 WMI 提供者，它會公開其管理功能。</span><span class="sxs-lookup"><span data-stu-id="08e4d-113">Many Windows features have an associated WMI provider that exposes their management capabilities.</span></span> <span data-ttu-id="08e4d-114">若要取得 WMI 提供者，請執行 WMI 查詢來取得 __Provider WMI 類別的實例，如下列查詢所示。</span><span class="sxs-lookup"><span data-stu-id="08e4d-114">To get WMI providers, run a WMI query that gets instances of the __Provider WMI class, such as the following query.</span></span>

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a><span data-ttu-id="08e4d-115">WMI 的三個元件</span><span class="sxs-lookup"><span data-stu-id="08e4d-115">THREE COMPONENTS OF WMI</span></span>

<span data-ttu-id="08e4d-116">下列三個 WMI 元件會與 Windows PowerShell 互動：命名空間、提供者和類別。</span><span class="sxs-lookup"><span data-stu-id="08e4d-116">The following three components of WMI interact with Windows PowerShell: Namespaces, Providers, and Classes.</span></span>

<span data-ttu-id="08e4d-117">WMI 命名空間會將 WMI 提供者和 WMI 類別組織成相關元件的群組。</span><span class="sxs-lookup"><span data-stu-id="08e4d-117">WMI Namespaces organize WMI providers and WMI classes into groups of related components.</span></span> <span data-ttu-id="08e4d-118">如此一來，它們就類似 .NET Framework 命名空間。</span><span class="sxs-lookup"><span data-stu-id="08e4d-118">In this way, they are similar to .NET Framework namespaces.</span></span>
<span data-ttu-id="08e4d-119">命名空間不是實體位置，而是比較類似的邏輯資料庫。</span><span class="sxs-lookup"><span data-stu-id="08e4d-119">Namespaces are not physical locations, but are more like logical databases.</span></span>
<span data-ttu-id="08e4d-120">所有 WMI 命名空間都是 __Namespace 系統類別的實例。</span><span class="sxs-lookup"><span data-stu-id="08e4d-120">All WMI namespaces are instances of the __Namespace system class.</span></span> <span data-ttu-id="08e4d-121">預設的 WMI 命名空間是 \/ Microsoft Windows 2000) 之後 (根 CIMV2。</span><span class="sxs-lookup"><span data-stu-id="08e4d-121">The default WMI namespace is Root\/CIMV2 (since Microsoft Windows 2000).</span></span> <span data-ttu-id="08e4d-122">若要使用 Windows PowerShell 取得目前會話中的 WMI 命名空間，請使用具有下列格式的命令。</span><span class="sxs-lookup"><span data-stu-id="08e4d-122">To use Windows PowerShell to get WMI namespaces in the current session, use a command with the following format.</span></span>

```powershell
Get-WmiObject -Class __Namespace
```

<span data-ttu-id="08e4d-123">若要取得其他命名空間中的 WMI 命名空間，請使用 Namespace 參數來變更搜尋的位置。</span><span class="sxs-lookup"><span data-stu-id="08e4d-123">To get WMI namespaces in other namespaces, use the Namespace parameter to change the location of the search.</span></span> <span data-ttu-id="08e4d-124">下列命令會尋找位於根/Cimv2/Applications 命名空間中的 WMI 命名空間。</span><span class="sxs-lookup"><span data-stu-id="08e4d-124">The following command finds WMI namespaces that reside in the Root/Cimv2/Applications namespace.</span></span>

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

<span data-ttu-id="08e4d-125">WMI 命名空間是階層式的。</span><span class="sxs-lookup"><span data-stu-id="08e4d-125">WMI namespaces are hierarchical.</span></span> <span data-ttu-id="08e4d-126">因此，若要取得特定系統上的所有命名空間清單，則必須執行從根命名空間開始的遞迴查詢。</span><span class="sxs-lookup"><span data-stu-id="08e4d-126">Therefore, obtaining a list of all namespaces on a particular system requires performing a recursive query starting at the root namespace.</span></span>

<span data-ttu-id="08e4d-127">WMI 提供者會公開 Windows 可管理物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="08e4d-127">WMI Providers expose information about Windows manageable objects.</span></span> <span data-ttu-id="08e4d-128">提供者會從元件中取出資料，並透過 WMI 將該資料傳遞至管理應用程式，例如 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="08e4d-128">A provider retrieves data from a component, and passes that data through WMI to a management application, such as Windows PowerShell.</span></span> <span data-ttu-id="08e4d-129">大部分的 WMI 提供者都是動態提供者，這表示它們會在透過管理應用程式要求時動態取得資料。</span><span class="sxs-lookup"><span data-stu-id="08e4d-129">Most WMI providers are dynamic providers, which means that they obtain the data dynamically when it is requested through the management application.</span></span>

## <a name="finding-wmi-classes"></a><span data-ttu-id="08e4d-130">尋找 WMI 類別</span><span class="sxs-lookup"><span data-stu-id="08e4d-130">FINDING WMI CLASSES</span></span>

<span data-ttu-id="08e4d-131">在 Windows 8 的預設安裝中，根 Cimv2 中有1100以上的 WMI 類別 \/ 。</span><span class="sxs-lookup"><span data-stu-id="08e4d-131">In a default installation of Windows 8, there are more than 1,100 WMI classes in Root\/Cimv2.</span></span> <span data-ttu-id="08e4d-132">有了許多 WMI 類別，挑戰就變成識別要用來執行特定工作的適當 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="08e4d-132">With this many WMI classes, the challenge becomes identifying the appropriate WMI class to use to perform a specific task.</span></span> <span data-ttu-id="08e4d-133">Windows PowerShell 3.0 提供兩種方式來尋找與特定主題相關的 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="08e4d-133">Windows PowerShell 3.0 provides two ways to find WMI classes that are related to a specific topic.</span></span>

<span data-ttu-id="08e4d-134">例如，若要在跟磁片相關的根 \\ CIMV2 wmi 命名空間中尋找 wmi 類別，您可以使用如下所示的查詢。</span><span class="sxs-lookup"><span data-stu-id="08e4d-134">For example,to find WMI classes in the root\\CIMV2 WMI namespace that are related to disks, you can use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *disk*
```

<span data-ttu-id="08e4d-135">若要尋找與記憶體相關的 WMI 類別，您可以使用如下所示的查詢。</span><span class="sxs-lookup"><span data-stu-id="08e4d-135">To find WMI classes that are related to memory, you might use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *memory*
```

<span data-ttu-id="08e4d-136">CIM Cmdlet 也提供探索 WMI 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="08e4d-136">The CIM cmdlets also provide the ability to discover WMI classes.</span></span> <span data-ttu-id="08e4d-137">若要這樣做，請使用 Get-CIMClass Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="08e4d-137">To do this, use the Get-CIMClass cmdlet.</span></span> <span data-ttu-id="08e4d-138">此處顯示的命令會列出與影片相關的 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="08e4d-138">The command shown here lists WMI classes related to video.</span></span>

```powershell
Get-CimClass *video*
```

<span data-ttu-id="08e4d-139">索引標籤擴充可在變更 WMI 命名空間時運作，因此使用 tab 鍵擴充可輕鬆地探索子 WMI 命名空間。</span><span class="sxs-lookup"><span data-stu-id="08e4d-139">Tab expansion works when changing WMI namespaces, and therefore use of tab expansion makes sub-WMI namespaces easily discoverable.</span></span> <span data-ttu-id="08e4d-140">在下列範例中，Get-CimClass Cmdlet 會列出與電源設定相關的 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="08e4d-140">In the following example, the Get-CimClass cmdlet lists WMI classes related to power settings.</span></span>
<span data-ttu-id="08e4d-141">若要找到它，請輸入 `root/CIMV2/` 命名空間，然後按下 tab 鍵數次，直到 power namespace 出現為止。</span><span class="sxs-lookup"><span data-stu-id="08e4d-141">To find it, type the `root/CIMV2/` namespace and then press the Tab key several times until the power namespace appears.</span></span> <span data-ttu-id="08e4d-142">命令如下：</span><span class="sxs-lookup"><span data-stu-id="08e4d-142">Here is the command:</span></span>

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
