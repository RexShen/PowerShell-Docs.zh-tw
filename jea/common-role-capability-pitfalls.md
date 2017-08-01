---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "常見的角色功能問題"
ms.technology: powershell
ms.openlocfilehash: 8e928ec07ef98b2ec8186a27d3aefa1450a3a424
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
### <a name="common-role-capability-pitfalls"></a><span data-ttu-id="d0946-103">常見的角色功能問題</span><span class="sxs-lookup"><span data-stu-id="d0946-103">Common Role Capability Pitfalls</span></span>
<span data-ttu-id="d0946-104">當您執行這項程序時，可能會發生一些常見的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d0946-104">You may run into a few common pitfalls if you go through this process yourself.</span></span>
<span data-ttu-id="d0946-105">下列快速指南說明如何在修改及建立新端點時，找出並修正這些問題︰</span><span class="sxs-lookup"><span data-stu-id="d0946-105">Here is a quick guide explaining how to identify and remediate these issues when modifying or creating a new endpoint:</span></span>

#### <a name="functions-vs-cmdlets"></a><span data-ttu-id="d0946-106">函式與Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d0946-106">Functions vs. Cmdlets</span></span>
<span data-ttu-id="d0946-107">使用 PowerShell 撰寫的 PowerShell 命令稱為 PowerShell 函式。</span><span class="sxs-lookup"><span data-stu-id="d0946-107">PowerShell commands written in PowerShell are PowerShell functions.</span></span>
<span data-ttu-id="d0946-108">撰寫成特定 .NET 類別的 PowerShell 命令稱為 PowerShell Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d0946-108">PowerShell commands written as specialized .NET classes are PowerShell cmdlets.</span></span>
<span data-ttu-id="d0946-109">您可以執行 `Get-Command` 來查看命令類型。</span><span class="sxs-lookup"><span data-stu-id="d0946-109">You can check the command type by running `Get-Command`.</span></span>

#### <a name="visibleproviders"></a><span data-ttu-id="d0946-110">VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="d0946-110">VisibleProviders</span></span>
<span data-ttu-id="d0946-111">您必須公開命令所需的任何提供者。</span><span class="sxs-lookup"><span data-stu-id="d0946-111">You will need to expose any providers your commands need.</span></span>
<span data-ttu-id="d0946-112">最常見的是檔案系統提供者，但您可能也需要公開其他提供者，像是登錄提供者。</span><span class="sxs-lookup"><span data-stu-id="d0946-112">The most common is the FileSystem provider, but you may also need to expose others, like the Registry provider.</span></span>
<span data-ttu-id="d0946-113">如需提供者簡介，請參閱這篇 [Hey, Scripting Guy 部落格文章](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d0946-113">For an introduction to providers, check out this [Hey, Scripting Guy blog post](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span></span>
<span data-ttu-id="d0946-114">公開提供者時請小心，通常最好是定義自己的函式來搭配基礎提供者使用，而不是直接公開 JEA 工作階段中的提供者。</span><span class="sxs-lookup"><span data-stu-id="d0946-114">Be careful when exposing providers -- often, it is better to define your own function that works with the underlying providers than to directly expose the provider in a JEA session.</span></span>
<span data-ttu-id="d0946-115">如此一來，您仍然可以允許使用者使用檔案、登錄機碼等，但會保留使用者可以使用自訂驗證邏輯處理**哪些**檔案和登錄機碼的控制權。</span><span class="sxs-lookup"><span data-stu-id="d0946-115">This way, you can still allow users to work with files, registry keys, etc. but retain control over **which** files and registry keys they can work with using custom validation logic.</span></span>

