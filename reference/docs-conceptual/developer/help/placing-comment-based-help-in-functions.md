---
title: 在函式中放置以批註為基礎的協助 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367777"
---
# <a name="placing-comment-based-help-in-functions"></a>將註解型說明置於函式

本主題說明如何為函式放置以批註為基礎的協助，讓 `Get-Help` Cmdlet 將以批註為基礎的說明主題與正確的函式產生關聯。

## <a name="where-to-place-comment-based-help-for-a-function"></a>要在何處放置函式以批註為基礎的說明

- 在函式主體的開頭。

- 在函式主體的結尾。

- `Function` 關鍵字之前。 當函式在腳本或腳本模組中時，以批註為基礎的說明和 `Function` 關鍵字的最後一行之間不能有一個以上的空白行。 否則，`Get-Help` 會將說明與腳本建立關聯，而不是與函式相關聯。

## <a name="examples-of-help-placement-in-a-function"></a>說明放置在函式中的範例

 下列範例會顯示函式之以批註為基礎之說明的三個放置選項。

### <a name="help-at-the-beginning-of-a-function-body"></a>函式主體開頭的說明

 下列範例會顯示在函式主體開頭的以批註為基礎。

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

### <a name="help-at-the-end-of-a-function-body"></a>函式主體結尾的說明

 下列範例會顯示以批註為基礎的函式主體結尾。

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

 下列範例會根據函式關鍵字前面的一行來顯示批註。

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```