---
ms.date: 07/09/2019
keywords: dsc,gpo,powershell,configuration,setup
title: 快速入門 - 將群組原則轉換至 DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953465"
---
> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>快速入門：將群組原則轉換至 DSC

您可以從群組原則或 Azure 資訊安全中心基準產生 DSC 設定。 [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) 模組包含下列可完成這項工作的命令。

- `ConvertFrom-GPO` - 轉換群組原則，儲存為檔案。 您也可以指定包含多個原則的目錄，這些原則會合併為單一組態。
  - 若要將群組原則匯出至您的環境，請使用 [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) Cmdlet，或遵循[將 GPO 匯出到檔案](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file)中的指示。
- `ConvertFrom-SCM` - 轉換安全性合規性管理員基準，儲存為 `.xml` 檔案。
- `ConvertFrom-ASC` - 轉換 Azure 安全性中心基準，儲存為 `.json` 檔案。
- `Merge-GPOs` - 轉換群組原則，套用至目標電腦。

上述的 Cmdlet 會將基準轉換為 DSC `.mof` 檔案。 您也可以選擇輸出設定指令碼 (`.ps1`)，以便您編輯和重新編譯。 Cmdlet 會偵測缺少資源或重複資源區塊的編譯錯誤。 可能導致編譯錯誤的資源區塊會加上註解。

下列範例會將 [Microsoft 安全性基準](https://www.microsoft.com/en-us/download/details.aspx?id=55319)轉換為 DSC 設定指令碼 (`.ps1`) 和 `.mof` 檔案。

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

執行命令之後，您會在建立於目前路徑下方的預設「輸出」目錄中看到兩個檔案。

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

每個受控節點也需要下列兩個模組：

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** 是社群開發的解決方案，可讓搜尋 DSC 變得更容易；社群解決方案的支援由專案維護人員而不是 Microsoft 提供。 您可以在 [GitHub](https://github.com/microsoft/BaselineManagement) 上針對 **BaselineManagement** 提出新的問題。

## <a name="next-steps"></a>接下來的步驟

- 若要將您的設定指令碼上傳至 Azure 自動化狀態設定，請參閱[開始使用](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation)。
- 將 **SecurityPolicyDSC** 和 **AuditPolicyDSC** 模組新增至您的[自動化帳戶](/azure/automation/shared-resources/modules)。
- 在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。
