---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "建立網域控制站"
ms.technology: powershell
ms.openlocfilehash: 80b957ed666ca626c6083041cf99c263e2e0dc27
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
### <a name="creating-a-domain-controller"></a><span data-ttu-id="238f0-103">建立網域控制站</span><span class="sxs-lookup"><span data-stu-id="238f0-103">Creating a Domain Controller</span></span>

<span data-ttu-id="238f0-104">本文假設您的電腦已加入網域。</span><span class="sxs-lookup"><span data-stu-id="238f0-104">This document assumes that your machine is domain joined.</span></span>
<span data-ttu-id="238f0-105">如果您目前沒有可加入的網域，本節可協助您使用 DSC 快速地建立網域控制站。</span><span class="sxs-lookup"><span data-stu-id="238f0-105">If you currently don't have a domain to join, this section can help you quickly stand up a domain controller using DSC.</span></span>

#### <a name="prerequisites"></a><span data-ttu-id="238f0-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="238f0-106">Prerequisites</span></span>

1.  <span data-ttu-id="238f0-107">電腦位於內部網路</span><span class="sxs-lookup"><span data-stu-id="238f0-107">The machine is on an internal network</span></span>
2.  <span data-ttu-id="238f0-108">電腦未加入現有的網域</span><span class="sxs-lookup"><span data-stu-id="238f0-108">The machine is not joined to an existing domain</span></span>
3.  <span data-ttu-id="238f0-109">電腦執行 Windows Server 2016 或已安裝 WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="238f0-109">The machine is running Windows Server 2016 or has WMF 5.0 installed</span></span>

#### <a name="install-xactivedirectory"></a><span data-ttu-id="238f0-110">安裝 xActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="238f0-110">Install xActiveDirectory</span></span>
<span data-ttu-id="238f0-111">如果您的電腦具有使用中的網際網路連線，請在提升權限的 PowerShell 視窗中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="238f0-111">If your machine has an active internet connection, run the following command in an elevated PowerShell window:</span></span>
```PowerShell
Install-Module xActiveDirectory -Force
```
<span data-ttu-id="238f0-112">如果您沒有網際網路連線，請將 xActiveDirectory 安裝到另一部電腦，然後將 xActiveDirectory 資料夾複製到您電腦上的 "C:\Program Files\WindowsPowerShell\Modules" 資料夾。</span><span class="sxs-lookup"><span data-stu-id="238f0-112">If you do not have an internet connection, install xActiveDirectory to another machine and then copy the xActiveDirectory folder to the "C:\Program Files\WindowsPowerShell\Modules" folder on your machine.</span></span>

<span data-ttu-id="238f0-113">若要確認安裝是否成功，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="238f0-113">To confirm the installation succeeded, run the following command:</span></span>
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### <a name="set-up-a-domain-with-dsc"></a><span data-ttu-id="238f0-114">使用 DSC 設定網域</span><span class="sxs-lookup"><span data-stu-id="238f0-114">Set up a domain with DSC</span></span>
<span data-ttu-id="238f0-115">複製 PowerShell 中的下列指令碼，將您的電腦設為新網域中的網域控制站。</span><span class="sxs-lookup"><span data-stu-id="238f0-115">Copy the following script in PowerShell to make your machine a Domain Controller in a new domain.</span></span>
<span data-ttu-id="238f0-116">**作者的附註︰有所提供的認證未使用的已知問題。為了安全起見，請記住您的本機系統管理員密碼。**</span><span class="sxs-lookup"><span data-stu-id="238f0-116">**AUTHOR'S NOTE: THERE IS A KNOWN ISSUE WITH THE CREDENTIALS PROVIDED NOT BEING USED.  TO BE SAFE, DON'T FORGET YOUR LOCAL ADMIN PASSWORD.**</span></span>

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }

}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
<span data-ttu-id="238f0-117">您的電腦會重新啟動幾次。</span><span class="sxs-lookup"><span data-stu-id="238f0-117">Your machine will restart a few times.</span></span>
<span data-ttu-id="238f0-118">一旦您看到 "C:\temp.txt" 檔案包含「網域已建立」，就知道處理程序完成。</span><span class="sxs-lookup"><span data-stu-id="238f0-118">You will know the process is complete once you see a file called "C:\temp.txt" containing "Domain has been created."</span></span>

#### <a name="set-up-users-and-groups"></a><span data-ttu-id="238f0-119">設定使用者和群組</span><span class="sxs-lookup"><span data-stu-id="238f0-119">Set up Users and Groups</span></span>
<span data-ttu-id="238f0-120">下列命令會設定您網域中的 Operator 和 Helpdesk 群組，以及屬於該群組的對應非系統管理員使用者。</span><span class="sxs-lookup"><span data-stu-id="238f0-120">The following commands will set up an Operator and Helpdesk group in your domain and a corresponding non-administrator user who is a member of that group.</span></span>
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

