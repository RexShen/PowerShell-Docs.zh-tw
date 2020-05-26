---
title: 模組和嵌入式管理單元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: b3d8209ea7e3e8353e73ebce1531991ec9519c74
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811657"
---
# <a name="modules-and-snap-ins"></a>模組與嵌入式管理單元

您可以使用模組（由 Windows PowerShell 2.0 引進）或嵌入式管理單元，將 Cmdlet 新增至會話。一旦將 Cmdlet 新增至會話，它就可以由主應用程式以程式設計方式執行，或在命令列以互動方式執行。

基於下列原因，建議您使用模組做為將 Cmdlet 新增至會話的傳遞方法：

- 模組可讓您藉由載入定義 Cmdlet 的元件來新增 Cmdlet。 不需要執行嵌入式管理單元類別。

- 模組可讓您新增其他資源，例如變數、函式、腳本、類型和格式檔案等等。

- 嵌入式管理單元只能用來將 Cmdlet 和提供者新增至會話。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](writing-a-windows-powershell-module.md)

[撰寫 Windows PowerShell Cmdlet](../cmdlet/cmdlet-overview.md)
