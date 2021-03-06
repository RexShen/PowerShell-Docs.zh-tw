---
ms.date: 09/13/2016
ms.topic: reference
title: 顯示錯誤資訊
description: 顯示錯誤資訊
ms.openlocfilehash: 37a3adb91d0e616a5c7f27bcab866f8da139f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653050"
---
# <a name="displaying-error-information"></a>顯示錯誤資訊

本主題討論使用者可以顯示錯誤資訊的方式。

當您的 Cmdlet 遇到錯誤時，錯誤資訊的呈現方式預設會類似下列錯誤輸出。

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

不過，使用者可以藉由將變數設定為，以依分類來查看錯誤 `$ErrorView` `"CategoryView"` 。 類別目錄檢視會顯示錯誤記錄中的特定資訊，而不是錯誤的任意文字描述。 如果您有一長串要掃描的錯誤，此視圖會很有用。 在類別目錄檢視中，先前的錯誤訊息會顯示如下。

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

如需有關錯誤類別的詳細資訊，請參閱 [Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
