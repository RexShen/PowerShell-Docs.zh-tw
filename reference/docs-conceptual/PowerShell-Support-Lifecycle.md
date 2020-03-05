---
title: PowerShell Core 支援週期
description: 控管 PowerShell Core 支援的原則
ms.date: 08/06/2018
ms.openlocfilehash: 8cf8a0ac6140d28e55b065bf711763ba1c681d63
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706252"
---
# <a name="powershell-core-support-lifecycle"></a>PowerShell Core 支援週期

PowerShell Core 是一組可以與 Windows PowerShell 分開出貨、安裝和設定的不同工具和元件。 因此，Windows 7/8.1/10 或 Windows Server 授權合約不包含 PowerShell Core。

不過，PowerShell Core 是由傳統 Microsoft 支援合約支援，包含[頂級][]、[Microsoft Enterprise 合約][enterprise-agreement]與[微軟軟體保證][assurance]。
您也可以提出您問題的支援要求，付費獲得 PowerShell Core 的[輔助支援][]。

## <a name="community-support"></a>社群支援

我們也會在您可提出問題、Bug 或功能要求的 GitHub 上提供[社群支援][]。
此外，您也可以在 Microsoft [PowerShell Tech Community][]，或在 [PowerShell][pshub] 中樞頁面中，社群區段所列的任何論壇中，尋求其他社群成員的協助。 我們不保證社群能夠及時處理或解決您的問題。 如果您有需要立即注意的問題，則應該使用傳統付費支援選項。

## <a name="lifecycle-of-powershell-core"></a>PowerShell Core 生命週期

PowerShell Core 會採用 [Microsoft 現代化生命週期原則][modern]。 此支援生命週期是要保持客戶的最新版本最新資訊。

大約每六個月更新 PowerShell Core 6.x 版分支一次 (例如 6.0、6.1、6.2 等等)

> [!IMPORTANT]
> 您必須在每個新次要版本發行之後的六個月內進行更新，才能持續接收支援。

例如，如果 PowerShell Core 6.1 是在 2018 年 7 月1 日發行，就必須在 2019 年 1 月 1 日之前更新至 PowerShell Core 6.1 以繼續獲得支援。

> [!IMPORTANT]
> 您必須在每個新修補程式版本發行之後的 30 天內進行更新，才能繼續接收支援。

例如，如果您是執行 PowerShell Core 6.1，而且 6.1.3 在 2019 年 2 月19 日發行，您就必須在 2019 年 3 月 21 日 (也就是發行之後的第 30 天) 之前更新至 PowerShell Core 6.1.3 以繼續獲得支援。 如果需要修補程式，我們會在下一次累計更新中發行。

現代化生命週期原則也需要 Microsoft 在中斷產品 (即 PowerShell Core) 支援之前的 12 個月通知客戶。

最後，我們預期 PowerShell Core 會採用長期維護方法。 透過這個方法，我們僅需要提供服務和安全性更新，就能保持對特定 6.x 分支/版本的支援。

## <a name="supported-platforms"></a>支援的平台

若要確認您使用的平台與 PowerShell Core 版本是受支援的，請參閱下表。

我們的社群也針對部分平台貢獻了套件，但這些套件未受正式支援。 這些套件在表格中標示為 `Community`。

列為 `Experimental` 的平台為非正式支援，但可用於實驗和提供意見反應。

| 平台                                          |      6.2      |    7.0    |
| ------------------------------------------------- | :-----------: | :-------: |
| Windows 8.1 和 10                               |   支援   | 支援 |
| Windows Server 2012 R2、2016                      |   支援   | 支援 |
| [Windows Server 半年通道][semi-annual] |   支援   | 支援 |
| Ubuntu 16.04 和 18.04                            |   支援   | 支援 |
| Ubuntu 19.10 (透過 Snap 套件)                   |   社群   | 社群 |
| Ubuntu 20.04 (透過 Snap 套件)                   |   社群   | 社群 |
| Debian 9                                          |   支援   | 支援 |
| Debian 10                                         | 不支援 | 支援 |
| CentOS 7                                          |   支援   | 支援 |
| CentOS 8                                          | 不支援 | 支援 |
| Red Hat Enterprise Linux 7                        |   支援   | 支援 |
| Red Hat Enterprise Linux 8                        | 不支援 | 支援 |
| Fedora 30                                         | 不支援 | 支援 |
| Alpine 3.8                                        |   查看注意事項    | 查看注意事項  |
| Alpine 3.9 與 3.10                               | 不支援 | 查看注意事項  |
| macOS 10.12+                                      |   支援   | 支援 |
| Arch                                              |   社群   | 社群 |
| Raspbian                                          |   社群   | 社群 |
| Kali                                              |   社群   | 社群 |
| AppImage (作用於多個 Linux 平台)      |   社群   | 社群 |
| [Snap 套件](https://snapcraft.io/powershell)   |   請參閱備註    | 請參閱備註  |

> [!NOTE]
> 和您執行套件所在的發行版本一樣，也支援 Snap 套件。

> [!NOTE]
> Alpine 不支援 CIM、PowerShell Remoting 與 DSC。

## <a name="powershell-releases-end-of-life"></a>PowerShell 版本生命週期結束

下表根據 [PowerShell Core 的生命週期](#lifecycle-of-powershell-core)，列出各種版本的停止支援日期。

| 版本 | 生命週期結束                   |
|---------|-------------------------------|
| 6.0     | 2019 年 2 月 13 日             |
| 6.1     | 2019 年 9 月 28 日            |
| 6.2     | 7 發行後的 6 個月     |

## <a name="unsupported-platforms"></a>不支援的平台

當平台版本到達平台擁有者所定義的生命週期結束時間時，PowerShell Core 也會停止支援該平台版本。 先前推出的套件仍然可供需要存取的客戶取得，但將不再提供任何類型的正式支援和更新。

這表示發行版本擁有者已停止支援下列版本，因此不再支援。

| 平台       | 版本 | 生命週期結束                                                                                                                        |
| -------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Debian         | 8       | [2018 年 6 月](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                                  |
| Fedora         | 24      | [2017 年 8 月](https://fedoramagazine.org/fedora-24-eol/)                                                                           |
| Fedora         | 25      | [2017 年 12 月](https://fedoramagazine.org/fedora-25-end-life/)                                                                    |
| Fedora         | 26      | [2018 年 5 月](https://fedoramagazine.org/fedora-26-end-life/)                                                                         |
| Fedora         | 27      | [2018 年 11 月](https://fedoramagazine.org/fedora-27-end-of-life/)                                                                 |
| Fedora         | 28      | [2019 年 5 月](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                      |
| openSUSE       | 42.1    | [2017 年 5 月](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                            |
| openSUSE       | 42.2    | [2018 年 1 月](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                        |
| openSUSE       | 42.3    | [2019 年 7 月](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                           |
| Ubuntu         | 14.04   | [2019 年 4 月](https://wiki.ubuntu.com/Releases)                                                                                     |
| Ubuntu         | 16.10   | [2017 年 7 月](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                               |
| Ubuntu         | 17.04   | [2018 年 1 月](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                                 |
| Ubuntu         | 17.10   | [2018 年 7 月](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                               |
| Windows        | 7       | [2020 年 1 月](https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [2020 年 1 月](https://support.microsoft.com/en-us/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>授權附註

PowerShell Core 是透過 [MIT 授權][]所發行。 透過此授權，而且沒有付費支援合約，則使用者就只有[社群支援][]。 運用社群支援，Microsoft 不保證會回應或修正。

## <a name="windows-powershell-module"></a>Windows PowerShell 模組

除非產品模組明確支援 PowerShell Core，否則 PowerShell Core 支援不包含那些模組。 例如，使用隨附為 Windows Server 一部分的 `ActiveDirectory` 模組，就是不支援的案例。

不過，在某些情況下，未明確支援 PowerShell Core 的模組可能會相容。 安裝 [WindowsPSModulePath][] 模組，即可將 Windows PowerShell 新增至 `PSModulePath`PowerShell Core `PSModulePath`。

首先，請從 PowerShell 資源庫安裝 **WindowsPSModulePath** 模組：

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>實驗性功能

[實驗性功能][]僅限於[社群支援](#community-support)。

## <a name="release-history"></a>版本歷程記錄

下表包含 PowerShell 主要版本的時間表。 此表格僅供作為歷程記錄參考。 不適合用來判斷支援週期。

|       版本        | 發行日期 |                                                                     附註                                                                      |
| -------------------- | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| PowerShell 7.0 (LTS) |   2020 年 3 月   | 以 .NET Core 3.1 (LTS) 建置                                                                                                                  |
| PowerShell 6.0       |   2018 年 1 月   | 第一版，以 .NET Core 2.1 建置。 可在 Windows、Linux 與 macOS 上安裝。                                                              |
| PowerShell 5.1       |   2016 年 8 月   | 於 Windows 10 年度更新版與 Windows Server 2016 中發行                                                                             |
| PowerShell 5.0       |   2016 年 2 月   | 於 Windows Management Framework (WMF) 5.0 中發行                                                                                            |
| PowerShell 4.0       |   2013 年 10 月   | 與 Windows Server 2012 R2 整合於 Windows 8.1 中。 可在 Windows 7 SP1、Windows Server 2008 R2 SP1 與 Windows Server 2012 上安裝。 |
| PowerShell 3.0       |   2012 年 10 月   | 與 Windows Server 2012 整合於 Windows 8 中。 可在 Windows 7 SP1、Windows Server 2008 SP1 與 Windows Server 2008 R2 SP1 上安裝。  |
| PowerShell 2.0       |   2009 年 7 月   | 與 Windows Server 2008 R2 整合於 Windows 7 中。 可在 Windows XP SP3、Windows Server 2003 SP2 與 Windows Vista SP1 上安裝。            |
| PowerShell 1.0       |   2006 年 11 月   | 可在 Windows XP SP2、Windows Server 2003 SP1 與 Windows Vista 上安裝。 為 Windows Server 2008 的選用元件。                          |

<!-- hyperlink references -->
[頂級]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[社群支援]: https://github.com/powershell/powershell/issues
[pshub]: https://docs.microsoft.com/powershell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[輔助支援]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 授權]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[實驗性功能]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
