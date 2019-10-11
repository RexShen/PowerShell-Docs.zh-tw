---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC WaitForSome 資源
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952975"
---
# <a name="dsc-waitforsome-resource"></a>DSC WaitForSome 資源

> 適用於：Windows PowerShell 5.x

您可以在 [DSC 設定](../../../configurations/configurations.md)中的節點區塊內使用 **WaitForSome**「預期狀態設定」(DSC) 資源，以指定與其他節點上之設定的相依性。

如果 **ResourceName** 屬性所指定的資源處於預期狀態的節點達到 **NodeName** 屬性所定義的節點數目下限 (由 **NodeCount** 指定)，此資源即可視為成功。

> [!NOTE]
> **WaitForSome** 資源使用 Windows 遠端管理來檢查其他節點的狀態。 如需 WinRM 連接埠和安全性需求的詳細資訊，請參閱 [PowerShell 遠端安全性考量](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)。

## <a name="syntax"></a>語法

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Properties

|屬性 |描述 |
|---|---|
|NodeCount |若要將此資源視為成功，必須處於預期狀態的節點數目下限。 |
|NodeName |所要依據之資源的目標節點。 |
|ResourceName |所要依據的資源名稱。 如果此資源屬於不同的設定，請將名稱格式化為 `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`。 |
|RetryIntervalSec |進行重試之前的秒數。 最小值為 1。 |
|RetryCount |重試次數上限。 |
|ThrottleLimit |可同時連線的電腦數目。 預設值為 `New-CimSession` 預設值。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

如需有關如何使用此資源的範例，請參閱[指定跨節點相依性](../../../configurations/crossNodeDependencies.md)