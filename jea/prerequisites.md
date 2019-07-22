---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 必要條件
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734289"
---
# <a name="prerequisites"></a><span data-ttu-id="f1bf3-103">必要條件</span><span class="sxs-lookup"><span data-stu-id="f1bf3-103">Prerequisites</span></span>

<span data-ttu-id="f1bf3-104">Just Enough Administration 是 PowerShell 5.0 和更高版本隨附的功能。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="f1bf3-105">本文描述必須滿足才能開始使用 JEA 的必要條件。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="f1bf3-106">檢查已安裝哪個版本的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1bf3-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="f1bf3-107">若要檢查哪個版本的 PowerShell 安裝在您的系統上，請在 Windows PowerShell 提示字元中檢查 `$PSVersionTable` 變數。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="f1bf3-108">JEA 適用於 PowerShell 5.0 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="f1bf3-109">如需完整的功能，建議您為系統安裝最新版的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="f1bf3-110">下表說明 JEA 在 Windows Server 上的可用性：</span><span class="sxs-lookup"><span data-stu-id="f1bf3-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="f1bf3-111">伺服器作業系統</span><span class="sxs-lookup"><span data-stu-id="f1bf3-111">Server Operating System</span></span> |                <span data-ttu-id="f1bf3-112">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="f1bf3-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="f1bf3-113">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="f1bf3-113">Windows Server 2016+</span></span>    | <span data-ttu-id="f1bf3-114">預先安裝</span><span class="sxs-lookup"><span data-stu-id="f1bf3-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="f1bf3-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f1bf3-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="f1bf3-116">具完整功能性的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f1bf3-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="f1bf3-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f1bf3-117">Windows Server 2012</span></span>     | <span data-ttu-id="f1bf3-118">具完整功能性的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f1bf3-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="f1bf3-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="f1bf3-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="f1bf3-120">功能有限 <sup>1</sup> 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f1bf3-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="f1bf3-121">您也可以在家用或工作電腦上使用 JEA：</span><span class="sxs-lookup"><span data-stu-id="f1bf3-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="f1bf3-122">用戶端作業系統</span><span class="sxs-lookup"><span data-stu-id="f1bf3-122">Client Operating System</span></span> |                   <span data-ttu-id="f1bf3-123">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="f1bf3-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="f1bf3-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="f1bf3-124">Windows 10 1607+</span></span>        | <span data-ttu-id="f1bf3-125">預先安裝</span><span class="sxs-lookup"><span data-stu-id="f1bf3-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="f1bf3-126">Windows 10 1603、1511</span><span class="sxs-lookup"><span data-stu-id="f1bf3-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="f1bf3-127">預先安裝，功能有限<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="f1bf3-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="f1bf3-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="f1bf3-128">Windows 10 1507</span></span>         | <span data-ttu-id="f1bf3-129">無法使用</span><span class="sxs-lookup"><span data-stu-id="f1bf3-129">Not available</span></span>                                        |
| <span data-ttu-id="f1bf3-130">Windows 8、8.1</span><span class="sxs-lookup"><span data-stu-id="f1bf3-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="f1bf3-131">具完整功能性的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f1bf3-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="f1bf3-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="f1bf3-132">Windows 7</span></span>               | <span data-ttu-id="f1bf3-133">功能有限 <sup>1</sup> 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f1bf3-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="f1bf3-134"><sup>1</sup> 在 Windows Server 2008 R2 或 Windows 7 上無法設定 JEA 使用群組受控服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="f1bf3-135">*支援*虛擬帳戶和其他 JEA 功能。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="f1bf3-136"><sup>2</sup> Windows 10 1511 版和 1603 版不支援下列 JEA 功能：</span><span class="sxs-lookup"><span data-stu-id="f1bf3-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="f1bf3-137">以群組受控服務帳戶執行</span><span class="sxs-lookup"><span data-stu-id="f1bf3-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="f1bf3-138">工作階段設定中的條件式存取規則</span><span class="sxs-lookup"><span data-stu-id="f1bf3-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="f1bf3-139">使用者磁碟機</span><span class="sxs-lookup"><span data-stu-id="f1bf3-139">The user drive</span></span>
  - <span data-ttu-id="f1bf3-140">將存取權授與本機使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f1bf3-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="f1bf3-141">若要取得這些功能的支援，請將 Windows 更新為 1607 版 (年度更新版) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="f1bf3-142">安裝 Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="f1bf3-142">Install Windows Management Framework</span></span>

<span data-ttu-id="f1bf3-143">如果您執行較舊版本的 PowerShell，則可能需要使用最新的 Windows Management Framework (WMF) 更新來更新系統。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="f1bf3-144">如需詳細資訊，請參閱 [WMF](/powershell/wmf/overview) 文件。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="f1bf3-145">建議您先測試工作負載的 WMF 相容性，再升級所有的伺服器。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="f1bf3-146">Windows 10 使用者應安裝最新的功能更新，以取得目前版本的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="f1bf3-147">啟用 PowerShell 遠端</span><span class="sxs-lookup"><span data-stu-id="f1bf3-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="f1bf3-148">PowerShell 遠端提供 JEA 建置的基礎。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="f1bf3-149">必須先確保已啟用 PowerShell 遠端並經過適當保護，才能使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="f1bf3-150">如需詳細資訊，請參閱 [WinRM 安全性](/powershell/scripting/learn/remoting/winrmsecurity)。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="f1bf3-151">Windows Server 2012、2012 R2 和 2016 中預設已啟用 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="f1bf3-152">您可以在提升權限的 PowerShell 視窗中執行下列命令，來啟用 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="f1bf3-153">啟用 PowerShell 模組和指令碼區塊記錄 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="f1bf3-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="f1bf3-154">下列步驟可啟用系統上所有 PowerShell 動作的記錄。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="f1bf3-155">JEA 不需要 PowerShell 模組記錄，不過建議您開啟記錄，以確保使用者執行的命令會記錄在中央位置。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="f1bf3-156">您可以使用群組原則設定 PowerShell 模組記錄原則。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="f1bf3-157">在工作站上開啟本機群組原則編輯器，或在 Active Directory 網域控制站上的群組原則管理主控台上開啟群組原則物件</span><span class="sxs-lookup"><span data-stu-id="f1bf3-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="f1bf3-158">瀏覽至 [電腦設定]\\[系統管理範本]\\[Windows 元件]\\[Windows PowerShell] </span><span class="sxs-lookup"><span data-stu-id="f1bf3-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="f1bf3-159">按兩下 [開啟模組記錄] </span><span class="sxs-lookup"><span data-stu-id="f1bf3-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="f1bf3-160">按一下 [啟用] </span><span class="sxs-lookup"><span data-stu-id="f1bf3-160">Click **Enabled**</span></span>
5. <span data-ttu-id="f1bf3-161">在 [選項] 區段中，按一下模組名稱旁邊的 [顯示] </span><span class="sxs-lookup"><span data-stu-id="f1bf3-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="f1bf3-162">在快顯視窗中鍵入 `*`，記錄來自所有模組的命令。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="f1bf3-163">按一下 [確定]  設定原則</span><span class="sxs-lookup"><span data-stu-id="f1bf3-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="f1bf3-164">按兩下 [開啟 PowerShell 指令碼區塊記錄] </span><span class="sxs-lookup"><span data-stu-id="f1bf3-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="f1bf3-165">按一下 [啟用] </span><span class="sxs-lookup"><span data-stu-id="f1bf3-165">Click **Enabled**</span></span>
10. <span data-ttu-id="f1bf3-166">按一下 [確定]  設定原則</span><span class="sxs-lookup"><span data-stu-id="f1bf3-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="f1bf3-167">(僅限已加入網域的電腦) 執行 `gpupdate` 或等待群組原則處理已更新的原則並套用設定</span><span class="sxs-lookup"><span data-stu-id="f1bf3-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="f1bf3-168">您也可以透過 [群組原則] 啟用全系統 PowerShell 文字記錄。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f1bf3-169">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="f1bf3-169">Next steps</span></span>

[<span data-ttu-id="f1bf3-170">建立角色功能檔案</span><span class="sxs-lookup"><span data-stu-id="f1bf3-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="f1bf3-171">建立工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="f1bf3-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="f1bf3-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1bf3-172">See also</span></span>

[<span data-ttu-id="f1bf3-173">WinRM 安全性</span><span class="sxs-lookup"><span data-stu-id="f1bf3-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="f1bf3-174">PowerShell ♥ 藍色小組</span><span class="sxs-lookup"><span data-stu-id="f1bf3-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
