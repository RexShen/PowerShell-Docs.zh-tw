---
ms.date: 2017-10-17
contributor: keithb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Save-Script
ms.openlocfilehash: b54e8ba074b7cadd52df781c9021332ccc90f9fd
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2017
---
# <a name="save-script"></a>Save-Script

Save-Script Cmdlet 可讓您將指令碼檔案儲存到指定的位置，藉以檢閱指令碼檔案。

## <a name="description"></a>描述

Save-Script Cmdlet 會儲存指定的指令碼。

## <a name="cmdlet-syntax"></a>Cmdlet 語法

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet 線上說明參考資料

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>範例命令

### <a name="example-1-save-a-script-from-a-repository"></a>範例 1︰儲存存放庫中的指令碼
這個命令會將 GalleryINT 存放庫中之指令碼 Fabrikam-ClientScript 的最新版本儲存至本機資料夾 C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>範例 2：從 Find-Script Cmdlet 傳送以儲存指令碼版本

第一個命令會尋找 GalleryINT 存放庫中是否有 1.5 版的 Fabrikam-ClientScript，並將它儲存至資料夾 C:\ScriptSharingDemo

第二個命令會驗證已儲存的指令碼中繼資料。

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a>範例 3：儲存存放庫中指令碼的發行前版本
這個命令會將 GalleryINT 存放庫中之指令碼 Fabrikam-ClientScript 的最新版本儲存至本機資料夾 C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```

