---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 22298a898bd45a9be5eaf98d4963b98ab1bf063b
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196678"
---
# <span data-ttu-id="123ee-103">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="123ee-103">Stop-Transcript</span></span>

## <span data-ttu-id="123ee-104">概要</span><span class="sxs-lookup"><span data-stu-id="123ee-104">SYNOPSIS</span></span>
<span data-ttu-id="123ee-105">停止文字記錄。</span><span class="sxs-lookup"><span data-stu-id="123ee-105">Stops a transcript.</span></span>

## <span data-ttu-id="123ee-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="123ee-106">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="123ee-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="123ee-107">DESCRIPTION</span></span>
<span data-ttu-id="123ee-108">此 `Stop-Transcript` Cmdlet 會停止 Cmdlet 所啟動的文字記錄 `Start-Transcript` 。</span><span class="sxs-lookup"><span data-stu-id="123ee-108">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="123ee-109">或者，您可以結束工作階段以停止文字記錄。</span><span class="sxs-lookup"><span data-stu-id="123ee-109">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="123ee-110">範例</span><span class="sxs-lookup"><span data-stu-id="123ee-110">EXAMPLES</span></span>

### <span data-ttu-id="123ee-111">範例 1︰停止所有文字記錄</span><span class="sxs-lookup"><span data-stu-id="123ee-111">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="123ee-112">此命令會停止所有文字記錄。</span><span class="sxs-lookup"><span data-stu-id="123ee-112">This command stops all transcripts.</span></span>

## <span data-ttu-id="123ee-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="123ee-113">PARAMETERS</span></span>

### <span data-ttu-id="123ee-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="123ee-114">CommonParameters</span></span>
<span data-ttu-id="123ee-115">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="123ee-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="123ee-116">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="123ee-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="123ee-117">輸入</span><span class="sxs-lookup"><span data-stu-id="123ee-117">INPUTS</span></span>

### <span data-ttu-id="123ee-118">無</span><span class="sxs-lookup"><span data-stu-id="123ee-118">None</span></span>
<span data-ttu-id="123ee-119">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="123ee-119">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="123ee-120">輸出</span><span class="sxs-lookup"><span data-stu-id="123ee-120">OUTPUTS</span></span>

### <span data-ttu-id="123ee-121">System.String</span><span class="sxs-lookup"><span data-stu-id="123ee-121">System.String</span></span>
<span data-ttu-id="123ee-122">此 Cmdlet 會傳回包含狀態訊息和輸出檔路徑的字串。</span><span class="sxs-lookup"><span data-stu-id="123ee-122">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="123ee-123">注意</span><span class="sxs-lookup"><span data-stu-id="123ee-123">NOTES</span></span>

* <span data-ttu-id="123ee-124">如果文字記錄尚未啟動，此命令便會失敗。</span><span class="sxs-lookup"><span data-stu-id="123ee-124">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="123ee-125">相關連結</span><span class="sxs-lookup"><span data-stu-id="123ee-125">RELATED LINKS</span></span>

[<span data-ttu-id="123ee-126">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="123ee-126">Start-Transcript</span></span>](Start-Transcript.md)
