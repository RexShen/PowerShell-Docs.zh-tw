---
description: 描述 PowerShell 中的完整和相對路徑名稱格式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: b58fdd62803bfb654c9c69acda390d63341aacd9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207840"
---
# <a name="about-path-syntax"></a>關於路徑語法

## <a name="short-description"></a>簡短描述
描述 PowerShell 中的完整和相對路徑名稱格式。

## <a name="long-description"></a>詳細描述

可透過 PowerShell 提供者存取之資料存放區中的所有專案，都可以透過其路徑名稱來唯一識別。 路徑名稱是專案名稱、專案所在的容器和子容器的組合，以及用來存取容器的 PowerShell 磁片磁碟機。

在 PowerShell 中，路徑名稱分為兩種類型：完整和相對。 完整路徑名稱由組成路徑的所有元素組成。 下列語法顯示完整路徑名稱中的元素：

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

\<provider\>預留位置是指您用來存取資料存放區的 PowerShell 提供者。 例如，FileSystem 提供者可讓您存取電腦上的檔案和目錄。 這個語法的元素是選擇性的，而且永遠不需要，因為磁片磁碟機名稱在所有提供者中都是唯一的。

\<drive\>預留位置是指特定 powershell 提供者所支援的 powershell 磁片磁碟機。 在 FileSystem 提供者的情況下，PowerShell 磁片磁碟機對應至您系統上設定的 Windows 磁片磁碟機。 例如，如果您的系統包含 A：磁片磁碟機和 C：磁片磁碟機，FileSystem 提供者會在 PowerShell 中建立相同的磁片磁碟機。

指定磁片磁碟機之後，您必須指定包含該專案的任何容器和子容器。 您必須以它們存在於資料存放區中的階層順序來指定容器。 換句話說，您必須從父容器開始，然後是父容器中的子容器，依此類推。 此外，每個容器的前面都必須加上反斜線。  (請注意，PowerShell 可讓您使用正斜線來與其他 PowerShells 相容。 ) 

指定容器和子容器之後，您必須提供專案名稱，並在前面加上反斜線。 例如，C： \\ Windows System32 目錄中 Shell.dll 檔案的完整路徑名稱如下所示 \\ ：

```powershell
C:\Windows\System32\Shell.dll
```

在此情況下，用於存取容器的磁片磁碟機為 C：磁片磁碟機、最上層容器是 Windows、subcontainer 是位於 Windows 容器) 內的 System32 (，且該專案 Shell.dll。

在某些情況下，您不需要指定完整路徑名稱，而可以改為使用相對路徑名稱。 相對路徑名稱是根據目前的工作位置。 PowerShell 可讓您根據目前工作位置的相對位置來識別專案。 您可以使用特殊字元來指定相對路徑名稱。 下表說明每個字元，並提供相對路徑名稱和完整路徑名稱的範例。 資料表中的範例是以目前正在設定為 C:\windows。的工作目錄為基礎。

|符號|描述               |相對路徑    |完整路徑          |
|------|--------------------------|-----------------|-------------------|
|.     |目前的位置          |.\\系統        |c： \\ Windows \\ 系統|
|..    |目前位置的父系|..\\Program Files|c： \\ Program Files  |
|\     |目前的磁片磁碟機根目錄     |\\Program Files  |c： \\ Program Files  |
|      |location                  |                 |                   |
|以上|沒有特殊字元     |系統           |c： \\ Windows \\ 系統|

當您在命令中使用路徑名稱時，您可以使用完整路徑名稱或相對路徑名稱的相同方式來輸入該名稱。 例如，假設您目前的工作目錄是 C:\windows。 下列 Get-ChildItem 命令會捕獲 C:\Techdocs 目錄中的所有專案：

```powershell
Get-ChildItem \techdocs
```

反斜線表示應該使用目前工作位置的磁片磁碟機根目錄。 因為工作目錄是 C： \\ Windows，磁片磁碟機根目錄是 c：磁片磁碟機。 因為 techdocs 目錄位於根目錄，所以您只需要指定反斜線。

您可以使用下列命令來達到相同的結果：

```powershell
Get-ChildItem c:\techdocs
```

無論您使用的是完整路徑名稱或相對路徑名稱，路徑名稱都不是唯一的，因為它會找出一個專案，但也是因為它會唯一識別該專案，即使該專案與其他容器中的另一個專案共用相同的名稱。

比方說，假設您有兩個名為 Results.txt 的檔案。
第一個檔案位於名稱為 C： Techdocs Jan 的目錄中 \\ \\ ，而第二個檔案則位於名稱為 c： Techdocs 的目錄中 \\ \\ 。第一個檔案的路徑名稱 (C： \\ Techdocs \\ Jan \\Results.txt) 和第二個檔案的路徑名稱 (c： \\ Techdocs \\ 二月Results.txt) \\ 可讓您清楚區分這兩個檔案。

## <a name="see-also"></a>另請參閱

[about_Locations](about_Locations.md)
