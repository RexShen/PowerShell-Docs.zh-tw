---
title: "指定跨節點相依性"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 04aa6292dee991060669e1ac770cf98cbba41bfc
ms.openlocfilehash: f4c64d3603fd01f29a63f8b180057714bf3d1197

---

# 指定跨節點相依性

> 適用於：Windows PowerShell 5.0

DSC 提供特殊的資源 **WaitForAll**、**WaitForAny** 與 **WaitForSome**，可以用在設定中指定其他節點上設定的相依性。 這些資源的行為如下所示︰

* **WaitForAll**︰如果指定的資源在定義於 **NodeName** 屬性中的所有目標節點上，皆為所需的狀態，即會成功。
* **WaitForAny**︰如果指定的資源在定義於 **NodeName** 屬性中的至少一個目標節點上，為所需的狀態，即會成功。
* **WaitForSome**：除了 **NodeName** 屬性外，指定一個 **NodeCount** 屬性。 如果資源至少有在最少的節點數目 (由 **NodeName** 屬性所定義的 **NodeCount** 指定) 上為所需的狀態，該資源即成功。 

## 使用 WaitForXXXX 資源

若要使用 **WaitForXXXX** 資源，需要建立指定要等候之 DSC 資源與節點的該資源類型資源區塊。 然後使用 **DependsOn** 屬性 (在設定中的任一其他資源區塊中)，等候 **WaitForXXXX** 節點內指定的條件成功。

例如，在下列設定中，目標節點正在等候 **xADDomain** 資源在 **MyDC** 節點上在 15 秒的間隔內最多重試 30 次完成，之後目標節點才能加入網域。

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

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
            Name             = 'MyPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

>**注意︰**根據預設，WaitForXXX 資源會嘗試一次，然後才失敗。 雖然並非必要，但通常要指定重試間隔與計數。

## 另請參閱
* [DSC 設定](configurations.md)
* [DSC 資源](resources.md)
* [設定本機設定管理員](metaConfig.md)




<!--HONumber=Jun16_HO4-->


