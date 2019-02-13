---
ms.date: 11/06/2018
contributor: JKeithB
keywords: 資源庫,powershell,cmdlet,psgallery,psget
title: 使用本機 PSRepositories
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679283"
---
# <a name="working-with-local-powershellget-repositories"></a>使用本機 PowerShellGet 存放庫

PowerShellGet 模組支援的存放庫以外的 「 PowerShell 資源庫。
這些 cmdlet 會啟用下列案例：

- 支援在您的環境中使用的一組受信任且預先驗證的 PowerShell 模組
- 測試建置 PowerShell 模組或指令碼的 CI/CD 管線
- 將 PowerShell 指令碼和模組傳遞給無法存取網際網路的系統

本文說明如何設定本機的 PowerShell 存放庫。 本文亦涵蓋[OfflinePowerShellGetDeploy][]模組可從 PowerShell 資源庫。 此模組包含 cmdlet 來安裝最新版的 PowerShellGet 到您的本機儲存機制。

## <a name="local-repository-types"></a>本機存放庫類型

有兩種方式可建立本機的 PSRepository:NuGet 伺服器或檔案共用。 每個類型都有其優缺點：

NuGet 伺服器

| 優點| 缺點 |
| --- | --- |
| 精確地模擬 powershell 資源庫功能 | 多層式應用程式所需作業計劃與支援 |
| NuGet 整合了 Visual Studio 中，其他工具 | 驗證模型和所需的 NuGet 帳戶管理 |
| NuGet 支援中的中繼資料`.Nupkg`套件 | 發行需要 API 金鑰管理與維護 |
| 提供搜尋、 套件管理等。 | |

檔案共用

| 優點| 缺點 |
| --- | --- |
| 易於設定、 備份和維護 | PowerShellGet 所使用的中繼資料無法使用 |
| 簡單的安全性模式-使用者共用的權限 | 沒有 UI，超過基本的檔案共用 |
| 沒有條件約束，例如取代現有的項目 | 有限的安全性並沒有記錄，誰負責更新項目 |

PowerShellGet 適用於型別和尋找版本和相依性安裝支援。
不過，適用於 「 PowerShell 資源庫的某些功能不適用於基底的 NuGet 伺服器或檔案共用。

- 一切都已封裝-指令碼、 模組、 DSC 資源，或角色功能沒有任何差異。
- 檔案共用伺服器看不見套件中繼資料，包括標記。

## <a name="creating-a-local-repository"></a>建立本機儲存機制

下列文章列出的步驟設定您自己的 NuGet 伺服器。

- [NuGet.Server][]

請遵循新增套件的點為止的步驟。 步驟[發行套件](#publishing-to-a-local-repository)本文稍後所述。

檔案共用為基礎儲存機制中，請確定您的使用者具有存取檔案共用的權限。

## <a name="registering-a-local-repository"></a>註冊本機存放庫

可用的存放庫之前，必須註冊使用`Register-PSRepository`命令。
在以下範例中， **InstallationPolicy**設為*信任*，假設您信任您自己的存放庫。

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

請記下的兩個命令的處理方式之間的差異**ScriptSourceLocation**。 檔案共用為基礎的存放庫，如**SourceLocation**並**ScriptSourceLocation**必須相符。 針對 web 為基礎的存放庫，它們必須不同，因此在此範例中的尾端"/"新增至**SourceLocation**。

如果您想要預設存放庫新建的 PSRepository 時，您必須取消註冊所有其他 PSRepositories。 例如：

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> 存放庫名稱 'PSGallery' 被保留給使用 「 PowerShell 資源庫。 您可以取消註冊 PSGallery，但您無法重複使用任何其他存放庫名稱 PSGallery。

如果您需要還原 PSGallery，執行下列命令：

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>發行至本機存放庫

一旦您已註冊本機 PSRepository，您可以發行至您的本機 PSRepository。 有兩個主要的發行案例： 發佈您自己的模組和發行 PSGallery 的模組。

### <a name="publishing-a-module-you-authored"></a>發行您所撰寫的模組

使用`Publish-Module`和`Publish-Script`發佈您的模組到您本機的 PSRepository 由 PowerShell 資源庫的相同方式。

- 指定您的程式碼的位置
- 提供 API 金鑰
- 指定存放庫名稱。 例如，`-PSRepository LocalPSRepo`

> [!NOTE]
> 您必須在 NuGet 伺服器中，建立帳戶，然後登入，以產生並儲存的 API 金鑰。
> 檔案共用，使用任何非空白字串做為 NuGetApiKey 值。

範例：

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 若要確保安全性，API 金鑰不應該硬式編碼在指令碼中。 使用安全金鑰管理系統。

### <a name="publishing-a-module-from-the-psgallery"></a>發行來自 PSGallery 的模組

若要發行到您本機的 PSRepository PSGallery 的模組，您可以使用 '儲存封裝' cmdlet。

- 指定封裝的名稱
- 指定 'NuGet' 作為提供者
- PSGallery 位置指定的來源 （ https://www.powershellgallery.com/api/v2)
- 指定本機儲存機制的路徑

範例：

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

如果您本機的 PSRepository 是以 web 為基礎，它會需要額外的步驟來發佈使用 nuget.exe。

請參閱使用文件[nuget.exe][]。

## <a name="installing-powershellget-on-a-disconnected-system"></a>在中斷連線的系統上安裝 PowerShellGet

部署 PowerShellGet 會要求系統，以從網際網路中斷連線的環境中難以就行了。 PowerShellGet 已安裝最新版本的第一次使用它的啟動程序。 PowerShell 資源庫中的 OfflinePowerShellGetDeploy 模組提供支援此啟動程序的處理序的 cmdlet。

若要啟動離線部署，您需要：

- 下載並安裝 OfflinePowerShellGetDeploy 您連線到網際網路的系統和中斷連線的系統
- 下載 PowerShellGet 和其相依性連線網際網路的系統使用`Save-PowerShellGetForOffline`cmdlet
- 從連線網際網路的系統的 PowerShellGet 和其相依性複製到已中斷連線的系統
- 使用`Install-PowerShellGetOffline`PowerShellGet 和其相依性放置於適當的資料夾已中斷連線的系統上

下列命令使用`Save-PowerShellGetForOffline`放資料夾中的所有元件 `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

此時，您必須進行的內容`F:\OfflinePowerShellGet`能夠中斷連線的系統。 執行`Install-PowerShellGetOffline`中斷連線的系統上安裝 PowerShellGet cmdlet。

> [!NOTE]
> 很重要，您無法執行 PowerShellGet 中的 PowerShell 工作階段，再執行這些命令。 PowerShellGet 載入工作階段之後, 就無法更新的元件。 如果您不小心啟動 PowerShellGet，結束並重新啟動 PowerShell。

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

執行這些命令之後，您已準備好發佈至本機存放庫的 PowerShellGet 項目。

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> 若要確保安全性，API 金鑰不應該硬式編碼在指令碼中。 使用安全金鑰管理系統。

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
