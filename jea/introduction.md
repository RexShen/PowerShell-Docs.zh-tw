---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "簡介"
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="introduction"></a><span data-ttu-id="2594a-103">簡介</span><span class="sxs-lookup"><span data-stu-id="2594a-103">Introduction</span></span>

##  <a name="motivation"></a><span data-ttu-id="2594a-104">**動機**</span><span class="sxs-lookup"><span data-stu-id="2594a-104">**Motivation**</span></span>  
<span data-ttu-id="2594a-105">當您將系統的特殊權限存取授與某人時，就是將您的信任界限延伸到該人員。</span><span class="sxs-lookup"><span data-stu-id="2594a-105">When you grant someone privileged access to your systems, you extend your trust boundary to that person.</span></span>
<span data-ttu-id="2594a-106">這會帶來風險，因為系統管理員是受攻擊面。</span><span class="sxs-lookup"><span data-stu-id="2594a-106">This is a risk -- administrators are an attack surface.</span></span>
<span data-ttu-id="2594a-107">內部攻擊和認證遭竊是常見的真實情況。</span><span class="sxs-lookup"><span data-stu-id="2594a-107">Insider attacks and stolen credentials are both real and common.</span></span>

##  <a name="not-a-new-problem"></a><span data-ttu-id="2594a-108">**不是新問題**</span><span class="sxs-lookup"><span data-stu-id="2594a-108">**Not a new problem**</span></span>  
<span data-ttu-id="2594a-109">您可能很熟悉最低權限原則，並可能透過應用程式使用其提供的某種角色型存取控制 (RBAC)。</span><span class="sxs-lookup"><span data-stu-id="2594a-109">You are probably very familiar with the principle of least privilege, and you might use some form of role-based access control (RBAC) with applications that provide it.</span></span>
<span data-ttu-id="2594a-110">不過，這些解決方案的效率和管理能力通常因其廣泛的範圍和不精確而受到限制。</span><span class="sxs-lookup"><span data-stu-id="2594a-110">However, the effectiveness and manageability of these solutions are often limited by their broad scope and imprecision.</span></span>
<span data-ttu-id="2594a-111">此外，RBAC 涵蓋範圍也有間隙。</span><span class="sxs-lookup"><span data-stu-id="2594a-111">Furthermore, there are gaps in RBAC coverage.</span></span>
<span data-ttu-id="2594a-112">例如，在 Windows 中，特殊權限存取主要是二元切換參數，迫使您在將使用者加入 Administrators 群組時，授與不必要的權限。</span><span class="sxs-lookup"><span data-stu-id="2594a-112">For example, in Windows, privileged access is largely a binary switch, forcing you to give unnecessary permissions when adding users to the Administrators group.</span></span>

##  <a name="just-enough-administration-jea"></a><span data-ttu-id="2594a-113">**Just Enough Administration (JEA)**</span><span class="sxs-lookup"><span data-stu-id="2594a-113">**Just Enough Administration (JEA)**</span></span> 
<span data-ttu-id="2594a-114">透過 PowerShell 遠端提供角色型存取控制 (RBAC) 平台。</span><span class="sxs-lookup"><span data-stu-id="2594a-114">Provides a role-based access control (RBAC) platform through PowerShell Remoting.</span></span>
<span data-ttu-id="2594a-115">它可讓特定使用者在伺服器上執行特定管理工作，而不需要授與系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="2594a-115">*It allows specific users to perform specific administrative tasks on servers without giving them administrator rights.*</span></span>
<span data-ttu-id="2594a-116">這可讓您填滿現有 RBAC 解決方案的間隙，並簡化這些設定的管理工作。</span><span class="sxs-lookup"><span data-stu-id="2594a-116">This allows you to fill in the gaps between your existing RBAC solutions, and simplifies management of those settings.</span></span>

