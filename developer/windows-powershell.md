---
title: Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 7627ab336ddc40ab47c3017eed77c78bbdac4e7f
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470819"
---
# <a name="windows-powershell"></a><span data-ttu-id="3da4b-102">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3da4b-102">Windows PowerShell</span></span>

<span data-ttu-id="3da4b-103">更新日期：2013 年 7 月 8日日</span><span class="sxs-lookup"><span data-stu-id="3da4b-103">Updated: July 8, 2013</span></span>

<span data-ttu-id="3da4b-104">Windows PowerShell® 是以工作為基礎的命令列殼層和指令碼語言，專為系統管理所設計。</span><span class="sxs-lookup"><span data-stu-id="3da4b-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="3da4b-105">Windows PowerShell® 建基於.NET Framework，可協助 IT 專業人員與進階使用者控制和自動化 Windows 作業系統與在 Windows 執行的應用程式管理。</span><span class="sxs-lookup"><span data-stu-id="3da4b-105">Built on the .NET Framework, Windows PowerShell® helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="3da4b-106">發佈文件會寫入主要適用於 cmdlet、 提供者，與主機應用程式開發人員需要 Windows PowerShell 所提供的 Api 的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="3da4b-106">The documents published here are written primarily for cmdlet, provider, and host application developers who require reference information about the APIs provided by Windows PowerShell.</span></span>
<span data-ttu-id="3da4b-107">不過，系統管理員也可能會發現這些實用的文件所提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="3da4b-107">However, system administrators might also find the information provided by these documents useful.</span></span>

<span data-ttu-id="3da4b-108">若要開始使用 Windows PowerShell 所需的基本資訊，請參閱 Getting Started with Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3da4b-108">For the basic information needed to start using Windows PowerShell, see Getting Started with Windows PowerShell .</span></span>

## <a name="windows-powershell-documents-on-msdn"></a><span data-ttu-id="3da4b-109">MSDN 上的 Windows PowerShell 文件</span><span class="sxs-lookup"><span data-stu-id="3da4b-109">Windows PowerShell Documents on MSDN</span></span>

- <span data-ttu-id="3da4b-110">[安裝 Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md)提供如何安裝 Windows PowerShell SDK 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3da4b-110">[Installing the Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md) Provides information about how to install the Windows PowerShell SDK.</span></span>

- <span data-ttu-id="3da4b-111">[撰寫 Windows PowerShell 模組](./module/writing-a-windows-powershell-module.md)提供給系統管理員、 指令碼的開發人員，cmdlet 開發人員必須封裝並散發其 Windows PowerShell 解決方案的資訊。</span><span class="sxs-lookup"><span data-stu-id="3da4b-111">[Writing a Windows PowerShell Module](./module/writing-a-windows-powershell-module.md) Provides information for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell solutions.</span></span>

- <span data-ttu-id="3da4b-112">[撰寫 Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md)提供設計和實作指令程式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3da4b-112">[Writing a Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Provides information for designing and implementing cmdlets.</span></span>

- <span data-ttu-id="3da4b-113">[撰寫 Windows PowerShell 提供者](./provider/writing-a-windows-powershell-provider.md)提供設計和實作 Windows PowerShell 提供者相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3da4b-113">[Writing a Windows PowerShell Provider](./provider/writing-a-windows-powershell-provider.md) Provides information for designing and implementing Windows PowerShell providers.</span></span> <span data-ttu-id="3da4b-114">它會協助您了解 Windows PowerShell 提供者的運作方式，並提供範例程式碼，可用來啟動設計或撰寫您自己的提供者。</span><span class="sxs-lookup"><span data-stu-id="3da4b-114">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

- <span data-ttu-id="3da4b-115">[撰寫 Windows PowerShell 主應用程式](./hosting/writing-a-windows-powershell-host-application.md)提供可用在設計主應用程式的程式管理員和開發人員實作它們的資訊。</span><span class="sxs-lookup"><span data-stu-id="3da4b-115">[Writing a Windows PowerShell Host Application](./hosting/writing-a-windows-powershell-host-application.md) Provides information that can be used by program managers who are designing host applications and by developers who are implementing them.</span></span> <span data-ttu-id="3da4b-116">主應用程式可以定義命令所在的本機或遠端電腦上，執行，請開啟工作階段的 runspace，叫用同步或非同步地根據需求的應用程式的命令。</span><span class="sxs-lookup"><span data-stu-id="3da4b-116">The host application can, define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

- <span data-ttu-id="3da4b-117">[撰寫 PowerShell 格式化檔案](./format/writing-a-powershell-formatting-file.md)提供為控制命令 （cmdlet、 函數和指令碼） 所傳回的物件的顯示格式的格式化檔案撰寫的資訊。</span><span class="sxs-lookup"><span data-stu-id="3da4b-117">[Writing a PowerShell Formatting File](./format/writing-a-powershell-formatting-file.md) Provides information for the authoring of formatting files, which control the display format for the objects that are returned by commands (cmdlets, functions, and scripts).</span></span>

- <span data-ttu-id="3da4b-118">[Windows PowerShell 參考](./windows-powershell-reference.md)提供撰寫 cmdlet、 提供者，以及裝載應用程式，使用的 Api，以及其他支援的 Api 的參考內容。</span><span class="sxs-lookup"><span data-stu-id="3da4b-118">[Windows PowerShell Reference](./windows-powershell-reference.md) Provides reference content for the APIs used in writing cmdlets, providers, and host applications, as well as other supporting APIs.</span></span>
