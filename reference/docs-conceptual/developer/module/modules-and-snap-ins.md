---
ms.date: 09/13/2016
ms.topic: reference
title: 模組與嵌入式管理單元
description: 模組與嵌入式管理單元
ms.openlocfilehash: de4ff1de9a29b78d7783fe7ed0265f5516db1fb4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658676"
---
# <a name="modules-and-snap-ins"></a>模組與嵌入式管理單元

您可以使用 Windows PowerShell 2.0) 或嵌入式管理單元 (引進的模組，將 Cmdlet 新增至會話。一旦將指令程式新增至會話，它就可以由主應用程式以程式設計方式執行，或在命令列以互動方式執行。

基於下列原因，建議您使用模組作為將 Cmdlet 新增至會話的傳遞方法：

- 模組可讓您藉由載入已定義 Cmdlet 的元件來新增 Cmdlet。 不需要執行嵌入式管理單元類別。

- 模組可讓您新增其他資源，例如變數、函式、腳本、類型和格式化檔案等等。

- 嵌入式管理單元只能用來將 Cmdlet 和提供者新增至會話。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](writing-a-windows-powershell-module.md)

[撰寫 Windows PowerShell Cmdlet](../cmdlet/cmdlet-overview.md)
