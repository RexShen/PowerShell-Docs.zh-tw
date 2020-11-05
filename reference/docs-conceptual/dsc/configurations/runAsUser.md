---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 搭配使用認證與 DSC 資源
description: DSC 允許您提供認證至設定，使您可以在特定使用者帳戶的內容 (而非本機系統帳戶) 中套用組態設定。
ms.openlocfilehash: e4ca39e099afacd7cb06c4d9ef889f94deb73cee
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645074"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="4079d-104">搭配使用認證與 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4079d-104">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="4079d-105">適用於：Windows PowerShell 5.0、Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4079d-105">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="4079d-106">您可以在設定中使用自動 **PsDscRunAsCredential** 屬性，以一組指定的認證來執行 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4079d-106">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="4079d-107">DSC 預設會使用系統帳戶執行每項資源，</span><span class="sxs-lookup"><span data-stu-id="4079d-107">By default, DSC runs each resource as the system account.</span></span> <span data-ttu-id="4079d-108">但有些時候仍須以使用者身分執行，例如在特定使用者內容中安裝 MSI 封裝；設定使用者的登錄機碼；存取使用者的特定本機目錄；或存取網路共用等等。</span><span class="sxs-lookup"><span data-stu-id="4079d-108">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span> <span data-ttu-id="4079d-109">針對您指定至 **PSDSCRunAsCredential** 的所有帳戶， **SeInteractiveLogonRight** 皆為目標電腦的必要項目。</span><span class="sxs-lookup"><span data-stu-id="4079d-109">The **SeInteractiveLogonRight** is required, by the target machine, for any account you specify to **PSDSCRunAsCredential**.</span></span> <span data-ttu-id="4079d-110">如需詳細資訊，請參閱[帳戶權限常數](/windows/desktop/secauthz/account-rights-constants)。</span><span class="sxs-lookup"><span data-stu-id="4079d-110">For more information, see [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants).</span></span>

<span data-ttu-id="4079d-111">每個 DSC 資源都有 **PsDscRunAsCredential** 屬性，可設為任何使用者認證 ( [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件)。</span><span class="sxs-lookup"><span data-stu-id="4079d-111">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span> <span data-ttu-id="4079d-112">此認證可硬式編碼成設定中的屬性值，也可將此值設為 [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential)，如此將會在編譯設定時提示使用者輸入認證 (如需編譯設定的相關資訊，請參閱[設定](configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="4079d-112">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4079d-113">在 PowerShell 5.0 中，不支援在呼叫複合資源的設定中使用 **PsDscRunAsCredential** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4079d-113">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> <span data-ttu-id="4079d-114">在 PowerShell 5.1 中，支援在呼叫複合資源的設定中使用 **PsDscRunAsCredential** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4079d-114">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span> <span data-ttu-id="4079d-115">PowerShell 4.0 中無法使用 **PsDscRunAsCredential** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4079d-115">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="4079d-116">下列範例使用了 `Get-Credential` 提示使用者提供認證。</span><span class="sxs-lookup"><span data-stu-id="4079d-116">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span> <span data-ttu-id="4079d-117">**Registry** 資源可用於變更指定Windows 命令提示字元視窗背景色彩的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="4079d-117">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> <span data-ttu-id="4079d-118">此範例假設您的 `C:\publicKeys\targetNode.cer` 中包含有效的憑證，且該憑證的指紋為所顯示的值。</span><span class="sxs-lookup"><span data-stu-id="4079d-118">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span> <span data-ttu-id="4079d-119">如需在 DSC 設定 MOF 檔案中加密認證的資訊，請參閱[保護 MOF 檔案](../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="4079d-119">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
