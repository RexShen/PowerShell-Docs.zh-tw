---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: cc54c94426d754ff2d3bf658e3e92083f02cd6c7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

## <a name="synopsis"></a>概要

解除安裝 Windows PowerShell® Web 應用程式。

## <a name="syntax"></a>語法

### <a name="default"></a>Default
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>描述

**Uninstall-PswaWebApplication** Cmdlet 會解除安裝 Windows PowerShell Web 應用程式並從 IIS 移除網站。 此 Cmdlet 不會解除安裝 IIS 或已安裝的任何其他功能，因為 Windows PowerShell 需要這些功能才能執行。

## <a name="parameters"></a>參數

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

表示已刪除 **Install\_PswaWebApplication** Cmdlet (搭配 **UseTestCertificate** 參數) 所建立的測試憑證。
只會移除與 **Install-PswaWebApplication** Cmdlet 所建立的測試憑證同名的測試憑證。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | true                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;String&gt;

指定要解除安裝的 Web 應用程式名稱。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 1                                    |
| 預設值                        | pswa                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;String&gt;

指定 Web 應用程式安裝所在的網站名稱。

|||  
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | 預設網站                     |
| 接受管線輸入？               | false                                |
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

顯示執行 Cmdlet 後會發生的情況。
未執行 Cmdlet。

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

此 Cmdlet 不會接受任何輸入。

## <a name="outputs"></a>輸出

此 Cmdlet 不會傳回任何輸出。

## <a name="examples"></a>範例

### <a name="example-1"></a>範例 1

此命令會解除安裝 Windows PowerShell Web 應用程式。
如果您使用預設值來安裝 Windows PowerShell Web 應用程式，則可以使用此 Cmdlet 將它解除安裝。

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>範例 2

此命令會解除安裝 Windows PowerShell Web 應用程式，並會刪除與應用程式建立關聯的測試憑證。
如果您使用預設值來安裝 Windows PowerShell Web 應用程式並建立測試憑證，則可以使用此 Cmdlet 將它解除安裝。

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>範例 3 {#example-3 .subHeading}

此命令會在安裝期間指定自訂網站和應用程式時，解除安裝 Windows PowerShell Web 應用程式。
此命令會移除名為 *MySite* 的網站及名為 *TestApplication* 的應用程式，並指定同時刪除與應用程式建立關聯的測試憑證。

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>相關主題

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
