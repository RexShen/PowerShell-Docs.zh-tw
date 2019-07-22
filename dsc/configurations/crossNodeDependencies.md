---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 指定跨節點相依性
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734680"
---
# <a name="specifying-cross-node-dependencies"></a>指定跨節點相依性

> 適用於：Windows PowerShell 5.0

DSC 提供特殊的資源 **WaitForAll**、**WaitForAny** 與 **WaitForSome**，可以用在設定中指定其他節點上設定的相依性。 這些資源的行為如下所示︰

- **WaitForAll**：如果指定的資源在定義於 **NodeName** 屬性中的所有目標節點上，皆為所需的狀態，即會成功。
- **WaitForAny**：如果指定的資源在定義於 **NodeName** 屬性中的至少一個目標節點上，為所需的狀態，即會成功。
- **WaitForSome**：除了 **NodeName** 屬性外，指定一個 **NodeCount** 屬性。 如果資源至少有在最少的節點數目 (由 **NodeName** 屬性所定義的 **NodeCount** 指定) 上為所需的狀態，該資源即成功。

## <a name="syntax"></a>語法

**WaitForAll** 和 **WaitForAny** 資源共用相同的語法。 在以下範例中使用 **WaitForAny** 或 **WaitForAll** 取代 \<ResourceType\>。
和 **DependsOn** 關鍵字一樣，您必須將名稱格式化為 "[ResourceType]ResourceName"。 如果資源屬於個別的 [Configuration](configurations.md)，請在格式化的字串中加入 **ConfigurationName**，例如 "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]"。 **NodeName** 是目前資源應該等候的電腦或 Node。

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

**WaitForSome** 資源與上述的範例擁有類似的語法，但多了 **NodeCount** 索引鍵。 **NodeCount** 指出目前資源應等候的 Node 數目。

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

所有的 **WaitForXXXX** 都共用下列語法索引鍵。

|屬性|  描述   |
|---------|---------------------|
| RetryIntervalSec| 進行重試之前的秒數。 最小值為 1。|
| RetryCount| 重試次數上限。|
| ThrottleLimit| 可同時連線的電腦數目。 預設值為 `New-CimSession` 預設值。|
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 如需詳細資訊，請參閱 [DependsOn](resource-depends-on.md)|
| PsDscRunAsCredential | 請參閱[以使用者認證執行 DSC](./runAsUser.md) |

## <a name="using-waitforxxxx-resources"></a>使用 WaitForXXXX 資源

每個 **WaitForXXXX** 資源都會等候指定的資源在指定的 Node 上完成。
在相同 Configuration 上的其他資源，接著可以使用 **DependsOn** 索引鍵，「相依於」  **WaitForXXXX** 資源。

例如，在下列設定中，目標節點正在等候 **xADDomain** 資源在 **MyDC** 節點上在 15 秒的間隔內最多重試 30 次完成，之後目標節點才能加入網域。

根據預設，**WaitForXXX** 資源會嘗試一次，然後才失敗。 雖然並非必要，但通常要指定 **RetryCount** 與 **RetryIntervalSec**。

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

當您編譯 Configuration 時，會產生兩個 ".mof" 檔案。 使用 [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet，將這兩個 ".mof" 檔案套用至目標 Node

> [!NOTE]
> **WaitForXXX** 資源使用 Windows 遠端管理來檢查其他節點的狀態。
> 如需 WinRM 連接埠和安全性需求的詳細資訊，請參閱 [PowerShell 遠端安全性考量](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)。

## <a name="see-also"></a>另請參閱

- [DSC 設定](configurations.md)
- [使用資源相依性](resource-depends-on.md)
- [DSC 資源](../resources/resources.md)
- [設定本機設定管理員](../managing-nodes/metaConfig.md)
