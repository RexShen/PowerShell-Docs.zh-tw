---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 開始使用 Linux 預期狀態設定 (DSC)
description: 本主題說明如何開始使用 Linux 的 PowerShell 預期狀態設定 (DSC)。
ms.openlocfilehash: 826707654a297306c39d4dfcfd3941f56b7cf91d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651123"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="efbef-104">開始使用 Linux 預期狀態設定 (DSC)</span><span class="sxs-lookup"><span data-stu-id="efbef-104">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="efbef-105">本主題說明如何開始使用 Linux 的 PowerShell 預期狀態設定 (DSC)。</span><span class="sxs-lookup"><span data-stu-id="efbef-105">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span>
<span data-ttu-id="efbef-106">如需 DSC 的一般資訊，請參閱[開始使用 Windows PowerShell 預期狀態設定](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="efbef-106">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="efbef-107">支援的 Linux 作業系統版本</span><span class="sxs-lookup"><span data-stu-id="efbef-107">Supported Linux operation system versions</span></span>

<span data-ttu-id="efbef-108">DSC for Linux 支援下列 Linux 作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="efbef-108">The following Linux operating system versions are supported by DSC for Linux.</span></span>

- <span data-ttu-id="efbef-109">CentOS 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="efbef-109">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="efbef-110">Debian GNU/Linux 6、7 及 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="efbef-110">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="efbef-111">Oracle Linux 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="efbef-111">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="efbef-112">Red Hat Enterprise Linux Server 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="efbef-112">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="efbef-113">SUSE Linux Enterprise Server 10、11 和 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="efbef-113">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="efbef-114">Ubuntu Server 12.04 LTS、14.04 LTS、16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="efbef-114">Ubuntu Server 12.04 LTS, 14.04 LTS, 16.04 LTS (x86/x64)</span></span>

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="efbef-115">安裝 DSC for Linux</span><span class="sxs-lookup"><span data-stu-id="efbef-115">Installing DSC for Linux</span></span>

<span data-ttu-id="efbef-116">您必須先安裝[開放式管理基礎結構 (OMI)](https://github.com/Microsoft/omi)，才能安裝 DSC for Linux。</span><span class="sxs-lookup"><span data-stu-id="efbef-116">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="efbef-117">安裝 OMI</span><span class="sxs-lookup"><span data-stu-id="efbef-117">Installing OMI</span></span>

<span data-ttu-id="efbef-118">Linux 的 Desired State Configuration 需要開放式管理基礎結構 (OMI) CIM 伺服器版本 1.0.8.1 或更新的版本。</span><span class="sxs-lookup"><span data-stu-id="efbef-118">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="efbef-119">OMI 可以從 The Open Group 下載：[開放式管理基礎結構 (OMI)](https://github.com/Microsoft/omi)。</span><span class="sxs-lookup"><span data-stu-id="efbef-119">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="efbef-120">若要安裝 OMI，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。</span><span class="sxs-lookup"><span data-stu-id="efbef-120">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="efbef-121">RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="efbef-121">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="efbef-122">DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。</span><span class="sxs-lookup"><span data-stu-id="efbef-122">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="efbef-123">ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。</span><span class="sxs-lookup"><span data-stu-id="efbef-123">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="efbef-124">若要判斷已安裝的 OpenSSL 版本，請執行命令 `openssl version`。</span><span class="sxs-lookup"><span data-stu-id="efbef-124">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="efbef-125">執行下列命令，在 CentOS 7 x64 系統上安裝 OMI。</span><span class="sxs-lookup"><span data-stu-id="efbef-125">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="efbef-126">安裝 DSC</span><span class="sxs-lookup"><span data-stu-id="efbef-126">Installing DSC</span></span>

<span data-ttu-id="efbef-127">適用於 Linux 的 DSC 可從存放庫中的 [PowerShell-DSC-for-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294) \(英文\) 存放庫下載。</span><span class="sxs-lookup"><span data-stu-id="efbef-127">DSC for Linux is available for download from the [PowerShell-DSC-for-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294) repository in the repository.</span></span>

<span data-ttu-id="efbef-128">若要安裝 DSC，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。</span><span class="sxs-lookup"><span data-stu-id="efbef-128">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="efbef-129">RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="efbef-129">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="efbef-130">DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。</span><span class="sxs-lookup"><span data-stu-id="efbef-130">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="efbef-131">ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。</span><span class="sxs-lookup"><span data-stu-id="efbef-131">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="efbef-132">若要判斷已安裝的 OpenSSL 版本，請執行命令 openssl version。</span><span class="sxs-lookup"><span data-stu-id="efbef-132">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="efbef-133">執行下列命令，在 CentOS 7 x64 系統上安裝 DSC。</span><span class="sxs-lookup"><span data-stu-id="efbef-133">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="efbef-134">使用 DSC for Linux</span><span class="sxs-lookup"><span data-stu-id="efbef-134">Using DSC for Linux</span></span>

<span data-ttu-id="efbef-135">下列章節說明如何在 Linux 電腦上建立並執行 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="efbef-135">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="efbef-136">建立設定 MOF 文件</span><span class="sxs-lookup"><span data-stu-id="efbef-136">Creating a configuration MOF document</span></span>

<span data-ttu-id="efbef-137">Windows PowerShell 設定關鍵字可用來建立 Windows 電腦的設定，就像 Linux 電腦一樣。</span><span class="sxs-lookup"><span data-stu-id="efbef-137">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="efbef-138">下列步驟說明如何使用 Windows PowerShell 建立 Linux 電腦的設定文件。</span><span class="sxs-lookup"><span data-stu-id="efbef-138">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="efbef-139">匯入 nx 模組。</span><span class="sxs-lookup"><span data-stu-id="efbef-139">Import the nx module.</span></span> <span data-ttu-id="efbef-140">Nx Windows PowerShell 模組包含 DSC for Linux 內建資源的結構描述，並且必須安裝到本機電腦，然後匯入設定中。</span><span class="sxs-lookup"><span data-stu-id="efbef-140">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="efbef-141">若要安裝 nx 模組，請將 nx 模組目錄複製到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 或 `$PSHOME\Modules`。</span><span class="sxs-lookup"><span data-stu-id="efbef-141">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="efbef-142">nx 模組包含在 DSC for Linux 安裝套件中。</span><span class="sxs-lookup"><span data-stu-id="efbef-142">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="efbef-143">若要在您的設定中匯入 nx 模組，請使用 `Import-DSCResource` 命令：</span><span class="sxs-lookup"><span data-stu-id="efbef-143">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="efbef-144">定義設定，然後產生設定文件：</span><span class="sxs-lookup"><span data-stu-id="efbef-144">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="efbef-145">將設定推送至 Linux 電腦</span><span class="sxs-lookup"><span data-stu-id="efbef-145">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="efbef-146">設定文件 (MOF 檔案) 可以使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 推送至 Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="efbef-146">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="efbef-147">若要從遠端針對 Linux 電腦使用此 Cmdlet 及 [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) \(英文\) 或 [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) \(英文\) Cmdlet，您必須使用 CIMSession。</span><span class="sxs-lookup"><span data-stu-id="efbef-147">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="efbef-148">[New-CimSession](/powershell/module/CimCmdlets/New-CimSession) Cmdlet 是用來針對 Linux 電腦建立 **CIMSession** 。</span><span class="sxs-lookup"><span data-stu-id="efbef-148">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a **CIMSession** to the Linux computer.</span></span>

<span data-ttu-id="efbef-149">下列程式碼示範如何建立 DSC for Linux 的 CIMSession。</span><span class="sxs-lookup"><span data-stu-id="efbef-149">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> <span data-ttu-id="efbef-150">針對 [推送] 模式，使用者認證必須是在 Linux 電腦上的根使用者。</span><span class="sxs-lookup"><span data-stu-id="efbef-150">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span> <span data-ttu-id="efbef-151">DSC for Linux 僅支援 SSL/TLS 連線，必須使用 `New-CimSession` 並將 –UseSSL 參數設為 $true。</span><span class="sxs-lookup"><span data-stu-id="efbef-151">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span> <span data-ttu-id="efbef-152">OMI (DSC) 所使用的 SSL 憑證在此檔案中指定：`/etc/opt/omi/conf/omiserver.conf`，屬性為：pemfile 和 keyfile。</span><span class="sxs-lookup"><span data-stu-id="efbef-152">The SSL certificate used by OMI (for DSC) is specified in the file: `/etc/opt/omi/conf/omiserver.conf` with the properties: pemfile and keyfile.</span></span> <span data-ttu-id="efbef-153">如果此憑證不受您正在執行 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) Cmdlet 的 Windows 電腦信任，您可以使用 CIMSession 選項 `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true` 選擇忽略憑證驗證</span><span class="sxs-lookup"><span data-stu-id="efbef-153">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="efbef-154">執行下列命令，將 DSC 設定推送至 Linux 節點。</span><span class="sxs-lookup"><span data-stu-id="efbef-154">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="efbef-155">以提取伺服器散發設定</span><span class="sxs-lookup"><span data-stu-id="efbef-155">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="efbef-156">可以用提取伺服器來散發設定給 Linux 電腦，就像 Windows 電腦一樣。</span><span class="sxs-lookup"><span data-stu-id="efbef-156">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="efbef-157">如需使用提取伺服器的指引，請參閱 [Windows PowerShell 預期狀態設定提取伺服器](../pull-server/pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="efbef-157">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="efbef-158">如需使用提取伺服器與 Linux 電腦的其他資訊與限制，請參閱 Linux 的預期狀態設定版本資訊。</span><span class="sxs-lookup"><span data-stu-id="efbef-158">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="efbef-159">在本機使用設定</span><span class="sxs-lookup"><span data-stu-id="efbef-159">Working with configurations locally</span></span>

<span data-ttu-id="efbef-160">DSC for Linux 包含指令碼以使用本機 Linux 電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="efbef-160">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="efbef-161">這些指令碼位於 `/opt/microsoft/dsc/Scripts` 並且包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="efbef-161">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="efbef-162">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="efbef-162">GetDscConfiguration.py</span></span>

  <span data-ttu-id="efbef-163">傳回套用到此電腦的目前設定。</span><span class="sxs-lookup"><span data-stu-id="efbef-163">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="efbef-164">類似於 Windows PowerShell Cmdlet 的 `Get-DscConfiguration` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="efbef-164">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

  `# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="efbef-165">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="efbef-165">GetDscLocalConfigurationManager.py</span></span>

  <span data-ttu-id="efbef-166">傳回套用到此電腦的目前中繼設定。</span><span class="sxs-lookup"><span data-stu-id="efbef-166">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="efbef-167">類似於 [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="efbef-167">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

  `# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="efbef-168">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="efbef-168">InstallModule.py</span></span>

  <span data-ttu-id="efbef-169">安裝自訂 DSC 資源模組。</span><span class="sxs-lookup"><span data-stu-id="efbef-169">Installs a custom DSC resource module.</span></span> <span data-ttu-id="efbef-170">需要包含模組共用物件的程式庫和結構描述 MOF 檔案的 .zip 檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="efbef-170">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

 `# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="efbef-171">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="efbef-171">RemoveModule.py</span></span>

  <span data-ttu-id="efbef-172">移除自訂的 DSC 資源模組。</span><span class="sxs-lookup"><span data-stu-id="efbef-172">Removes a custom DSC resource module.</span></span> <span data-ttu-id="efbef-173">需要有要移除的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="efbef-173">Requires the name of the module to remove.</span></span>

  `# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="efbef-174">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="efbef-174">StartDscLocalConfigurationManager.py</span></span>

  <span data-ttu-id="efbef-175">將設定 MOF 檔案套用至電腦。</span><span class="sxs-lookup"><span data-stu-id="efbef-175">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="efbef-176">類似於 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="efbef-176">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="efbef-177">需要有要套用的設定 MOF 路徑。</span><span class="sxs-lookup"><span data-stu-id="efbef-177">Requires the path to the configuration MOF to apply.</span></span>

  `# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="efbef-178">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="efbef-178">SetDscLocalConfigurationManager.py</span></span>

  <span data-ttu-id="efbef-179">將中繼設定 MOF 檔案套用至電腦。</span><span class="sxs-lookup"><span data-stu-id="efbef-179">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="efbef-180">類似於 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="efbef-180">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="efbef-181">需要有要套用的中繼設定 MOF 路徑。</span><span class="sxs-lookup"><span data-stu-id="efbef-181">Requires the path to the Meta Configuration MOF to apply.</span></span>

  `# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="efbef-182">Linux 記錄檔的 PowerShell 預期狀態設定</span><span class="sxs-lookup"><span data-stu-id="efbef-182">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="efbef-183">會對 DSC for Linux 訊息產生下列記錄檔。</span><span class="sxs-lookup"><span data-stu-id="efbef-183">The following log files are generated for DSC for Linux messages.</span></span>

|     <span data-ttu-id="efbef-184">記錄檔</span><span class="sxs-lookup"><span data-stu-id="efbef-184">Log file</span></span>      |     <span data-ttu-id="efbef-185">目錄</span><span class="sxs-lookup"><span data-stu-id="efbef-185">Directory</span></span>      |                                               <span data-ttu-id="efbef-186">描述</span><span class="sxs-lookup"><span data-stu-id="efbef-186">Description</span></span>                                                |
| ----------------- | ------------------ | -------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="efbef-187">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="efbef-187">**omiserver.log**</span></span> | `/var/opt/omi/log` | <span data-ttu-id="efbef-188">OMI CIM 伺服器作業相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="efbef-188">Messages relating to the operation of the OMI CIM server.</span></span>                                                |
| <span data-ttu-id="efbef-189">**dsc.log**</span><span class="sxs-lookup"><span data-stu-id="efbef-189">**dsc.log**</span></span>       | `/var/opt/omi/log` | <span data-ttu-id="efbef-190">與本機設定管理員 (LCM) 和 DSC 資源作業的作業相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="efbef-190">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span> |
