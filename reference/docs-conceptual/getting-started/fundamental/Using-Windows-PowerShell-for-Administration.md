---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用 Windows PowerShell 進行管理"
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: fa87745b9be04d14de37a308d870b73c5a98cf83
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="using-windows-powershell-for-administration"></a>使用 Windows PowerShell 進行管理
Windows PowerShell 的基本目標是透過互動方式或指令碼，對系統提供更好且更輕鬆的系統管理控制。 本章逐步解說使用 Windows PowerShell 管理 Windows 系統的許多特定問題的解決方案。 雖然我們未在《Windows PowerShell 使用者手冊》中討論指令碼或函式，但是稍後可以透過指令碼或作為函式來使用解決方案。 我們將顯示的範例會將函式包含為解決方案一部分來解決問題。

在整個解決方案描述中，您將看到混合使用特定 Cmdlet、一般 Get-WmiObject Cmdlet 及外部工具 (為 Windows 和 .NET Framework 基礎結構的一部分) 的解決方案。 使用外部工具是 Windows PowerShell 的長期設計目的其中之一。 甚至，系統成長時，使用者將持續遇到可用工具組未執行所需任何作業的情況。 Windows PowerShell 嘗試支援整合來自每個可能替代情況的解決方案，而不是單獨促進對 Cmdlet 實作的依存性。

