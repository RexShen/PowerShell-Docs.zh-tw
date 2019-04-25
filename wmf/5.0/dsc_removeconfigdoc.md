---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: eec82b0cb9860d07a282a07c414c3723be313fa4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085672"
---
# <a name="remove-dsc-documents"></a>移除 DSC 文件

當設定文件傳遞至 DSC 時，文件會經歷各種階段 (擱置、目前、之前)。 我們在 [Windows RT 8.1、Windows 8.1 及 Windows Server 2012 R2 的 2014 年 11 月更新彙總套件](https://support.microsoft.com/kb/3000850)中，在 Windows PowerShell 4.0 增加了 DSC 的新 cmdlet：`Remove-DscConfigurationDocument`。
