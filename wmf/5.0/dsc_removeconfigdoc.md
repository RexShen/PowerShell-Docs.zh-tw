---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 16255a0f369c3df5a2131c075fc9f7006b517a63
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="remove-dsc-documents"></a>移除 DSC 文件

當設定文件傳遞至 DSC 時，文件會經歷各種階段 (擱置、目前、之前)。 我們在 [Windows RT 8.1、Windows 8.1 及 Windows Server 2012 R2 的 2014 年 11 月更新彙總套件](https://support.microsoft.com/kb/3000850)中，在 Windows PowerShell 4.0 增加了 DSC 的新 cmdlet：`Remove-DscConfigurationDocument`。