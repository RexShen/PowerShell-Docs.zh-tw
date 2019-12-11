---
ms.date: 11/06/2018
contributor: JKeithB
keywords: 資源庫,powershell,cmdlet,psgallery,psget
title: 使用本機 PSRepository
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327989"
---
# <a name="working-with-local-powershellget-repositories"></a>使用本機 PowerShellGet 存放庫

PowerShellGet 模組支援 PowerShell 資源庫以外的存放庫。
這些 Cmdlet 會啟用下列案例：

- 支援一組受信任且預先驗證的 PowerShell 模組，以便在您的環境中使用
- 測試建置 PowerShell 模組或指令碼的 CI/CD 管線
- 將 PowerShell 指令碼和模組傳遞給無法存取網際網路的系統

本文說明如何設定本機 PowerShell 存放庫。 本文亦涵蓋可從 PowerShell 資源庫取得的 [OfflinePowerShellGetDeploy][] 模組。 此模組所包含的 Cmdlet 可將最新版的 PowerShellGet 安裝到您的本機存放庫。

## <a name="local-repository-types"></a>本機存放庫類型

有兩種方式可用來建立本機 PSRepository：NuGet 伺服器或檔案共用。 每個類型都有優點和缺點：

NuGet 伺服器

| 優點| 缺點 |
| --- | --- |
| 精確地模擬 PowerShellGallery 功能 | 多層式應用程式需要作業規劃與支援 |
| NuGet 整合了 Visual Studio，其他工具 | 需要驗證模型和 NuGet 帳戶管理 |
| NuGet 支援 `.Nupkg` 套件的中繼資料 | 發佈需要 API 金鑰管理與維護 |
| 提供搜尋、套件管理等。 | |

檔案共用

| 優點| 缺點 |
| --- | --- |
| 易於設定、備份和維護 | 無法使用 PowerShellGet 所使用的中繼資料 |
| 簡單的安全性模式：共用上的使用者權限 | 除基本的檔案共用之外沒有任何 UI |
| 沒有取代現有項目之類的條件約束 | 安全性有限，而且不會記錄誰負責更新哪些項目 |

PowerShellGet 適用於任一個類型，並支援尋找版本和相依性安裝。
不過，部分適用於 PowerShell 資源庫的功能不適用基底 NuGet 伺服器或檔案共用。

- 所有項目均為套件：指令碼、模組、DSC 資源或角色功能間並無任何差異。
- 檔案共用伺服器看不到包括標記在內的套件中繼資料。

## <a name="creating-a-local-repository"></a>建立本機存放庫

下列文章列出設定您自己 NuGet 伺服器的步驟。

- [NuGet.Server][]

遵循步驟來新增套件。 [發佈套件](#publishing-to-a-local-repository)的步驟將於本文稍後討論。

針對以檔案共用為基礎的存放庫，確定您的使用者具有存取檔案共用的權限。

## <a name="registering-a-local-repository"></a>註冊本機存放庫

您必須先使用 `Register-PSRepository` 命令來註冊存放庫，才能加以使用。
在下列範例中，會將 **InstallationPolicy** 設定為 *Trusted* (假設您信任自己的存放庫)。

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

請記下這兩個命令如何處理 **ScriptSourceLocation** 之間的差異。 針對以檔案共用為基礎的存放庫，**SourceLocation** 和 **ScriptSourceLocation** 必須相符。 針對以 Web 為基礎的存放庫，它們必須不同，因此在此範例中，會在 **SourceLocation** 尾端新增 "/"。

如果您想要使新建的 PSRepository 成為預設存放庫，就必須取消註冊所有其他 PSRepository。 例如：

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> 存放庫名稱 'PSGallery' 會保留，以供 PowerShell 資源庫使用。 您可以取消註冊 PSGallery，但無法針對任何其他存放庫重複使用 PSGallery 這個名稱。

如果您需要還原 PSGallery，請執行下列命令：

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>發佈至本機存放庫

一旦註冊本機 PSRepository 之後，就能發佈到您的本機 PSRepository。 有兩個主要發佈案例：發佈您自己的模組和從 PSGallery 發佈模組。

### <a name="publishing-a-module-you-authored"></a>發佈您所撰寫的模組

使用 `Publish-Module` 和 `Publish-Script`，以您針對 PowerShell 資源庫所做的相同方式來將模組發佈到本機 PSRepository。

- 指定程式碼的位置
- 提供 API 金鑰
- 指定存放庫名稱。 例如，`-PSRepository LocalPSRepo`

> [!NOTE]
> 您必須在 NuGet 伺服器中建立帳戶，然後登入以產生並儲存 API 金鑰。
> 針對檔案共用，為 NuGetApiKey 值使用任何非空白的字串。

範例：

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 為確保安全性，不應將 API 金鑰硬式編碼於指令碼中。 使用安全金鑰管理系統。

### <a name="publishing-a-module-from-the-psgallery"></a>從 PSGallery 發佈模組

若要從 PSGallery 將模組發佈到您的本機 PSRepository，您可以使用 'Save-Package' Cmdlet。

- 指定套件名稱
- 指定 'NuGet' 作為提供者
- 指定 PSGallery 位置作為來源 (https://www.powershellgallery.com/api/v2)
- 指定本機存放庫的路徑

範例：

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

如果本機 PSRepository 會以 Web 為基礎，它需要額外的步驟，才能使用 nuget.exe 來發佈。

請參閱使用 [nuget.exe][] 的文件。

## <a name="installing-powershellget-on-a-disconnected-system"></a>在中斷連線的系統上安裝 PowerShellGet

在要求系統中斷與網路網路連線的環境內，很難部署 PowerShellGet。 PowerShellGet 有一個啟動程序流程，可在第一次使用時安裝最新版本。 PowerShell 資源庫中的 OfflinePowerShellGetDeploy 模組提供支援此啟動程序流程的 Cmdlet。

若要啟動離線部署，您需要：

- 下載 OfflinePowerShellGetDeploy 並安裝至您連線到網際網路的系統和中斷連線的系統
- 在連線到網際網路的系統上，使用 `Save-PowerShellGetForOffline` Cmdlet 來下載 PowerShellGet 及其相依性
- 將 PowerShellGet 及其相依性從連線到網際網路的系統複製到中斷連線的系統
- 在中斷連線的系統上使用 `Install-PowerShellGetOffline`，以將 PowerShellGet 及其相依性放置於適當的資料夾

下列命令會使用 `Save-PowerShellGetForOffline`，將所有元件放入 `f:\OfflinePowerShellGet` 資料夾

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

此時，您必須讓 `F:\OfflinePowerShellGet` 的內容可供中斷連線的系統使用。 執行 `Install-PowerShellGetOffline` Cmdlet，以在中斷連線的系統上安裝 PowerShellGet。

> [!NOTE]
> 執行這些命令之前，不要在 PowerShell 工作階段上執行 PowerShellGet，這點很重要。 將 PowerShellGet 載入至工作階段之後，就無法更新元件。 如果您不小心啟動了 PowerShellGet，請結束並重新啟動 PowerShell。

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

執行這些命令之後，您就已經準備好將 PowerShellGet 發佈至本機存放庫。

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 為確保安全性，不應將 API 金鑰硬式編碼於指令碼中。 使用安全金鑰管理系統。

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
