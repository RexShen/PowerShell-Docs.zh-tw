---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203491"
---
# <span data-ttu-id="15f0c-103">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="15f0c-103">Show-EventLog</span></span>

## <span data-ttu-id="15f0c-104">概要</span><span class="sxs-lookup"><span data-stu-id="15f0c-104">SYNOPSIS</span></span>
<span data-ttu-id="15f0c-105">在 [事件檢視器] 中顯示本機或遠端電腦的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="15f0c-105">Displays the event logs of the local or a remote computer in Event Viewer.</span></span>

## <span data-ttu-id="15f0c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="15f0c-106">SYNTAX</span></span>

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="15f0c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="15f0c-107">DESCRIPTION</span></span>
<span data-ttu-id="15f0c-108">**Show-EventLog** Cmdlet 會在本機電腦上開啟事件檢視器，並在本機電腦或遠端電腦上顯示所有傳統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="15f0c-108">The **Show-EventLog** cmdlet opens Event Viewer on the local computer and displays in it all of the classic event logs on the local computer or a remote computer.</span></span>

<span data-ttu-id="15f0c-109">在 Windows Vista 或更新版本的 Windows 作業系統中，若要開啟 [事件檢視器]，則目前的使用者必須是本機電腦上 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="15f0c-109">To open Event Viewer on Windows Vista and later versions of the Windows operating system, the current user must be a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="15f0c-110">包含 **eventlog** 名詞 ( **eventlog** Cmdlet 的指令程式) 只會在傳統事件記錄檔上運作。</span><span class="sxs-lookup"><span data-stu-id="15f0c-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="15f0c-111">在 Windows Vista 和更新版本的 Windows 作業系統中，若要從使用「Windows 事件記錄檔」技術的記錄檔中取得事件，請使用 Get-WinEvent Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="15f0c-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="15f0c-112">範例</span><span class="sxs-lookup"><span data-stu-id="15f0c-112">EXAMPLES</span></span>

### <span data-ttu-id="15f0c-113">範例 1︰顯示本機電腦的事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="15f0c-113">Example 1: Display event logs for the local computer</span></span>

```
PS C:\> Show-EventLog
```

<span data-ttu-id="15f0c-114">此命令會開啟 [事件檢視器]，並顯示本機電腦上的傳統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="15f0c-114">This command opens Event Viewer and displays in it the classic event logs on the local computer.</span></span>

### <span data-ttu-id="15f0c-115">範例 2︰顯示遠端電腦的事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="15f0c-115">Example 2: Display event logs for a remote computer</span></span>

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

<span data-ttu-id="15f0c-116">此命令會開啟 [事件檢視器]，並顯示 Server01 電腦上的傳統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="15f0c-116">This command opens Event Viewer and displays in it the classic event logs on the Server01 computer.</span></span>

## <span data-ttu-id="15f0c-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="15f0c-117">PARAMETERS</span></span>

### <span data-ttu-id="15f0c-118">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="15f0c-118">-ComputerName</span></span>
<span data-ttu-id="15f0c-119">指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="15f0c-119">Specifies a remote computer.</span></span>
<span data-ttu-id="15f0c-120">**Show-EventLog** 會顯示本機電腦上事件檢視器中指定電腦的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="15f0c-120">**Show-EventLog** displays the event logs from the specified computer in Event Viewer on the local computer.</span></span>
<span data-ttu-id="15f0c-121">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="15f0c-121">The default is the local computer.</span></span>

<span data-ttu-id="15f0c-122">輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="15f0c-122">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="15f0c-123">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="15f0c-123">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="15f0c-124">即使您的電腦未設定為執行遠端命令，您仍然可以使用 *ComputerName* 參數。</span><span class="sxs-lookup"><span data-stu-id="15f0c-124">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f0c-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15f0c-125">CommonParameters</span></span>
<span data-ttu-id="15f0c-126">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="15f0c-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15f0c-127">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="15f0c-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="15f0c-128">輸入</span><span class="sxs-lookup"><span data-stu-id="15f0c-128">INPUTS</span></span>

### <span data-ttu-id="15f0c-129">無</span><span class="sxs-lookup"><span data-stu-id="15f0c-129">None</span></span>
<span data-ttu-id="15f0c-130">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="15f0c-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="15f0c-131">輸出</span><span class="sxs-lookup"><span data-stu-id="15f0c-131">OUTPUTS</span></span>

### <span data-ttu-id="15f0c-132">無</span><span class="sxs-lookup"><span data-stu-id="15f0c-132">None</span></span>
<span data-ttu-id="15f0c-133">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="15f0c-133">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="15f0c-134">注意</span><span class="sxs-lookup"><span data-stu-id="15f0c-134">NOTES</span></span>

* <span data-ttu-id="15f0c-135">[事件檢視器] 一開啟，Windows PowerShell 命令提示字元就會傳回。</span><span class="sxs-lookup"><span data-stu-id="15f0c-135">The Windows PowerShell command prompt returns as soon as Event Viewer opens.</span></span> <span data-ttu-id="15f0c-136">您可以在 [事件檢視器] 開啟時於目前的工作階段中工作。</span><span class="sxs-lookup"><span data-stu-id="15f0c-136">You can work in the current session while Event Viewer is open.</span></span>

  <span data-ttu-id="15f0c-137">因為此 Cmdlet 需要使用者介面，它無法在 Windows Server 的 Server Core 安裝上使用。</span><span class="sxs-lookup"><span data-stu-id="15f0c-137">Because this cmdlet requires a user interface, it does not work on Server Core installations of Windows Server.</span></span>

*

## <span data-ttu-id="15f0c-138">相關連結</span><span class="sxs-lookup"><span data-stu-id="15f0c-138">RELATED LINKS</span></span>

[<span data-ttu-id="15f0c-139">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="15f0c-139">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="15f0c-140">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="15f0c-140">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="15f0c-141">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="15f0c-141">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="15f0c-142">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="15f0c-142">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="15f0c-143">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="15f0c-143">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="15f0c-144">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="15f0c-144">Write-EventLog</span></span>](Write-EventLog.md)
