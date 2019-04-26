---
title: 函式中放置註解型說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083190"
---
# <a name="placing-comment-based-help-in-functions"></a>將註解型說明置於函式

本主題說明函式的註解型說明的位置，讓`Get-Help`cmdlet 關聯正確的函式中的註解為基礎的 [說明] 主題。

## <a name="where-to-place-comment-based-help-for-a-function"></a>函式的註解型說明的位置

- 函式主體的開頭。

- 在函式主體結束。

- 之前`Function`關鍵字。 指令碼或指令碼模組中函式時，不能有一個以上的空白行之間最後一行的註解型說明和`Function`關鍵字。 否則，`Get-Help`產生關聯的說明，使用指令碼，而非與函式。

## <a name="examples-of-help-placement-in-a-function"></a>說明放置函式中的範例

 下列範例會顯示每個函式的註解型說明的三個的放置選項。

### <a name="help-at-the-beginning-of-a-function-body"></a>協助在函式主體的開頭

 下列範例會示範註解為基礎的函式主體開頭。

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

### <a name="help-at-the-end-of-a-function-body"></a>協助函式主體的結尾

 下列範例會示範註解為基礎，函式主體的結尾。

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

### <a name="help-before-the-function-keyword"></a>在 Function 關鍵字前面說明

 下列範例顯示在 function 關鍵字前面的行註解為基礎。

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```