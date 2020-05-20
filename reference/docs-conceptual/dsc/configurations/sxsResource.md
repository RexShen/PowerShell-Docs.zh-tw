---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 匯入所安裝資源的特定版本
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953985"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>匯入所安裝資源的特定版本

> 適用於：Windows PowerShell 5.0

在 PowerShell 5.0 中，各個版本的 DSC 資源均可於一部電腦上並存安裝。 資源模組可將各個版本的資源儲存於以版本命名的資料夾中。

## <a name="installing-separate-resource-versions-side-by-side"></a>並存安裝各個資源版本

您可以使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet 的 **MinimumVersion**、**MaximumVersion** 與 **RequiredVersion** 參數，指定要安裝的模組版本。 呼叫 **Install-Module** 但未指定版本，會安裝最新的版本。

例如，**xFailOverCluster** 模組有多個版本，每個模組各包含一個 **xCluster** 資源。 呼叫 **Install-Module** 但未指定版本號碼，就會安裝最新版的模組。

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

若要安裝特定版本的模組，請將 **RequiredVersion** 指定為 1.1.0.0。 這會並存安裝指定的版本與已安裝的版本。

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

現在，您會在使用 `Get-DSCResource` 時看到列出這兩個版本的模組。

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>在設定中指定資源版本

如果電腦上安裝了各個資源版本，則當您在設定中使用該資源時，必須指定其版本。 若要這麼做，請指定 **Import-DscResource** 關鍵字的 **ModuleVersion** 參數。 若您無法指定安裝了多重版本之資源的資源模組版本，設定便會產生錯誤。

下列設定示範如何指定要呼叫之資源的版本︰

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>注意︰PowerShell 4.0 中無法使用 Import-DscResource 的 ModuleVersion 參數。 在 PowerShell 4.0 中您可以指定模組版本，方法是將模組規格物件傳遞至 Import-DscResource 的 ModuleName 參數。 模組規格物件是包含 ModuleName 與 RequiredVersion 索引鍵的雜湊表。 例如：

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

這也適用於 PowerShell 5.0 版，但仍然建議您使用 **ModuleVersion** 參數。

## <a name="see-also"></a>另請參閱

- [DSC 設定](configurations.md)
- [DSC 資源](../resources/resources.md)
