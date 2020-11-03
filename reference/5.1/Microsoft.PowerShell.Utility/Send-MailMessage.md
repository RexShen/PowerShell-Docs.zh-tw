---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 6f98c95e6c0144f76393e9d28454833097894512
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203147"
---
# <span data-ttu-id="9a91b-103">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="9a91b-103">Send-MailMessage</span></span>

## <span data-ttu-id="9a91b-104">概要</span><span class="sxs-lookup"><span data-stu-id="9a91b-104">SYNOPSIS</span></span>
<span data-ttu-id="9a91b-105">傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="9a91b-105">Sends an email message.</span></span>

## <span data-ttu-id="9a91b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9a91b-106">SYNTAX</span></span>

### <span data-ttu-id="9a91b-107">全部</span><span class="sxs-lookup"><span data-stu-id="9a91b-107">All</span></span>

```
Send-MailMessage [-To] <string[]> [-Subject] <string> [[-Body] <string>] [[-SmtpServer] <string>]
 -From <string> [-Attachments <string[]>] [-Bcc <string[]>] [-BodyAsHtml] [-Encoding <Encoding>]
 [-Cc <string[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 [-Priority <MailPriority>] [-Credential <pscredential>] [-UseSsl] [-Port <int>]
 [<CommonParameters>]
```

## <span data-ttu-id="9a91b-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9a91b-108">DESCRIPTION</span></span>

<span data-ttu-id="9a91b-109">`Send-MailMessage`Cmdlet 會從 PowerShell 內傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="9a91b-109">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="9a91b-110">您必須指定 Simple Mail Transfer Protocol (SMTP) server，否則 `Send-MailMessage` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="9a91b-110">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="9a91b-111">使用 **SmtpServer** 參數或將變數設定 `$PSEmailServer` 為有效的 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a91b-111">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="9a91b-112">指派給的值 `$PSEmailServer` 是 PowerShell 的預設 SMTP 設定。</span><span class="sxs-lookup"><span data-stu-id="9a91b-112">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="9a91b-113">如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9a91b-113">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="9a91b-114">`Send-MailMessage`Cmdlet 已淘汰。</span><span class="sxs-lookup"><span data-stu-id="9a91b-114">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="9a91b-115">此 Cmdlet 不保證 SMTP 伺服器的安全連線。</span><span class="sxs-lookup"><span data-stu-id="9a91b-115">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="9a91b-116">雖然 PowerShell 沒有立即可用的取代功能，但我們建議您不要使用 `Send-MailMessage` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-116">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="9a91b-117">如需詳細資訊，請參閱 [平臺相容性注意事項 DE0005](https://aka.ms/SendMailMessage)。</span><span class="sxs-lookup"><span data-stu-id="9a91b-117">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="9a91b-118">範例</span><span class="sxs-lookup"><span data-stu-id="9a91b-118">EXAMPLES</span></span>

### <span data-ttu-id="9a91b-119">範例1：將電子郵件從一個人傳送給另一個人</span><span class="sxs-lookup"><span data-stu-id="9a91b-119">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="9a91b-120">此範例會將一則電子郵件訊息傳送給其他人。</span><span class="sxs-lookup"><span data-stu-id="9a91b-120">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="9a91b-121">需要 **From** 、 **To** 和 **Subject** 參數 `Send-MailMessage` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-121">The **From** , **To** , and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="9a91b-122">此範例 `$PSEmailServer` 會使用 SMTP 伺服器的預設變數，所以不需要 **SmtpServer** 參數。</span><span class="sxs-lookup"><span data-stu-id="9a91b-122">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="9a91b-123">此 `Send-MailMessage` Cmdlet 會使用 **From** 參數來指定訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="9a91b-123">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="9a91b-124">**To** 參數會指定訊息的收件者。</span><span class="sxs-lookup"><span data-stu-id="9a91b-124">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="9a91b-125">**Subject** 參數會使用文字字串 **測試郵件** 做為訊息，因為不包含選擇性的 **Body** 參數。</span><span class="sxs-lookup"><span data-stu-id="9a91b-125">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="9a91b-126">範例2：傳送附件</span><span class="sxs-lookup"><span data-stu-id="9a91b-126">Example 2: Send an attachment</span></span>

<span data-ttu-id="9a91b-127">此範例會傳送含有附件的電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="9a91b-127">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="9a91b-128">此 `Send-MailMessage` Cmdlet 會使用 **From** 參數來指定訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="9a91b-128">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="9a91b-129">**To** 參數會指定訊息的收件者。</span><span class="sxs-lookup"><span data-stu-id="9a91b-129">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="9a91b-130">**Subject** 參數描述訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="9a91b-130">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="9a91b-131">**Body** 參數是訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="9a91b-131">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="9a91b-132">**附件** 參數會指定目前目錄中附加至電子郵件訊息的檔案。</span><span class="sxs-lookup"><span data-stu-id="9a91b-132">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="9a91b-133">**Priority** 參數會將訊息設定為 **高** 優先順序。</span><span class="sxs-lookup"><span data-stu-id="9a91b-133">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="9a91b-134">**-DeliveryNotificationOption** 參數會指定 **OnSuccess** 和 **OnFailure** 這兩個值。</span><span class="sxs-lookup"><span data-stu-id="9a91b-134">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure** .</span></span> <span data-ttu-id="9a91b-135">寄件者將會收到電子郵件通知，以確認訊息傳遞成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="9a91b-135">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="9a91b-136">**SmtpServer** 參數會將 SMTP 伺服器設定為 **smtp.fabrikam.com** 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-136">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com** .</span></span>

### <span data-ttu-id="9a91b-137">範例3：將電子郵件傳送至郵寄清單</span><span class="sxs-lookup"><span data-stu-id="9a91b-137">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="9a91b-138">此範例會將電子郵件訊息傳送至郵寄清單。</span><span class="sxs-lookup"><span data-stu-id="9a91b-138">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="9a91b-139">此 `Send-MailMessage` Cmdlet 會使用 **From** 參數來指定訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="9a91b-139">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="9a91b-140">**To** 參數會指定訊息的收件者。</span><span class="sxs-lookup"><span data-stu-id="9a91b-140">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="9a91b-141">**Cc** 參數會將訊息的副本傳送給指定的收件者。</span><span class="sxs-lookup"><span data-stu-id="9a91b-141">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="9a91b-142">**密件副本** 參數會傳送訊息的密件副本。</span><span class="sxs-lookup"><span data-stu-id="9a91b-142">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="9a91b-143">密件複製是由其他收件者隱藏的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="9a91b-143">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="9a91b-144">**Subject** 參數是訊息，因為不包含選用的 **Body** 參數。</span><span class="sxs-lookup"><span data-stu-id="9a91b-144">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="9a91b-145">**Credential** 參數會指定用來傳送訊息的網域系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="9a91b-145">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="9a91b-146">**UseSsl** 參數會指定安全通訊端層 (SSL) 建立安全連線。</span><span class="sxs-lookup"><span data-stu-id="9a91b-146">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="9a91b-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9a91b-147">PARAMETERS</span></span>

### <span data-ttu-id="9a91b-148">-Attachments</span><span class="sxs-lookup"><span data-stu-id="9a91b-148">-Attachments</span></span>

<span data-ttu-id="9a91b-149">指定要附加至電子郵件訊息之檔案的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="9a91b-149">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="9a91b-150">您可以使用此參數，或使用管線將路徑和檔案名傳送至 `Send-MailMessage` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-150">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-151">-Bcc</span><span class="sxs-lookup"><span data-stu-id="9a91b-151">-Bcc</span></span>

<span data-ttu-id="9a91b-152">指定可接收郵件副本但未列為訊息收件者的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="9a91b-152">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="9a91b-153">輸入 (選用) 和電子郵件地址的名稱，例如 `Name <someone@fabrikam.com>` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-153">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-154">-Body</span><span class="sxs-lookup"><span data-stu-id="9a91b-154">-Body</span></span>

<span data-ttu-id="9a91b-155">指定電子郵件訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="9a91b-155">Specifies the content of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-156">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="9a91b-156">-BodyAsHtml</span></span>

<span data-ttu-id="9a91b-157">指定 **Body** 參數的值包含 HTML。</span><span class="sxs-lookup"><span data-stu-id="9a91b-157">Specifies that the value of the **Body** parameter contains HTML.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-158">-Cc</span><span class="sxs-lookup"><span data-stu-id="9a91b-158">-Cc</span></span>

<span data-ttu-id="9a91b-159">指定傳送電子郵件訊息副本 (副本) 的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="9a91b-159">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="9a91b-160">輸入 (選用) 和電子郵件地址的名稱，例如 `Name <someone@fabrikam.com>` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-160">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="9a91b-161">-Credential</span></span>

<span data-ttu-id="9a91b-162">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9a91b-162">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="9a91b-163">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="9a91b-163">The default is the current user.</span></span>

<span data-ttu-id="9a91b-164">輸入使用者名稱，例如 **User01** 或 **Domain01\User01** 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-164">Type a user name, such as **User01** or **Domain01\User01** .</span></span> <span data-ttu-id="9a91b-165">或者，輸入 **PSCredential** 物件，例如 Cmdlet 中的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-165">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="9a91b-166">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="9a91b-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9a91b-167">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="9a91b-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-168">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="9a91b-168">-DeliveryNotificationOption</span></span>

<span data-ttu-id="9a91b-169">指定電子郵件訊息的傳遞通知選項。</span><span class="sxs-lookup"><span data-stu-id="9a91b-169">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="9a91b-170">您可以指定多個值。</span><span class="sxs-lookup"><span data-stu-id="9a91b-170">You can specify multiple values.</span></span>
<span data-ttu-id="9a91b-171">None 是預設值。</span><span class="sxs-lookup"><span data-stu-id="9a91b-171">None is the default value.</span></span> <span data-ttu-id="9a91b-172">這個參數的別名是 **DNO** 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-172">The alias for this parameter is **DNO** .</span></span>

<span data-ttu-id="9a91b-173">傳遞通知會傳送至 **From** 參數中的位址。</span><span class="sxs-lookup"><span data-stu-id="9a91b-173">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="9a91b-174">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="9a91b-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9a91b-175">`None`：沒有通知。</span><span class="sxs-lookup"><span data-stu-id="9a91b-175">`None`: No notification.</span></span>
- <span data-ttu-id="9a91b-176">`OnSuccess`：如果傳遞成功，便通知。</span><span class="sxs-lookup"><span data-stu-id="9a91b-176">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="9a91b-177">`OnFailure`：如果傳遞失敗，請通知。</span><span class="sxs-lookup"><span data-stu-id="9a91b-177">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="9a91b-178">`Delay`：通知是否延遲傳遞。</span><span class="sxs-lookup"><span data-stu-id="9a91b-178">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="9a91b-179">`Never`：永不通知。</span><span class="sxs-lookup"><span data-stu-id="9a91b-179">`Never`: Never notify.</span></span>

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-180">-Encoding</span><span class="sxs-lookup"><span data-stu-id="9a91b-180">-Encoding</span></span>

<span data-ttu-id="9a91b-181">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="9a91b-181">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="9a91b-182">預設值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="9a91b-182">The default value is `Default`.</span></span>

<span data-ttu-id="9a91b-183">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="9a91b-183">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9a91b-184">`ASCII` 使用 ASCII (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="9a91b-184">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="9a91b-185">`BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="9a91b-185">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="9a91b-186">`Default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-186">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="9a91b-187">`OEM` 使用對應至系統目前 OEM 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="9a91b-187">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="9a91b-188">`Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="9a91b-188">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="9a91b-189">`UTF7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="9a91b-189">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="9a91b-190">`UTF8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="9a91b-190">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="9a91b-191">`UTF32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="9a91b-191">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-192">-From</span><span class="sxs-lookup"><span data-stu-id="9a91b-192">-From</span></span>

<span data-ttu-id="9a91b-193">需要 **From** 參數。</span><span class="sxs-lookup"><span data-stu-id="9a91b-193">The **From** parameter is required.</span></span> <span data-ttu-id="9a91b-194">此參數會指定寄件者的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="9a91b-194">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="9a91b-195">輸入 (選用) 和電子郵件地址的名稱，例如 `Name <someone@fabrikam.com>` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-195">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-196">-Port</span><span class="sxs-lookup"><span data-stu-id="9a91b-196">-Port</span></span>

<span data-ttu-id="9a91b-197">指定 SMTP 伺服器上的替代連接埠。</span><span class="sxs-lookup"><span data-stu-id="9a91b-197">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="9a91b-198">預設值為 25，這是預設的 SMTP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="9a91b-198">The default value is 25, which is the default SMTP port.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-199">-Priority</span><span class="sxs-lookup"><span data-stu-id="9a91b-199">-Priority</span></span>

<span data-ttu-id="9a91b-200">指定電子郵件訊息的優先順序。</span><span class="sxs-lookup"><span data-stu-id="9a91b-200">Specifies the priority of the email message.</span></span> <span data-ttu-id="9a91b-201">預設值為 Normal。</span><span class="sxs-lookup"><span data-stu-id="9a91b-201">Normal is the default.</span></span> <span data-ttu-id="9a91b-202">此參數可接受的值為 Normal、High 及 Low。</span><span class="sxs-lookup"><span data-stu-id="9a91b-202">The acceptable values for this parameter are Normal, High, and Low.</span></span>

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-203">-SmtpServer</span><span class="sxs-lookup"><span data-stu-id="9a91b-203">-SmtpServer</span></span>

<span data-ttu-id="9a91b-204">指定傳送電子郵件訊息的 SMTP 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="9a91b-204">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="9a91b-205">預設值為喜好設定變數的值 `$PSEmailServer` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-205">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="9a91b-206">如果未設定喜好設定變數，且未使用此參數，則 `Send-MailMessage` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="9a91b-206">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-207">-Subject</span><span class="sxs-lookup"><span data-stu-id="9a91b-207">-Subject</span></span>

<span data-ttu-id="9a91b-208">需要 **Subject** 參數。</span><span class="sxs-lookup"><span data-stu-id="9a91b-208">The **Subject** parameter is required.</span></span> <span data-ttu-id="9a91b-209">此參數會指定電子郵件訊息的主旨。</span><span class="sxs-lookup"><span data-stu-id="9a91b-209">This parameter specifies the subject of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-210">-To</span><span class="sxs-lookup"><span data-stu-id="9a91b-210">-To</span></span>

<span data-ttu-id="9a91b-211">需要 **參數。**</span><span class="sxs-lookup"><span data-stu-id="9a91b-211">The **To** parameter is required.</span></span> <span data-ttu-id="9a91b-212">此參數會指定收件者的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="9a91b-212">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="9a91b-213">如果有多個收件者，請以逗號分隔其位址 (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-213">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="9a91b-214">輸入 (選用) 和電子郵件地址的名稱，例如 `Name <someone@fabrikam.com>` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-214">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-215">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="9a91b-215">-UseSsl</span></span>

<span data-ttu-id="9a91b-216">安全通訊端層 (SSL) 通訊協定是用來建立遠端電腦的安全連線，以傳送郵件。</span><span class="sxs-lookup"><span data-stu-id="9a91b-216">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="9a91b-217">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="9a91b-217">By default, SSL is not used.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9a91b-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9a91b-218">CommonParameters</span></span>

<span data-ttu-id="9a91b-219">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9a91b-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9a91b-220">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9a91b-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9a91b-221">輸入</span><span class="sxs-lookup"><span data-stu-id="9a91b-221">INPUTS</span></span>

### <span data-ttu-id="9a91b-222">System.String</span><span class="sxs-lookup"><span data-stu-id="9a91b-222">System.String</span></span>

<span data-ttu-id="9a91b-223">您可以透過管道將附件的路徑和檔案名傳送至 `Send-MailMessage` 。</span><span class="sxs-lookup"><span data-stu-id="9a91b-223">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="9a91b-224">輸出</span><span class="sxs-lookup"><span data-stu-id="9a91b-224">OUTPUTS</span></span>

### <span data-ttu-id="9a91b-225">無</span><span class="sxs-lookup"><span data-stu-id="9a91b-225">None</span></span>

<span data-ttu-id="9a91b-226">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="9a91b-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9a91b-227">注意</span><span class="sxs-lookup"><span data-stu-id="9a91b-227">NOTES</span></span>

## <span data-ttu-id="9a91b-228">相關連結</span><span class="sxs-lookup"><span data-stu-id="9a91b-228">RELATED LINKS</span></span>

[<span data-ttu-id="9a91b-229">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="9a91b-229">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="9a91b-230">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="9a91b-230">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)
