---
title: GetProc03 (VB.NET) 範例程式碼 |Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: ad8a7b13d30b77acdaa2f5365b9b2da02aaeedce
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771918"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03 (VB.NET) 範例程式碼

下列程式碼顯示 `Get-Process` 可接受管線輸入的 Cmdlet 的執行方式。 這個實作為定義 `Name` 參數，它會接受管線輸入、根據提供的名稱從本機電腦抓取進程資訊，然後使用[WriteObject (system.object，system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為將物件傳送至管線的輸出機制。

## <a name="code-sample"></a>程式碼範例

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
