---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 指定跨節點相依性
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400626"
---
# <a name="specifying-cross-node-dependencies"></a>指定跨節點相依性

> 適用於：Windows PowerShell 5.0

DSC 提供特殊的資源 **WaitForAll**、**WaitForAny** 與 **WaitForSome**，可以用在設定中指定其他節點上設定的相依性。 這些資源的行為如下所示︰

- **WaitForAll**:如果指定的資源所需的狀態中所定義的所有目標節點上會成功**NodeName**屬性。
- **WaitForAny**:如果指定的資源處於預期狀態的至少其中一個定義的目標節點成功**NodeName**屬性。
- **WaitForSome**:指定**NodeCount**屬性，除了**NodeName**屬性。 如果資源至少有在最少的節點數目 (由 **NodeName** 屬性所定義的 **NodeCount** 指定) 上為所需的狀態，該資源即成功。

## <a name="syntax"></a>語法

**WaitForAll**並**WaitForAny**資源共用相同的語法。 取代\<ResourceType\>在下列範例中使用**WaitForAny**或是**WaitForAll**。
像是**DependsOn**關鍵字，您必須設定為"[ResourceType] ResourceName"名稱的格式。 如果資源屬於個別[組態](configurations.md)，包括**ConfigurationName**格式化字串中"[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]"。 **NodeName**電腦，或的節點，在其等候目前的資源。

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

**WaitForSome**資源至上面的範例，類似的語法，但新增**NodeCount**索引鍵。 **NodeCount**指出目前的資源應該等候的節點數。

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

所有**WaitForXXXX**將金鑰分享給下列語法。

| 屬性 | 描述 | |RetryIntervalSec |重試之前的秒數。 最小值為 1。 ||RetryCount |重試的次數上限。 ||ThrottleLimit |可同時連接的機器數目。 預設值是`New-CimSession`預設。 | |DependsOn |指出必須執行另一個資源的設定，才能設定此資源。 如需詳細資訊，請參閱 < [DependsOn](resource-depends-on.md)| |PsDscRunAsCredential |請參閱[使用使用者認證的 DSC](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>使用 WaitForXXXX 資源

每個**WaitForXXXX**資源等候指定的節點上完成指定的資源。 相同的組態中的其他資源即可*而定* **WaitForXXXX**資源使用**DependsOn**索引鍵。

例如，在下列設定中，目標節點正在等候 **xADDomain** 資源在 **MyDC** 節點上在 15 秒的間隔內最多重試 30 次完成，之後目標節點才能加入網域。

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

當您編譯設定時，會產生兩個 「.mof 」 檔案。 這兩個 「.mof"檔案套用到使用的目標節點[Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet

>**注意：** 預設 WaitForXXX 資源會嘗試一次，則失敗。 雖然您不需要，您通常會想要指定**RetryCount**並**RetryIntervalSec**。

## <a name="see-also"></a>另請參閱

- [DSC 設定](configurations.md)
- [使用資源相依性](resource-depends-on.md)
- [DSC 資源](../resources/resources.md)
- [設定本機設定管理員](../managing-nodes/metaConfig.md)
