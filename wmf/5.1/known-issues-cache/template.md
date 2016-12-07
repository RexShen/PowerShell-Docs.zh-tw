---
title: "已知問題或限制寫上的範例範本"
contributor: 
ms.openlocfilehash: e3b98044902cb6665e06582c8259bd5defd6f2ca
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
>注意︰請提供建議的描述性標題和簡短描述

## <a name="example-erroneous-executionpolicy-errors"></a>範例：錯誤的 ExecutionPolicy 錯誤 ##
在 Windows 7 上，使用 PowerShell 模組和 DSC 資源可能會報告 ExecutionPolicy 的相關錯誤。

### <a name="resolution"></a>解決方法

若要解決此問題，請在提升權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令，將 **ExecutionPolicy** 設定為 **RemoteSigned**：

```powershell
Set-ExecutionPolicy RemoteSigned
```
