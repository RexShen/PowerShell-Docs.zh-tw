---
description: 說明如何從 PowerShell 中的工作位置存取專案。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: ed8d17b7f217c86ba3161f017e2794524d5da829
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207628"
---
# <a name="about_locations"></a>about_Locations

## <a name="short-description"></a>簡短描述

說明如何從 PowerShell 中的工作位置存取專案。

## <a name="long-description"></a>詳細描述

目前的工作位置是命令指向的預設位置。
換句話說，如果您未提供指向受命令影響的專案或位置的明確路徑，則這是 PowerShell 所使用的位置。 在大部分情況下，目前的工作位置是透過 PowerShell FileSystem 提供者存取的磁片磁碟機，在某些情況下，則是該磁片磁碟機上的目錄。
例如，您可以將目前的工作位置設定為下列位置：

```powershell
C:\Program Files\Windows PowerShell
```

因此，除非明確提供另一個路徑，否則所有命令都會從這個位置處理。

即使磁片磁碟機不是目前磁片磁碟機，PowerShell 仍會維護每個磁片磁碟機目前的工作位置。 這可讓您只參考另一個位置的磁片磁碟機，從目前的工作位置存取專案。
例如，假設您目前的工作位置是 C： \\ Windows。 現在，假設您使用下列命令將目前的工作位置變更為 HKLM：磁片磁碟機：

```powershell
Set-Location HKLM:
```

雖然目前的位置現在是登錄磁片磁碟機，但您仍然可以 \\ 使用 c：磁片磁碟機存取 c： Windows 目錄中的專案，如下列範例所示：

```powershell
Get-ChildItem C:
```

PowerShell 會記住，該磁片磁碟機目前的工作位置是 Windows 目錄，因此它會從該目錄抓取專案。 如果您執行下列命令，結果會相同：

```powershell
Get-ChildItem C:\Windows
```

在 PowerShell 中，您可以使用 Get-Location 命令判斷目前的工作位置，也可以使用 Set-Location 命令來設定目前的工作位置。 例如，下列命令會將目前的工作位置設定為 C：磁片磁碟機的 Windows 目錄：

```powershell
Set-Location c:\windows
```

設定目前的工作位置之後，您仍然可以從其他磁片磁碟機存取專案，只要在命令中包含磁片磁碟機名稱 (後面加上冒號) 即可，如下列範例所示：

```powershell
Get-ChildItem HKLM:\software
```

範例命令會抓取登錄中 HKEY 本機電腦 hive 的 Software 容器中的專案清單。

PowerShell 也可讓您使用特殊字元來代表目前的工作位置和其父位置。 若要表示目前的工作位置，請使用單一句點。 若要表示目前工作位置的父系，請使用兩個句點。 例如，下列程式會指定目前工作位置中的系統子目錄：

```powershell
Get-ChildItem .\system
```

如果目前的工作位置是 C： \\ windows，此命令會傳回 c： windows 系統中所有專案的 \\ 清單 \\ 。 但是，如果您使用兩個句點，則會使用目前工作目錄的父目錄，如下列範例所示：

```powershell
Get-ChildItem ..\"program files"
```

在此情況下，PowerShell 會將兩個句點視為 C：磁片磁碟機，因此命令會抓取 C： Program Files 目錄中的所有專案 \\ 。

開頭為斜線的路徑會識別來自目前磁片磁碟機根目錄的路徑。 例如，如果您目前的工作位置是 C： \\ Program Files \\ PowerShell，則磁片磁碟機的根目錄是 c。因此，下列命令會列出 C： Windows 目錄中的所有專案 \\ ：

```powershell
Get-ChildItem \windows
```

如果您在提供容器或專案的名稱時，未指定以磁片磁碟機名稱、斜線或句號開頭的路徑，則會假設容器或專案位於目前的工作位置。 例如，如果您目前的工作位置是 C： \\ windows，則下列命令會傳回 c： \\ windows 系統目錄中的所有專案 \\ ：

```powershell
Get-ChildItem system
```

如果您指定檔案名而不是目錄名稱，則 PowerShell 會傳回該檔案的詳細資料， (假設該檔案位於目前工作位置) 。

## <a name="see-also"></a>另請參閱

[Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

[about_Providers](about_Providers.md)

[about_Path_Syntax](about_Path_Syntax.md)
