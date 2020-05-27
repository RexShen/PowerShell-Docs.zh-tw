---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: WMF 5.1 的已知問題
ms.openlocfilehash: 4f4c85e1f4984d9e91ea74ba65fdbf7188c5c7ab
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808704"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="c1eb8-103">WMF 5.1 的已知問題</span><span class="sxs-lookup"><span data-stu-id="c1eb8-103">Known Issues in WMF 5.1</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="c1eb8-104">以系統管理員身分啟動 PowerShell 捷徑</span><span class="sxs-lookup"><span data-stu-id="c1eb8-104">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="c1eb8-105">安裝 WMF 時，如果您嘗試以系統管理員身分從捷徑啟動 PowerShell，可能會收到「未指定的錯誤」訊息。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-105">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span> <span data-ttu-id="c1eb8-106">您現在可以系統管理員以外的身分重新開啟捷徑，捷徑將會以系統管理員身分運作。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-106">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="c1eb8-107">Pester</span><span class="sxs-lookup"><span data-stu-id="c1eb8-107">Pester</span></span>

<span data-ttu-id="c1eb8-108">在此版本中，當您在 Nano 伺服器使用 Pester 時有兩個問題應該要注意︰</span><span class="sxs-lookup"><span data-stu-id="c1eb8-108">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="c1eb8-109">因為完整 CLR 和核心 CLR 之間的差異，針對 Pester 本身執行測試時會導致某些失敗。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-109">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="c1eb8-110">特別是，**XmlDocument** 類型中無法使用 **Validate** 方法。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-110">In particular, the **Validate** method is not available on the **XmlDocument** type.</span></span> <span data-ttu-id="c1eb8-111">已知有六個嘗試驗證 NUnit 輸出記錄檔結構描述的測試會失敗。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-111">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="c1eb8-112">有一個程式碼涵蓋範圍測試失敗，因為 Nano 伺服器中沒有 **WindowsFeature** DSC 資源存在。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-112">One code coverage test fails because the **WindowsFeature** DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="c1eb8-113">不過，這些失敗通常是無害的，可以放心地忽略。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-113">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="c1eb8-114">作業驗證</span><span class="sxs-lookup"><span data-stu-id="c1eb8-114">Operation Validation</span></span>

- <span data-ttu-id="c1eb8-115">因為不具有效的說明 URI，導致 Microsoft.PowerShell.Operation.Validation 模組的 `Update-Help` 失敗</span><span class="sxs-lookup"><span data-stu-id="c1eb8-115">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="c1eb8-116">解除安裝 WMF 之後的 DSC</span><span class="sxs-lookup"><span data-stu-id="c1eb8-116">DSC after uninstall WMF</span></span>

- <span data-ttu-id="c1eb8-117">解除安裝 WMF 不會從組態資料夾中刪除 DSC MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-117">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="c1eb8-118">若 MOF 文件包含更新且無法在舊版系統上使用的內容，DSC 便無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-118">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="c1eb8-119">在此情況下，請從提高權限的 PowerShell 主控台中執行下列指令碼，以清除 DSC 狀態。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-119">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="c1eb8-120">JEA 虛擬帳戶</span><span class="sxs-lookup"><span data-stu-id="c1eb8-120">JEA Virtual Accounts</span></span>

<span data-ttu-id="c1eb8-121">WMF 5.0 中設定為使用虛擬帳戶的 JEA 端點與工作階段設定，在升級為 WMF 5.1 之後將不會設定為使用虛擬帳戶。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-121">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span> <span data-ttu-id="c1eb8-122">這表示在 JEA 工作階段中執行的命令將會以連線使用者的身分執行，而不是使用暫時的系統管理員帳戶，這將能避免使用者執行需要提高權限的命令。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-122">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span> <span data-ttu-id="c1eb8-123">若要還原虛擬帳戶，您需要取消註冊，然後重新註冊使用虛擬帳戶的所有工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="c1eb8-123">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```
