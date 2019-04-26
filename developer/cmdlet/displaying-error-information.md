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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068278"
---
# <a name="displaying-error-information"></a>顯示錯誤資訊

本主題討論使用者可以在其中顯示錯誤資訊的方式。

Cmdlet 會發生錯誤，錯誤資訊的呈現方式，根據預設，看起來像下列的錯誤輸出。

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

不過，使用者可以檢視錯誤依分類 splittunneling`$ErrorView`變數設為`"CategoryView"`。 類別目錄檢視會顯示從錯誤記錄，而不是錯誤的任意文字描述的特定資訊。 此檢視可能很有用，如果您有一長串的掃描錯誤。 在類別目錄檢視中，先前的錯誤訊息隨即出現，如下所示。

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

如需有關錯誤類別目錄的詳細資訊，請參閱[Windows PowerShell 的錯誤記錄](./windows-powershell-error-records.md)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
