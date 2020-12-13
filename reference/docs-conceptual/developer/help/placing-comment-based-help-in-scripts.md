---
ms.date: 09/12/2016
ms.topic: reference
title: 將註解型說明置於指令碼
description: 將註解型說明置於指令碼
ms.openlocfilehash: b0d32b7ab063269085899a643b0c3a17da2073fc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645443"
---
# <a name="placing-comment-based-help-in-scripts"></a>將註解型說明置於指令碼

本主題說明如何為腳本放置以批註為基礎的說明，讓 `Get-Help` Cmdlet 將批註式說明主題與腳本產生關聯，而不是與腳本中可能的任何函式建立關聯。

## <a name="where-to-place-comment-based-help-for-a-script"></a>放置腳本 Comment-Based 說明的位置

- 指令檔的開頭。

  腳本說明可以在腳本中的前面加上批註和空白行。

- 指令檔的結尾。

  如果腳本主體中的第一個專案 (在 [說明]) 之後是函式宣告，則腳本說明和函式宣告的結尾必須至少有兩個空白行。 否則，說明會被視為函數的說明，而不是腳本的說明。

## <a name="examples-of-help-placement-in-a-script"></a>腳本中說明位置的範例

下列範例會顯示腳本的批註式說明的每個放置選項。

### <a name="help-at-the-beginning-of-a-script"></a>腳本開頭的說明

下列範例顯示以批註為基礎的腳本開頭。

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>腳本結尾的說明

 下列範例顯示以批註為基礎的腳本結尾。

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```
