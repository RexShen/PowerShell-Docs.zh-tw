---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: 軟體清查記錄 (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855433"
---
# <a name="software-inventory-logging-sil"></a>軟體清查記錄 (SIL)

> [!IMPORTANT]
> 在已執行 SIL 的 Windows Server 2012 R2 伺服器上安裝 WMF 5.x 時，在 WMF 安裝之後，必須執行一次 Start-SilLogging Cmdlet，因為安裝程序將會不當停止軟體清查記錄功能。

軟體清查記錄是為了在取得安裝在伺服器本機上的 Microsoft 軟體正確資料時，能夠減少運作成本，尤其是在 IT 環境中的許多伺服器上 (假設已在 IT 環境中安裝並執行軟體)。 假設一個已設定，您可以將這份資料轉送到彙總伺服器，並使用統一的自動程序將記錄資料收集在一個地方。

雖然您也能透過直接查詢每部電腦來記錄軟體清查資料，但是軟體清查記錄能使用由每部伺服器啟動的轉送 (經由網路) 架構，這樣可以克服一般會在許多軟體清查和資產管理案例中遇到的伺服器探索難題。 軟體清查記錄使用 SSL 保護透過 HTTPS 轉送到彙總伺服器的資料。 將資料存放在一個地方可以在有需要時更輕鬆地分析、操控及共用資料。

此功能不會將這份資料傳送給 Microsoft。 軟體清查記錄資料和功能僅供伺服器軟體授權擁有者及系統管理員使用。

如需軟體清查記錄 Cmdlet 的詳細資訊和相關文件，請參閱[在 Windows Server 2012 R2 中管理軟體清查記錄](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11))。
