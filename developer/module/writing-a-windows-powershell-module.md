---
title: 撰寫 Windows PowerShell 模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082051"
---
# <a name="writing-a-windows-powershell-module"></a>撰寫 Windows PowerShell 模組

這份文件會寫入系統管理員、 指令碼的開發人員，和指令程式的開發人員必須封裝並散發其 Windows PowerShell cmdlet。 您可以藉由使用 Windows PowerShell 模組，來封裝及散發您的 Windows PowerShell 解決方案，而不使用已編譯的語言。

Windows PowerShell 模組可讓您將資料分割、 組織和擷取成獨立、 可重複使用單位的 Windows PowerShell 程式碼。 使用這些可重複使用的單位，您可以輕鬆地共用您的模組，直接與其他人。 如果您是指令碼開發人員，您也可以重新封裝來建立自訂指令碼為基礎的應用程式的第三方模組。 模組，類似於在其他指令碼的語言，例如 Perl 及 Python，模組可讓備妥可重複使用、 可轉散發套件的元件，使用額外的好處是讓您重新封裝並擷取多個元件的指令碼解決方案建立自訂解決方案。

在其最基本功能，Windows PowerShell 會將儲存為模組為.psm1 檔案中任何有效 Windows PowerShell 指令碼。 PowerShell 也會自動將視為二進位 cmdlet 中的任何組件的模組。 不過，您也可以使用模組 （或更具體來說，模組資訊清單） 組合在一起的整個解決方案。 下列案例描述 Windows PowerShell 模組的一般用法。

### <a name="libraries"></a>程式庫

模組可以用來封裝及散發一致的程式庫執行常見工作的函式。 一般而言，這些函式的名稱會共用反映使用中的常見工作的一或多個名詞。 這些函式也可以與.NET Framework 類別類似，因為它們可以有公用和私用成員。 比方說，程式庫可以包含一組函式檔案傳輸。 在此情況下，名詞反映常見的工作可能是"file"。

### <a name="configuration"></a>設定

模組可用來新增特定 cmdlet、 提供者、 函數和變數來自訂您的環境。

### <a name="compiled-code-development-and-distribution"></a>已編譯程式碼開發和散佈

Cmdlet 和提供者的開發人員可以使用模組來測試和發佈其已編譯的程式碼，而不需要建立的嵌入式管理單元。他們可以匯入包含已編譯的程式碼為 （二進位模組） 模組的組件，而不需要建立並註冊的嵌入式管理單元。

## <a name="see-also"></a>另請參閱

[了解 Windows PowerShell 模組](./understanding-a-windows-powershell-module.md)

[如何撰寫 PowerShell 指令碼模組](./how-to-write-a-powershell-script-module.md)

[如何撰寫 PowerShell 二進位模組](./how-to-write-a-powershell-binary-module.md)

[如何撰寫 PowerShell 模組資訊清單](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)

[匯入 PowerShell 模組](./importing-a-powershell-module.md)

[安裝 PowerShell 模組](./installing-a-powershell-module.md)
