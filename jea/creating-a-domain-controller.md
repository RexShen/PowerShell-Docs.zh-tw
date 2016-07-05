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
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 12fc529cfb21db260c9d1a2af87e2c3825d2ec4e

---

### 建立網域控制站

本文假設您的電腦已加入網域。
如果您目前沒有可加入的網域，本節可協助您使用 DSC 快速地建立網域控制站。

#### 必要條件

1.  電腦位於內部網路
2.  電腦未加入現有的網域
3.  電腦執行 Windows Server 2016 或已安裝 WMF 5.0

#### 安裝 xActiveDirectory
如果您的電腦具有使用中的網際網路連線，請在提升權限的 PowerShell 視窗中執行下列命令︰
```PowerShell
Install-Module xActiveDirectory -Force
```
如果您沒有網際網路連線，請將 xActiveDirectory 安裝到另一部電腦，然後將 xActiveDirectory 資料夾複製到您電腦上的 "C:\Program Files\WindowsPowerShell\Modules" 資料夾。

若要確認安裝是否成功，請執行下列命令：
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### 使用 DSC 設定網域
複製 PowerShell 中的下列指令碼，將您的電腦設為新網域中的網域控制站。
**作者的附註︰有所提供的認證未使用的已知問題。  為了安全起見，請記住您的本機系統管理員密碼。**

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
您的電腦會重新啟動幾次。
一旦您看到 "C:\temp.txt" 檔案包含「網域已建立」，就知道處理程序完成。

#### 設定使用者和群組
下列命令會設定您網域中的 Operator 和 Helpdesk 群組，以及屬於該群組的對應非系統管理員使用者。
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```




<!--HONumber=Jun16_HO4-->


