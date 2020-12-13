---
ms.date: 09/13/2016
ms.topic: reference
title: 設計 Windows PowerShell 提供者
description: 設計 Windows PowerShell 提供者
ms.openlocfilehash: 89e1fa9cfc0a2e5928a358aad4244c8e9152fe1a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654533"
---
# <a name="designing-your-windows-powershell-provider"></a>設計 Windows PowerShell 提供者

如果您的產品或設定會公開一組儲存的資料，例如使用者要流覽或流覽的資料庫，您應該執行 Windows PowerShell 提供者。 此外，如果您的產品提供容器，即使它不是多層的容器，也適合用來執行 Windows PowerShell 提供者。 例如，如果 Cmdlet 動詞複製、移動、重新命名、新增或移除，您可能會想要執行 Windows PowerShell 容器提供者，以做為您產品或設定資料的作業。

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell 路徑識別您的提供者

Windows PowerShell 執行時間使用 Windows PowerShell 路徑來存取適當的 Windows PowerShell 提供者。 當 Cmdlet 指定其中一個路徑時，執行時間會知道要使用哪一個提供者來存取相關聯的資料存放區。 這些路徑包含磁片磁碟機路徑、提供者限定路徑、提供者直接路徑，以及提供者內部路徑。 每個 Windows PowerShell 提供者都必須支援這些路徑中的一或多個。

如需 Windows PowerShell 路徑的詳細資訊，請參閱 Windows PowerShell 的運作方式。

### <a name="defining-a-drive-qualified-path"></a>定義 Drive-Qualified 路徑

若要允許使用者存取位於實體磁片磁碟機的資料，您的 Windows PowerShell 提供者必須支援磁片磁碟機限定路徑。 此路徑會以磁片磁碟機名稱開頭，後面接著冒號 (： ) ，例如 mydrive： \ abc\bar。

### <a name="defining-a-provider-qualified-path"></a>定義 Provider-Qualified 路徑

若要允許 Windows PowerShell 執行時間初始化和取消初始化提供者，您的 Windows PowerShell 提供者必須支援提供者限定的路徑。 例如，FileSystem：： \\ \uncshare\abc\bar 是 Windows PowerShell 所提供之 FileSystem 提供者的提供者限定路徑。

### <a name="defining-a-provider-direct-path"></a>定義 Provider-Direct 路徑

若要允許遠端存取您的 Windows PowerShell 提供者，它應該支援提供者直接路徑，直接傳遞給目前位置的 Windows PowerShell 提供者。 例如，登錄 Windows PowerShell 提供者可以使用 \\ \server\regkeypath 作為提供者直接路徑。

### <a name="defining-a-provider-internal-path"></a>定義 Provider-Internal 路徑

若要允許提供者 Cmdlet 使用非 Windows PowerShell 的應用程式開發介面來存取資料 () Api，您的 Windows PowerShell 提供者應該支援提供者內部路徑。 此路徑會以提供者限定路徑中的 "：：" 來表示。 例如，filesystem Windows PowerShell 提供者的提供者內部路徑為 \\ \uncshare\abc\bar。

## <a name="changing-stored-data"></a>變更儲存的資料

覆寫修改基礎資料存放區的方法時，請一律呼叫 [Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 方法，並以該方法所變更之專案的最新版本。 提供者基礎結構會判斷是否需要將專案物件傳遞給管線，例如當使用者指定-PassThru 參數時。 如果抓取最新的專案是高成本的作業 (效能方面，) 您可以測試內容。 PassThru 屬性來判斷您是否真的需要撰寫產生的專案。

## <a name="choose-a-base-class-for-your-provider"></a>為您的提供者選擇基類

Windows PowerShell 提供許多基類，可讓您用來執行自己的 Windows PowerShell 提供者。 設計提供者時，請選擇您的需求最適合的基類（如本節所述）。

每個 Windows PowerShell 提供者基類都可提供一組 Cmdlet。 本節說明 Cmdlet，但不會描述其參數。

使用會話狀態時，Windows PowerShell 執行時間會提供數個位置 Cmdlet 給某些 Windows PowerShell 提供者使用，例如 `Get-Location` 、 `Set-Location` 、 `Pop-Location` 和 `Push-Location` Cmdlet。 您可以使用 `Get-Help` Cmdlet 來取得這些位置 Cmdlet 的相關資訊。

### <a name="cmdletprovider-base-class"></a>CmdletProvider 基類

[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別會定義基本 Windows PowerShell 提供者。 這個類別支援提供者宣告，並提供許多可供所有 Windows PowerShell 提供者使用的屬性和方法。
指令程式會叫用類別， `Get-PSProvider` 以列出會話的所有可用提供者。
此 Cmdlet 的執行是由會話狀態所提供。

> [!NOTE]
> 所有 Windows PowerShell 語言範圍都可使用 Windows PowerShell 提供者。

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider 基類

[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別會定義 Windows PowerShell 磁片磁碟機提供者，以支援新增磁片磁碟機、移除現有磁片磁碟機，以及初始化預設磁片磁碟機的作業。 例如，Windows PowerShell 提供的 FileSystem 提供者會針對所有掛接的磁片磁碟機（例如硬碟和 CD/DVD 裝置磁片磁碟機）初始化磁片磁碟機。

這個類別是衍生自 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 基類的類別。 下表列出這個類別所公開的 Cmdlet。 除了列出的指令程式之外， `Get-PSDrive` (會話狀態所公開的 Cmdlet) 是用來取出可用磁片磁碟機的相關 Cmdlet。

|      Cmdlet      |                             定義                              |
| ---------------- | ------------------------------------------------------------------- |
| `New-PSDrive`    | 為會話建立新的磁片磁碟機，並串流磁片磁碟機資訊。 |
| `Remove-PSDrive` | 從會話中移除磁片磁碟機。                                   |

### <a name="itemcmdletprovider-base-class"></a>System.management.automation.provider.itemCmdletprovider 基類

[System.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別會定義一個 Windows PowerShell 專案提供者，此提供者會在資料存放區的個別專案上執行作業，而且不會假設任何容器或導覽功能。 這個類別是衍生自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 基類的類別。 下表列出這個類別所公開的 Cmdlet。

|     Cmdlet     |                                                                                                                                                            定義                                                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-Item`   | 清除位於指定位置之專案的目前內容，並以提供者指定的「清除」值取代它。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。                                                                                   |
| `Get-Item`     | 從指定的位置抓取專案，並串流處理結果物件。                                                                                                                                                                                                                                                  |
| `Invoke-Item`  | 在指定的路徑上叫用專案的預設動作。                                                                                                                                                                                                                                                                   |
| `Set-Item`     | 使用指定的值，在指定的位置設定專案。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。                                                                                                                                                   |
| `Resolve-Path` | 解析 Windows PowerShell 路徑的萬用字元，以及串流路徑資訊。                                                                                                                                                                                                                                              |
| `Test-Path`    | 測試指定的路徑，如果存在，則傳回， `true` `false` 否則傳回。 這個 Cmdlet 是為了支援 `IsContainer` [Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 方法的參數所執行。 |

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider 基類

[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別會定義一個 Windows PowerShell 的容器提供者，將資料存放區專案的容器公開給使用者。 請注意，只有當有一個容器 () 的專案中沒有任何嵌套容器時，才可以使用 Windows PowerShell 的容器提供者。 如果有嵌套的容器，則您必須執行 Windows PowerShell 的流覽提供者。

這個類別是衍生自 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 基類的類別。 下表定義這個類別所執行的 Cmdlet。

|     Cmdlet      |                                                                        定義                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Copy-Item`     | 將專案從某個位置複製到另一個位置。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。 |
| `Get-Childitem` | 抓取指定位置的子專案，並以物件的形式串流處理。                                                                        |
| `New-Item`      | 在指定的位置建立新的專案，並串流處理結果物件。                                                                           |
| `Remove-Item`   | 從指定的位置移除專案。                                                                                                               |
| `Rename-Item`   | 將專案重新命名于指定的位置。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。 |

### <a name="navigationcmdletprovider-base-class"></a>>navigationCmdletprovider 基類

[>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別會定義 Windows PowerShell 的流覽提供者，以針對使用多個容器的專案執行作業。 這個類別是衍生自 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 基類的類別。 下表列出這個類別所公開的 Cmdlet。

|    Cmdlet    |                                                                      定義                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Combine-Path | 使用路徑之間的提供者特定分隔符號，將兩個路徑結合成單一路徑。 此 Cmdlet 會串流處理字串。                               |
| `Move-Item`  | 將專案移至指定的位置。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。 |

相關的 Cmdlet 是 Windows PowerShell 提供的基本 Parse-Path Cmdlet。 您可以使用這個 Cmdlet 來剖析 Windows PowerShell 路徑，以支援 `Parent` 參數。 它會串流處理父路徑字串。

## <a name="select-provider-interfaces-to-support"></a>選取要支援的提供者介面

除了衍生自其中一個 Windows PowerShell 基類之外，您的 Windows PowerShell 提供者也可以衍生自下列一或多個提供者介面，以支援其他功能。 本節定義這些介面和各項支援的 Cmdlet。 它不會描述介面支援之 Cmdlet 的參數。 Cmdlet 參數資訊可在線上使用 `Get-Command` 和 `Get-Help` Cmdlet 取得。

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面會定義一個內容提供者，以針對資料項目的內容執行作業。 下表列出這個介面所公開的 Cmdlet。

|     Cmdlet      |                                                                                        定義                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Add-Content`   | 將指定的值長度附加至指定之專案的內容。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。 |
| `Clear-Content` | 將指定專案的內容設定為「清除」值。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。               |
| `Get-Content`   | 抓取指定專案的內容，並串流結果物件。                                                                                                         |
| `Set-Content`   | 取代指定之專案的現有內容。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。                     |

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)介面會定義 Windows PowerShell 提供者的屬性，以在資料存放區中對專案的屬性執行作業。 下表列出這個介面所公開的 Cmdlet。

> [!NOTE]
> `Path`這些 Cmdlet 上的參數表示專案的路徑，而不是識別屬性。

|        Cmdlet        |                                                                                   定義                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-ItemProperty` | 將指定專案的屬性設定為「清除」值。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。      |
| `Get-ItemProperty`   | 從指定的專案抓取屬性，並串流處理結果物件。                                                                                                |
| `Set-ItemProperty`   | 使用指定的值，設定指定之專案的屬性。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。 |

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

[IdynamicpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)介面（衍生自[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)）會定義提供者，以指定其所支援 Cmdlet 的動態參數。」的提供者。 這種類型的提供者會處理可在執行時間定義屬性的作業，例如新的屬性作業。 在具有靜態定義屬性的專案上，無法進行這類作業。
下表列出這個介面所公開的 Cmdlet。

|        Cmdlet         |                                                                                定義                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Copy-ItemProperty`   | 將屬性從指定的專案複製到另一個專案。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。 |
| `Move-ItemProperty`   | 將屬性從指定的專案移至另一個專案。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。  |
| `New-ItemProperty`    | 在指定的專案上建立屬性，並串流處理結果物件。                                                                                             |
| `Remove-ItemProperty` | 移除指定之專案的屬性。                                                                                                                              |
| `Rename-ItemProperty` | 重新命名指定之專案的屬性。 除非指定了輸出物件的參數，否則這個 Cmdlet 不會透過管線傳遞輸出物件 `PassThru` 。                 |

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

[IsecuritydescriptorCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider)介面會將安全描述項功能新增至提供者。 此介面可讓使用者取得並設定資料存放區中專案的安全描述項資訊。 下表列出這個介面所公開的 Cmdlet。

|  Cmdlet   |                                                                                                                                                                                                          定義                                                                                                                                                                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Get-Acl` | 抓取存取控制清單中包含 (ACL) 的資訊，這是用來保護作業系統資源的安全描述項的一部分，例如檔案或物件。                                                                                                                                                                                                                                      |
| `Set-Acl` | 設定 ACL 的資訊。 它是以 Accesscontrol) 的專案為指定的路徑所指定之 (專案上的 [Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) 實例形式。 如果 Windows PowerShell 提供者支援安全性資訊的設定，則此 Cmdlet 可以設定登錄中的檔案、機碼和子機碼，或任何其他提供者專案的相關資訊。 |

## <a name="see-also"></a>另請參閱

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 的運作方式](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
