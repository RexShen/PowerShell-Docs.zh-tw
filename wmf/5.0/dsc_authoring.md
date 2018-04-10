---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 3b2c268cd10d7c421b3d1fc73a7bbeaa4714f5fc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="f4904-102">使用 PowerShell ISE 撰寫增強功能</span><span class="sxs-lookup"><span data-stu-id="f4904-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="f4904-103">以 Windows PowerShell ISE 撰寫 DSC 設定更容易，這都多虧了下列的增強功能︰</span><span class="sxs-lookup"><span data-stu-id="f4904-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="f4904-104">在區塊的空白行輸入 **Ctrl+空格鍵**，列出**設定**區塊或**節點**區塊中的所有 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="f4904-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="f4904-105">**列舉**類型資源屬性的自動完成功能。</span><span class="sxs-lookup"><span data-stu-id="f4904-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="f4904-106">DSC 資源 **DependsOn** 屬性的自動完成功能，以設定的其他資源執行個體為基礎。</span><span class="sxs-lookup"><span data-stu-id="f4904-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="f4904-107">更好的資源屬性值 TAB 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="f4904-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="f4904-108">**注意︰**資源屬性值必須先為空字串，您才能使用 Ctrl+空格鍵列出選項。</span><span class="sxs-lookup"><span data-stu-id="f4904-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="f4904-109">按 **Tab** 鍵可循環選擇選項。</span><span class="sxs-lookup"><span data-stu-id="f4904-109">Pressing **Tab** cycles through options.</span></span>