---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 設定中的條件陳述式及迴圈
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736891"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>設定中的條件陳述式及迴圈

您可以使用 PowerShell 的流程控制關鍵字，讓[設定](configurations.md)更為動態。 此文章將說明如何使用條件陳述式與迴圈，來讓您的 `Configuration` 更為動態。 將條件式和迴圈與[參數](add-parameters-to-a-configuration.md)和[設定資料](configData.md)結合，可以在編譯您的`Configuration`時提供更多的彈性和控制。

就像函式或指令碼區塊一樣，您可以在 `Configuration` 中使用任何 PowerShell 語言功能。
只有在呼叫 `Configuration` 以編譯 `.mof` 檔案時，才會評估您所使用的陳述式。 以下範例顯示了示範概念的案例。 條件陳述式和迴圈通常與參數和設定資料一起使用。

在此範例中，**服務**資源區塊在編譯時間會擷取服務的目前狀態，以產生維護其目前的狀態的 `.mof` 檔案。

> [!NOTE]
> 使用動態資源區塊將優先考慮 Intellisense 的有效性。 在編譯 `Configuration` 之前，PowerShell 剖析器無法判斷指定的值是否可接受。

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

此外，您可以使用  **迴圈為目前電腦上的每個服務建立**服務`foreach`資源區塊。

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

您也可以使用 `Configuration` 陳述式，僅為線上電腦建立 `if`。

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> 上述範例中的動態資源區塊會參考目前的電腦。 在這種情況下，這將是您正在撰寫 `Configuration` 的電腦，而不是目標節點。

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>摘要

總之，您可以在 `Configuration` 中使用任何 PowerShell 語言功能。

這包括像是：

- 自訂物件
- 雜湊表
- 字串操作
- 遠端
- WMI 和 CIM
- ActiveDirectory 物件
- 及其他...

`Configuration` 中定義的任何 PowerShell 程式碼都將在編譯時間進行評估，但您也可以在包含 `Configuration` 的指令碼中放置程式碼。 當您匯入 `Configuration` 時，會執行 `Configuration` 區塊以外的任何程式碼。

## <a name="see-also"></a>另請參閱

- [將參數新增至設定](add-parameters-to-a-configuration.md)
- [從設定中分離設定資料](configData.md)
