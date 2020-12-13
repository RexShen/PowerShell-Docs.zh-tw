---
ms.date: 09/13/2016
ms.topic: reference
title: 如何建立 Windows PowerShell 提供者
description: 如何建立 Windows PowerShell 提供者
ms.openlocfilehash: 51f19bf0dfa5f976a5045ae1342730c8f22f695e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647485"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>如何建立 Windows PowerShell 提供者

本節說明如何建立 Windows PowerShell 提供者。 您可以透過兩種方式來考慮 Windows PowerShell 提供者。 對使用者而言，提供者代表一組儲存的資料。 例如，儲存的資料可以是 Internet Information Services (IIS) 的中繼資料、Microsoft Windows 登錄、Windows 檔案系統、Active Directory，以及 Windows PowerShell 儲存的變數和別名資料。

對開發人員而言，Windows PowerShell 提供者是使用者與使用者需要存取的資料之間的介面。 從這個觀點來看，本節所述的每種提供者類型都支援一組特定的基類和介面，可讓 Windows PowerShell 執行時間以一般方式向使用者公開特定的 Cmdlet。

## <a name="providers-provided-by-windows-powershell"></a>Windows PowerShell 提供的提供者

Windows PowerShell 提供數個提供者 (例如，FileSystem 提供者、登錄提供者，以及用來存取已知資料存放區的別名提供者) 。 如需 Windows PowerShell 所提供提供者的詳細資訊，請使用下列命令來存取線上說明：

**PS>get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>使用 Windows PowerShell 路徑存取儲存的資料

Windows PowerShell 提供者可透過使用 Windows PowerShell 路徑，以程式設計方式存取 Windows PowerShell 執行時間和命令。 大部分的情況下，這些路徑是用來透過提供者直接存取資料。 不過，某些路徑可以解析成提供者內部路徑，讓 Cmdlet 使用非 Windows PowerShell 的應用程式設計介面 (Api) 存取資料。 如需有關 Windows PowerShell 提供者如何在 Windows PowerShell 內運作的詳細資訊，請參閱 [Windows PowerShell 的運作方式](/previous-versions/ms714658(v=vs.85))。

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>使用 Windows PowerShell 磁片磁碟機公開提供者 Cmdlet

Windows PowerShell 提供者會使用虛擬 Windows PowerShell 磁片磁碟機公開其支援的 Cmdlet。
Windows PowerShell 適用于 Windows PowerShell 磁片磁碟機的下列規則：

- 磁片磁碟機的名稱可以是任何英數位序列。
- 您可以在路徑上的任何有效點（稱為「根」）指定磁片磁碟機。
- 您可以針對任何儲存的資料（而不只是檔案系統）執行磁片磁碟機。
- 每個磁片磁碟機都會保留自己目前的工作位置，讓使用者可以在磁片磁碟機之間切換時保留內容。

## <a name="in-this-section"></a>本節內容

下表列出的主題包含建立在彼此之上的程式碼範例。 從第二個主題開始，Windows PowerShell 執行時間可以初始化並解除初始化基本 Windows PowerShell 提供者，下一個主題新增了存取資料的功能，下一個主題新增了可在儲存的資料) 的專案中操作 (資料的功能，依此類推。

|                                                    主題                                                    |                                                                                         定義                                                                                          |
| ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [設計 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)               | 本主題討論在執行 Windows PowerShell 提供者之前，您應該考慮的事項。 它會摘要說明所使用的 Windows PowerShell 提供者基類和介面。 |
| [建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)           | 本主題說明如何建立 Windows PowerShell 提供者，讓 Windows PowerShell 執行時間初始化和取消初始化提供者。                                        |
| [建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)           | 本主題說明如何建立可讓使用者透過 Windows PowerShell 磁片磁碟機存取資料存放區的 Windows PowerShell 提供者。                                                |
| [建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)             | 本主題說明如何建立可讓使用者運算元據存放區中之專案的 Windows PowerShell 提供者。                                                                  |
| [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)   | 本主題說明如何建立可讓使用者在多層資料存放區上工作的 Windows PowerShell 提供者。                                                                        |
| [建立 Windows PowerShell 瀏覽提供者](./creating-a-windows-powershell-navigation-provider.md) | 本主題說明如何建立 Windows PowerShell 提供者，讓使用者以階層方式流覽資料存放區的專案。                                           |
| [建立 Windows PowerShell 內容提供者](./creating-a-windows-powershell-content-provider.md)       | 本主題說明如何建立 Windows PowerShell 提供者，以允許使用者運算元據存放區中的專案內容。                                                       |
| [建立 Windows PowerShell 屬性提供者](./creating-a-windows-powershell-property-provider.md)     | 本主題說明如何建立 Windows PowerShell 提供者，以允許使用者運算元據存放區中專案的屬性。                                                    |

## <a name="see-also"></a>另請參閱

[Windows PowerShell 的運作方式](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)
