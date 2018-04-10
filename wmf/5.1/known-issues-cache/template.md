---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
title: 已知問題或限制寫上的範例範本
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="29fe2-103">注意︰請提供建議的描述性標題和簡短描述</span><span class="sxs-lookup"><span data-stu-id="29fe2-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="29fe2-104">範例：錯誤的 ExecutionPolicy 錯誤</span><span class="sxs-lookup"><span data-stu-id="29fe2-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="29fe2-105">在 Windows 7 上，使用 PowerShell 模組和 DSC 資源可能會報告 ExecutionPolicy 的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="29fe2-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="29fe2-106">解決方法</span><span class="sxs-lookup"><span data-stu-id="29fe2-106">Resolution</span></span>

<span data-ttu-id="29fe2-107">若要解決此問題，請在提升權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令，將 **ExecutionPolicy** 設定為 **RemoteSigned**：</span><span class="sxs-lookup"><span data-stu-id="29fe2-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```