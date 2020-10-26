---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 必要條件
description: 本文描述必須滿足才能開始使用 JEA 的必要條件。
ms.openlocfilehash: 5cc70a06887a2d0a840cc83117f865d3148056e1
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501723"
---
# <a name="prerequisites"></a><span data-ttu-id="dfaef-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="dfaef-104">Prerequisites</span></span>

<span data-ttu-id="dfaef-105">Just Enough Administration 是 PowerShell 5.0 和更高版本隨附的功能。</span><span class="sxs-lookup"><span data-stu-id="dfaef-105">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="dfaef-106">本文描述必須滿足才能開始使用 JEA 的必要條件。</span><span class="sxs-lookup"><span data-stu-id="dfaef-106">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>

## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="dfaef-107">檢查已安裝哪個版本的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfaef-107">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="dfaef-108">若要檢查哪個版本的 PowerShell 安裝在您的系統上，請在 Windows PowerShell 提示字元中檢查 `$PSVersionTable` 變數。</span><span class="sxs-lookup"><span data-stu-id="dfaef-108">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="dfaef-109">JEA 適用於 PowerShell 5.0 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="dfaef-109">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="dfaef-110">如需完整的功能，建議您為系統安裝最新版的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dfaef-110">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="dfaef-111">下表說明 JEA 在 Windows Server 上的可用性：</span><span class="sxs-lookup"><span data-stu-id="dfaef-111">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="dfaef-112">伺服器作業系統</span><span class="sxs-lookup"><span data-stu-id="dfaef-112">Server Operating System</span></span> |                <span data-ttu-id="dfaef-113">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="dfaef-113">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="dfaef-114">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="dfaef-114">Windows Server 2016+</span></span>    | <span data-ttu-id="dfaef-115">預先安裝</span><span class="sxs-lookup"><span data-stu-id="dfaef-115">Preinstalled</span></span>                                   |
| <span data-ttu-id="dfaef-116">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="dfaef-116">Windows Server 2012 R2</span></span>  | <span data-ttu-id="dfaef-117">具完整功能性的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="dfaef-117">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="dfaef-118">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="dfaef-118">Windows Server 2012</span></span>     | <span data-ttu-id="dfaef-119">具完整功能性的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="dfaef-119">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="dfaef-120">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="dfaef-120">Windows Server 2008 R2</span></span>  | <span data-ttu-id="dfaef-121">功能有限 <sup>1</sup> 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="dfaef-121">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="dfaef-122">您也可以在家用或工作電腦上使用 JEA：</span><span class="sxs-lookup"><span data-stu-id="dfaef-122">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="dfaef-123">用戶端作業系統</span><span class="sxs-lookup"><span data-stu-id="dfaef-123">Client Operating System</span></span> |                   <span data-ttu-id="dfaef-124">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="dfaef-124">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="dfaef-125">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="dfaef-125">Windows 10 1607+</span></span>        | <span data-ttu-id="dfaef-126">預先安裝</span><span class="sxs-lookup"><span data-stu-id="dfaef-126">Preinstalled</span></span>                                         |
| <span data-ttu-id="dfaef-127">Windows 10 1603、1511</span><span class="sxs-lookup"><span data-stu-id="dfaef-127">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="dfaef-128">預先安裝，功能有限<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="dfaef-128">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="dfaef-129">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="dfaef-129">Windows 10 1507</span></span>         | <span data-ttu-id="dfaef-130">無法使用</span><span class="sxs-lookup"><span data-stu-id="dfaef-130">Not available</span></span>                                        |
| <span data-ttu-id="dfaef-131">Windows 8、8.1</span><span class="sxs-lookup"><span data-stu-id="dfaef-131">Windows 8, 8.1</span></span>          | <span data-ttu-id="dfaef-132">具完整功能性的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="dfaef-132">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="dfaef-133">Windows 7</span><span class="sxs-lookup"><span data-stu-id="dfaef-133">Windows 7</span></span>               | <span data-ttu-id="dfaef-134">功能有限 <sup>1</sup> 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="dfaef-134">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="dfaef-135"><sup>1</sup> 在 Windows Server 2008 R2 或 Windows 7 上無法設定 JEA 使用群組受控服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="dfaef-135"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="dfaef-136">*支援* 虛擬帳戶和其他 JEA 功能。</span><span class="sxs-lookup"><span data-stu-id="dfaef-136">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="dfaef-137"><sup>2</sup> Windows 10 1511 版和 1603 版不支援下列 JEA 功能：</span><span class="sxs-lookup"><span data-stu-id="dfaef-137"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="dfaef-138">以群組受控服務帳戶執行</span><span class="sxs-lookup"><span data-stu-id="dfaef-138">Running as a group-managed service account</span></span>
  - <span data-ttu-id="dfaef-139">工作階段設定中的條件式存取規則</span><span class="sxs-lookup"><span data-stu-id="dfaef-139">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="dfaef-140">使用者磁碟機</span><span class="sxs-lookup"><span data-stu-id="dfaef-140">The user drive</span></span>
  - <span data-ttu-id="dfaef-141">將存取權授與本機使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="dfaef-141">Granting access to local user accounts</span></span>

  <span data-ttu-id="dfaef-142">若要取得這些功能的支援，請將 Windows 更新為 1607 版 (年度更新版) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="dfaef-142">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="dfaef-143">安裝 Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="dfaef-143">Install Windows Management Framework</span></span>

<span data-ttu-id="dfaef-144">如果您執行較舊版本的 PowerShell，則可能需要使用最新的 Windows Management Framework (WMF) 更新來更新系統。</span><span class="sxs-lookup"><span data-stu-id="dfaef-144">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="dfaef-145">如需詳細資訊，請參閱 [WMF](/powershell/scripting/wmf/overview) 文件。</span><span class="sxs-lookup"><span data-stu-id="dfaef-145">For more information, see the [WMF documentation](/powershell/scripting/wmf/overview).</span></span>

<span data-ttu-id="dfaef-146">建議您先測試工作負載的 WMF 相容性，再升級所有的伺服器。</span><span class="sxs-lookup"><span data-stu-id="dfaef-146">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="dfaef-147">Windows 10 使用者應安裝最新的功能更新，以取得目前版本的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="dfaef-147">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="dfaef-148">啟用 PowerShell 遠端</span><span class="sxs-lookup"><span data-stu-id="dfaef-148">Enable PowerShell Remoting</span></span>

<span data-ttu-id="dfaef-149">PowerShell 遠端提供 JEA 建置的基礎。</span><span class="sxs-lookup"><span data-stu-id="dfaef-149">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="dfaef-150">必須先確保已啟用 PowerShell 遠端並經過適當保護，才能使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="dfaef-150">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="dfaef-151">如需詳細資訊，請參閱 [WinRM 安全性](/powershell/scripting/learn/remoting/winrmsecurity)。</span><span class="sxs-lookup"><span data-stu-id="dfaef-151">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="dfaef-152">Windows Server 2012、2012 R2 和 2016 中預設已啟用 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="dfaef-152">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="dfaef-153">您可以在提升權限的 PowerShell 視窗中執行下列命令，來啟用 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="dfaef-153">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="dfaef-154">啟用 PowerShell 模組和指令碼區塊記錄 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="dfaef-154">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="dfaef-155">下列步驟可啟用系統上所有 PowerShell 動作的記錄。</span><span class="sxs-lookup"><span data-stu-id="dfaef-155">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="dfaef-156">JEA 不需要 PowerShell 模組記錄，不過建議您開啟記錄，以確保使用者執行的命令會記錄在中央位置。</span><span class="sxs-lookup"><span data-stu-id="dfaef-156">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="dfaef-157">您可以使用群組原則設定 PowerShell 模組記錄原則。</span><span class="sxs-lookup"><span data-stu-id="dfaef-157">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="dfaef-158">在工作站上開啟本機群組原則編輯器，或在 Active Directory 網域控制站上的群組原則管理主控台上開啟群組原則物件</span><span class="sxs-lookup"><span data-stu-id="dfaef-158">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="dfaef-159">瀏覽至 [電腦設定]\\[系統管理範本]\\[Windows 元件]\\[Windows PowerShell]</span><span class="sxs-lookup"><span data-stu-id="dfaef-159">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="dfaef-160">按兩下 [開啟模組記錄] </span><span class="sxs-lookup"><span data-stu-id="dfaef-160">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="dfaef-161">按一下 [啟用]</span><span class="sxs-lookup"><span data-stu-id="dfaef-161">Click **Enabled**</span></span>
5. <span data-ttu-id="dfaef-162">在 [選項] 區段中，按一下模組名稱旁邊的 [顯示]</span><span class="sxs-lookup"><span data-stu-id="dfaef-162">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="dfaef-163">在快顯視窗中鍵入 `*`，記錄來自所有模組的命令。</span><span class="sxs-lookup"><span data-stu-id="dfaef-163">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="dfaef-164">按一下 [確定] 設定原則</span><span class="sxs-lookup"><span data-stu-id="dfaef-164">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="dfaef-165">按兩下 [開啟 PowerShell 指令碼區塊記錄] </span><span class="sxs-lookup"><span data-stu-id="dfaef-165">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="dfaef-166">按一下 [啟用]</span><span class="sxs-lookup"><span data-stu-id="dfaef-166">Click **Enabled**</span></span>
10. <span data-ttu-id="dfaef-167">按一下 [確定] 設定原則</span><span class="sxs-lookup"><span data-stu-id="dfaef-167">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="dfaef-168">(僅限已加入網域的電腦) 執行 `gpupdate` 或等待群組原則處理已更新的原則並套用設定</span><span class="sxs-lookup"><span data-stu-id="dfaef-168">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="dfaef-169">您也可以透過 [群組原則] 啟用全系統 PowerShell 文字記錄。</span><span class="sxs-lookup"><span data-stu-id="dfaef-169">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dfaef-170">下一步</span><span class="sxs-lookup"><span data-stu-id="dfaef-170">Next steps</span></span>

[<span data-ttu-id="dfaef-171">建立角色功能檔案</span><span class="sxs-lookup"><span data-stu-id="dfaef-171">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="dfaef-172">建立工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="dfaef-172">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="dfaef-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfaef-173">See also</span></span>

[<span data-ttu-id="dfaef-174">WinRM 安全性</span><span class="sxs-lookup"><span data-stu-id="dfaef-174">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="dfaef-175">PowerShell ♥ 藍色小組</span><span class="sxs-lookup"><span data-stu-id="dfaef-175">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
