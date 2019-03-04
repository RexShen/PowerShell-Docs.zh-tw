---
title: 如何匯入使用模組的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859144"
---
# <a name="how-to-import-cmdlets-using-modules"></a>如何使用模組來匯入 Cmdlet

本主題描述如何使用二進位模組匯入 cmdlet 的 Windows PowerShell 工作階段。

> [!NOTE]
> 模組的成員可以包括 cmdlet、 提供者、 函式、 變數、 別名及更多。 嵌入式管理單元可以包含 cmdlet 和提供者。

## <a name="how-to-load-cmdlets-using-a-module"></a>如何將使用模組的 cmdlet

1. 建立組件檔案中的 cmdlet 會實作為具有相同名稱的模組資料夾。 在此程序，在中建立的模組資料夾`system32`資料夾。

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. 請確定`PSModulePath`環境變數包含在新的模組資料夾的路徑。 根據預設，[系統] 資料夾已新增至`PSModulePath`環境變數。

3. 將指令程式組件複製到模組資料夾中。

4. 執行下列命令以將 cmdlet 新增至工作階段：

   `import-module [Module_Name]`

   此程序可用來測試您的 cmdlet。 它會在工作階段的組件新增的所有 cmdlet。 如需有關模組的詳細資訊，請查看不同類型的模組，不同的方式載入模組，以及如何限制會匯出模組的項目[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[安裝模組](../module/installing-a-powershell-module.md)