---
title: 顯示錯誤資訊 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369967"
---
# <a name="displaying-error-information"></a>顯示錯誤資訊

本主題討論使用者可以顯示錯誤資訊的方式。

當您的 Cmdlet 遇到錯誤時，根據預設，錯誤資訊的呈現會類似下列錯誤輸出。

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

不過，使用者可以藉由將 `$ErrorView` 變數設定為 `"CategoryView"`，來依分類來查看錯誤。 類別目錄檢視會顯示錯誤記錄中的特定資訊，而不是錯誤的任意文字描述。 如果您有很長的錯誤清單要掃描，這個視圖會很有用。 在 [類別目錄] 視圖中，先前的錯誤訊息會顯示如下。

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

如需錯誤類別目錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
