---
title: RunSpace08 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 67172a0f8d6daf2f5b9965d1a18f7698daddbe1a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784685"
---
# <a name="runspace08-code-sample"></a>RunSpace08 程式碼範例

以下是[建立可將參數新增至命令的主控台應用程式](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)中所述之 Runspace08 範例的原始程式碼。
這個範例應用程式會建立一個執行空間、建立管線、將兩個命令新增至管線、將兩個參數新增至第二個命令，然後執行管線。 新增至管線的命令是 `Get-Process` 和 `Sort-Object` Cmdlet。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
