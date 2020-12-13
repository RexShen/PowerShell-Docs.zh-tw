---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell SDK
description: Windows PowerShell SDK
ms.openlocfilehash: 751ccb02741db0ea63df1768dec4a19c5fa9ce92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390196"
---
# <a name="windows-powershell"></a><span data-ttu-id="a57b5-103">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a57b5-103">Windows PowerShell</span></span>

<span data-ttu-id="a57b5-104">更新日期：2013年7月8日</span><span class="sxs-lookup"><span data-stu-id="a57b5-104">Updated: July 8, 2013</span></span>

<span data-ttu-id="a57b5-105">Windows PowerShell &reg; 是以工作為基礎的命令列 shell 和指令碼語言，專為系統管理所設計。</span><span class="sxs-lookup"><span data-stu-id="a57b5-105">Windows PowerShell&reg; is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="a57b5-106">Windows PowerShell &reg; 可協助 IT 專業人員和 power 使用者控制及自動化 windows 作業系統和應用程式在 windows 上執行的系統管理工作，並以 .NET Framework 為基礎。</span><span class="sxs-lookup"><span data-stu-id="a57b5-106">Built on the .NET Framework, Windows PowerShell&reg; helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="a57b5-107">此處發佈的檔主要是針對需要 Windows PowerShell 所提供之 Api 相關參考資訊的 Cmdlet、提供者和主應用程式開發人員所撰寫。</span><span class="sxs-lookup"><span data-stu-id="a57b5-107">The documents published here are written primarily for cmdlet, provider, and host application developers who require reference information about the APIs provided by Windows PowerShell.</span></span>
<span data-ttu-id="a57b5-108">不過，系統管理員可能也會發現這些檔所提供的資訊很有用。</span><span class="sxs-lookup"><span data-stu-id="a57b5-108">However, system administrators might also find the information provided by these documents useful.</span></span>

<span data-ttu-id="a57b5-109">如需開始使用 Windows PowerShell 所需的基本資訊，請參閱 Windows PowerShell 的消費者入門。</span><span class="sxs-lookup"><span data-stu-id="a57b5-109">For the basic information needed to start using Windows PowerShell, see Getting Started with Windows PowerShell .</span></span>

## <a name="windows-powershell-documents"></a><span data-ttu-id="a57b5-110">Windows PowerShell 檔</span><span class="sxs-lookup"><span data-stu-id="a57b5-110">Windows PowerShell Documents</span></span>

- <span data-ttu-id="a57b5-111">[安裝 WINDOWS POWERSHELL SDK](./installing-the-windows-powershell-sdk.md) 提供如何安裝 Windows PowerShell SDK 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a57b5-111">[Installing the Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md) Provides information about how to install the Windows PowerShell SDK.</span></span>

- <span data-ttu-id="a57b5-112">[撰寫 Windows PowerShell 模組](./module/writing-a-windows-powershell-module.md) 為需要封裝和散發其 Windows PowerShell 解決方案的系統管理員、腳本開發人員和 Cmdlet 開發人員提供資訊。</span><span class="sxs-lookup"><span data-stu-id="a57b5-112">[Writing a Windows PowerShell Module](./module/writing-a-windows-powershell-module.md) Provides information for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell solutions.</span></span>

- <span data-ttu-id="a57b5-113">[撰寫 Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) 提供用來設計和執行 Cmdlet 的資訊。</span><span class="sxs-lookup"><span data-stu-id="a57b5-113">[Writing a Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Provides information for designing and implementing cmdlets.</span></span>

- <span data-ttu-id="a57b5-114">[撰寫 Windows PowerShell 提供者](./provider/writing-a-windows-powershell-provider.md) 提供用來設計和執行 Windows PowerShell 提供者的資訊。</span><span class="sxs-lookup"><span data-stu-id="a57b5-114">[Writing a Windows PowerShell Provider](./provider/writing-a-windows-powershell-provider.md) Provides information for designing and implementing Windows PowerShell providers.</span></span> <span data-ttu-id="a57b5-115">它將協助您瞭解 Windows PowerShell 提供者的運作方式，並提供可用來開始設計或撰寫您自己的提供者的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="a57b5-115">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

- <span data-ttu-id="a57b5-116">[撰寫 Windows PowerShell 主應用程式](./hosting/writing-a-windows-powershell-host-application.md) 提供的資訊可供設計主應用程式的程式管理員以及執行這些應用程式的開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="a57b5-116">[Writing a Windows PowerShell Host Application](./hosting/writing-a-windows-powershell-host-application.md) Provides information that can be used by program managers who are designing host applications and by developers who are implementing them.</span></span> <span data-ttu-id="a57b5-117">主機應用程式可以定義命令執行所在的執行時間、在本機或遠端電腦上開啟會話，以及根據應用程式的需求，以同步或非同步方式叫用命令。</span><span class="sxs-lookup"><span data-stu-id="a57b5-117">The host application can, define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

- <span data-ttu-id="a57b5-118">[撰寫 PowerShell 格式設定檔](./format/writing-a-powershell-formatting-file.md) 案提供編寫格式化檔案的相關資訊，這些檔案可控制命令所傳回之物件的顯示格式 (Cmdlet、函式和腳本) 。</span><span class="sxs-lookup"><span data-stu-id="a57b5-118">[Writing a PowerShell Formatting File](./format/writing-a-powershell-formatting-file.md) Provides information for the authoring of formatting files, which control the display format for the objects that are returned by commands (cmdlets, functions, and scripts).</span></span>

- <span data-ttu-id="a57b5-119">[Windows PowerShell 參考](./windows-powershell-reference.md) 提供用於撰寫 Cmdlet、提供者和主機應用程式之 Api 的參考內容，以及其他支援的 Api。</span><span class="sxs-lookup"><span data-stu-id="a57b5-119">[Windows PowerShell Reference](./windows-powershell-reference.md) Provides reference content for the APIs used in writing cmdlets, providers, and host applications, as well as other supporting APIs.</span></span>
