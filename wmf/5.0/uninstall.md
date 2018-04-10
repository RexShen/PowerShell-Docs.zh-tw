---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 78ae7ecd40b4d8ad0a6750f43002986483ab18a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="0486f-102">解除安裝指示</span><span class="sxs-lookup"><span data-stu-id="0486f-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="0486f-103">使用 [命令提示字元]</span><span class="sxs-lookup"><span data-stu-id="0486f-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="0486f-104">開啟 **[命令提示字元]**。</span><span class="sxs-lookup"><span data-stu-id="0486f-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="0486f-105">執行 [Windows Update 獨立啟動器](https://support.microsoft.com/en-us/kb/934307)，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="0486f-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="0486f-106">在 Windows Server 2012 R2 和 Windows 8.1 上：</span><span class="sxs-lookup"><span data-stu-id="0486f-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="0486f-107">在 Windows Server 2012 上：</span><span class="sxs-lookup"><span data-stu-id="0486f-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="0486f-108">在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上：</span><span class="sxs-lookup"><span data-stu-id="0486f-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="0486f-109">使用 [控制台]</span><span class="sxs-lookup"><span data-stu-id="0486f-109">Using Control Panel</span></span>
1.  <span data-ttu-id="0486f-110">開啟 **[控制台]**。</span><span class="sxs-lookup"><span data-stu-id="0486f-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="0486f-111">開啟 **[程式集]**，然後開啟 **[解除安裝程式]**。</span><span class="sxs-lookup"><span data-stu-id="0486f-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="0486f-112">按一下 **[檢視安裝的更新]**。</span><span class="sxs-lookup"><span data-stu-id="0486f-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="0486f-113">從已安裝的更新清單中選取 **[Windows Management Framework 5.0]**。</span><span class="sxs-lookup"><span data-stu-id="0486f-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="0486f-114">這會對應到 *KB3134758*、*KB3134759* 或 *KB3134760*。</span><span class="sxs-lookup"><span data-stu-id="0486f-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="0486f-115">按一下 **[解除安裝]**。</span><span class="sxs-lookup"><span data-stu-id="0486f-115">Click **Uninstall.**</span></span>