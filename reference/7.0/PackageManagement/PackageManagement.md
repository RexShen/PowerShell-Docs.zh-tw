---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113634
Help Version: 7.0.1.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 01b1bce187cd0526e56abc812f91b44a2c022a29
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890850"
---
# PackageManagement 模組

## 說明

本主題顯示套件管理 Cmdlet 的說明主題。

> [!IMPORTANT]
> 從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。 如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。 使用下列命令，以確保您使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。

## PackageManagement Cmdlet

### [Find-Package](Find-Package.md)
尋找可用套件來源中的軟體套件。

### [Find-PackageProvider](Find-PackageProvider.md)
傳回可供安裝的套件管理封裝提供者的清單。

### [Get-Package](Get-Package.md)
傳回與 **PackageManagement** 一起安裝的所有軟體套件清單。

### [Get-PackageProvider](Get-PackageProvider.md)
傳回連接到套件管理的封裝提供者清單。

### [Get-PackageSource](Get-PackageSource.md)
取得為封裝提供者註冊的封裝來源清單。

### [Import-PackageProvider](Import-PackageProvider.md)
將套件管理封裝提供者加入至目前的會話。

### [Install-Package](Install-Package.md)
安裝一或多個軟體套件。

### [Install-PackageProvider](Install-PackageProvider.md)
安裝一或多個套件管理封裝提供者。

### [Register-PackageSource](Register-PackageSource.md)
加入指定套件提供者的套件來源。

### [Save-Package](Save-Package.md)
將封裝儲存到本機電腦，而不進行安裝。

### [Set-PackageSource](Set-PackageSource.md)
取代指定封裝提供者的封裝來源。

### [Uninstall-Package](Uninstall-Package.md)
卸載一或多個軟體套件。

### [Unregister-PackageSource](Unregister-PackageSource.md)
移除已註冊的套件來源。
