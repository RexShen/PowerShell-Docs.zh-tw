---
ms.date: 1/17/2019
keywords: dsc,powershell,設定,安裝
title: 重新啟動節點
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676833"
---
# <a name="reboot-a-node"></a>重新啟動節點

> [!NOTE]
> 本主題討論如何重新啟動節點。 為了讓重新開機，才能成功**ActionAfterReboot**並**RebootNodeIfNeeded**必須正確設定的 LCM 設定。
> 若要深入了解本機設定管理員設定，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)，或[設定本機設定管理員 (v4)](../managing-nodes/metaConfig4.md)。

節點可重新啟動從資源中，使用`$global:DSCMachineStatus`旗標。 若要設定這個旗標`1`中`Set-TargetResource`函式會強制重新啟動之後直接的節點 LCM**設定**方法目前的資源。 使用此旗標， **xPendingReboot**重新開機是否擱置中偵測到的資源之外 DSC。

您[組態](configurations.md)可能會執行需要重新啟動節點的步驟。 例如，這可能包括項目：

- Windows: 更新
- 軟體安裝
- 檔案重新命名
- 電腦重新命名

**XPendingReboot**資源檢查特定電腦的位置，以判斷是否暫止重新開機。 如果節點要求 DSC，之外重新開機**xPendingReboot**的資源集`$global:DSCMachineStatus`旗標設為`1`強制重新開機，並解決問題的暫止。

> [!NOTE]
> 任何 DSC 資源可以指示來設定這個旗標，重新啟動節點 LCM`Set-TargetResource`函式。 如需詳細資訊，請參閱 <<c0> [ 撰寫自訂 DSC 資源與 MOF](../resources/authoringResourceMOF.md)。

## <a name="syntax"></a>語法

```
xPendingReboot [String] #ResourceName
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

## <a name="properties"></a>Properties

| 屬性 | 描述 |
| --- | --- |
| 名稱| 必須是唯一的每個執行個體設定中之資源的必要的參數。|
| SkipComponentBasedServicing | 元件為基礎的服務元件所觸發的略過重新開機。 |
| SkipWindowsUpdate | 由 Windows Update 所觸發的略過重新開機。|
| SkipPendingFileRename | 略過暫止檔案重新命名重新開機。 |
| SkipCcmClientSDK | 由 ConfigMgr 用戶端所觸發的略過重新開機。 |
| SkipComputerRename | 略過重新觸發開機的電腦重新命名。 |
| PSDSCRunAsCredential | 支援 v5。 指定的使用者身分執行的資源。 |
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 如需詳細資訊，請參閱[使用 DependsOn](resource-depends-on.md)|

## <a name="example"></a>範例

下列範例會安裝使用 Microsoft Exchange [xExchange](https://github.com/PowerShell/xExchange)資源。
在安裝中，整個**xPendingReboot**資源用來重新啟動節點。

> [!NOTE]
> 這個範例需要可將 Exchange server 新增至樹系的權限的帳戶的認證。 如需有關如何在 DSC 中使用認證的詳細資訊，請參閱[處理 DSC 的認證](../configurations/configDataCredentials.md)

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
    Import-DscResource -Module xPendingReboot

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
        xPendingReboot BeforeExchangeInstall
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
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> 這個範例假設您已設定您的本機設定管理員，來允許重新開機，並繼續在重新開機後的設定。

## <a name="where-to-download"></a>若要下載的位置

您可以下載本主題的下列位置，或使用 「 PowerShell 資源庫中使用的資源。

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
