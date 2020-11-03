---
description: 描述 **CimSession** 物件，以及 CIM 會話與 PowerShell 會話之間的差異。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CimSession
ms.openlocfilehash: 21015e1457dfcc037dd65cbf3b2f7f85c9076106
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206663"
---
# <a name="about-cimsession"></a>關於 CimSession

## <a name="short-description"></a>簡短描述
描述 **CimSession** 物件，以及 CIM 會話與 PowerShell 會話之間的差異。

## <a name="long-description"></a>完整描述

通用訊息模型 (CIM) 會話是代表本機電腦或遠端電腦之連接的用戶端物件。 您可以使用 CIM 會話來替代 (Pssession) 的 PowerShell 會話。 這兩種方法都有其優點。

您可以使用指令 `New-CimSession` 程式來建立 CIM 會話，其中包含連線的相關資訊，例如電腦名稱稱、連接所使用的通訊協定、會話識別碼和實例識別碼。

在您建立 **CimSession** 物件來指定建立連線所需的資訊之後，PowerShell 就無法立即建立連接。 當 Cmdlet 使用 CIM 會話時，PowerShell 會連接到指定的電腦，然後當 Cmdlet 完成時，PowerShell 就會終止連線。

如果您建立 **PSSession** 而不是使用 CIM 會話，則 PowerShell 會驗證連接設定，然後建立並維護連接。 如果您使用 CIM 會話，則在需要時 PowerShell 不會開啟網路連接。 如需 PowerShell 會話的詳細資訊，請參閱 [about_PSSessions](about_PSSessions.md)。

## <a name="when-to-use-a-cim-session"></a>使用 CIM 會話的時機

只有搭配 Windows Management Instrumentation (WMI) 提供者或 CIM over WS-Man 接受 CIM 會話的 Cmdlet。 若為其他 Cmdlet，請使用 **pssession** 。

當您使用 CIM 會話時，PowerShell 會在本機用戶端上執行 Cmdlet。 它會使用 CIM 會話連接至 WMI 提供者。 目的電腦不需要 PowerShell，甚至是任何版本的 Windows 作業系統。

相反地，Cmdlet 會使用在目的電腦上執行的 **PSSession** 執行。
目標系統上需要有 PowerShell。 此外，此 Cmdlet 會將資料傳送回本機電腦。 PowerShell 會管理透過連線傳送的資料，並將大小保持在 Windows 遠端管理 (WinRM) 所設定的限制內。 CIM 會話不會強加 WinRM 限制。

## <a name="using-cdxml-cmdlets"></a>使用 CDXML Cmdlet

以 CIM 為基礎的 Cmdlet 定義 XML (CDXML) Cmdlet 可以撰寫成使用任何 WMI 提供者。 所有 WMI 提供者都會使用 **CimSession** 物件。 如需 CDXML 的詳細資訊，請參閱 [cdxml 定義和詞彙](/previous-versions/windows/desktop/wmi_v2/cdxml-overview)。

CDXML Cmdlet 具有可採用 **CimSession** 物件陣列的自動 **CimSession** 參數。 根據預設，PowerShell 會將並行 CIM 連接數目限制為15。 這項限制可由執行 **ThrottleLimit** 的 CDXML Cmdlet 覆寫。 若要瞭解 **ThrottleLimit** ，請參閱個別的 Cmdlet 檔。

## <a name="see-also"></a>另請參閱

[New-CimSession](xref:CimCmdlets.New-CimSession)

[about_PSSessions](about_PSSessions.md)
