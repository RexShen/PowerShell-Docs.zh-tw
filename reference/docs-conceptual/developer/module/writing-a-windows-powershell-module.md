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
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360617"
---
# <a name="writing-a-windows-powershell-module"></a>撰寫 Windows PowerShell 模組

本檔是針對需要封裝和散佈其 Windows PowerShell Cmdlet 的系統管理員、腳本開發人員和 Cmdlet 開發人員所撰寫。 藉由使用 Windows PowerShell 模組，您可以封裝和散發您的 Windows PowerShell 解決方案，而不需要使用已編譯的語言。

Windows PowerShell 模組可讓您將 Windows PowerShell 程式碼分割、組織及抽象化成獨立、可重複使用的單位。 有了這些可重複使用的單位，您就可以輕鬆地直接與其他人共用您的模組。 如果您是腳本開發人員，也可以重新封裝協力廠商模組，以建立自訂的腳本架構應用程式。 模組與其他指令碼語言（例如 Perl 和 Python）中的模組類似，可讓生產環境準備好使用可轉散發元件的腳本解決方案，還有額外的優點可讓您將多個元件重新封裝並抽象化至建立自訂解決方案。

在最基本的情況下，Windows PowerShell 會將儲存在 .psm1 檔案中的任何有效 Windows PowerShell 腳本程式碼視為模組。 PowerShell 也會自動將任何二元 Cmdlet 元件視為模組。 不過，您也可以使用模組（或更明確地說，模組資訊清單）將整個解決方案組合在一起。 下列案例說明 Windows PowerShell 模組的一般用法。

### <a name="libraries"></a>媒體櫃

模組可以用來封裝和散發執行一般工作的功能緊密程式庫。 一般而言，這些函式的名稱會共用一或多個名詞，以反映它們所用的一般工作。 這些函式也可以與 .NET Framework 類別類似，因為它們可以有公用和私用成員。 例如，程式庫可以包含一組用於檔案傳輸的函數。 在此情況下，反映一般工作的名詞可能是 "file"。

### <a name="configuration"></a>設定

您可以藉由新增特定的 Cmdlet、提供者、函式和變數，使用模組來自訂您的環境。

### <a name="compiled-code-development-and-distribution"></a>已編譯的程式碼開發和散發

Cmdlet 和提供者開發人員可以使用模組來測試和散佈其已編譯的程式碼，而不需要建立嵌入式管理單元。他們可以將包含已編譯器代碼的元件匯入為模組（二進位模組），而不需要建立及註冊嵌入式管理單元。

## <a name="see-also"></a>另請參閱

[瞭解 Windows PowerShell 模組](./understanding-a-windows-powershell-module.md)

[如何撰寫 PowerShell 腳本模組](./how-to-write-a-powershell-script-module.md)

[如何撰寫 PowerShell 二進位模組](./how-to-write-a-powershell-binary-module.md)

[如何撰寫 PowerShell 模組資訊清單](how-to-write-a-powershell-module-manifest.md)

[修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)

[匯入 PowerShell 模組](./importing-a-powershell-module.md)

[安裝 PowerShell 模組](./installing-a-powershell-module.md)
