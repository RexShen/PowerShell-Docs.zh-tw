---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "列入封鎖清單"
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
### <a name="on-blacklisting"></a><span data-ttu-id="e95ef-103">列入封鎖清單</span><span class="sxs-lookup"><span data-stu-id="e95ef-103">On Blacklisting</span></span>
<span data-ttu-id="e95ef-104">試用 JEA 之後，您可能想知道它是否可以將命令列入封鎖清單。</span><span class="sxs-lookup"><span data-stu-id="e95ef-104">After playing around with JEA, you may be wondering if it is possible to blacklist commands.</span></span>
<span data-ttu-id="e95ef-105">這是合理的要求，但目前不在 JEA 的規劃中，原因如下︰</span><span class="sxs-lookup"><span data-stu-id="e95ef-105">This is an understandable request, but it is not currently planned for JEA for the following reasons:</span></span>

1.  <span data-ttu-id="e95ef-106">我們已將 JEA 設計為限制操作員只執行他們所需的動作。</span><span class="sxs-lookup"><span data-stu-id="e95ef-106">We designed JEA to limit operators to only the actions they need to do.</span></span>
<span data-ttu-id="e95ef-107">封鎖清單則相反。</span><span class="sxs-lookup"><span data-stu-id="e95ef-107">A blacklist is the opposite.</span></span>

2.  <span data-ttu-id="e95ef-108">PowerShell 命令作者在設計 PowerShell 命令時並未考慮到 JEA。</span><span class="sxs-lookup"><span data-stu-id="e95ef-108">PowerShell command authors did not design PowerShell commands with the JEA in mind.</span></span>
<span data-ttu-id="e95ef-109">在 Windows Server 2016 的全新安裝上，可立即使用的命令約有 1520 個。</span><span class="sxs-lookup"><span data-stu-id="e95ef-109">On a fresh install of Windows Server 2016, there are about 1520 commands immediately available.</span></span>
<span data-ttu-id="e95ef-110">這些命令的威脅模式並未納入使用者以提升權限的帳戶身分執行命令的可能性。</span><span class="sxs-lookup"><span data-stu-id="e95ef-110">The threat models for these commands did not include the possibility that a user would be running commands as a more privileged account.</span></span>
<span data-ttu-id="e95ef-111">例如，特定命令可依設計插入程式碼 (例如核心 PowerShell 模組中的 Add-Type 和 Invoke-Command)。</span><span class="sxs-lookup"><span data-stu-id="e95ef-111">For example, certain commands allow for code injection by design (e.g. Add-Type and Invoke-Command in the core PowerShell module).</span></span>
<span data-ttu-id="e95ef-112">當您公開我們已知的特定命令時，JEA 可能會警告您，但我們尚未根據新的威脅模式重新評估 Windows 中的所有其他命令。</span><span class="sxs-lookup"><span data-stu-id="e95ef-112">JEA can warn you when you expose the specific commands we know about, but we have not re-assessed every other command in Windows based on the new threat model.</span></span>
<span data-ttu-id="e95ef-113">您必須了解透過 JEA 公開之命令的功能。</span><span class="sxs-lookup"><span data-stu-id="e95ef-113">You must understand the capabilities of the commands you exposing through JEA.</span></span>  

3.  <span data-ttu-id="e95ef-114">此外，即使 JEA 封鎖了具有程式碼插入弱點的所有命令，也無法保證惡意使用者不會使用其他相關命令來執行列入封鎖清單的動作。</span><span class="sxs-lookup"><span data-stu-id="e95ef-114">Furthermore, even if JEA blocked all commands with code-injection vulnerabilities, there is no guarantee that a malicious user would not be able to carry out a blacklisted action with another related command.</span></span>
<span data-ttu-id="e95ef-115">除非您了解要公開的所有命令，否則您無法保證不會發生特定動作。</span><span class="sxs-lookup"><span data-stu-id="e95ef-115">Unless you understand all of the commands that you are exposing, it is impossible for you to guarantee that a certain action is not possible.</span></span>
<span data-ttu-id="e95ef-116">不論使用允許清單或封鎖清單，您都有責任了解要公開哪些命令。</span><span class="sxs-lookup"><span data-stu-id="e95ef-116">The burden is on you to understand what commands you are exposing, whether they are using a whitelist or a blacklist.</span></span>
<span data-ttu-id="e95ef-117">您無法管理封鎖清單會公開的命令數目，因此 JEA 會改用允許清單實作。</span><span class="sxs-lookup"><span data-stu-id="e95ef-117">The number of commands a blacklist would expose is unmanageable, so JEA is implemented using whitelists instead.</span></span>

