---
ms.date: 01/17/2019
keywords: dsc,powershell,設定,安裝
title: 重新啟動節點
description: 有許多組態設定可能會要求電腦重新開機，以完成設定變更。 此文章說明如何管理設定中的重新開機。
ms.openlocfilehash: d2b0f77c34ebcb006821da1f4f8d7c4b046f7a95
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645117"
---
# <a name="reboot-a-node"></a>重新啟動節點

> [!NOTE]
> 本主題討論如何重新啟動節點。 必須正確設定 **ActionAfterReboot** 和 **RebootNodeIfNeeded** LCM 設定，才能成功重新開機。 若要查看本機設定管理員設定，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)或[設定本機設定管理員 (v4)](../managing-nodes/metaConfig4.md)。

使用 `$global:DSCMachineStatus` 旗標即可從資源內重新啟動節點。 在 `Set-TargetResource` 函式中將此旗標設為 `1`，會強制 LCM 在目前資源的 **Set** 方法之後，直接重新啟動節點。 使用此旗標， **ComputerManagementDsc** 資源模組中的 [PendingReboot](https://github.com/PowerShell/ComputerManagementDsc) 資源會偵測 DSC 外部是否有擱置的重新開機。

您的[設定](configurations.md)會執行需要重新啟動節點的步驟。 這可能包括下列項目：

- Windows 更新
- 軟體安裝
- 檔案重新命名
- 電腦重新命名

**PendingReboot** 資源會檢查特定的電腦位置來判斷重新啟動是否暫止。 如果節點要求在 DSC 外重新啟動，則 **PendingReboot** 資源會將 `$global:DSCMachineStatus` 旗標設定為 `1` 來強制重新啟動並解決暫止狀況。

> [!NOTE]
> 任何 DSC 資源皆可在 `Set-TargetResource` 函式中設定此旗標，指示 LCM 重新啟動節點。 如需詳細資訊，請參閱[使用 MOF 撰寫自訂的 DSC 資源](../resources/authoringResourceMOF.md)。

## <a name="syntax"></a>語法

```
PendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>屬性

| 屬性 | 描述 |
| --- | --- |
| Name| 在設定內，資源每個執行個體的必要參數都必須為唯一。|
| SkipComponentBasedServicing | 以元件為基礎服務元件所觸發的略過重新啟動。 |
| SkipWindowsUpdate | Windows Update 所觸發的略過重新啟動。|
| SkipPendingFileRename | 略過暫止檔案重新命名重新啟動。 |
| SkipCcmClientSDK | ConfigMgr 用戶端所觸發的略過重新啟動。 |
| SkipComputerRename | 電腦重新命名所觸發的略過重新啟動。 |
| PSDSCRunAsCredential | v5 支援。 以指定的使用者身分執行資源。 |
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName** ，而它的類型是 **ResourceType** ，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 如需詳細資訊，請參閱[使用 DependsOn](resource-depends-on.md)|

## <a name="example"></a>範例

下列範例會使用 [xExchange](https://github.com/PowerShell/xExchange) 資源來安裝 Microsoft Exchange。 在整個安裝過程中，都使用 **PendingReboot** 資源來重新啟動節點。

> [!NOTE]
> 這個範例需要有權將 Exchange 伺服器新增至樹系的帳戶認證。 如需在 DSC 中使用認證的詳細資訊，請參閱[處理 DSC 的認證](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module ComputerManagementDsc

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        PendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> 這個範例假設您已設定本機設定管理員允許重新啟動，並在重新啟動後繼續設定。

## <a name="where-to-download"></a>下載位置

您可在下列位置下載本主題中使用的資源，或使用 PowerShell 資源庫。

- [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc)
- [xExchange](https://github.com/PowerShell/xExchange)
