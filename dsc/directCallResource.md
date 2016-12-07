---
title: "直接呼叫 DSC 資源方法"
ms.date: 2016-05-16
keywords: "PowerShell，DSC"
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 97d97a36830088d6ee1296cda5310e087fc41893
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="calling-dsc-resource-methods-directly"></a>直接呼叫 DSC 資源方法

>適用於：Windows PowerShell 5.0

您可以使用 [Invoke DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) Cmdlet，直接呼叫 DSC 資源的函數或方法 (MOF 形式資源的 **Get-TargetResource**、**Set-TargetResource** 以及 **Test-TargetResource** 函數，或是類別形式資源的 **Get**、**Set** 與 **Test** 方法)。 這類方法適用於協力廠商想要使用 DSC 資源時，或是作為開發資源的有力工具。 

這個 Cmdlet 通常搭配中繼設定屬性 `refreshMode = 'Disabled'` 一起使用，但可用於任何 **refreshMode** 設定。

呼叫 **Invoke DscResource** Cmdlet 時，可以使用 **Method** 參數來指定要呼叫的方法或函數。 您指定資源的屬性，方法是將雜湊表作為 **Property** 參數值加以傳遞。

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

>**注意︰** 不支援直接呼叫複合資源方法。 請改為呼叫組成複合資源之基礎資源的方法。

## <a name="see-also"></a>另請參閱
- [撰寫自訂的 DSC 資源與 MOF](authoringResourceMOF.md) 
- [使用 PowerShell 類別撰寫自訂的 DSC 資源](authoringResourceClass.md)
- [對 DSC 資源執行偵錯](debugResource.md)

