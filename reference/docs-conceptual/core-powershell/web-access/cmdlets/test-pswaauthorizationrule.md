---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>概要

確認是否有指定使用者、電腦或端點的規則。

## <a name="syntax"></a>語法

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>描述

**Test-PswaAuthorizationRule** Cmdlet 會確認是否有指定使用者、電腦或端點的規則。
此 Cmdlet 也可用來測試授權規則，以驗證特定使用者、電腦或端點存取要求是否已獲授權。
根據預設，此 Cmdlet 會評估授權檔案中的所有規則。
不過，您可以指定要測試的規則子集。

您可以使用此 Cmdlet 來為驗證失敗進行疑難排解。

此 Cmdlet 的參數會對應至 Windows PowerShell® Web 存取登入頁面上的欄位。

## <a name="parameters"></a>參數

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;String&gt;

指定要測試的元件名稱。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | true                                 |
| 位置？                            | 2                                    |
| 預設值                        | 無                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;String&gt;

指定要測試的 Windows PowerShell 工作階段設定名稱，也稱為端點或 Runspace。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 3                                    |
| 預設值                        | 無                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;Uri&gt;

指定要測試的連線 URI。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | true                                 |
| 位置？                            | 2                                    |
| 預設值                        | 無                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

指定您要用來測試 Windows PowerShell Web 存取授權規則之使用者帳戶的 **PSCredential** 物件。 如果您未新增這個參數，此 Cmdlet 就會使用目前登入的使用者帳戶。 若要取得從遠端測試授權規則所需的 **PSCredential** 物件，請執行 [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) Cmdlet。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | 無                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

指定要測試的規則子集。 如果未指定這個參數，則此 Cmdlet 會測試所有授權規則。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | 無                                 |
| 接受管線輸入？               | True (ByValue)                       |
| 接受萬用字元？          | false                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;String&gt;

指定要測試的使用者名稱。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | true                                 |
| 位置？                            | 1                                    |
| 預設值                        | 無                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。
如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。

## <a name="inputs"></a>輸入

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

此 Cmdlet 會接受 PswaAuthorizationRule 物件的陣列作為輸入。

## <a name="outputs"></a>輸出

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

此 Cmdlet 會產生 PswaAuthorizationRule 物件的陣列作為輸出。

## <a name="examples"></a>範例

### <a name="example-1"></a>範例 1

此範例會測試所有授權規則，以顯示允許使用者 *contoso\\mhanson* 連線到電腦 *srv2* 並使用名為 *test* 之 Windows PowerShell 工作階段設定的所有規則。

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>範例 2

此範例會測試所有授權規則，以確認哪些授權規則適用於使用者 *contoso\\mhanson*。

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>相關主題

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
