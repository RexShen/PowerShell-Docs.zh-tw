---
ms.date: 09/12/2016
ms.topic: reference
title: 將註解型說明置於函式
description: 將註解型說明置於函式
ms.openlocfilehash: 3bd72f0c71d8f6ad54c43c99f044423c072fdeeb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658198"
---
# <a name="placing-comment-based-help-in-functions"></a>將註解型說明置於函式

本主題說明如何為函式放置以批註為基礎的說明，讓 `Get-Help` Cmdlet 將批註式說明主題與正確的函式產生關聯。

## <a name="where-to-place-comment-based-help-for-a-function"></a>放置函式 Comment-Based 說明的位置

- 在函數主體的開頭。

- 在函數主體的結尾。

- 關鍵字之前 `Function` 。 當函式在腳本或腳本模組中時，以批註為基礎的說明和關鍵字的最後一行之間不能有一個以上的空白行 `Function` 。 否則，請 `Get-Help` 將說明與腳本產生關聯，而不是使用函數。

## <a name="examples-of-help-placement-in-a-function"></a>函數中說明位置的範例

下列範例會顯示函式之批註式說明的三個放置選項。

### <a name="help-at-the-beginning-of-a-function-body"></a>函數主體開頭的說明

下列範例顯示以批註為基礎的函式主體開頭。

```powershell
function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}
```

### <a name="help-at-the-end-of-a-function-body"></a>函數主體結尾的說明

 下列範例顯示以批註為基礎的函式主體結尾。

```powershell
function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}
```

### <a name="help-before-the-function-keyword"></a>Function 關鍵字之前的說明

 下列範例會根據 function 關鍵字之前的行，顯示批註。

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```
