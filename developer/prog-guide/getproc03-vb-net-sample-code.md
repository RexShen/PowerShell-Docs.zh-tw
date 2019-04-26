---
title: GetProc03 (VB.NET) 範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081643"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03 (VB.NET) 範例程式碼

下列程式碼顯示實作`Get-Process`cmdlet 可接受管線輸入。 此實作會定義`Name`接受管線輸入參數會從本機電腦，根據提供的名稱，擷取程序資訊，然後使用[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)方法，將物件傳送至管線的輸出機制。

## <a name="code-sample"></a>程式碼範例

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->