---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 472a4c8fbb9eb0d37827aff4fcfd6bb9a67f4743
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202287"
---
# <span data-ttu-id="43239-103">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="43239-103">Get-PSSnapin</span></span>

## <span data-ttu-id="43239-104">概要</span><span class="sxs-lookup"><span data-stu-id="43239-104">SYNOPSIS</span></span>
<span data-ttu-id="43239-105">取得電腦上的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-105">Gets the Windows PowerShell snap-ins on the computer.</span></span>

## <span data-ttu-id="43239-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43239-106">SYNTAX</span></span>

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## <span data-ttu-id="43239-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="43239-107">DESCRIPTION</span></span>
<span data-ttu-id="43239-108">**PSSnapin** 指令程式會取得已新增至目前會話或已在系統上註冊的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-108">The **Get-PSSnapin** cmdlet gets the Windows PowerShell snap-ins that have been added to the current session or that have been registered on the system.</span></span>
<span data-ttu-id="43239-109">此 Cmdlet 會以偵測到的順序列出嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-109">This cmdlet lists the snap-ins in the order in which they are detected.</span></span>

<span data-ttu-id="43239-110">**PSSnapin** 只會取得已註冊的嵌入式管理單元。若要註冊 Windows PowerShell 嵌入式管理單元，請使用 Microsoft .NET Framework 2.0 隨附的 Installutil.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="43239-110">**Get-PSSnapin** gets only registered snap-ins. To register a Windows PowerShell snap-in, use the InstallUtil tool included with the Microsoft .NET Framework 2.0.</span></span>
<span data-ttu-id="43239-111">如需詳細資訊，請參閱 MSDN library 中的 [如何註冊 Cmdlet、提供者和主機應用程式](https://go.microsoft.com/fwlink/?LinkID=143619) 。</span><span class="sxs-lookup"><span data-stu-id="43239-111">For more information, see [How to Register Cmdlets, Providers, and Host Applications](https://go.microsoft.com/fwlink/?LinkID=143619) in the MSDN library.</span></span>

<span data-ttu-id="43239-112">從 Windows PowerShell 3.0 開始，Windows PowerShell 中包含的核心命令已經封裝成模組。</span><span class="sxs-lookup"><span data-stu-id="43239-112">Starting in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span>
<span data-ttu-id="43239-113">**Microsoft.PowerShell.Core** 是一個例外，它是一個嵌入式管理單元 (PSSnapin)。</span><span class="sxs-lookup"><span data-stu-id="43239-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="43239-114">依照預設，只會新增 **Microsoft.PowerShell.Core** 嵌入式管理單元至工作階段。</span><span class="sxs-lookup"><span data-stu-id="43239-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span>
<span data-ttu-id="43239-115">模組會在第一次使用時自動匯入，而您可以使用 Import-Module Cmdlet 來匯入它們。</span><span class="sxs-lookup"><span data-stu-id="43239-115">Modules are imported automatically on first use and you can use the Import-Module cmdlet to import them.</span></span>

## <span data-ttu-id="43239-116">範例</span><span class="sxs-lookup"><span data-stu-id="43239-116">EXAMPLES</span></span>

### <span data-ttu-id="43239-117">範例 1︰取得目前載入的嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="43239-117">Example 1: Get snap-ins that are currently loaded</span></span>

```
PS C:\> Get-PSSnapIn
```

<span data-ttu-id="43239-118">此命令取得工作階段中目前載入的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-118">This command gets the Windows PowerShell snap-ins that are currently loaded in the session.</span></span>
<span data-ttu-id="43239-119">這包括隨 Windows PowerShell 安裝，以及已新增至工作階段的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-119">This includes the snap-ins that are installed with Windows PowerShell and those that have been added to the session.</span></span>

### <span data-ttu-id="43239-120">範例 2︰取得已註冊的嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="43239-120">Example 2: Get snap-ins that have been registered</span></span>

```
PS C:\> get-PSSnapIn -Registered
```

<span data-ttu-id="43239-121">此命令取得已在電腦上註冊 (包括已新增至工作階段) 的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-121">This command gets the Windows PowerShell snap-ins that have been registered on the computer, including those that have already been added to the session.</span></span>
<span data-ttu-id="43239-122">輸出不包括隨 Windows PowerShell 或 Windows PowerShell 嵌入式管理單元動態連結程式庫 (DLL) 安裝，但尚未在系統上註冊的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-122">The output does not include snap-ins that are installed with Windows PowerShell or Windows PowerShell snap-in dynamic-link libraries (DLLs) that have not yet been registered on the system.</span></span>

### <span data-ttu-id="43239-123">範例 3︰取得目前的嵌入式管理單元中符合字串的項目</span><span class="sxs-lookup"><span data-stu-id="43239-123">Example 3: Get current snap-ins that match a string</span></span>

```
PS C:\> Get-PSSnapIn -Name smp*
```

<span data-ttu-id="43239-124">此命令取得目前工作階段中名稱以 smp 開頭的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-124">This command gets the Windows PowerShell snap-ins in the current session that have names that begin with smp.</span></span>

## <span data-ttu-id="43239-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43239-125">PARAMETERS</span></span>

### <span data-ttu-id="43239-126">-Name</span><span class="sxs-lookup"><span data-stu-id="43239-126">-Name</span></span>
<span data-ttu-id="43239-127">指定嵌入式管理單元名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="43239-127">Specifies an array of snap-in names.</span></span>
<span data-ttu-id="43239-128">此 Cmdlet 只會取得指定的 Windows PowerShell 嵌入式管理單元。允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="43239-128">This cmdlet gets only the specified Windows PowerShell snap-ins. Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43239-129">-Registered</span><span class="sxs-lookup"><span data-stu-id="43239-129">-Registered</span></span>
<span data-ttu-id="43239-130">指示此 Cmdlet 取得已在系統上註冊的 Windows PowerShell 嵌入式管理單元 (即使它們尚未新增至工作階段)。</span><span class="sxs-lookup"><span data-stu-id="43239-130">Indicates that this cmdlet gets the Windows PowerShell snap-ins that have been registered on the system even if they have not yet been added to the session.</span></span>

<span data-ttu-id="43239-131">隨 Windows PowerShell 安裝的嵌入式管理單元不會出現在此清單中。</span><span class="sxs-lookup"><span data-stu-id="43239-131">The snap-ins that are installed with Windows PowerShell do not appear in this list.</span></span>

<span data-ttu-id="43239-132">如果沒有這個參數， **PSSnapin** 會取得已新增至會話的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-132">Without this parameter, **Get-PSSnapin** gets the Windows PowerShell snap-ins that have been added to the session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43239-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43239-133">CommonParameters</span></span>
<span data-ttu-id="43239-134">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="43239-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43239-135">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="43239-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43239-136">輸入</span><span class="sxs-lookup"><span data-stu-id="43239-136">INPUTS</span></span>

### <span data-ttu-id="43239-137">無</span><span class="sxs-lookup"><span data-stu-id="43239-137">None</span></span>
<span data-ttu-id="43239-138">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43239-138">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="43239-139">輸出</span><span class="sxs-lookup"><span data-stu-id="43239-139">OUTPUTS</span></span>

### <span data-ttu-id="43239-140">System.Management.Automation.PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="43239-140">System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="43239-141">Get-PSSnapin 對於取得的每個嵌入式管理單元，會傳回一個物件。</span><span class="sxs-lookup"><span data-stu-id="43239-141">Get-PSSnapin returns an object for each snap-in that it gets.</span></span>

## <span data-ttu-id="43239-142">注意</span><span class="sxs-lookup"><span data-stu-id="43239-142">NOTES</span></span>

* <span data-ttu-id="43239-143">從 Windows PowerShell 3.0 開始，與 Windows PowerShell 一起安裝的核心命令已經封裝成模組。</span><span class="sxs-lookup"><span data-stu-id="43239-143">Starting in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="43239-144">在 Windows PowerShell 2.0，以及在較新版本之 Windows PowerShell 中建立舊式工作階段的主機程式中，核心命令是封裝成嵌入式管理單元 ( **PSSnapin** )。</span><span class="sxs-lookup"><span data-stu-id="43239-144">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins ( **PSSnapin** ).</span></span> <span data-ttu-id="43239-145">**Microsoft.PowerShell.Core** 是一個例外，它一律是一個嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43239-145">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="43239-146">此外，遠端工作階段 (例如由 New-PSSession cmdlet 所啟動的遠端工作階段) 都是包含核心嵌入式管理單元的舊式工作階段。</span><span class="sxs-lookup"><span data-stu-id="43239-146">Also, remote sessions, such as those started by the New-PSSession cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="43239-147">如需有關使用核心模組建立較新樣式會話的 **CreateDefault2** 方法的詳細資訊，請參閱 MSDN library 中的 [CreateDefault2 方法](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) 。</span><span class="sxs-lookup"><span data-stu-id="43239-147">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) in the MSDN library.</span></span>

## <span data-ttu-id="43239-148">相關連結</span><span class="sxs-lookup"><span data-stu-id="43239-148">RELATED LINKS</span></span>

[<span data-ttu-id="43239-149">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="43239-149">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="43239-150">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="43239-150">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
