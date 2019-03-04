---
title: 在 指令碼中放置註解型說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860764"
---
# <a name="placing-comment-based-help-in-scripts"></a>將註解型說明置於指令碼

本主題說明的指令碼的註解型說明的位置，讓`Get-Help`cmdlet 與指令碼而非與可能的指令碼中的任何函式，將註解為基礎的 [說明] 主題。

## <a name="where-to-place-comment-based-help-for-a-script"></a>如需指令碼的註解型說明的位置

- 在指令碼檔案開頭。 指令碼說明可以是指令碼中僅前面加上註解和空白的行。

- 在指令碼檔案的結尾。

  如果函式宣告 （之後的說明） 的指令碼主體中的第一個項目，必須有至少兩個空白的行之間的指令碼說明函式宣告。 否則，說明會解譯為所說明的函式而言不指令碼的說明。

## <a name="examples-of-help-placement-in-a-script"></a>在指令碼中的說明位置的範例

 下列範例會顯示每個指令碼的註解型說明的放置選項。

### <a name="help-at-the-beginning-of-a-script"></a>協助在指令碼的開頭

 下列範例會示範註解為基礎的指令碼開頭。

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>在指令碼結尾處的協助

 下列範例會示範註解為基礎的指令碼結尾。

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```