---
title: "使用多個版本的資源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 01720794aa1d200428c2729463fba92970f9cb56
ms.openlocfilehash: 716ecd9b14976dd70b69a740850ab53670387956

---

# 使用多個版本的資源

> 適用於：Windows PowerShell 5.0

在 PowerShell 5.0，DSC 資源可以有多個版本，且各版本可於一部電腦上並存安裝。 而其運作方式則是在相同的模組資料夾中，包含多個版本的資源模組。

## 並存安裝多個資源版本

您可以使用 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) Cmdlet 的 **MinimumVersion**、**MaximumVersion** 與 **RequiredVersion** 參數，指定要安裝的模組版本。 呼叫 **Install-Module** 但未指定版本，會安裝最新的版本。

例如，多個版本的 **xFailOverCluster** 模組，每個皆包含 **xCluster** 資源。 呼叫 **Install-Module** 但未指定版本號碼的結果如下：

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

現在，如果再次呼叫 **Install-Module**，但指定 **RequiredVersion** 為 1.1.0.0，會產生以下結果︰

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## 在設定中指定資源版本

如果在電腦上安裝了多個資源，當您在設定中使用該資源時，必須指定版本。 若要這麼做，請指定 **Import-DscResource** 關鍵字的 **ModuleVersion** 參數。 若您無法指定安裝了多重版本之資源的資源模組版本，設定便會產生錯誤。

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

## 另請參閱
* [DSC 設定](configurations.md)
* [DSC 資源](resources.md)




<!--HONumber=Jun16_HO4-->


