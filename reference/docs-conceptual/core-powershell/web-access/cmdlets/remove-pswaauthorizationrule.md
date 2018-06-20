---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189028"
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>概要

從 Windows PowerShell® Web 存取移除指定的授權規則。

## <a name="syntax"></a>語法

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>規則
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>描述

從 Windows PowerShell Web 存取中移除指定的授權規則。

## <a name="parameters"></a>參數

### <a name="-force"></a>-Force

在不提示確認的情況下執行 Cmdlet。 根據預設，此 Cmdlet 會先要求確認，再繼續進行。

|||
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | 無                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

指定要移除之一或多個規則的識別碼。

|||
|-|-|
| 別名                              | 無                                 |
| 必要？                            | true                                 |
| 位置？                            | 2                                    |
| 預設值                        | 無                                 |
| 接受管線輸入？               | True (ByValue, ByPropertyName)       |
| 接受萬用字元？          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

指定要移除的規則。

|||
|-|-|
| 別名                              | 無                                 |
| 必要？                            | true                                 |
| 位置？                            | 2                                    |
| 預設值                        | 無                                 |
| 接受管線輸入？               | True (ByValue)                       |
| 接受萬用字元？          | false                                |

### <a name="-confirm"></a>-Confirm

執行 Cmdlet 之前先提示您確認。

|||
|-|-|
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | false                                |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-whatif"></a>-WhatIf

顯示執行 Cmdlet 後會發生的情況。 未執行 Cmdlet。

|||
|-|-|
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | false                                |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。
如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。

## <a name="inputs"></a>輸入

### <a name="int"></a>int\[\]

此 Cmdlet 會接受整數陣列或 PswaAuthorizationRule 物件的陣列。

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

此 Cmdlet 會接受整數陣列或 PswaAuthorizationRule 物件的陣列。

## <a name="outputs"></a>輸出

此 Cmdlet 不會產生任何輸出。

## <a name="examples"></a>範例

### <a name="example-1"></a>範例 1

此範例會移除識別碼為 *2* 的授權規則。

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>範例 2 {#example-2 .subHeading}

此範例會移除所有授權規則，也會要求使用者確認。

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>相關主題

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)