---
title: 顯示錯誤資訊 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e542110e9c35a74c5d4c112b0a831f7f8ad9242e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774570"
---
# <a name="displaying-error-information"></a>顯示錯誤資訊

本主題討論使用者可以顯示錯誤資訊的方式。

當您的 Cmdlet 遇到錯誤時，根據預設，錯誤資訊的呈現會類似下列錯誤輸出。

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

不過，使用者可以藉由將變數設定為，依類別來查看錯誤 `$ErrorView` `"CategoryView"` 。 類別目錄檢視會顯示錯誤記錄中的特定資訊，而不是錯誤的任意文字描述。 如果您有很長的錯誤清單要掃描，這個視圖會很有用。 在 [類別目錄] 視圖中，先前的錯誤訊息會顯示如下。

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

如需錯誤類別目錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
