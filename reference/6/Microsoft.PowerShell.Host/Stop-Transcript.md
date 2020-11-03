---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 5f02f59e778c55b2292bb4533cf2f8aaab2dbb7d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196676"
---
# <span data-ttu-id="f62d9-103">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="f62d9-103">Stop-Transcript</span></span>

## <span data-ttu-id="f62d9-104">概要</span><span class="sxs-lookup"><span data-stu-id="f62d9-104">SYNOPSIS</span></span>
<span data-ttu-id="f62d9-105">停止文字記錄。</span><span class="sxs-lookup"><span data-stu-id="f62d9-105">Stops a transcript.</span></span>

## <span data-ttu-id="f62d9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f62d9-106">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="f62d9-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f62d9-107">DESCRIPTION</span></span>

<span data-ttu-id="f62d9-108">此 `Stop-Transcript` Cmdlet 會停止 Cmdlet 所啟動的文字記錄 `Start-Transcript` 。</span><span class="sxs-lookup"><span data-stu-id="f62d9-108">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="f62d9-109">或者，您可以結束工作階段以停止文字記錄。</span><span class="sxs-lookup"><span data-stu-id="f62d9-109">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="f62d9-110">範例</span><span class="sxs-lookup"><span data-stu-id="f62d9-110">EXAMPLES</span></span>

### <span data-ttu-id="f62d9-111">範例 1︰停止所有文字記錄</span><span class="sxs-lookup"><span data-stu-id="f62d9-111">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="f62d9-112">此命令會停止所有文字記錄。</span><span class="sxs-lookup"><span data-stu-id="f62d9-112">This command stops all transcripts.</span></span>

## <span data-ttu-id="f62d9-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f62d9-113">PARAMETERS</span></span>

### <span data-ttu-id="f62d9-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f62d9-114">CommonParameters</span></span>

<span data-ttu-id="f62d9-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f62d9-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f62d9-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f62d9-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f62d9-117">輸入</span><span class="sxs-lookup"><span data-stu-id="f62d9-117">INPUTS</span></span>

### <span data-ttu-id="f62d9-118">無</span><span class="sxs-lookup"><span data-stu-id="f62d9-118">None</span></span>

<span data-ttu-id="f62d9-119">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f62d9-119">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f62d9-120">輸出</span><span class="sxs-lookup"><span data-stu-id="f62d9-120">OUTPUTS</span></span>

### <span data-ttu-id="f62d9-121">System.String</span><span class="sxs-lookup"><span data-stu-id="f62d9-121">System.String</span></span>

<span data-ttu-id="f62d9-122">此 Cmdlet 會傳回包含狀態訊息和輸出檔路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="f62d9-122">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="f62d9-123">注意</span><span class="sxs-lookup"><span data-stu-id="f62d9-123">NOTES</span></span>

* <span data-ttu-id="f62d9-124">如果文字記錄尚未啟動，此命令便會失敗。</span><span class="sxs-lookup"><span data-stu-id="f62d9-124">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="f62d9-125">相關連結</span><span class="sxs-lookup"><span data-stu-id="f62d9-125">RELATED LINKS</span></span>

[<span data-ttu-id="f62d9-126">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="f62d9-126">Start-Transcript</span></span>](Start-Transcript.md)
