---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 必要條件
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734289"
---
# <a name="prerequisites"></a>必要條件

Just Enough Administration 是 PowerShell 5.0 和更高版本隨附的功能。 本文描述必須滿足才能開始使用 JEA 的必要條件。


## <a name="check-which-version-of-powershell-is-installed"></a>檢查已安裝哪個版本的 PowerShell

若要檢查哪個版本的 PowerShell 安裝在您的系統上，請在 Windows PowerShell 提示字元中檢查 `$PSVersionTable` 變數。

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA 適用於 PowerShell 5.0 和更高版本。 如需完整的功能，建議您為系統安裝最新版的 PowerShell。 下表說明 JEA 在 Windows Server 上的可用性：

| 伺服器作業系統 |                JEA 可用性                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016+    | 預先安裝                                   |
| Windows Server 2012 R2  | 具完整功能性的 WMF 5.1                |
| Windows Server 2012     | 具完整功能性的 WMF 5.1                |
| Windows Server 2008 R2  | 功能有限 <sup>1</sup> 的 WMF 5.1 |

您也可以在家用或工作電腦上使用 JEA：

| 用戶端作業系統 |                   JEA 可用性                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | 預先安裝                                         |
| Windows 10 1603、1511   | 預先安裝，功能有限<sup>2</sup> |
| Windows 10 1507         | 無法使用                                        |
| Windows 8、8.1          | 具完整功能性的 WMF 5.1                      |
| Windows 7               | 功能有限 <sup>1</sup> 的 WMF 5.1       |

- <sup>1</sup> 在 Windows Server 2008 R2 或 Windows 7 上無法設定 JEA 使用群組受控服務帳戶。 *支援*虛擬帳戶和其他 JEA 功能。

- <sup>2</sup> Windows 10 1511 版和 1603 版不支援下列 JEA 功能：

  - 以群組受控服務帳戶執行
  - 工作階段設定中的條件式存取規則
  - 使用者磁碟機
  - 將存取權授與本機使用者帳戶

  若要取得這些功能的支援，請將 Windows 更新為 1607 版 (年度更新版) 或更高版本。

### <a name="install-windows-management-framework"></a>安裝 Windows Management Framework

如果您執行較舊版本的 PowerShell，則可能需要使用最新的 Windows Management Framework (WMF) 更新來更新系統。 如需詳細資訊，請參閱 [WMF](/powershell/wmf/overview) 文件。

建議您先測試工作負載的 WMF 相容性，再升級所有的伺服器。

Windows 10 使用者應安裝最新的功能更新，以取得目前版本的 Windows PowerShell。

## <a name="enable-powershell-remoting"></a>啟用 PowerShell 遠端

PowerShell 遠端提供 JEA 建置的基礎。 必須先確保已啟用 PowerShell 遠端並經過適當保護，才能使用 JEA。 如需詳細資訊，請參閱 [WinRM 安全性](/powershell/scripting/learn/remoting/winrmsecurity)。

Windows Server 2012、2012 R2 和 2016 中預設已啟用 PowerShell 遠端。 您可以在提升權限的 PowerShell 視窗中執行下列命令，來啟用 PowerShell 遠端。

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>啟用 PowerShell 模組和指令碼區塊記錄 (選擇性)

下列步驟可啟用系統上所有 PowerShell 動作的記錄。 JEA 不需要 PowerShell 模組記錄，不過建議您開啟記錄，以確保使用者執行的命令會記錄在中央位置。

您可以使用群組原則設定 PowerShell 模組記錄原則。

1. 在工作站上開啟本機群組原則編輯器，或在 Active Directory 網域控制站上的群組原則管理主控台上開啟群組原則物件
2. 瀏覽至 [電腦設定]\\[系統管理範本]\\[Windows 元件]\\[Windows PowerShell] 
3. 按兩下 [開啟模組記錄] 
4. 按一下 [啟用] 
5. 在 [選項] 區段中，按一下模組名稱旁邊的 [顯示] 
6. 在快顯視窗中鍵入 `*`，記錄來自所有模組的命令。
7. 按一下 [確定]  設定原則
8. 按兩下 [開啟 PowerShell 指令碼區塊記錄] 
9. 按一下 [啟用] 
10. 按一下 [確定]  設定原則
11. (僅限已加入網域的電腦) 執行 `gpupdate` 或等待群組原則處理已更新的原則並套用設定

您也可以透過 [群組原則] 啟用全系統 PowerShell 文字記錄。

## <a name="next-steps"></a>接下來的步驟

[建立角色功能檔案](role-capabilities.md)

[建立工作階段設定檔](session-configurations.md)

## <a name="see-also"></a>另請參閱

[WinRM 安全性](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ 藍色小組](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
