---
ms.date: 07/09/2019
keywords: dsc,gpo,powershell,configuration,setup
title: 快速入門 - 將群組原則轉換至 DSC
description: 此快速入門說明將 Windows 群組原則轉換為 DSC 設定的必要步驟。
ms.openlocfilehash: b67f6dd2cf6c91d90fa6ac5b6367f9efc7f40ee0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644702"
---
# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="fab30-104">快速入門：將群組原則轉換至 DSC</span><span class="sxs-lookup"><span data-stu-id="fab30-104">Quickstart: Convert Group Policy into DSC</span></span>

> <span data-ttu-id="fab30-105">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fab30-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="fab30-106">您可以從群組原則或 Azure 資訊安全中心基準產生 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="fab30-106">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="fab30-107">[BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) 模組包含下列可完成這項工作的命令。</span><span class="sxs-lookup"><span data-stu-id="fab30-107">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="fab30-108">`ConvertFrom-GPO` - 轉換群組原則，儲存為檔案。</span><span class="sxs-lookup"><span data-stu-id="fab30-108">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="fab30-109">您也可以指定包含多個原則的目錄，這些原則會合併為單一組態。</span><span class="sxs-lookup"><span data-stu-id="fab30-109">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="fab30-110">若要將群組原則匯出至您的環境，請使用 [Backup-GPO](/powershell/module/grouppolicy/backup-gpo) Cmdlet，或遵循[將 GPO 匯出到檔案](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file)中的指示。</span><span class="sxs-lookup"><span data-stu-id="fab30-110">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="fab30-111">`ConvertFrom-SCM` - 轉換安全性合規性管理員基準，儲存為 `.xml` 檔案。</span><span class="sxs-lookup"><span data-stu-id="fab30-111">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="fab30-112">`ConvertFrom-ASC` - 轉換 Azure 安全性中心基準，儲存為 `.json` 檔案。</span><span class="sxs-lookup"><span data-stu-id="fab30-112">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="fab30-113">`Merge-GPOs` - 轉換群組原則，套用至目標電腦。</span><span class="sxs-lookup"><span data-stu-id="fab30-113">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="fab30-114">上述的 Cmdlet 會將基準轉換為 DSC `.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="fab30-114">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="fab30-115">您也可以選擇輸出設定指令碼 (`.ps1`)，以便您編輯和重新編譯。</span><span class="sxs-lookup"><span data-stu-id="fab30-115">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="fab30-116">Cmdlet 會偵測缺少資源或重複資源區塊的編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="fab30-116">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="fab30-117">可能導致編譯錯誤的資源區塊會加上註解。</span><span class="sxs-lookup"><span data-stu-id="fab30-117">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="fab30-118">下列範例會將 [Microsoft 安全性基準](https://www.microsoft.com/download/details.aspx?id=55319)轉換為 DSC 設定指令碼 (`.ps1`) 和 `.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="fab30-118">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="fab30-119">執行命令之後，您會在建立於目前路徑下方的預設「輸出」目錄中看到兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="fab30-119">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

<span data-ttu-id="fab30-120">每個受控節點也需要下列兩個模組：</span><span class="sxs-lookup"><span data-stu-id="fab30-120">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="fab30-121">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="fab30-121">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="fab30-122">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="fab30-122">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="fab30-123">**BaselineManagement** 是社群開發的解決方案，可讓搜尋 DSC 變得更容易；社群解決方案的支援由專案維護人員而不是 Microsoft 提供。</span><span class="sxs-lookup"><span data-stu-id="fab30-123">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="fab30-124">您可以在 [GitHub](https://github.com/microsoft/BaselineManagement) 上針對 **BaselineManagement** 提出新的問題。</span><span class="sxs-lookup"><span data-stu-id="fab30-124">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fab30-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fab30-125">Next steps</span></span>

- <span data-ttu-id="fab30-126">若要將您的設定指令碼上傳至 Azure 自動化狀態設定，請參閱[開始使用](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation)。</span><span class="sxs-lookup"><span data-stu-id="fab30-126">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="fab30-127">將 **SecurityPolicyDSC** 和 **AuditPolicyDSC** 模組新增至您的 [自動化帳戶](/azure/automation/shared-resources/modules)。</span><span class="sxs-lookup"><span data-stu-id="fab30-127">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="fab30-128">在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。</span><span class="sxs-lookup"><span data-stu-id="fab30-128">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
