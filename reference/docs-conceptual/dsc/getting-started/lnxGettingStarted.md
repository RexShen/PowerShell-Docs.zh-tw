---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 開始使用 Linux 預期狀態設定 (DSC)
ms.openlocfilehash: 64657dda04fa2df97fa2ad7c7a5c2d15b66a270a
ms.sourcegitcommit: 4bb44f183dcbfa8dced57f075812e02d3b45fd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301330"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="2e51f-103">開始使用 Linux 預期狀態設定 (DSC)</span><span class="sxs-lookup"><span data-stu-id="2e51f-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="2e51f-104">本主題說明如何開始使用 Linux 的 PowerShell 預期狀態設定 (DSC)。</span><span class="sxs-lookup"><span data-stu-id="2e51f-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="2e51f-105">如需 DSC 的一般資訊，請參閱[開始使用 Windows PowerShell 預期狀態設定](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2e51f-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="2e51f-106">支援的 Linux 作業系統版本</span><span class="sxs-lookup"><span data-stu-id="2e51f-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="2e51f-107">DSC for Linux 支援下列 Linux 作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="2e51f-107">The following Linux operating system versions are supported by DSC for Linux.</span></span>

- <span data-ttu-id="2e51f-108">CentOS 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2e51f-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="2e51f-109">Debian GNU/Linux 6、7 及 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2e51f-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="2e51f-110">Oracle Linux 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2e51f-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="2e51f-111">Red Hat Enterprise Linux Server 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2e51f-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="2e51f-112">SUSE Linux Enterprise Server 10、11 和 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2e51f-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="2e51f-113">Ubuntu Server 12.04 LTS、14.04 LTS、16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="2e51f-113">Ubuntu Server 12.04 LTS, 14.04 LTS, 16.04 LTS (x86/x64)</span></span>

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="2e51f-114">安裝 DSC for Linux</span><span class="sxs-lookup"><span data-stu-id="2e51f-114">Installing DSC for Linux</span></span>

<span data-ttu-id="2e51f-115">您必須先安裝[開放式管理基礎結構 (OMI)](https://github.com/Microsoft/omi)，才能安裝 DSC for Linux。</span><span class="sxs-lookup"><span data-stu-id="2e51f-115">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="2e51f-116">安裝 OMI</span><span class="sxs-lookup"><span data-stu-id="2e51f-116">Installing OMI</span></span>

<span data-ttu-id="2e51f-117">Linux 的 Desired State Configuration 需要開放式管理基礎結構 (OMI) CIM 伺服器版本 1.0.8.1 或更新的版本。</span><span class="sxs-lookup"><span data-stu-id="2e51f-117">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="2e51f-118">OMI 可以從 The Open Group 下載：[開放式管理基礎結構 (OMI)](https://github.com/Microsoft/omi)。</span><span class="sxs-lookup"><span data-stu-id="2e51f-118">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="2e51f-119">若要安裝 OMI，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。</span><span class="sxs-lookup"><span data-stu-id="2e51f-119">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="2e51f-120">RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="2e51f-120">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="2e51f-121">DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。</span><span class="sxs-lookup"><span data-stu-id="2e51f-121">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="2e51f-122">ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。</span><span class="sxs-lookup"><span data-stu-id="2e51f-122">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="2e51f-123">若要判斷已安裝的 OpenSSL 版本，請執行命令 `openssl version`。</span><span class="sxs-lookup"><span data-stu-id="2e51f-123">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="2e51f-124">執行下列命令，在 CentOS 7 x64 系統上安裝 OMI。</span><span class="sxs-lookup"><span data-stu-id="2e51f-124">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="2e51f-125">安裝 DSC</span><span class="sxs-lookup"><span data-stu-id="2e51f-125">Installing DSC</span></span>

<span data-ttu-id="2e51f-126">您可以從[這裡](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294)下載 DSC for Linux。</span><span class="sxs-lookup"><span data-stu-id="2e51f-126">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="2e51f-127">若要安裝 DSC，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。</span><span class="sxs-lookup"><span data-stu-id="2e51f-127">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="2e51f-128">RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="2e51f-128">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="2e51f-129">DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。</span><span class="sxs-lookup"><span data-stu-id="2e51f-129">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="2e51f-130">ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。</span><span class="sxs-lookup"><span data-stu-id="2e51f-130">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="2e51f-131">若要判斷已安裝的 OpenSSL 版本，請執行命令 openssl version。</span><span class="sxs-lookup"><span data-stu-id="2e51f-131">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="2e51f-132">執行下列命令，在 CentOS 7 x64 系統上安裝 DSC。</span><span class="sxs-lookup"><span data-stu-id="2e51f-132">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="2e51f-133">使用 DSC for Linux</span><span class="sxs-lookup"><span data-stu-id="2e51f-133">Using DSC for Linux</span></span>

<span data-ttu-id="2e51f-134">下列章節說明如何在 Linux 電腦上建立並執行 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="2e51f-134">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="2e51f-135">建立設定 MOF 文件</span><span class="sxs-lookup"><span data-stu-id="2e51f-135">Creating a configuration MOF document</span></span>

<span data-ttu-id="2e51f-136">Windows PowerShell 設定關鍵字可用來建立 Windows 電腦的設定，就像 Linux 電腦一樣。</span><span class="sxs-lookup"><span data-stu-id="2e51f-136">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="2e51f-137">下列步驟說明如何使用 Windows PowerShell 建立 Linux 電腦的設定文件。</span><span class="sxs-lookup"><span data-stu-id="2e51f-137">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="2e51f-138">匯入 nx 模組。</span><span class="sxs-lookup"><span data-stu-id="2e51f-138">Import the nx module.</span></span> <span data-ttu-id="2e51f-139">Nx Windows PowerShell 模組包含 DSC for Linux 內建資源的結構描述，並且必須安裝到本機電腦，然後匯入設定中。</span><span class="sxs-lookup"><span data-stu-id="2e51f-139">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="2e51f-140">若要安裝 nx 模組，請將 nx 模組目錄複製到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 或 `$PSHOME\Modules`。</span><span class="sxs-lookup"><span data-stu-id="2e51f-140">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="2e51f-141">nx 模組包含在 DSC for Linux 安裝套件中。</span><span class="sxs-lookup"><span data-stu-id="2e51f-141">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="2e51f-142">若要在您的設定中匯入 nx 模組，請使用 `Import-DSCResource` 命令：</span><span class="sxs-lookup"><span data-stu-id="2e51f-142">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="2e51f-143">定義設定，然後產生設定文件：</span><span class="sxs-lookup"><span data-stu-id="2e51f-143">Define a configuration and generate the configuration document:</span></span>

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

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="2e51f-144">將設定推送至 Linux 電腦</span><span class="sxs-lookup"><span data-stu-id="2e51f-144">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="2e51f-145">設定文件 (MOF 檔案) 可以使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 推送至 Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="2e51f-145">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="2e51f-146">若要從遠端針對 Linux 電腦使用此 Cmdlet 及 [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) \(英文\) 或 [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) \(英文\) Cmdlet，您必須使用 CIMSession。</span><span class="sxs-lookup"><span data-stu-id="2e51f-146">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="2e51f-147">[New-CimSession](/powershell/module/CimCmdlets/New-CimSession) Cmdlet 會用來建立 Linux 電腦的 CIMSession。</span><span class="sxs-lookup"><span data-stu-id="2e51f-147">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="2e51f-148">下列程式碼示範如何建立 DSC for Linux 的 CIMSession。</span><span class="sxs-lookup"><span data-stu-id="2e51f-148">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

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
> <span data-ttu-id="2e51f-149">針對 [推送] 模式，使用者認證必須是在 Linux 電腦上的根使用者。</span><span class="sxs-lookup"><span data-stu-id="2e51f-149">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="2e51f-150">DSC for Linux 僅支援 SSL/TLS 連線，必須使用 `New-CimSession` 並將 –UseSSL 參數設為 $true。</span><span class="sxs-lookup"><span data-stu-id="2e51f-150">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="2e51f-151">OMI (DSC) 所使用的 SSL 憑證在此檔案中指定：`/etc/opt/omi/conf/omiserver.conf`，屬性為：pemfile 和 keyfile。</span><span class="sxs-lookup"><span data-stu-id="2e51f-151">The SSL certificate used by OMI (for DSC) is specified in the file: `/etc/opt/omi/conf/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="2e51f-152">如果此憑證不受您正在執行 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) Cmdlet 的 Windows 電腦信任，您可以使用 CIMSession 選項 `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true` 選擇忽略憑證驗證</span><span class="sxs-lookup"><span data-stu-id="2e51f-152">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="2e51f-153">執行下列命令，將 DSC 設定推送至 Linux 節點。</span><span class="sxs-lookup"><span data-stu-id="2e51f-153">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="2e51f-154">以提取伺服器散發設定</span><span class="sxs-lookup"><span data-stu-id="2e51f-154">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="2e51f-155">可以用提取伺服器來散發設定給 Linux 電腦，就像 Windows 電腦一樣。</span><span class="sxs-lookup"><span data-stu-id="2e51f-155">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="2e51f-156">如需使用提取伺服器的指引，請參閱 [Windows PowerShell 預期狀態設定提取伺服器](../pull-server/pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="2e51f-156">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="2e51f-157">如需使用提取伺服器與 Linux 電腦的其他資訊與限制，請參閱 Linux 的預期狀態設定版本資訊。</span><span class="sxs-lookup"><span data-stu-id="2e51f-157">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="2e51f-158">在本機使用設定</span><span class="sxs-lookup"><span data-stu-id="2e51f-158">Working with configurations locally</span></span>

<span data-ttu-id="2e51f-159">DSC for Linux 包含指令碼以使用本機 Linux 電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="2e51f-159">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="2e51f-160">這些指令碼位於 `/opt/microsoft/dsc/Scripts` 並且包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="2e51f-160">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="2e51f-161">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="2e51f-161">GetDscConfiguration.py</span></span>

<span data-ttu-id="2e51f-162">傳回套用到此電腦的目前設定。</span><span class="sxs-lookup"><span data-stu-id="2e51f-162">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="2e51f-163">類似於 Windows PowerShell Cmdlet 的 `Get-DscConfiguration` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e51f-163">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="2e51f-164">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="2e51f-164">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="2e51f-165">傳回套用到此電腦的目前中繼設定。</span><span class="sxs-lookup"><span data-stu-id="2e51f-165">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="2e51f-166">類似於 [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e51f-166">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="2e51f-167">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="2e51f-167">InstallModule.py</span></span>

<span data-ttu-id="2e51f-168">安裝自訂 DSC 資源模組。</span><span class="sxs-lookup"><span data-stu-id="2e51f-168">Installs a custom DSC resource module.</span></span> <span data-ttu-id="2e51f-169">需要包含模組共用物件的程式庫和結構描述 MOF 檔案的 .zip 檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="2e51f-169">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="2e51f-170">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="2e51f-170">RemoveModule.py</span></span>

<span data-ttu-id="2e51f-171">移除自訂的 DSC 資源模組。</span><span class="sxs-lookup"><span data-stu-id="2e51f-171">Removes a custom DSC resource module.</span></span> <span data-ttu-id="2e51f-172">需要有要移除的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="2e51f-172">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="2e51f-173">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="2e51f-173">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="2e51f-174">將設定 MOF 檔案套用至電腦。</span><span class="sxs-lookup"><span data-stu-id="2e51f-174">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="2e51f-175">類似於 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e51f-175">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="2e51f-176">需要有要套用的設定 MOF 路徑。</span><span class="sxs-lookup"><span data-stu-id="2e51f-176">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="2e51f-177">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="2e51f-177">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="2e51f-178">將中繼設定 MOF 檔案套用至電腦。</span><span class="sxs-lookup"><span data-stu-id="2e51f-178">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="2e51f-179">類似於 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e51f-179">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="2e51f-180">需要有要套用的中繼設定 MOF 路徑。</span><span class="sxs-lookup"><span data-stu-id="2e51f-180">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="2e51f-181">Linux 記錄檔的 PowerShell 預期狀態設定</span><span class="sxs-lookup"><span data-stu-id="2e51f-181">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="2e51f-182">會對 DSC for Linux 訊息產生下列記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2e51f-182">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="2e51f-183">記錄檔</span><span class="sxs-lookup"><span data-stu-id="2e51f-183">Log file</span></span>|<span data-ttu-id="2e51f-184">目錄</span><span class="sxs-lookup"><span data-stu-id="2e51f-184">Directory</span></span>|<span data-ttu-id="2e51f-185">描述</span><span class="sxs-lookup"><span data-stu-id="2e51f-185">Description</span></span>|
|---|---|---|
|<span data-ttu-id="2e51f-186">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="2e51f-186">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="2e51f-187">OMI CIM 伺服器作業相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="2e51f-187">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="2e51f-188">**dsc.log**</span><span class="sxs-lookup"><span data-stu-id="2e51f-188">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="2e51f-189">與本機設定管理員 (LCM) 和 DSC 資源作業的作業相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="2e51f-189">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
