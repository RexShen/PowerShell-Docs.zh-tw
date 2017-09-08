---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 43997320ec7ab779b2061a0af88f97db0b7e93d6
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2017
---
#  <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

##  <a name="synopsis"></a>概要

傳回一組 Windows PowerShell® Web 存取授權規則。

##  <a name="syntax"></a>語法

###  <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

###  <a name="name"></a>名稱
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>描述

**Get-PswaAuthorizationRule** Cmdlet 會傳回一組 Windows PowerShell® Web 存取授權規則。
如果未指定 **Id** 參數和 **RuleName** 參數，則此 Cmdlet 會列出所有規則。 **Id** 參數可用來篩選結果。

## <a name="parameters"></a>參數

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

指定此 Cmdlet 應該會取得之規則的識別碼。 如果未指定任何識別碼，此 Cmdlet 會傳回所有授權規則。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 2                                    |
| 預設值                        | 無                                 |
| 接受管線輸入？               | True (ByValue, ByPropertyName)       |
| 接受萬用字元？          | false                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String\[\]&gt;

指定要擷取之授權規則的名稱。 此參數會傳回完全符合此陣列中字串之規則名稱的任何規則。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | true                                 |
| 位置？                            | 2                                    |
| 預設值                        | 無                                 |
| 接受管線輸入？               | True (ByValue, ByPropertyName)       |
| 接受萬用字元？          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。
如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。

## <a name="inputs"></a>輸入

###  <a name="int"></a>int\[\]

此 Cmdlet 會接受整數陣列或字串值陣列作為輸入。

###  <a name="string"></a>String\[\]

此 Cmdlet 會接受整數陣列或字串值陣列作為輸入。

##  <a name="outputs"></a>輸出

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

此 Cmdlet 會產生 PswaAuthorizationRule 物件作為輸出。


## <a name="examples"></a>範例

### <a name="example-1"></a>範例 1

此範例會取得所有規則。

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>範例 2

此範例會取得識別碼為 *2* 的規則。

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>範例 3 {#example-3 .subHeading}

此範例示範該 Cmdlet 如何接受來自管線的值。
此 Cmdlet 會傳遞規則識別碼和規則名稱。

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

##  <a name="related-topics"></a>相關主題

-  [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
-  [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
-  [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
-  [Install-PswaWebApplication](install-pswawebapplication.md)
