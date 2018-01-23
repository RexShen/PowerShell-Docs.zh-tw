---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC WaitForAll 資源"
ms.openlocfilehash: 2054d2af7cd7dd839c62e77c1d4b6eee5cff34ab
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforall-resource"></a>DSC WaitForAll 資源

> 適用於︰Windows PowerShell 5.0 及更新版本

您可以在 [DSC 設定](configurations.md)中的節點區塊內使用 **WaitForAll**「預期狀態設定」(DSC) 資源，以指定與其他節點上之設定的相依性。

如果 **ResourceName** 屬性所指定的資源在 **NodeName** 屬性所定義的所有目標節點上都處於預期狀態，此資源即可視為成功。


## <a name="syntax"></a>語法

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Properties

|  屬性  |  描述   | 
|---|---| 
| ResourceName| 所要依據的資源名稱。| 
| NodeName| 所要依據之資源的目標節點。| 
| RetryIntervalSec| 進行重試之前的秒數。 最小值為 1。| 
| RetryCount| 重試次數上限。| 
| ThrottleLimit| 可同時連線的電腦數目。 預設值為 new-cimsession default。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。|


## <a name="example"></a>範例

如需有關如何使用此資源的範例，請參閱[指定跨節點相依性](crossNodeDependencies.md)

