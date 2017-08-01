---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "JEA 上的報告"
ms.technology: powershell
ms.openlocfilehash: 3e7bd2755281f491bba8a905df018fb2e1cac6ff
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="reporting-on-jea"></a><span data-ttu-id="5df56-103">JEA 上的報告</span><span class="sxs-lookup"><span data-stu-id="5df56-103">Reporting on JEA</span></span>
<span data-ttu-id="5df56-104">因為 JEA 允許非特殊權限使用者在特殊權限內容中執行，所以記錄和稽核格外重要。</span><span class="sxs-lookup"><span data-stu-id="5df56-104">Because JEA allows non-privileged users to run in a privileged context, logging and auditing are extremely important.</span></span>
<span data-ttu-id="5df56-105">在本節中，我們將執行您可以用來協助記錄和報告的所有工具。</span><span class="sxs-lookup"><span data-stu-id="5df56-105">In this section, we'll run through the tools you can use to help you with logging and reporting.</span></span>

## <a name="reporting-on-jea-actions"></a><span data-ttu-id="5df56-106">報告 JEA 動作</span><span class="sxs-lookup"><span data-stu-id="5df56-106">Reporting on JEA Actions</span></span>
### <a name="over-the-shoulder-transcription"></a><span data-ttu-id="5df56-107">潛在文字記錄</span><span class="sxs-lookup"><span data-stu-id="5df56-107">Over-the-Shoulder Transcription</span></span>
<span data-ttu-id="5df56-108">摘要說明 PowerShell 工作階段狀況的其中一個最快速方法是回顧人員輸入的內容。</span><span class="sxs-lookup"><span data-stu-id="5df56-108">One of the quickest ways to get a summary of what's happening in a PowerShell session is to look over the shoulder of the person typing.</span></span>
<span data-ttu-id="5df56-109">您會看到其命令及這些命令的輸出安然無恙。</span><span class="sxs-lookup"><span data-stu-id="5df56-109">You see their commands, the output of those commands, and all is well.</span></span>
<span data-ttu-id="5df56-110">即使發生問題，至少您知道。</span><span class="sxs-lookup"><span data-stu-id="5df56-110">Or it's not, but at least you'll know.</span></span>
<span data-ttu-id="5df56-111">PowerShell 文字記錄的設計是為了讓您有與事實類似的檢視。</span><span class="sxs-lookup"><span data-stu-id="5df56-111">PowerShell transcription is designed to give you a similar view after the fact.</span></span>

<span data-ttu-id="5df56-112">使用工作階段設定中的 "TranscriptDirectory" 欄位時，PowerShell 會自動記錄在指定工作階段中執行之所有動作的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="5df56-112">When using the "TranscriptDirectory" field in your Session Configuration, PowerShell will automatically record a transcript of all actions taken in a given session.</span></span>
<span data-ttu-id="5df56-113">您可以在下列位置，找到本文工作階段的文字記錄："$env:ProgramData\JEAConfiguration\Transcripts"</span><span class="sxs-lookup"><span data-stu-id="5df56-113">You can find transcripts from your sessions in this document here: "$env:ProgramData\JEAConfiguration\Transcripts"</span></span>

<span data-ttu-id="5df56-114">如您所見，文字記錄會記錄「已連線」的使用者、「執行身分」使用者、在工作階段中執行之命令等相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5df56-114">As you can tell, the transcript records information about the "Connected" user, the "Run As" user, the commands run in the session, and more.</span></span>
<span data-ttu-id="5df56-115">如需 PowerShell 文字記錄的詳細資訊，請參閱這篇[部落格文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5df56-115">For more information about PowerShell transcription, check out [this blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>

### <a name="powershell-event-logs"></a><span data-ttu-id="5df56-116">PowerShell 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="5df56-116">PowerShell Event Logs</span></span>
<span data-ttu-id="5df56-117">當您開啟模組記錄時，所有 PowerShell 動作也會記錄在一般 Windows 事件記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="5df56-117">When you have module logging turned on, all PowerShell actions are also recorded in regular Windows Event logs.</span></span>
<span data-ttu-id="5df56-118">這比處理文字記錄稍微複雜，但提供給您的詳細程度會很實用。</span><span class="sxs-lookup"><span data-stu-id="5df56-118">This is slightly messier to deal with when compared to transcripts, but the level of detail it gives you can be useful.</span></span>

<span data-ttu-id="5df56-119">在 "PowerShell" 作業記錄中，如果您已啟用模組記錄，事件識別碼 4104 會記錄所叫用的每個命令。</span><span class="sxs-lookup"><span data-stu-id="5df56-119">In the "PowerShell" operational log, Event ID 4104 will record each command invoked if you have enabled module logging.</span></span>

### <a name="other-event-logs"></a><span data-ttu-id="5df56-120">其他事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="5df56-120">Other Event Logs</span></span>
<span data-ttu-id="5df56-121">不同於 PowerShell 記錄檔和文字記錄，其他記錄機制不會擷取「已連線的使用者」。</span><span class="sxs-lookup"><span data-stu-id="5df56-121">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the "Connected User".</span></span>
<span data-ttu-id="5df56-122">您必須在其他記錄檔與 PowerShell 記錄檔之間進行一些相互關聯，以對應到所執行的動作。</span><span class="sxs-lookup"><span data-stu-id="5df56-122">You will need to do some correlation between other logs and PowerShell logs to match up actions taken.</span></span>

<span data-ttu-id="5df56-123">在「Windows 遠端管理」作業記錄中，事件識別碼 193 會記錄連線使用者的 SID 和名稱，以及 RunAs 虛擬帳戶的 SID，以便協助此相互關聯。</span><span class="sxs-lookup"><span data-stu-id="5df56-123">In the "Windows Remote Management" operational log, Event ID 193 will record the Connecting User's SID and Name, as well as the RunAs Virtual Account's SID to assist with this correlation.</span></span>
<span data-ttu-id="5df56-124">您可能也注意到 RunAs 虛擬帳戶的名稱結尾包含連線使用者的網域和使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="5df56-124">You may have also noticed that the name of the RunAs Virtual Account includes the connecting user's domain and username at the end.</span></span>

## <a name="reporting-on-jea-configuration"></a><span data-ttu-id="5df56-125">報告 JEA 設定</span><span class="sxs-lookup"><span data-stu-id="5df56-125">Reporting on JEA Configuration</span></span>
### <a name="get-pssessionconfiguration"></a><span data-ttu-id="5df56-126">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5df56-126">Get-PSSessionConfiguration</span></span>
<span data-ttu-id="5df56-127">為了精確地報告環境的狀態，請務必了解您在電腦上設定的 JEA 端點數目。</span><span class="sxs-lookup"><span data-stu-id="5df56-127">In order to accurately report on the state of your environment, it's important to know how many JEA endpoints you have set up on your machine.</span></span>
<span data-ttu-id="5df56-128">`Get-PSSessionConfiguration` 便能執行此作業。</span><span class="sxs-lookup"><span data-stu-id="5df56-128">`Get-PSSessionConfiguration` does just that.</span></span>

### <a name="get-pssessioncapability"></a><span data-ttu-id="5df56-129">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="5df56-129">Get-PSSessionCapability</span></span>
<span data-ttu-id="5df56-130">透過 JEA 端點手動報告任何指定使用者的功能可能相當複雜。</span><span class="sxs-lookup"><span data-stu-id="5df56-130">Manually reporting on the capabilities of any given user through a JEA endpoint can be quite complex.</span></span>
<span data-ttu-id="5df56-131">您可能必須檢查幾個角色功能。</span><span class="sxs-lookup"><span data-stu-id="5df56-131">You would potentially need to inspect several role capabilities.</span></span>
<span data-ttu-id="5df56-132">所幸 "Get-PSSessionCapability" Cmdlet 可執行此作業。</span><span class="sxs-lookup"><span data-stu-id="5df56-132">Fortunately, the "Get-PSSessionCapability" cmdlet does this.</span></span>

<span data-ttu-id="5df56-133">若要對此進行測試，請從系統管理員的 PowerShell 命令提示字元執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="5df56-133">To test this out, run the following command from an administrator PowerShell prompt:</span></span>
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```

