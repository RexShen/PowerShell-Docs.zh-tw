---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用 Windows PowerShell 撰寫指令碼"
ms.assetid: c425d27a-bb41-4947-8d73-ba5480bc8ee0
ms.openlocfilehash: ac276938c71fa1627a2c9d3346269b89950184d9
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="scripting-with-windows-powershell"></a><span data-ttu-id="94193-103">使用 Windows PowerShell 撰寫指令碼</span><span class="sxs-lookup"><span data-stu-id="94193-103">Scripting with Windows PowerShell</span></span>

<span data-ttu-id="94193-104">Windows PowerShell® 是以工作為基礎的命令列殼層和指令碼語言，專為系統管理所設計。</span><span class="sxs-lookup"><span data-stu-id="94193-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="94193-105">Windows PowerShell 是以 .NET Framework 為基礎所建置，可協助 IT 專業人員與進階使用者控制和自動化管理 Windows 作業系統與在 Windows 上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="94193-105">Built on the .NET Framework, Windows PowerShell helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="94193-106">Windows PowerShell 命令 (稱為 *Cmdlet*) 可讓您從命令列管理電腦。</span><span class="sxs-lookup"><span data-stu-id="94193-106">Windows PowerShell commands, called *cmdlets*, let you manage the computers from the command line.</span></span> <span data-ttu-id="94193-107">Windows PowerShell *提供者* 可讓您如同存取檔案系統般輕易地存取資料存放區 (如登錄和憑證存放區)。</span><span class="sxs-lookup"><span data-stu-id="94193-107">Windows PowerShell *providers* let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="94193-108">此外，Windows PowerShell 擁有豐富的運算式剖析器以及完整開發的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="94193-108">In addition, Windows PowerShell has a rich expression parser and a fully developed scripting language.</span></span>

<span data-ttu-id="94193-109">Windows PowerShell 包含下列功能：</span><span class="sxs-lookup"><span data-stu-id="94193-109">Windows PowerShell includes the following features:</span></span>

-   <span data-ttu-id="94193-110">用來執行一般系統管理工作 (例如管理登錄、服務、處理程序與事件記錄檔) 以及使用 Windows Management Instrumentation (WMI) 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="94193-110">Cmdlets for performing common system administration tasks, such as managing the registry, services, processes, and event logs, and using Windows Management Instrumentation (WMI).</span></span>
-   <span data-ttu-id="94193-111">適用於現有指令碼和命令列工具的工作型指令碼語言與支援。</span><span class="sxs-lookup"><span data-stu-id="94193-111">A task-based scripting language and support for existing scripts and command-line tools.</span></span>
-   <span data-ttu-id="94193-112">一致的設計。</span><span class="sxs-lookup"><span data-stu-id="94193-112">Consistent design.</span></span> <span data-ttu-id="94193-113">因為 Cmdlet 和系統資料存放區使用通用語法和命名慣例，資料可以輕易地共用，且一個 Cmdlet 的輸出可以做為另一個 Cmdlet 的輸入，而不需要重新格式化或操作。</span><span class="sxs-lookup"><span data-stu-id="94193-113">Because cmdlets and system data stores use common syntax and naming conventions, data can be shared easily and the output from one cmdlet can be used as the input to another cmdlet without reformatting or manipulation.</span></span>
-   <span data-ttu-id="94193-114">作業系統的簡化命令型瀏覽，可讓使用者使用瀏覽檔案系統的相同技巧，瀏覽登錄與其他資料存放區。</span><span class="sxs-lookup"><span data-stu-id="94193-114">Simplified, command-based navigation of the operating system, which lets users navigate the registry and other data stores by using the same techniques that they use to navigate the file system.</span></span>
-   <span data-ttu-id="94193-115">強大的物件操作功能。</span><span class="sxs-lookup"><span data-stu-id="94193-115">Powerful object manipulation capabilities.</span></span> <span data-ttu-id="94193-116">物件可以直接操作或傳送到其他工具或資料庫。</span><span class="sxs-lookup"><span data-stu-id="94193-116">Objects can be directly manipulated or sent to other tools or databases.</span></span>
-   <span data-ttu-id="94193-117">可延伸介面。</span><span class="sxs-lookup"><span data-stu-id="94193-117">Extensible interface.</span></span> <span data-ttu-id="94193-118">獨立軟體廠商和企業開發人員可以建置自訂工具和公用程式來管理其軟體。</span><span class="sxs-lookup"><span data-stu-id="94193-118">Independent software vendors and enterprise developers can build custom tools and utilities to administer their software.</span></span>

