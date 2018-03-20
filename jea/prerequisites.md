---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea,powershell,安全性"
title: "JEA 必要條件"
ms.openlocfilehash: e6ee16e34eb9f1f0b2f3601c1aa9e90ab4f785f1
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="prerequisites"></a><span data-ttu-id="16344-103">必要條件</span><span class="sxs-lookup"><span data-stu-id="16344-103">Prerequisites</span></span>

> <span data-ttu-id="16344-104">適用對象：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="16344-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="16344-105">Just Enough Administration 是 Windows PowerShell 5.0 和更新版本隨附的功能。</span><span class="sxs-lookup"><span data-stu-id="16344-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="16344-106">本主題說明必須滿足才能開始使用 JEA 的必要條件。</span><span class="sxs-lookup"><span data-stu-id="16344-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="16344-107">安裝 PHP</span><span class="sxs-lookup"><span data-stu-id="16344-107">Install JEA</span></span>

<span data-ttu-id="16344-108">JEA 適用於 Windows PowerShell 5.0 和更新版本，但如需完整的功能，建議您為系統安裝最新版的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="16344-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="16344-109">下表說明 JEA 在 Windows Server 上的可用性：</span><span class="sxs-lookup"><span data-stu-id="16344-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="16344-110">伺服器作業系統</span><span class="sxs-lookup"><span data-stu-id="16344-110">Server Operating System</span></span>   | <span data-ttu-id="16344-111">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="16344-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="16344-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="16344-112">Windows Server 2016</span></span>       | <span data-ttu-id="16344-113">預先安裝</span><span class="sxs-lookup"><span data-stu-id="16344-113">Preinstalled</span></span>
<span data-ttu-id="16344-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="16344-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="16344-115">具完整功能性的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="16344-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="16344-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="16344-116">Windows Server 2012</span></span>       | <span data-ttu-id="16344-117">具完整功能性的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="16344-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="16344-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="16344-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="16344-119">功能有限 <sup>1</sup> 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="16344-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="16344-120">您也可以在家用或工作電腦上使用 JEA：</span><span class="sxs-lookup"><span data-stu-id="16344-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="16344-121">用戶端作業系統</span><span class="sxs-lookup"><span data-stu-id="16344-121">Client Operating System</span></span>   | <span data-ttu-id="16344-122">JEA 可用性</span><span class="sxs-lookup"><span data-stu-id="16344-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="16344-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="16344-123">Windows 10 1607+</span></span>          | <span data-ttu-id="16344-124">預先安裝</span><span class="sxs-lookup"><span data-stu-id="16344-124">Preinstalled</span></span>
<span data-ttu-id="16344-125">Windows 10 1603、1511</span><span class="sxs-lookup"><span data-stu-id="16344-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="16344-126">預先安裝，功能有限<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="16344-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="16344-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="16344-127">Windows 10 1507</span></span>           | <span data-ttu-id="16344-128">無法使用</span><span class="sxs-lookup"><span data-stu-id="16344-128">Not available</span></span>
<span data-ttu-id="16344-129">Windows 8、8.1</span><span class="sxs-lookup"><span data-stu-id="16344-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="16344-130">具完整功能性的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="16344-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="16344-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="16344-131">Windows 7</span></span>                 | <span data-ttu-id="16344-132">功能有限 <sup>1</sup> 的 WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="16344-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="16344-133"><sup>1</sup> 在 Windows Server 2008 R2 或 Windows 7 無法設定 JEA 使用群組受管理的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="16344-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="16344-134">*支援*虛擬帳戶和其他 JEA 功能。</span><span class="sxs-lookup"><span data-stu-id="16344-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="16344-135"><sup>2</sup> Windows 10 1511 和 1603 版不支援下列 JEA 功能︰使用群組受管理的服務帳戶身分執行、工作階段設定中的條件式存取規則、使用者磁碟機，以及授與存取權給本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="16344-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="16344-136">若要取得這些功能的支援，請將 Windows 更新為 1607 版 (年度更新版) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="16344-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="16344-137">檢查已安裝哪個版本的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="16344-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="16344-138">若要檢查哪個版本的 PowerShell 安裝在您的系統上，請在 Windows PowerShell 提示字元中檢查 `$PSVersionTable` 變數。</span><span class="sxs-lookup"><span data-stu-id="16344-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="16344-139">如果「主要」版本等於或大於 **5**，您便可以使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="16344-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="16344-140">如需最佳的體驗，以及存取所有最新的功能，建議您在可能時升級到 PowerShell **5.1** 版。</span><span class="sxs-lookup"><span data-stu-id="16344-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="16344-141">安裝 Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="16344-141">Install Windows Management Framework</span></span>

<span data-ttu-id="16344-142">如果您執行較舊版本的 PowerShell，必須更新您的系統，使用最新的 Windows Management Framework (WMF) 更新。</span><span class="sxs-lookup"><span data-stu-id="16344-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="16344-143">更新套件和最新 WMF 版本資訊的連結都提供在[下載中心](https://aka.ms/WMF5)。</span><span class="sxs-lookup"><span data-stu-id="16344-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://aka.ms/WMF5).</span></span>

<span data-ttu-id="16344-144">強烈建議您先測試工作負載的 WMF 相容性，再升級所有的伺服器。</span><span class="sxs-lookup"><span data-stu-id="16344-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="16344-145">Windows 10 使用者應安裝最新的功能更新，以取得目前版本的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="16344-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="16344-146">啟用 PowerShell 遠端</span><span class="sxs-lookup"><span data-stu-id="16344-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="16344-147">PowerShell 遠端提供 JEA 建置的基礎。</span><span class="sxs-lookup"><span data-stu-id="16344-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="16344-148">因此必須確保已在系統上啟用 PowerShell 遠端並[經過適當保護](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)，才能使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="16344-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="16344-149">Windows Server 2012、2012 R2 和 2016 中預設已啟用 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="16344-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="16344-150">您可以在提升權限的 PowerShell 視窗中執行下列命令，來啟用 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="16344-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="16344-151">啟用 PowerShell 模組和指令碼區塊記錄 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="16344-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="16344-152">下列步驟可啟用系統上所有 PowerShell 動作的記錄。</span><span class="sxs-lookup"><span data-stu-id="16344-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="16344-153">JEA 不需要 PowerShell 模組記錄，不過強烈建議您將它開啟，以確保使用者執行的命令會記錄在中央位置。</span><span class="sxs-lookup"><span data-stu-id="16344-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="16344-154">您可以使用群組原則設定 PowerShell 模組記錄原則。</span><span class="sxs-lookup"><span data-stu-id="16344-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="16344-155">在工作站上開啟本機群組原則編輯器，或在 Active Directory 網域控制站上的群組原則管理主控台上開啟群組原則物件</span><span class="sxs-lookup"><span data-stu-id="16344-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="16344-156">瀏覽至 [電腦設定]\\[系統管理範本]\\[Windows 元件]\\[Windows PowerShell]</span><span class="sxs-lookup"><span data-stu-id="16344-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="16344-157">按兩下 [開啟模組記錄]</span><span class="sxs-lookup"><span data-stu-id="16344-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="16344-158">按一下 [啟用]</span><span class="sxs-lookup"><span data-stu-id="16344-158">Click **Enabled**</span></span>
5. <span data-ttu-id="16344-159">在 [選項] 區段中，按一下模組名稱旁邊的 [顯示]</span><span class="sxs-lookup"><span data-stu-id="16344-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="16344-160">在快顯視窗中輸入 "**\***"。</span><span class="sxs-lookup"><span data-stu-id="16344-160">Type "**\***" in the pop up window.</span></span> <span data-ttu-id="16344-161">這會指示 PowerShell 記錄來自所有模組的命令。</span><span class="sxs-lookup"><span data-stu-id="16344-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="16344-162">按一下 [確定] 設定原則</span><span class="sxs-lookup"><span data-stu-id="16344-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="16344-163">按兩下 [開啟 PowerShell 指令碼區塊記錄]</span><span class="sxs-lookup"><span data-stu-id="16344-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="16344-164">按一下 [啟用]</span><span class="sxs-lookup"><span data-stu-id="16344-164">Click **Enabled**</span></span>
10. <span data-ttu-id="16344-165">按一下 [確定] 設定原則</span><span class="sxs-lookup"><span data-stu-id="16344-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="16344-166">(僅限已加入網域的電腦) 執行 **gpupdate** 或等待群組原則處理已更新的原則並套用設定</span><span class="sxs-lookup"><span data-stu-id="16344-166">(On domain-joined machines only) Run **gpupdate** or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="16344-167">您也可以透過 [群組原則] 啟用全系統 PowerShell 文字記錄。</span><span class="sxs-lookup"><span data-stu-id="16344-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="16344-168">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="16344-168">Next steps</span></span>

- [<span data-ttu-id="16344-169">建立角色功能檔案</span><span class="sxs-lookup"><span data-stu-id="16344-169">Create a role capability file</span></span>](role-capabilities.md)
- [<span data-ttu-id="16344-170">建立工作階段設定檔</span><span class="sxs-lookup"><span data-stu-id="16344-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="16344-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16344-171">See also</span></span>

- [<span data-ttu-id="16344-172">PowerShell 遠端和 WinRM 安全性的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="16344-172">Additional information about PowerShell Remoting and WinRM security</span></span>](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [<span data-ttu-id="16344-173">*PowerShell ♥ 藍色小組*安全性部落格文章</span><span class="sxs-lookup"><span data-stu-id="16344-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

