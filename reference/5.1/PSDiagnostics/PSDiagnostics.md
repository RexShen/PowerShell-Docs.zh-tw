---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=855965
Help Version: 5.2.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: c61d6278-02a3-4618-ae37-a524d40a7f44
Module Name: PSDiagnostics
ms.date: 11/27/2018
schema: 2.0.0
title: PSDiagnostics 模組
ms.openlocfilehash: 7261b46fb0c15ac128be9897503c7a6bb7d5fccc
ms.sourcegitcommit: 3571b9e87e8881adbf7984cda46a63891039a987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "93201111"
---
# <span data-ttu-id="7a40d-103">PSDiagnostics 模組</span><span class="sxs-lookup"><span data-stu-id="7a40d-103">PSDiagnostics Module</span></span>

## <span data-ttu-id="7a40d-104">描述</span><span class="sxs-lookup"><span data-stu-id="7a40d-104">Description</span></span>

<span data-ttu-id="7a40d-105">PowerShell 診斷模組包含一組 Cmdlet，可讓您在 Windows 上的 PowerShell 中使用 ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="7a40d-105">The PowerShell Diagnostics Module contains a set of cmdlets that enables the use of ETW tracing in PowerShell on Windows.</span></span>

## <span data-ttu-id="7a40d-106">PSDiagnostics Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7a40d-106">PSDiagnostics Cmdlets</span></span>

### [<span data-ttu-id="7a40d-107">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="7a40d-107">Disable-PSTrace</span></span>](Disable-PSTrace.md)
<span data-ttu-id="7a40d-108">停用 Microsoft Windows PowerShell 事件提供者記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7a40d-108">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

### [<span data-ttu-id="7a40d-109">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="7a40d-109">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
<span data-ttu-id="7a40d-110">停止 PSWSManCombinedTrace 啟動的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="7a40d-110">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

### [<span data-ttu-id="7a40d-111">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="7a40d-111">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
<span data-ttu-id="7a40d-112">停止啟用-WSManTrace 所啟動的 WSMan 記錄會話。</span><span class="sxs-lookup"><span data-stu-id="7a40d-112">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

### [<span data-ttu-id="7a40d-113">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="7a40d-113">Enable-PSTrace</span></span>](Enable-PSTrace.md)
<span data-ttu-id="7a40d-114">啟用 Microsoft Windows-PowerShell 事件提供者記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7a40d-114">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

### [<span data-ttu-id="7a40d-115">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="7a40d-115">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)
<span data-ttu-id="7a40d-116">啟動已啟用 WSMan 和 PowerShell 提供者的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="7a40d-116">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

### [<span data-ttu-id="7a40d-117">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="7a40d-117">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
<span data-ttu-id="7a40d-118">啟動已啟用 WSMan 提供者的記錄會話。</span><span class="sxs-lookup"><span data-stu-id="7a40d-118">Start a logging session with the WSMan providers enabled.</span></span>

### [<span data-ttu-id="7a40d-119">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="7a40d-119">Get-LogProperties</span></span>](Get-LogProperties.md)
<span data-ttu-id="7a40d-120">抓取 Windows 事件記錄檔的屬性。</span><span class="sxs-lookup"><span data-stu-id="7a40d-120">Retrieves the properties of a Windows event log.</span></span>

### [<span data-ttu-id="7a40d-121">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="7a40d-121">Set-LogProperties</span></span>](Set-LogProperties.md)
<span data-ttu-id="7a40d-122">變更 Windows 事件記錄檔的屬性。</span><span class="sxs-lookup"><span data-stu-id="7a40d-122">Changes the properties of a Windows event log.</span></span>

### [<span data-ttu-id="7a40d-123">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="7a40d-123">Start-Trace</span></span>](Start-Trace.md)
<span data-ttu-id="7a40d-124">啟動事件追蹤記錄會話。</span><span class="sxs-lookup"><span data-stu-id="7a40d-124">Start an Event Trace logging session.</span></span>

### [<span data-ttu-id="7a40d-125">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="7a40d-125">Stop-Trace</span></span>](Stop-Trace.md)
<span data-ttu-id="7a40d-126">停止事件追蹤記錄會話。</span><span class="sxs-lookup"><span data-stu-id="7a40d-126">Stop an Event Trace logging session.</span></span>
