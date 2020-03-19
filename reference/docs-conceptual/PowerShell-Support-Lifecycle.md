---
title: PowerShell Core 支援週期
description: 控管 PowerShell Core 支援的原則
ms.date: 03/09/2020
ms.openlocfilehash: a1cd316b1d5351acd04c547bc35b3cc62a561429
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2020
ms.locfileid: "79090256"
---
# <a name="powershell-support-lifecycle"></a>PowerShell 支援生命週期

PowerShell 是一組與 Windows PowerShell 分開出貨、安裝及設定的不同工具與元件。 PowerShell 未包含在 Windows 授權合約中。

PowerShell 是由傳統 Microsoft 支援合約支援，包含[頂級][]、[Microsoft Enterprise 合約][enterprise-agreement]與 [Microsoft 軟體保證][assurance]。
您也可以透過提出您問題的支援要求，付費獲得 PowerShell 的[輔助支援][]。

## <a name="community-support"></a>社群支援

我們也會在您可提出問題、Bug 或功能要求的 GitHub 上提供[社群支援][]。
此外，您也可以在 Microsoft [PowerShell Tech Community][]，或在 [PowerShell][pshub] 中樞頁面中，社群區段所列的任何論壇中，尋求其他社群成員的協助。 我們不保證社群能夠及時處理或解決您的問題。 如果您有需要立即注意的問題，則應該使用傳統付費支援選項。

## <a name="lifecycle-of-powershell-7"></a>PowerShell 7 的生命週期

隨著 PowerShell 7 的發行，PowerShell 會持續依 [Microsoft 現代化生命週期原則][modern]繼續獲得支援，但支援日期會與 [.NET Core 的支援生命週期][Long-Term]連結。 在此服務方法中，客戶可以選擇長期支援 (LTS) 版本或目前版本。 PowerShell 7.0 為 LTS 版本。 其支援會隨著 .NET Core 3.1 的支援結束。 下一個 LTS 版本會隨著下一個 .NET Core LTS 版本一起推出。 請參閱 [PowerShell 版本生命週期結束表格](#powershell-releases-end-of-life)以取得目前的結束支援日期。 LTS 版本更新只包含重要安全性與服務的更新和修正，其設計目的是要避免對現有工作負載造成影響，或是將其降到最低。

目前版本是會在 LTS 版本之間發生的版本。 目前版本可能會包含重要修正、創新與新功能。 目前版本會在下一個目前或 LTS 版本發行後繼續獲得三個月的支援。

> [!IMPORTANT]
> 您必須安裝最新的修補程式更新以符合支援資格。 例如，如果您正在執行 PowerShell 7.0，且 7.0.1 已經發行，您便必須更新至 7.0.1 以符合支援資格。

## <a name="lifecycle-of-powershell-core-6x"></a>PowerShell Core 6.x 的生命週期

PowerShell Core 先前是使用 [Microsoft 現代化生命週期原則][modern]。 此支援生命週期是要保持客戶的最新版本最新資訊。

先前大約每六個月會更新 PowerShell Core 的 6.x 版分支一次 (例如：6.0、6.1、6.2 等等)。 不過，在發行 PowerShell 7 之後，便不會再發行任何 6.x 的次要版本。 PowerShell 6.2.x 在支援期間將會持續接收到服務更新。

> [!IMPORTANT]
> 您必須在每個新次要版本發行之後的六個月內進行更新，才能持續接收支援。

例如，如果 PowerShell Core 6.1 是在 2018 年 7 月1 日發行，就必須在 2019 年 1 月 1 日之前更新至 PowerShell Core 6.1 以繼續獲得支援。

> [!IMPORTANT]
> 您必須在每個新修補程式版本發行之後的 30 天內進行更新，才能繼續接收支援。

例如，如果您是執行 PowerShell Core 6.1，而且 6.1.3 在 2019 年 2 月19 日發行，您就必須在 2019 年 3 月 21 日 (也就是發行之後的第 30 天) 之前更新至 PowerShell Core 6.1.3 以繼續獲得支援。 如果需要修補程式，我們會在下一次累計更新中發行。

現代化生命週期原則也需要 Microsoft 在中斷產品 (即 PowerShell Core) 支援之前的 12 個月通知客戶。

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

根據 [PowerShell 的生命週期](#lifecycle-of-powershell-7)，下表會列出各種版本的停止支援日期。

| 版本 |    生命週期結束     |
| :-----: | ------------------ |
|   7.0   | 2022 年 12 月 3 日   |
|   6.2   | 2020 年 9 月 4 日  |
|   6.1   | 2019 年 9 月 28 日 |
|   6.0   | 2019 年 2 月 13 日  |

## <a name="unsupported-platforms"></a>不支援的平台

當平台版本到達平台擁有者所定義的生命週期結束時間時，PowerShell Core 也會停止支援該平台版本。 先前推出的套件仍然可供需要存取的客戶取得，但將不再提供任何類型的正式支援和更新。

這表示發行版本擁有者已停止支援下列版本，因此不再支援。

|    平台    | 版本 |                                                         生命週期結束                                                          |
| -------------- | :-----: | ---------------------------------------------------------------------------------------------------------------------------- |
| Debian         |    8    | [2018 年 6 月](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                            |
| Fedora         |   24    | [2017 年 8 月](https://fedoramagazine.org/fedora-24-eol/)                                                                     |
| Fedora         |   25    | [2017 年 12 月](https://fedoramagazine.org/fedora-25-end-life/)                                                              |
| Fedora         |   26    | [2018 年 5 月](https://fedoramagazine.org/fedora-26-end-life/)                                                                   |
| Fedora         |   27    | [2018 年 11 月](https://fedoramagazine.org/fedora-27-end-of-life/)                                                           |
| Fedora         |   28    | [2019 年 5 月](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                |
| openSUSE       |  42.1   | [2017 年 5 月](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                      |
| openSUSE       |  42.2   | [2018 年 1 月](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                  |
| openSUSE       |  42.3   | [2019 年 7 月](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                     |
| Ubuntu         |  14.04  | [2019 年 4 月](https://wiki.ubuntu.com/Releases)                                                                               |
| Ubuntu         |  16.10  | [2017 年 7 月](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                         |
| Ubuntu         |  17.04  | [2018 年 1 月](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                           |
| Ubuntu         |  17.10  | [2018 年 7 月](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                         |
| Windows        |    7    | [2020 年 1 月](https://support.microsoft.com/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [2020 年 1 月](https://support.microsoft.com/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>授權附註

PowerShell Core 是透過 [MIT 授權][]所發行。 透過此授權，而且沒有付費支援合約，則使用者就只有[社群支援][]。 運用社群支援，Microsoft 不保證會回應或修正。

## <a name="windows-powershell-compatibility"></a>Windows PowerShell 相容性

PowerShell 的支援生命週期不會涵蓋在 PowerShell 7 發行套件以外提供的模組。 例如，使用隨附為 Windows Server 一部分的 `ActiveDirectory` 模組，是由 [Windows 支援生命週期][]提供支援。

PowerShell 7 已改善與針對 Windows PowerShell 所撰寫之現有 PowerShell 模組之間的相容性。
如需詳細資訊，請參閱 [about_Windows_Compatibility][] 一文，以及[模組相容性清單][]。

> [!NOTE]
> [**WindowsPSModulePath**](https://www.powershellgallery.com/packages/WindowsPSModulePath) \(英文\) 模組在 PowerShell 7 中已無必要性，且已不再支援。

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
[頂級]: https://www.microsoft.com/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx
[社群支援]: /powershell/scripting/community/community-support
[pshub]: /powershell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[輔助支援]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[Long-Term]: https://dotnet.microsoft.com/platform/support/policy/dotnet-core
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[MIT 授權]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[about_Windows_Compatibility]: /powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility
[Windows 支援生命週期]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[模組相容性清單]: /powershell/scripting/whats-new/module-compatibility
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[實驗性功能]: /powershell/module/microsoft.powershell.core/about/about_powershell_config#experimentalfeatures
