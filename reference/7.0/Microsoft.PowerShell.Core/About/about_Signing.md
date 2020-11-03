---
description: 說明如何簽署腳本，讓它們符合 PowerShell 執行原則。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: 1b13abbea7f10280fa74bd6aa2061b2ba91da75c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206588"
---
# <a name="about-signing"></a>關於簽署

## <a name="short-description"></a>簡短描述
說明如何簽署腳本，讓它們符合 PowerShell 執行原則。

## <a name="long-description"></a>完整描述

受限制的執行原則不允許執行任何腳本。 **AllSigned** 和 **RemoteSigned** 執行原則會防止 PowerShell 執行沒有數位簽章的腳本。

本主題說明如何執行未簽署的選取腳本，即使執行原則是 **RemoteSigned** ，以及如何簽署腳本以供自己使用。

如需 PowerShell 執行原則的詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。

## <a name="to-permit-signed-scripts-to-run"></a>允許已簽署的腳本執行

當您第一次在電腦上啟動 PowerShell 時， **受限制** 的執行原則 (預設) 可能會生效。

**受限制** 的原則不允許執行任何腳本。

若要在您的電腦上尋找有效的執行原則，請輸入：

```powershell
Get-ExecutionPolicy
```

若要執行您在本機電腦上撰寫的未簽署腳本，以及其他使用者的已簽署腳本，請使用 [以系統管理員身分執行] 選項啟動 PowerShell，然後使用下列命令將電腦上的執行原則變更為 **RemoteSigned** ：

```powershell
Set-ExecutionPolicy RemoteSigned
```

如需詳細資訊，請參閱 Cmdlet 的說明主題 `Set-ExecutionPolicy` 。

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a>使用 RemoteSigned 執行原則執行未簽署的腳本

如果您的 PowerShell 執行原則是 **RemoteSigned** ，powershell 將不會執行從網際網路下載的未簽署腳本，包括您透過電子郵件和立即訊息程式收到的未簽署腳本。

如果您嘗試執行下載的腳本，PowerShell 會顯示下列錯誤訊息：

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

執行腳本之前，請先檢查程式碼，以確定您信任它。
腳本的效果與任何可執行檔程式相同。

若要執行未簽署的腳本，請使用 Unblock-File Cmdlet，或使用下列程式。

1. 將腳本檔案儲存在您的電腦上。
2. 按一下 [開始]，按一下 [我的電腦]，然後找出已儲存的腳本檔案。
3. 在腳本檔案上按一下滑鼠右鍵，然後按一下 [屬性]。
4. 按一下 [解除封鎖]。

如果從網際網路下載的腳本經過數位簽署，但您尚未選擇信任其發行者，則 PowerShell 會顯示下列訊息：

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

如果您信任發行者，請選取 [執行一次] 或 [永遠執行]。 如果您不信任發行者，請選取 [永不執行] 或 [不要執行]。 如果您選取 [永不執行] 或 [永遠執行]，PowerShell 將不會再次提示您輸入此發行者。

## <a name="methods-of-signing-scripts"></a>簽署腳本的方法

您可以簽署您所撰寫的腳本，以及您從其他來源取得的腳本。 簽署任何腳本之前，請檢查每個命令以確認可安全執行。

如需程式碼簽署的最佳作法，請參閱 [程式碼簽署最佳做法](/previous-versions/windows/hardware/design/dn653556(v=vs.85))。

如需如何簽署指令檔的詳細資訊，請參閱 [get-authenticodesignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)。

在 `New-SelfSignedCertificate` PowerShell 3.0 的 PKI 模組中引進的 Cmdlet 會建立適用于測試的自我簽署憑證。 如需詳細資訊，請參閱 New-SelfSignedCertificate Cmdlet 的說明主題。

若要將數位簽章新增至腳本，您必須使用程式碼簽署憑證來簽署。 有兩種類型的憑證適用于簽署腳本檔案：

- 憑證授權單位單位所建立的憑證：為了付費，公開憑證授權單位單位會驗證您的身分識別，並提供程式碼簽署憑證。 當您向知名的憑證授權單位單位購買憑證時，您可以與其他執行 Windows 的電腦上的使用者共用您的腳本，因為這些電腦信任憑證授權單位單位。

- 您建立的憑證：您可以建立自我簽署的憑證，讓您的電腦成為建立憑證的授權單位。 此憑證是免費的，可讓您在電腦上撰寫、簽署和執行腳本。 不過，自我簽署憑證所簽署的腳本將不會在其他電腦上執行。

一般而言，您只會使用自我簽署的憑證來簽署您自行撰寫用的腳本，以及簽署您從已驗證為安全的其他來源取得的腳本。 它並不適用于將共用的腳本，即使在企業內也是如此。

如果您建立自我簽署憑證，請務必在您的憑證上啟用強式私密金鑰保護。 這可防止惡意程式代表您簽署腳本。 本主題的結尾包含這些指示。

## <a name="create-a-self-signed-certificate"></a>建立自我簽署憑證

若要在中建立自我簽署憑證，請使用 `New-SelfSignedCertificate` PKI 模組中的 Cmdlet。 此模組是在 PowerShell 3.0 中引進，且包含在 Windows 8 和 Windows Server 2012 中。 如需詳細資訊，請參閱 Cmdlet 的說明主題 `New-SelfSignedCertificate` 。

若要在舊版 Windows 中建立自我簽署憑證，請使用憑證建立工具 `MakeCert.exe` 。 這項工具組含在 Microsoft .NET SDK (1.1 版和更新版本中) 和 Microsoft Windows SDK。

如需有關 MakeCert.exe 工具的語法和參數描述的詳細資訊，請參閱 [憑證建立工具 ( # A1) ](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80))。

若要使用 MakeCert.exe 工具來建立憑證，請在 [SDK 命令提示字元] 視窗中執行下列命令。

注意：第一個命令會建立您電腦的本機憑證授權單位單位。 第二個命令會從憑證授權單位單位產生個人憑證。

注意：您可以在命令出現時，完全複製或輸入命令。 雖然您可以變更憑證名稱，但不需要任何替代。

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

MakeCert.exe 工具會提示您輸入私密金鑰密碼。 密碼可確保沒有人可在未經您同意的情況下，使用或存取該憑證。
建立並輸入您可以記住的密碼。 您稍後將會使用此密碼來取得憑證。

若要確認憑證是否已正確產生，請使用下列命令來取得電腦上憑證存放區中的憑證。 您在檔案系統目錄中找不到憑證檔案。

在 PowerShell 提示字元中，輸入：

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

此命令會使用 PowerShell 憑證提供者來查看憑證的相關資訊。

如果已建立憑證，則輸出會在顯示中顯示識別憑證的憑證 **指紋** ，如下所示：

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a>簽署腳本

建立自我簽署憑證之後，您就可以簽署腳本。 如果您使用 **AllSigned** 執行原則，簽署腳本會允許您在電腦上執行腳本。

下列範例腳本會 `Add-Signature.ps1` 簽署腳本。 但是，如果您使用 **AllSigned** 執行原則，則必須先簽署腳本， `Add-Signature.ps1` 然後再執行它。

> [!IMPORTANT]
> 您必須使用 ASCII 或 UTF8NoBOM 編碼來儲存腳本。您可以簽署使用不同編碼方式的腳本檔案。 但是腳本無法執行，或包含腳本的模組無法匯入。

若要使用此腳本，請將下列文字複製到文字檔中，並將其命名為 `Add-Signature.ps1` 。

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

若要簽署 `Add-Signature.ps1` 腳本檔案，請在 PowerShell 命令提示字元中輸入下列命令：

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

腳本簽署之後，您就可以在本機電腦上執行它。 不過，腳本不會在 PowerShell 執行原則需要來自受信任授權單位的數位簽章之電腦上執行。 如果您嘗試，PowerShell 會顯示下列錯誤訊息：

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

如果當您執行未寫入的腳本時，PowerShell 會顯示此訊息，請將檔案視為處理任何未簽署的腳本。 檢查程式碼，以判斷您是否可以信任腳本。

## <a name="enable-strong-private-key-protection-for-your-certificate"></a>為您的憑證啟用強式私密金鑰保護

如果您的電腦上有私人憑證，惡意軟體可能會代表您簽署腳本，以授權 PowerShell 執行它們。

若要防止您自動簽署，請使用憑證管理員將 `Certmgr.exe` 簽署憑證匯出至檔案 `.pfx` 。 憑證管理員包含在 Microsoft .NET SDK、Microsoft Windows SDK 和 internet Explorer 中。

若要匯出憑證：

1. 啟動 [憑證管理員]。
2. 選取 PowerShell 本機憑證根目錄所發行的憑證。
3. 按一下 [匯出]，以啟動 [憑證匯出嚮導]。
4. 選取 [是，匯出私密金鑰]，然後按 [下一步]。
5. 選取 [啟用加強保護]。
6. 輸入密碼，然後再輸入一次以確認。
7. 輸入副檔名為 .pfx 的檔案名。
8. 按一下 [完成]。

若要重新匯入憑證：

1. 啟動 [憑證管理員]。
2. 按一下 [匯入] 以啟動 [憑證匯入嚮導]。
3. 開啟您在匯出程式期間建立的 .pfx 檔案的位置。
4. 在 [密碼] 頁面上，選取 [啟用加強私密金鑰保護]，然後輸入您在匯出過程中指派的密碼。
5. 選取 [個人] 憑證存放區。
6. 按一下 [完成]。

## <a name="prevent-the-signature-from-expiring"></a>防止簽章過期

在簽署憑證到期之前，腳本中的數位簽章是有效的，只要時間戳記伺服器可以確認簽署憑證有效時腳本已簽署。

因為大部分的簽署憑證僅適用于一年，所以使用時間戳伺服器可確保使用者可以使用您的腳本數年的時間。

## <a name="see-also"></a>另請參閱

[about_Execution_Policies](about_Execution_Policies.md)

[about_Profiles](about_Profiles.md)

[Get-executionpolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[程式碼簽署簡介](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))
