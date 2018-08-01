---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268294"
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>概要

在 IIS 中設定 Windows PowerShell Web 存取 Web 應用程式。

## <a name="syntax"></a>語法

### <a name="default"></a>Default
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>描述

**Install-PswaWebApplication** Cmdlet 會設定 Windows PowerShell Web 存取 Web 應用程式。
此 Cmdlet 會安裝 Web 應用程式、將它與網站建立關聯，並選擇性地使用 **useTestCertificate** 參數建立測試 SSL 憑證。 為了安全起見，網站管理員不應該將測試憑證用於生產環境。

## <a name="parameters"></a>參數

### <a name="-usetestcertificate"></a>-UseTestCertificate

指定建立測試憑證。 如果這個參數設定為 true，則此 Cmdlet 會建立測試憑證，並設定 Windows PowerShell Web 存取 Web 應用程式針對 HTTPS 要求使用憑證。 如果這個參數設定為 false，則不會建立憑證或繫結。 如果使用其他憑證進行 Windows PowerShell Web 存取，請將此值設定為 false。

|||
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 具名                                |
| 預設值                        | true                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-webapplicationname"></a>-WebApplicationName

指定 Web 應用程式的名稱。 這會顯示為 Windows PowerShell Web 存取 URL 的最後一部分。

|||
|-|-|
| 別名                              | 無                                 |
| 必要？                            | false                                |
| 位置？                            | 1                                    |
| 預設值                        | pswa                                 |
| 接受管線輸入？               | false                                |
| 接受萬用字元？          | false                                |

### <a name="-websitename"></a>-WebSiteName

指定要安裝此 Windows PowerShell Web 存取 Web 應用程式之網頁伺服器 (IIS) 網站的名稱。

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

這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。 如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216)。

## <a name="inputs"></a>輸入

此 Cmdlet 不會接受任何輸入。

## <a name="outputs"></a>輸出

此 Cmdlet 不會產生任何輸出。

## <a name="examples"></a>範例

### <a name="example-1"></a>範例 1

此範例會使用 **WebApplicationName** (*pswa*) 和 **WebSiteName** (預設網站) 參數的預設值，來安裝 PSWA Web 應用程式。

```
Install-PswaWebApplication
```

### <a name="example-2"></a>範例 2

此範例會使用 **WebApplicationName** 和 **WebSiteName** 參數的預設值，來安裝具有測試憑證的 PSWA Web 應用程式。

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>相關主題

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)