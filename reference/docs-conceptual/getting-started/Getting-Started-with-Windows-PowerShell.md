---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "開始使用 Windows PowerShell"
ms.assetid: b0e2ad92-875f-421d-b612-f624e644aa69
ms.openlocfilehash: 93a4d4a6bc0ebef6b6af7f7f8af59dec865bcfa3
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2017
---
# <a name="getting-started-with-windows-powershell"></a><span data-ttu-id="bc64f-103">開始使用 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc64f-103">Getting Started with Windows PowerShell</span></span>
<span data-ttu-id="bc64f-104">Windows PowerShell 是專為系統管理員所設計的 Windows 命令列殼層。</span><span class="sxs-lookup"><span data-stu-id="bc64f-104">Windows PowerShell is a Windows command-line shell designed especially for system administrators.</span></span> <span data-ttu-id="bc64f-105">Windows PowerShell 包含互動式提示和指令碼環境，可獨立使用或搭配使用。</span><span class="sxs-lookup"><span data-stu-id="bc64f-105">Windows PowerShell includes an interactive prompt and a scripting environment that can be used independently or in combination.</span></span>

<span data-ttu-id="bc64f-106">不同於大部分殼層會接受並傳回文字，Windows PowerShell 是以 .NET Framework Common Language Runtime (CLR) 和 .NET Framework 為建置基礎，因此會接受並傳回 .NET Framework 物件。</span><span class="sxs-lookup"><span data-stu-id="bc64f-106">Unlike most shells, which accept and return text, Windows PowerShell is built on top of the .NET Framework common language runtime (CLR) and the .NET Framework, and accepts and returns .NET Framework objects.</span></span> <span data-ttu-id="bc64f-107">環境的這項基本變更，為 Windows 的管理和設定帶來全新的工具和方法。</span><span class="sxs-lookup"><span data-stu-id="bc64f-107">This fundamental change in the environment brings entirely new tools and methods to the management and configuration of Windows.</span></span>

<span data-ttu-id="bc64f-108">Windows PowerShell 引進 Cmdlet (唸成 "command-let") 概念，這是內建於殼層的簡單、單一函式命令列工具。</span><span class="sxs-lookup"><span data-stu-id="bc64f-108">Windows PowerShell introduces the concept of a cmdlet (pronounced "command-let"), a simple, single-function command-line tool built into the shell.</span></span> <span data-ttu-id="bc64f-109">您可以個別使用每個 Cmdlet，但搭配使用這些簡單的工具來執行複雜的工作時，才能實現其功能。</span><span class="sxs-lookup"><span data-stu-id="bc64f-109">You can use each cmdlet separately, but their power is realized when you use these simple tools in combination to perform complex tasks.</span></span> <span data-ttu-id="bc64f-110">Windows PowerShell 包含一百個以上的基本核心 Cmdlet，而且您可以撰寫自己的 Cmdlet 並與其他使用者分享。</span><span class="sxs-lookup"><span data-stu-id="bc64f-110">Windows PowerShell includes more than one hundred basic core cmdlets, and you can write your own cmdlets and share them with other users.</span></span>

<span data-ttu-id="bc64f-111">如同許多殼層，Windows PowerShell 可讓您存取電腦上的檔案系統。</span><span class="sxs-lookup"><span data-stu-id="bc64f-111">Like many shells, Windows PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="bc64f-112">此外，Windows PowerShell*提供者*可讓您如同存取檔案系統般輕易地存取其他資料存放區 (如登錄和數位簽章憑證存放區)。</span><span class="sxs-lookup"><span data-stu-id="bc64f-112">In addition, Windows PowerShell *providers* enable you to access other data stores, such as the registry and the digital signature certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="bc64f-113">本入門指南提供 Windows PowerShell 簡介︰語言、Cmdlet、提供者及物件的使用。</span><span class="sxs-lookup"><span data-stu-id="bc64f-113">This Getting Started guide provides an introduction to Windows PowerShell: the language, the cmdlets, the providers, and the use of objects.</span></span>

<span data-ttu-id="bc64f-114">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="bc64f-114">In this topic:</span></span>

- [<span data-ttu-id="bc64f-115">Windows PowerShell 系統需求</span><span class="sxs-lookup"><span data-stu-id="bc64f-115">Windows PowerShell System Requirements</span></span>](../setup/Windows-PowerShell-System-Requirements.md)

- [<span data-ttu-id="bc64f-116">安裝 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc64f-116">Installing Windows PowerShell</span></span>](../setup/Installing-Windows-PowerShell.md)

- [<span data-ttu-id="bc64f-117">啟動 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc64f-117">Starting Windows PowerShell</span></span>](../setup/Starting-Windows-PowerShell.md)

- [<span data-ttu-id="bc64f-118">準備好使用 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc64f-118">Getting Ready to Use Windows PowerShell</span></span>](Getting-Ready-to-Use-Windows-PowerShell.md)

