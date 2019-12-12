---
title: GetProc03 （VB.NET）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360307"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03 (VB.NET) 範例程式碼

下列程式碼顯示可接受管線輸入的 `Get-Process` Cmdlet 的執行。 這個實作為定義一個接受管線輸入的 `Name` 參數，根據提供的名稱從本機電腦抓取進程資訊，然後使用[WriteObject （system.object，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為將物件傳送至管線的輸出機制。

## <a name="code-sample"></a>範例程式碼

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
