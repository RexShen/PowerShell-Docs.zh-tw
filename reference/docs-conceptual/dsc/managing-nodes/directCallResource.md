---
ms.date: 08/11/2020
keywords: dsc,powershell,設定,安裝
title: 直接呼叫 DSC 資源方法
ms.openlocfilehash: 029a278c938e414820e172b85fac3cb3ad4b4afa
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162489"
---
# <a name="calling-dsc-resource-methods-directly"></a>直接呼叫 DSC 資源方法

>適用於：Windows PowerShell 5.0

您可使用[Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) Cmdlet，直接呼叫 DSC 資源的函式或方法 (MOF 形資源的 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource` 函式，或類別形資源的 **Get**、**Set** 和 **Test** 方法)。 這類方法適用於協力廠商想要使用 DSC 資源時，或是作為開發資源的有力工具。

> [!NOTE]
> 在 PowerShell 7.0 以上的版本中，`Invoke-DscResource` 不再支援叫用 WMI DSC 資源。 這包括 **PSDesiredStateConfiguration** 中的**檔案**和**記錄**資源。

這個 Cmdlet 通常搭配中繼設定屬性 `refreshMode = 'Disabled'` 一起使用，但可用於任何 **refreshMode** 設定。

呼叫 `Invoke-DscResource` Cmdlet 時，您可使用 **Method** 參數來指定要呼叫的方法或函式。 您指定資源的屬性，方法是將雜湊表作為 **Property** 參數值加以傳遞。

直接呼叫資源方法的範例如下︰

## <a name="ensure-a-file-is-present"></a>請確定檔案存在

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>請測試檔案存在

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>請取得檔案的內容

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>[!NOTE]
> 不支援直接呼叫複合資源方法。 請改為呼叫組成複合資源之基礎資源的方法。

## <a name="see-also"></a>另請參閱

- [撰寫自訂的 DSC 資源與 MOF](../resources/authoringResourceMOF.md)
- [使用 PowerShell 類別撰寫自訂的 DSC 資源](../resources/authoringResourceClass.md)
- [對 DSC 資源執行偵錯](../troubleshooting/debugResource.md)
