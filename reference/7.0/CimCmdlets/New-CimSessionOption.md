---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 113652e3166f36e20106d3d60578069a32e2ab66
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201176"
---
# <span data-ttu-id="4f7f1-103">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="4f7f1-103">New-CimSessionOption</span></span>

## <span data-ttu-id="4f7f1-104">概要</span><span class="sxs-lookup"><span data-stu-id="4f7f1-104">SYNOPSIS</span></span>
<span data-ttu-id="4f7f1-105">指定 New-CimSession Cmdlet 的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-105">Specifies advanced options for the New-CimSession cmdlet.</span></span>

## <span data-ttu-id="4f7f1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f7f1-106">SYNTAX</span></span>

### <span data-ttu-id="4f7f1-107">ProtocolTypeSet (預設) </span><span class="sxs-lookup"><span data-stu-id="4f7f1-107">ProtocolTypeSet (Default)</span></span>

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### <span data-ttu-id="4f7f1-108">WSManParameterSet</span><span class="sxs-lookup"><span data-stu-id="4f7f1-108">WSManParameterSet</span></span>

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### <span data-ttu-id="4f7f1-109">DcomParameterSet</span><span class="sxs-lookup"><span data-stu-id="4f7f1-109">DcomParameterSet</span></span>

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## <span data-ttu-id="4f7f1-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4f7f1-110">DESCRIPTION</span></span>

<span data-ttu-id="4f7f1-111">此 `New-CimSessionOption` Cmdlet 會建立 CIM 會話選項物件的實例。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-111">The `New-CimSessionOption` cmdlet creates an instance of a CIM session options object.</span></span> <span data-ttu-id="4f7f1-112">您可以使用 CIM 會話選項物件作為 Cmdlet 的輸入， `New-CimSession` 以指定 cim 會話的選項。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-112">You use a CIM session options object as input to the `New-CimSession` cmdlet to specify the options for a CIM session.</span></span>

<span data-ttu-id="4f7f1-113">這個 Cmdlet 有兩個參數集，一個用於 WsMan 選項，另一個用於分散式元件物件模型 (DCOM) 選項。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-113">This cmdlet has two parameter sets, one for WsMan options and one for Distributed Component Object Model (DCOM) options.</span></span> <span data-ttu-id="4f7f1-114">根據您使用的參數，Cmdlet 會傳回 DCOM 會話選項的實例，或傳回 WsMan 會話選項。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-114">Depending on which parameters you use, the cmdlet returns either an instance of DCOM session options or returns WsMan session options.</span></span>

## <span data-ttu-id="4f7f1-115">範例</span><span class="sxs-lookup"><span data-stu-id="4f7f1-115">EXAMPLES</span></span>

### <span data-ttu-id="4f7f1-116">範例1：建立 DCOM 的 CIM 會話選項物件</span><span class="sxs-lookup"><span data-stu-id="4f7f1-116">Example 1: Create a CIM session options object for DCOM</span></span>

<span data-ttu-id="4f7f1-117">這個範例會建立 DCOM 通訊協定的 CIM 會話選項物件，並將它儲存在名為的變數中 `$so` 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-117">This example creates a CIM session options object for the DCOM protocol and stores it in a variable named `$so`.</span></span> <span data-ttu-id="4f7f1-118">然後將變數的內容傳遞給 `New-CimSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-118">The contents of the variable are then passed to the `New-CimSession` cmdlet.</span></span>
<span data-ttu-id="4f7f1-119">`New-CimSession` 然後使用變數中定義的選項，以名為 Server01 的遠端伺服器建立新的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-119">`New-CimSession` then creates a new CIM session with the remote server named Server01, using the options defined in the variable.</span></span>

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### <span data-ttu-id="4f7f1-120">範例2：建立 WsMan 的 CIM 會話選項物件</span><span class="sxs-lookup"><span data-stu-id="4f7f1-120">Example 2: Create a CIM session options object for WsMan</span></span>

<span data-ttu-id="4f7f1-121">這個範例會建立 WsMan 通訊協定的 CIM 會話選項物件。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-121">This example creates a CIM session options object for the WsMan protocol.</span></span> <span data-ttu-id="4f7f1-122">物件包含 **ProxyAuthentication** 參數所指定之 **Kerberos** 驗證模式的設定、由 **ProxyCredential** 參數指定的認證，並指定命令要略過 CA 檢查、略過 CN 檢查，然後使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-122">The object contains configuration for the authentication mode of **Kerberos** specified by the **ProxyAuthentication** parameter, the credentials specified by the **ProxyCredential** parameter, and specifies that the command is to skip the CA check, skip the CN check, and use SSL.</span></span>

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### <span data-ttu-id="4f7f1-123">範例3：建立已指定文化特性的 CIM 會話選項物件</span><span class="sxs-lookup"><span data-stu-id="4f7f1-123">Example 3: Create a CIM session options object with the culture specified</span></span>

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

<span data-ttu-id="4f7f1-124">此範例會指定用於 CIM 會話的文化特性。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-124">This example specifies the culture that is used for the CIM session.</span></span> <span data-ttu-id="4f7f1-125">依預設，在執行作業時，會使用用戶端的文化特性。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-125">By default, the culture of the client is used when performing operations.</span></span> <span data-ttu-id="4f7f1-126">不過，您可以使用 **culture** 參數覆寫預設文化特性。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-126">However, the default culture can be overridden using the **Culture** parameter.</span></span>

## <span data-ttu-id="4f7f1-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f7f1-127">PARAMETERS</span></span>

### <span data-ttu-id="4f7f1-128">-Culture</span><span class="sxs-lookup"><span data-stu-id="4f7f1-128">-Culture</span></span>

<span data-ttu-id="4f7f1-129">指定要用於 CIM 會話的使用者介面文化特性。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-129">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="4f7f1-130">使用下列其中一種格式來指定此參數的值：</span><span class="sxs-lookup"><span data-stu-id="4f7f1-130">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="4f7f1-131">格式的文化特性名稱， `<languagecode2>-<country/regioncode2>` 例如 "en-us"。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-131">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="4f7f1-132">包含 **CultureInfo** 物件的變數。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-132">A variable that contains a **CultureInfo** object.</span></span>
- <span data-ttu-id="4f7f1-133">取得 **CultureInfo** 物件的命令，例如 [Get 文化](../Microsoft.PowerShell.Utility/Get-Culture.md)特性</span><span class="sxs-lookup"><span data-stu-id="4f7f1-133">A command that gets a **CultureInfo** object, such as [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-134">-EncodePortInServicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="4f7f1-134">-EncodePortInServicePrincipalName</span></span>

<span data-ttu-id="4f7f1-135">表示 Kerberos 連接正在連接到服務主體名稱 (SPN 的服務) 包含服務埠號碼。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-135">Indicates that the Kerberos connection is connecting to a service whose service principal name (SPN) includes the service port number.</span></span> <span data-ttu-id="4f7f1-136">這種類型的連接並不常見。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-136">This type of connection is not common.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-137">-Encoding</span><span class="sxs-lookup"><span data-stu-id="4f7f1-137">-Encoding</span></span>

<span data-ttu-id="4f7f1-138">指定用於 WsMan 通訊協定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-138">Specifies the encoding used for the WsMan protocol.</span></span> <span data-ttu-id="4f7f1-139">此參數可接受的值為： **預設** 值、 **Utf8** 或 **Utf16** 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-139">The acceptable values for this parameter are: **Default** , **Utf8** , or **Utf16** .</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-140">-HttpPrefix</span><span class="sxs-lookup"><span data-stu-id="4f7f1-140">-HttpPrefix</span></span>

<span data-ttu-id="4f7f1-141">指定電腦名稱稱和埠號碼後面的 HTTP URL 部分。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-141">Specifies the part of the HTTP URL after the computer name and port number.</span></span> <span data-ttu-id="4f7f1-142">變更這種情況並不常見。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-142">Changing this is not common.</span></span> <span data-ttu-id="4f7f1-143">根據預設，此參數的值為 **/wsman** 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-143">By default, the value of this parameter is **/wsman** .</span></span>

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-144">-Impersonation</span><span class="sxs-lookup"><span data-stu-id="4f7f1-144">-Impersonation</span></span>

<span data-ttu-id="4f7f1-145">使用模擬建立 Windows Management Instrumentation (WMI) 的 DCOM 會話。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-145">Creates a DCOM session to Windows Management Instrumentation (WMI) using impersonation.</span></span>

<span data-ttu-id="4f7f1-146">這個參數的有效值為：</span><span class="sxs-lookup"><span data-stu-id="4f7f1-146">Valid values for this parameter are:</span></span>

- <span data-ttu-id="4f7f1-147">預設： DCOM 可以選擇使用其一般安全性協調演算法的模擬等級。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-147">Default: DCOM can choose the impersonation level using its normal security negotiation algorithm.</span></span>
- <span data-ttu-id="4f7f1-148">無：用戶端對伺服器是匿名的。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-148">None: The client is anonymous to the server.</span></span> <span data-ttu-id="4f7f1-149">伺服器進程可以模擬用戶端，但模擬權杖不包含任何資訊，也無法使用。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-149">The server process can impersonate the client, but the impersonation token does not contain any information and cannot be used.</span></span>
- <span data-ttu-id="4f7f1-150">識別：允許物件查詢呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-150">Identify: Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="4f7f1-151">模擬：允許物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-151">Impersonate: Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="4f7f1-152">Delegate：允許物件允許其他物件使用呼叫端的認證。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-152">Delegate: Allows objects to permit other objects to use the credentials of the caller.</span></span>

<span data-ttu-id="4f7f1-153">如果 **未** 指定模擬，Cmdlet 會 `New-CimSession` 使用模擬的值。 **Impersonate**</span><span class="sxs-lookup"><span data-stu-id="4f7f1-153">If **Impersonation** is not specified, the `New-CimSession` cmdlet uses the value of **Impersonate** .</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-154">-MaxEnvelopeSizeKB</span><span class="sxs-lookup"><span data-stu-id="4f7f1-154">-MaxEnvelopeSizeKB</span></span>

<span data-ttu-id="4f7f1-155">指定任一方向的 WsMan XML 訊息大小限制。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-155">Specifies the size limit of WsMan XML messages for either direction.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-156">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="4f7f1-156">-NoEncryption</span></span>

<span data-ttu-id="4f7f1-157">指定關閉資料加密。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-157">Specifies that data encryption is turned off.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-158">-PacketIntegrity</span><span class="sxs-lookup"><span data-stu-id="4f7f1-158">-PacketIntegrity</span></span>

<span data-ttu-id="4f7f1-159">指定建立至 WMI 的 DCOM 會話使用元件物件模型 (COM) _PacketIntegrity_ 功能。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-159">Specifies that the DCOM session created to WMI uses the Component Object Model (COM) _PacketIntegrity_ functionality.</span></span> <span data-ttu-id="4f7f1-160">根據預設，所有使用 DCOM 建立的 CIM 會話都會將 **PacketIntegrity** 參數設定為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-160">By default, all CIM sessions created using DCOM have the **PacketIntegrity** parameter set to **True** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-161">-PacketPrivacy</span><span class="sxs-lookup"><span data-stu-id="4f7f1-161">-PacketPrivacy</span></span>

<span data-ttu-id="4f7f1-162">使用 COM _PacketPrivacy_ 建立對 WMI 的 DCOM 會話。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-162">Creates a DCOM session to WMI using the COM _PacketPrivacy_ .</span></span> <span data-ttu-id="4f7f1-163">根據預設，所有使用 DCOM 建立的 CIM 會話都會將 **PacketPrivacy** 參數設定為 **true** 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-163">By default, all CIM sessions created using DCOM have the **PacketPrivacy** parameter set to **true** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-164">-Protocol</span><span class="sxs-lookup"><span data-stu-id="4f7f1-164">-Protocol</span></span>

<span data-ttu-id="4f7f1-165">指定要使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-165">Specifies the protocol to use.</span></span> <span data-ttu-id="4f7f1-166">此參數可接受的值為： **DCOM** 、 **Default** 或 **Wsman** 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-166">The acceptable values for this parameter are: **DCOM** , **Default** , or **Wsman** .</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-167">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="4f7f1-167">-ProxyAuthentication</span></span>

<span data-ttu-id="4f7f1-168">指定用於 proxy 解析的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-168">Specifies the authentication method to use for proxy resolution.</span></span> <span data-ttu-id="4f7f1-169">此參數可接受的值包括： **Default** 、 **Digest** 、 **Negotiate** 、 **Basic** 、 **Kerberos** 、 **NtlmDomain** 或 **CredSsp** 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-169">The acceptable values for this parameter are: **Default** , **Digest** , **Negotiate** , **Basic** , **Kerberos** , **NtlmDomain** , or **CredSsp** .</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-170">-ProxyCertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="4f7f1-170">-ProxyCertificateThumbprint</span></span>

<span data-ttu-id="4f7f1-171">指定用於 proxy 驗證的使用者帳戶 (x.509) 數位公開金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-171">Specifies the (x.509) digital public key certificate of a user account for proxy authentication.</span></span>
<span data-ttu-id="4f7f1-172">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-172">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="4f7f1-173">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-173">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="4f7f1-174">這些帳戶只能對應至本機使用者帳戶，而且無法使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-174">They can only be mapped to local user accounts and they do not work with domain accounts.</span></span>

<span data-ttu-id="4f7f1-175">若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell Cert：磁片磁碟機中的或 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-175">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-176">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="4f7f1-176">-ProxyCredential</span></span>

<span data-ttu-id="4f7f1-177">指定要用於 Proxy 驗證的認證。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-177">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="4f7f1-178">輸入下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="4f7f1-178">Enter one of the following:</span></span>

- <span data-ttu-id="4f7f1-179">包含 PSCredential 物件的變數。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-179">A variable that contains a PSCredential object.</span></span>
- <span data-ttu-id="4f7f1-180">可取得 PSCredential 物件的命令，例如 `Get-Credential`</span><span class="sxs-lookup"><span data-stu-id="4f7f1-180">A command that gets a PSCredential object, such as `Get-Credential`</span></span>

<span data-ttu-id="4f7f1-181">如果未設定此選項，則您不能指定任何認證。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-181">If this option is not set, then you cannot specify any credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-182">-ProxyType</span><span class="sxs-lookup"><span data-stu-id="4f7f1-182">-ProxyType</span></span>

<span data-ttu-id="4f7f1-183">指定要使用的主機名稱解析機制。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-183">Specifies the host name resolution mechanism to use.</span></span> <span data-ttu-id="4f7f1-184">此參數可接受的值為： **None** 、 **WinHttp** 、 **Auto** 或 **microsoft-windows-ie-internetexplorer** 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-184">The acceptable values for this parameter are: **None** , **WinHttp** , **Auto** , or **InternetExplorer** .</span></span>

<span data-ttu-id="4f7f1-185">此參數的預設值為 **microsoft-windows-ie-internetexplorer** 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-185">The default value of this parameter is **InternetExplorer** .</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-186">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="4f7f1-186">-SkipCACheck</span></span>

<span data-ttu-id="4f7f1-187">指出透過 HTTPS 連線時，用戶端不會驗證伺服器憑證是否由受信任的憑證授權單位單位 (CA) 簽署。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-187">Indicates that when connecting over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="4f7f1-188">只有當遠端電腦是使用另一種機制來信任時，例如當遠端電腦屬於實體安全且隔離的網路時，或當遠端電腦在 WinRM 設定中列為受信任的主機時，才使用此參數。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-188">Use this parameter only when the remote computer is trusted using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated, or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-189">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="4f7f1-189">-SkipCNCheck</span></span>

<span data-ttu-id="4f7f1-190">指出伺服器的憑證一般名稱 (CN) 不需要符合伺服器的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-190">Indicates that the certificate common name (CN) of the server does not need to match the hostname of the server.</span></span> <span data-ttu-id="4f7f1-191">此參數僅適用于使用 HTTPS 通訊協定的受信任電腦的遠端操作。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-191">Use this parameter for remote operations only with trusted computers that use the HTTPS protocol.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-192">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="4f7f1-192">-SkipRevocationCheck</span></span>

<span data-ttu-id="4f7f1-193">指出已略過伺服器憑證的撤銷檢查。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-193">Indicates that the revocation check for server certificates is skipped.</span></span> <span data-ttu-id="4f7f1-194">此參數僅適用于受信任的電腦。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-194">Use this parameter only for trusted computers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-195">-UICulture</span><span class="sxs-lookup"><span data-stu-id="4f7f1-195">-UICulture</span></span>

<span data-ttu-id="4f7f1-196">指定要用於 CIM 會話的使用者介面文化特性。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-196">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="4f7f1-197">使用下列其中一種格式來指定此參數的值：</span><span class="sxs-lookup"><span data-stu-id="4f7f1-197">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="4f7f1-198">格式的文化特性名稱， `<languagecode2>-<country/regioncode2>` 例如 "en-us"。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-198">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="4f7f1-199">包含 CultureInfo 物件的變數。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-199">A variable that contains a CultureInfo object.</span></span>
- <span data-ttu-id="4f7f1-200">取得 CultureInfo 物件的命令，例如 `Get-Culture` 。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-200">A command that gets a CultureInfo object, such as `Get-Culture`.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-201">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="4f7f1-201">-UseSsl</span></span>

<span data-ttu-id="4f7f1-202">指出應該使用 SSL 來建立與遠端電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-202">Indicates that SSL should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="4f7f1-203">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-203">By default, SSL is not used.</span></span> <span data-ttu-id="4f7f1-204">WsMan 會加密透過網路傳輸的所有內容，即使是在使用 HTTP 時也一樣。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-204">WsMan encrypts all content that is transmitted over the network, even when using HTTP.</span></span>

<span data-ttu-id="4f7f1-205">此參數可讓您指定 HTTPS （而非 HTTP）的額外保護。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-205">This parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="4f7f1-206">如果用於連線的埠上無法使用 SSL，且您指定此參數，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-206">If SSL is not available on the port used for the connection and you specify this parameter, then the command fails.</span></span>

<span data-ttu-id="4f7f1-207">建議您只有在未指定 **PacketPrivacy** 參數時，才使用此參數。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-207">It is recommended that you use this parameter only when the **PacketPrivacy** parameter is not specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4f7f1-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f7f1-208">CommonParameters</span></span>

<span data-ttu-id="4f7f1-209">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-209">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f7f1-210">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-210">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f7f1-211">輸入</span><span class="sxs-lookup"><span data-stu-id="4f7f1-211">INPUTS</span></span>

### <span data-ttu-id="4f7f1-212">無</span><span class="sxs-lookup"><span data-stu-id="4f7f1-212">None</span></span>

<span data-ttu-id="4f7f1-213">此 Cmdlet 不接受任何輸入物件。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-213">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="4f7f1-214">輸出</span><span class="sxs-lookup"><span data-stu-id="4f7f1-214">OUTPUTS</span></span>

### <span data-ttu-id="4f7f1-215">CIMSessionOption</span><span class="sxs-lookup"><span data-stu-id="4f7f1-215">CIMSessionOption</span></span>

<span data-ttu-id="4f7f1-216">這個 Cmdlet 會傳回包含 CIM 會話選項資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="4f7f1-216">This cmdlet returns an object that contains CIM session options information.</span></span>

## <span data-ttu-id="4f7f1-217">注意</span><span class="sxs-lookup"><span data-stu-id="4f7f1-217">NOTES</span></span>

## <span data-ttu-id="4f7f1-218">相關連結</span><span class="sxs-lookup"><span data-stu-id="4f7f1-218">RELATED LINKS</span></span>

[<span data-ttu-id="4f7f1-219">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4f7f1-219">Get-ChildItem</span></span>](../microsoft.powershell.management/get-childitem.md)

[<span data-ttu-id="4f7f1-220">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="4f7f1-220">Get-Credential</span></span>](../microsoft.powershell.security/get-credential.md)

[<span data-ttu-id="4f7f1-221">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="4f7f1-221">Get-Culture</span></span>](../microsoft.powershell.utility/get-culture.md)

[<span data-ttu-id="4f7f1-222">Get-Item</span><span class="sxs-lookup"><span data-stu-id="4f7f1-222">Get-Item</span></span>](../microsoft.powershell.management/get-item.md)

[<span data-ttu-id="4f7f1-223">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="4f7f1-223">New-CimSession</span></span>](New-CimSession.md)
