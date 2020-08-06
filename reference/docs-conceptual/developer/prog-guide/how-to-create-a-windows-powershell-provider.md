---
title: 如何建立 Windows PowerShell 提供者 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.openlocfilehash: 5e7424c035d22d0f5eb154b369427a6da80b1c49
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787099"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>如何建立 Windows PowerShell 提供者

本節說明如何建立 Windows PowerShell 提供者。 Windows PowerShell 提供者可透過兩種方式來考慮。 對使用者而言，提供者代表一組已儲存的資料。 例如，儲存的資料可以是 Internet Information Services (IIS) 的中繼資料、Microsoft Windows 登錄、Windows 檔案系統、Active Directory，以及 Windows PowerShell 所儲存的變數和別名資料。

對開發人員而言，Windows PowerShell 提供者是使用者與使用者需要存取的資料之間的介面。 從這個觀點來看，本節所述的每一種提供者都支援一組特定的基類和介面，可讓 Windows PowerShell 執行時間以一般方式向使用者公開特定 Cmdlet。

## <a name="providers-provided-by-windows-powershell"></a>Windows PowerShell 所提供的提供者

Windows PowerShell 提供數個提供者 (例如，FileSystem 提供者、登錄提供者，以及用來存取已知資料存放區的別名提供者) 。 如需 Windows PowerShell 提供之提供者的詳細資訊，請使用下列命令來存取線上說明：

**PS>get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>使用 Windows PowerShell 路徑存取儲存的資料

Windows powershell 提供者可以透過使用 Windows PowerShell 路徑，以程式設計方式存取 windows powershell 執行時間和命令。 在大部分的情況下，這些路徑是用來透過提供者直接存取資料。 不過，某些路徑可以解析成提供者內部路徑，讓 Cmdlet 可以使用非 Windows PowerShell 應用程式開發介面 (Api) 來存取資料。 如需 Windows powershell 提供者如何在 Windows PowerShell 中運作的詳細資訊，請參閱[Windows powershell 的運作方式](/previous-versions/ms714658(v=vs.85))。

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>使用 Windows PowerShell 磁片磁碟機公開提供者 Cmdlet

Windows PowerShell 提供者會使用虛擬 Windows PowerShell 磁片磁碟機來公開其支援的 Cmdlet。
Windows PowerShell 會針對 Windows PowerShell 磁片磁碟機套用下列規則：

- 磁片磁碟機的名稱可以是任何英數位元序列。
- 磁片磁碟機可以在路徑上的任何有效點指定，稱為「根」。
- 磁片磁碟機可以針對任何儲存的資料進行實作為，而不只是檔案系統。
- 每個磁片磁碟機都會保留它自己目前的工作位置，讓使用者可以在磁片磁碟機之間切換時保留內容。

## <a name="in-this-section"></a>本節內容

下表列出包含彼此建立之程式碼範例的主題。 從第二個主題開始，Windows PowerShell 執行時間可以初始化並初始化基本的 Windows PowerShell 提供者，下一個主題會加入存取資料的功能，下一個主題會加入功能來運算元據 (儲存的資料) 中的專案等等。

|                                                    主題                                                    |                                                                                         定義                                                                                          |
| ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [設計 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)               | 本主題討論您在執行 Windows PowerShell 提供者之前應考慮的事項。 它會摘要說明所使用的 Windows PowerShell 提供者基類和介面。 |
| [建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)           | 本主題說明如何建立 Windows PowerShell 提供者，以允許 Windows PowerShell 執行時間初始化和取消初始化提供者。                                        |
| [建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)           | 本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以透過 Windows PowerShell 磁片磁碟機存取資料存放區。                                                |
| [建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)             | 本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以運算元據存放區中的專案。                                                                  |
| [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)   | 本主題說明如何建立可讓使用者在多層資料存放區上工作的 Windows PowerShell 提供者。                                                                        |
| [建立 Windows PowerShell 瀏覽提供者](./creating-a-windows-powershell-navigation-provider.md) | 本主題說明如何建立 Windows PowerShell 提供者，讓使用者以階層方式流覽資料存放區的專案。                                           |
| [建立 Windows PowerShell 內容提供者](./creating-a-windows-powershell-content-provider.md)       | 本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以運算元據存放區中的專案內容。                                                       |
| [建立 Windows PowerShell 屬性提供者](./creating-a-windows-powershell-property-provider.md)     | 本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以運算元據存放區中專案的屬性。                                                    |

## <a name="see-also"></a>另請參閱

[Windows PowerShell 的運作方式](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)
