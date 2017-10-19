---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC WaitForSome 資源"
ms.openlocfilehash: 3ea9dc51cbb00cf6158abf114fdb31fd91307df9
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2017
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome 資源

> 適用於︰Windows PowerShell 5.0 及更新版本

您可以在 [DSC 設定](configurations.md)中的節點區塊內使用 **WaitForAny**「預期狀態設定」(DSC) 資源，以指定與其他節點上之設定的相依性。

如果 **ResourceName** 屬性所指定的資源處於預期狀態的節點達到 **NodeName** 屬性所定義的節點數目下限 (由 **NodeCount** 指定)，此資源即可視為成功。 


## <a name="syntax"></a>語法

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

## <a name="properties"></a>[內容]

|  屬性  |  描述   | 
|---|---| 
| NodeCount| 若要將此資源視為成功，必須處於預期狀態的節點數目下限。|
| NodeName| 所要依據之資源的目標節點。| 
| ResourceName| 所要依據的資源名稱。| 
| RetryIntervalSec| 進行重試之前的秒數。 最小值為 1。| 
| RetryCount| 重試次數上限。| 
| ThrottleLimit| 可同時連線的電腦數目。 預設值為 new-cimsession default。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。|
| PsDscRunAsCredential | 請參閱[以使用者認證執行 DSC](https://docs.microsoft.com/en-us/powershell/dsc/runasuser) |


## <a name="example"></a>範例

如需有關如何使用此資源的範例，請參閱[指定跨節點相依性](crossNodeDependencies.md)

