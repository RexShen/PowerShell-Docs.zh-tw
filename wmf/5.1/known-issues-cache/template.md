---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
title: "已知問題或限制寫上的範例範本"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
>注意︰請提供建議的描述性標題和簡短描述

<a id="example-erroneous-executionpolicy-errors" class="xliff"></a>
## 範例：錯誤的 ExecutionPolicy 錯誤 ##
在 Windows 7 上，使用 PowerShell 模組和 DSC 資源可能會報告 ExecutionPolicy 的相關錯誤。

<a id="resolution" class="xliff"></a>
### 解決方法

若要解決此問題，請在提升權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令，將 **ExecutionPolicy** 設定為 **RemoteSigned**：

```powershell
Set-ExecutionPolicy RemoteSigned
```

