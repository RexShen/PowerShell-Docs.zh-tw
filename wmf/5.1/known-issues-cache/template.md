---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.topic: conceptual
title: 已知問題或限制寫上的範例範本
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055542"
---
 ><span data-ttu-id="3619b-103">注意︰請提供建議的描述性標題和簡短描述</span><span class="sxs-lookup"><span data-stu-id="3619b-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="3619b-104">範例：錯誤的 ExecutionPolicy 錯誤</span><span class="sxs-lookup"><span data-stu-id="3619b-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="3619b-105">在 Windows 7 上，使用 PowerShell 模組和 DSC 資源可能會報告 ExecutionPolicy 的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="3619b-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="3619b-106">解決方法</span><span class="sxs-lookup"><span data-stu-id="3619b-106">Resolution</span></span>

<span data-ttu-id="3619b-107">若要解決此問題，請在提升權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令，將 **ExecutionPolicy** 設定為 **RemoteSigned**：</span><span class="sxs-lookup"><span data-stu-id="3619b-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
