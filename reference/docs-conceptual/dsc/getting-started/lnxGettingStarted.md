---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 開始使用 Linux 預期狀態設定 (DSC)
ms.openlocfilehash: 523b91741dba57a98ac6e7ba660a776568af7065
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953885"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="aad8f-103">開始使用 Linux 預期狀態設定 (DSC)</span><span class="sxs-lookup"><span data-stu-id="aad8f-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="aad8f-104">本主題說明如何開始使用 Linux 的 PowerShell 預期狀態設定 (DSC)。</span><span class="sxs-lookup"><span data-stu-id="aad8f-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="aad8f-105">如需 DSC 的一般資訊，請參閱[開始使用 Windows PowerShell 預期狀態設定](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="aad8f-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="aad8f-106">支援的 Linux 作業系統版本</span><span class="sxs-lookup"><span data-stu-id="aad8f-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="aad8f-107">DSC for Linux 支援下列 Linux 作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="aad8f-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="aad8f-108">CentOS 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="aad8f-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="aad8f-109">Debian GNU/Linux 6、7 及 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="aad8f-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="aad8f-110">Oracle Linux 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="aad8f-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="aad8f-111">Red Hat Enterprise Linux Server 5、6 和 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="aad8f-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="aad8f-112">SUSE Linux Enterprise Server 10、11 和 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="aad8f-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="aad8f-113">Ubuntu Server 12.04 LTS、14.04 LTS 及 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="aad8f-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="aad8f-114">下表描述 DSC for Linux 必要的套件相依性。</span><span class="sxs-lookup"><span data-stu-id="aad8f-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="aad8f-115">必要的套件</span><span class="sxs-lookup"><span data-stu-id="aad8f-115">Required package</span></span> |  <span data-ttu-id="aad8f-116">描述</span><span class="sxs-lookup"><span data-stu-id="aad8f-116">Description</span></span> |  <span data-ttu-id="aad8f-117">最低版本</span><span class="sxs-lookup"><span data-stu-id="aad8f-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="aad8f-118">glibc</span><span class="sxs-lookup"><span data-stu-id="aad8f-118">glibc</span></span>| <span data-ttu-id="aad8f-119">GNU 程式庫</span><span class="sxs-lookup"><span data-stu-id="aad8f-119">GNU Library</span></span>| <span data-ttu-id="aad8f-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="aad8f-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="aad8f-121">python</span><span class="sxs-lookup"><span data-stu-id="aad8f-121">python</span></span>| <span data-ttu-id="aad8f-122">Python</span><span class="sxs-lookup"><span data-stu-id="aad8f-122">Python</span></span>| <span data-ttu-id="aad8f-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="aad8f-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="aad8f-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="aad8f-124">omiserver</span></span>| <span data-ttu-id="aad8f-125">開放式管理基礎結構</span><span class="sxs-lookup"><span data-stu-id="aad8f-125">Open Management Infrastructure</span></span>| <span data-ttu-id="aad8f-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="aad8f-126">1.0.8.1</span></span>|
| <span data-ttu-id="aad8f-127">openssl</span><span class="sxs-lookup"><span data-stu-id="aad8f-127">openssl</span></span>| <span data-ttu-id="aad8f-128">OpenSSL 程式庫</span><span class="sxs-lookup"><span data-stu-id="aad8f-128">OpenSSL Libraries</span></span>| <span data-ttu-id="aad8f-129">0.9.8 或 1.0</span><span class="sxs-lookup"><span data-stu-id="aad8f-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="aad8f-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="aad8f-130">ctypes</span></span>| <span data-ttu-id="aad8f-131">Python CTypes 程式庫</span><span class="sxs-lookup"><span data-stu-id="aad8f-131">Python CTypes library</span></span>| <span data-ttu-id="aad8f-132">必須符合 Python 版本</span><span class="sxs-lookup"><span data-stu-id="aad8f-132">Must match Python version</span></span>|
| <span data-ttu-id="aad8f-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="aad8f-133">libcurl</span></span>| <span data-ttu-id="aad8f-134">cURL http 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="aad8f-134">cURL http client library</span></span>| <span data-ttu-id="aad8f-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="aad8f-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="aad8f-136">安裝 DSC for Linux</span><span class="sxs-lookup"><span data-stu-id="aad8f-136">Installing DSC for Linux</span></span>

<span data-ttu-id="aad8f-137">您必須先安裝[開放式管理基礎結構 (OMI)](https://github.com/Microsoft/omi)，才能安裝 DSC for Linux。</span><span class="sxs-lookup"><span data-stu-id="aad8f-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="aad8f-138">安裝 OMI</span><span class="sxs-lookup"><span data-stu-id="aad8f-138">Installing OMI</span></span>

<span data-ttu-id="aad8f-139">Linux 的 Desired State Configuration 需要開放式管理基礎結構 (OMI) CIM 伺服器版本 1.0.8.1 或更新的版本。</span><span class="sxs-lookup"><span data-stu-id="aad8f-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="aad8f-140">您可以從國際開放標準組織 (The Open Group) 下載 OMI：[開放式管理基礎結構 (OMI)](https://github.com/Microsoft/omi)。</span><span class="sxs-lookup"><span data-stu-id="aad8f-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="aad8f-141">若要安裝 OMI，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。</span><span class="sxs-lookup"><span data-stu-id="aad8f-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="aad8f-142">RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="aad8f-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="aad8f-143">DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。</span><span class="sxs-lookup"><span data-stu-id="aad8f-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="aad8f-144">ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。</span><span class="sxs-lookup"><span data-stu-id="aad8f-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="aad8f-145">若要判斷已安裝的 OpenSSL 版本，請執行命令 `openssl version`。</span><span class="sxs-lookup"><span data-stu-id="aad8f-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="aad8f-146">執行下列命令，在 CentOS 7 x64 系統上安裝 OMI。</span><span class="sxs-lookup"><span data-stu-id="aad8f-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="aad8f-147">安裝 DSC</span><span class="sxs-lookup"><span data-stu-id="aad8f-147">Installing DSC</span></span>

<span data-ttu-id="aad8f-148">您可以從[這裡](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294)下載 Linux 的 DSC。</span><span class="sxs-lookup"><span data-stu-id="aad8f-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="aad8f-149">若要安裝 DSC，請安裝適用於您的 Linux 系統 (.rpm 或.deb) 和 OpenSSL 版本 (ssl_098 或 ssl_100) 與架構 (x64/x86) 的套件。</span><span class="sxs-lookup"><span data-stu-id="aad8f-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="aad8f-150">RPM 套件適用於 CentOS、Red Hat Enterprise Linux、SUSE Linux Enterprise Server 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="aad8f-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="aad8f-151">DEB 套件適用於 Debian GNU/Linux 和 Ubuntu Server。</span><span class="sxs-lookup"><span data-stu-id="aad8f-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="aad8f-152">ssl_098 套件則適用於安裝 OpenSSL 0.9.8 的電腦，而 ssl_100 套件則適用於安裝 OpenSSL 1.0 的電腦。</span><span class="sxs-lookup"><span data-stu-id="aad8f-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="aad8f-153">若要判斷已安裝的 OpenSSL 版本，請執行命令 openssl version。</span><span class="sxs-lookup"><span data-stu-id="aad8f-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="aad8f-154">執行下列命令，在 CentOS 7 x64 系統上安裝 DSC。</span><span class="sxs-lookup"><span data-stu-id="aad8f-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="aad8f-155">使用 DSC for Linux</span><span class="sxs-lookup"><span data-stu-id="aad8f-155">Using DSC for Linux</span></span>

<span data-ttu-id="aad8f-156">下列章節說明如何在 Linux 電腦上建立並執行 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="aad8f-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="aad8f-157">建立設定 MOF 文件</span><span class="sxs-lookup"><span data-stu-id="aad8f-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="aad8f-158">Windows PowerShell 設定關鍵字可用來建立 Windows 電腦的設定，就像 Linux 電腦一樣。</span><span class="sxs-lookup"><span data-stu-id="aad8f-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="aad8f-159">下列步驟說明如何使用 Windows PowerShell 建立 Linux 電腦的設定文件。</span><span class="sxs-lookup"><span data-stu-id="aad8f-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="aad8f-160">匯入 nx 模組。</span><span class="sxs-lookup"><span data-stu-id="aad8f-160">Import the nx module.</span></span> <span data-ttu-id="aad8f-161">Nx Windows PowerShell 模組包含 DSC for Linux 內建資源的結構描述，並且必須安裝到本機電腦，然後匯入設定中。</span><span class="sxs-lookup"><span data-stu-id="aad8f-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="aad8f-162">若要安裝 nx 模組，請將 nx 模組目錄複製到 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 或 `$PSHOME\Modules`。</span><span class="sxs-lookup"><span data-stu-id="aad8f-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="aad8f-163">nx 模組包含在 DSC for Linux 安裝套件中。</span><span class="sxs-lookup"><span data-stu-id="aad8f-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="aad8f-164">若要在您的設定中匯入 nx 模組，請使用 `Import-DSCResource` 命令：</span><span class="sxs-lookup"><span data-stu-id="aad8f-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="aad8f-165">定義設定，然後產生設定文件：</span><span class="sxs-lookup"><span data-stu-id="aad8f-165">Define a configuration and generate the configuration document:</span></span>

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

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="aad8f-166">將設定推送至 Linux 電腦</span><span class="sxs-lookup"><span data-stu-id="aad8f-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="aad8f-167">設定文件 (MOF 檔案) 可以使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 推送至 Linux 電腦。</span><span class="sxs-lookup"><span data-stu-id="aad8f-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="aad8f-168">若要從遠端針對 Linux 電腦使用此 Cmdlet 及 [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) \(英文\) 或 [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) \(英文\) Cmdlet，您必須使用 CIMSession。</span><span class="sxs-lookup"><span data-stu-id="aad8f-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="aad8f-169">[New-CimSession](/powershell/module/CimCmdlets/New-CimSession) Cmdlet 用來建立 Linux 電腦的 CIMSession。</span><span class="sxs-lookup"><span data-stu-id="aad8f-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="aad8f-170">下列程式碼示範如何建立 DSC for Linux 的 CIMSession。</span><span class="sxs-lookup"><span data-stu-id="aad8f-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

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
> <span data-ttu-id="aad8f-171">針對 [推送] 模式，使用者認證必須是在 Linux 電腦上的根使用者。</span><span class="sxs-lookup"><span data-stu-id="aad8f-171">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="aad8f-172">DSC for Linux 僅支援 SSL/TLS 連線，必須使用 `New-CimSession` 並將 –UseSSL 參數設為 $true。</span><span class="sxs-lookup"><span data-stu-id="aad8f-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="aad8f-173">OMI (DSC) 所使用的 SSL 憑證在此檔案中指定：`/opt/omi/etc/omiserver.conf`，屬性為：pemfile 和 keyfile。</span><span class="sxs-lookup"><span data-stu-id="aad8f-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="aad8f-174">如果此憑證不受您正在執行 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) Cmdlet 的 Windows 電腦信任，您可以使用 CIMSession 選項：`-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true` 選擇忽略憑證驗證</span><span class="sxs-lookup"><span data-stu-id="aad8f-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="aad8f-175">執行下列命令，將 DSC 設定推送至 Linux 節點。</span><span class="sxs-lookup"><span data-stu-id="aad8f-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="aad8f-176">以提取伺服器散發設定</span><span class="sxs-lookup"><span data-stu-id="aad8f-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="aad8f-177">可以用提取伺服器來散發設定給 Linux 電腦，就像 Windows 電腦一樣。</span><span class="sxs-lookup"><span data-stu-id="aad8f-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="aad8f-178">如需使用提取伺服器的指引，請參閱 [Windows PowerShell 預期狀態設定提取伺服器](../pull-server/pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="aad8f-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="aad8f-179">如需使用提取伺服器與 Linux 電腦的其他資訊與限制，請參閱 Linux 的預期狀態設定版本資訊。</span><span class="sxs-lookup"><span data-stu-id="aad8f-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="aad8f-180">在本機使用設定</span><span class="sxs-lookup"><span data-stu-id="aad8f-180">Working with configurations locally</span></span>

<span data-ttu-id="aad8f-181">DSC for Linux 包含指令碼以使用本機 Linux 電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="aad8f-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="aad8f-182">這些指令碼位於 `/opt/microsoft/dsc/Scripts` 並且包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="aad8f-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="aad8f-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="aad8f-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="aad8f-184">傳回套用到此電腦的目前設定。</span><span class="sxs-lookup"><span data-stu-id="aad8f-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="aad8f-185">類似於 Windows PowerShell Cmdlet 的 `Get-DscConfiguration` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aad8f-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="aad8f-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="aad8f-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="aad8f-187">傳回套用到此電腦的目前中繼設定。</span><span class="sxs-lookup"><span data-stu-id="aad8f-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="aad8f-188">類似於 [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aad8f-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="aad8f-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="aad8f-189">InstallModule.py</span></span>

<span data-ttu-id="aad8f-190">安裝自訂 DSC 資源模組。</span><span class="sxs-lookup"><span data-stu-id="aad8f-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="aad8f-191">需要包含模組共用物件的程式庫和結構描述 MOF 檔案的 .zip 檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="aad8f-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="aad8f-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="aad8f-192">RemoveModule.py</span></span>

<span data-ttu-id="aad8f-193">移除自訂的 DSC 資源模組。</span><span class="sxs-lookup"><span data-stu-id="aad8f-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="aad8f-194">需要有要移除的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="aad8f-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="aad8f-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="aad8f-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="aad8f-196">將設定 MOF 檔案套用至電腦。</span><span class="sxs-lookup"><span data-stu-id="aad8f-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="aad8f-197">類似於 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aad8f-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="aad8f-198">需要有要套用的設定 MOF 路徑。</span><span class="sxs-lookup"><span data-stu-id="aad8f-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="aad8f-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="aad8f-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="aad8f-200">將中繼設定 MOF 檔案套用至電腦。</span><span class="sxs-lookup"><span data-stu-id="aad8f-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="aad8f-201">類似於 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aad8f-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="aad8f-202">需要有要套用的中繼設定 MOF 路徑。</span><span class="sxs-lookup"><span data-stu-id="aad8f-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="aad8f-203">Linux 記錄檔的 PowerShell 預期狀態設定</span><span class="sxs-lookup"><span data-stu-id="aad8f-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="aad8f-204">會對 DSC for Linux 訊息產生下列記錄檔。</span><span class="sxs-lookup"><span data-stu-id="aad8f-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="aad8f-205">記錄檔</span><span class="sxs-lookup"><span data-stu-id="aad8f-205">Log file</span></span>|<span data-ttu-id="aad8f-206">Directory</span><span class="sxs-lookup"><span data-stu-id="aad8f-206">Directory</span></span>|<span data-ttu-id="aad8f-207">描述</span><span class="sxs-lookup"><span data-stu-id="aad8f-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="aad8f-208">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="aad8f-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="aad8f-209">OMI CIM 伺服器作業相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="aad8f-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="aad8f-210">**dsc.log**</span><span class="sxs-lookup"><span data-stu-id="aad8f-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="aad8f-211">與本機設定管理員 (LCM) 和 DSC 資源作業的作業相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="aad8f-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
