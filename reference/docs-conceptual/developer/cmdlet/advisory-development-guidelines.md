---
title: 諮詢開發指導方針 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: dc8ef586954106f6d7fbce550dc22cd935018936
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782424"
---
# <a name="advisory-development-guidelines"></a><span data-ttu-id="2434d-102">建議性開發指導方針</span><span class="sxs-lookup"><span data-stu-id="2434d-102">Advisory Development Guidelines</span></span>

<span data-ttu-id="2434d-103">本節說明您應考慮的指導方針，以確保良好的開發和使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="2434d-103">This section describes guidelines that you should consider to ensure good development and user experiences.</span></span> <span data-ttu-id="2434d-104">有時候可能會套用，有時可能不會套用。</span><span class="sxs-lookup"><span data-stu-id="2434d-104">Sometimes they might apply, and sometimes they might not.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="2434d-105">設計指導方針</span><span class="sxs-lookup"><span data-stu-id="2434d-105">Design Guidelines</span></span>

<span data-ttu-id="2434d-106">設計 Cmdlet 時，應該考慮下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="2434d-106">The following guidelines should be considered when designing cmdlets.</span></span> <span data-ttu-id="2434d-107">當您找到適用于您情況的設計指導方針時，請務必查看類似方針的程式碼方針。</span><span class="sxs-lookup"><span data-stu-id="2434d-107">When you find a Design guideline that applies to your situation, be sure to look at the Code guidelines for similar guidelines.</span></span>

### <a name="support-an-inputobject-parameter-ad01"></a><span data-ttu-id="2434d-108">支援 (AD01 的 InputObject 參數) </span><span class="sxs-lookup"><span data-stu-id="2434d-108">Support an InputObject Parameter (AD01)</span></span>

<span data-ttu-id="2434d-109">由於 Windows PowerShell 會直接與 Microsoft .NET Framework 物件搭配運作，因此通常會提供 .NET Framework 物件，完全符合使用者執行特定作業所需的類型。</span><span class="sxs-lookup"><span data-stu-id="2434d-109">Because Windows PowerShell works directly with Microsoft .NET Framework objects, a .NET Framework object is often available that exactly matches the type the user needs to perform a particular operation.</span></span> <span data-ttu-id="2434d-110">`InputObject`這是接受這類物件做為輸入之參數的標準名稱。</span><span class="sxs-lookup"><span data-stu-id="2434d-110">`InputObject` is the standard name for a parameter that takes such an object as input.</span></span> <span data-ttu-id="2434d-111">例如， [StopProc 教學](./stopproc-tutorial.md)課程中的範例**停止程式**Cmdlet 會定義可 `InputObject` 支援管線輸入之 Process 類型的參數。</span><span class="sxs-lookup"><span data-stu-id="2434d-111">For example, the sample **Stop-Proc** cmdlet in the [StopProc Tutorial](./stopproc-tutorial.md) defines an `InputObject` parameter of type Process that supports the input from the pipeline.</span></span> <span data-ttu-id="2434d-112">使用者可以取得一組處理常式物件，操控它們以選取要停止的確切物件，然後直接將它們傳遞給**停止程式**Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2434d-112">The user can get a set of process objects, manipulate them to select the exact objects to stop, and then pass them to the **Stop-Proc** cmdlet directly.</span></span>

### <a name="support-the-force-parameter-ad02"></a><span data-ttu-id="2434d-113">支援 (AD02) 的 Force 參數</span><span class="sxs-lookup"><span data-stu-id="2434d-113">Support the Force Parameter (AD02)</span></span>

<span data-ttu-id="2434d-114">有時候，Cmdlet 必須保護使用者，使其無法執行要求的操作。</span><span class="sxs-lookup"><span data-stu-id="2434d-114">Occasionally, a cmdlet needs to protect the user from performing a requested operation.</span></span> <span data-ttu-id="2434d-115">這類 Cmdlet 應該支援 `Force` 參數，以允許使用者在有權執行作業時覆寫該保護。</span><span class="sxs-lookup"><span data-stu-id="2434d-115">Such a cmdlet should support a `Force` parameter to allow the user to override that protection if the user has permissions to perform the operation.</span></span>

<span data-ttu-id="2434d-116">例如，[移除專案](/powershell/module/microsoft.powershell.management/remove-item)Cmdlet 通常不會移除唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="2434d-116">For example, the [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet does not normally remove a read-only file.</span></span> <span data-ttu-id="2434d-117">不過，此 Cmdlet 支援 `Force` 參數，讓使用者可以強制移除唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="2434d-117">However, this cmdlet supports a `Force` parameter so a user can force removal of a read-only file.</span></span> <span data-ttu-id="2434d-118">如果使用者已經有修改唯讀屬性的許可權，而且使用者移除該檔案，則使用 `Force` 參數可簡化作業。</span><span class="sxs-lookup"><span data-stu-id="2434d-118">If the user already has permission to modify the read-only attribute, and the user removes the file, use of the `Force` parameter simplifies the operation.</span></span> <span data-ttu-id="2434d-119">不過，如果使用者沒有移除檔案的許可權， `Force` 參數就不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="2434d-119">However, if the user does not have permission to remove the file, the `Force` parameter has no effect.</span></span>

### <a name="handle-credentials-through-windows-powershell-ad03"></a><span data-ttu-id="2434d-120">透過 Windows PowerShell 處理認證 (AD03) </span><span class="sxs-lookup"><span data-stu-id="2434d-120">Handle Credentials Through Windows PowerShell (AD03)</span></span>

<span data-ttu-id="2434d-121">Cmdlet 應定義 `Credential` 代表認證的參數。</span><span class="sxs-lookup"><span data-stu-id="2434d-121">A cmdlet should define a `Credential` parameter to represent credentials.</span></span> <span data-ttu-id="2434d-122">這個參數的類型必須是[system.web](/dotnet/api/System.Management.Automation.PSCredential) ，而且必須使用 Credential 屬性宣告來定義。</span><span class="sxs-lookup"><span data-stu-id="2434d-122">This parameter must be of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) and must be defined using a Credential attribute declaration.</span></span> <span data-ttu-id="2434d-123">當未直接提供完整認證時，這項支援會自動提示使用者輸入使用者名稱、密碼或兩者。</span><span class="sxs-lookup"><span data-stu-id="2434d-123">This support automatically prompts the user for the user name, for the password, or for both when a full credential is not supplied directly.</span></span> <span data-ttu-id="2434d-124">如需認證屬性的詳細資訊，請參閱[Credential 屬性](./credential-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="2434d-124">For more information about the Credential attribute, see [Credential Attribute Declaration](./credential-attribute-declaration.md).</span></span>

### <a name="support-encoding-parameters-ad04"></a><span data-ttu-id="2434d-125"> (AD04) 支援編碼參數</span><span class="sxs-lookup"><span data-stu-id="2434d-125">Support Encoding Parameters (AD04)</span></span>

<span data-ttu-id="2434d-126">如果您的 Cmdlet 會讀取或寫入二進位格式的文字（例如寫入或讀取檔案系統中的檔案），則您的 Cmdlet 必須具有編碼參數，以指定二進位格式的文字編碼方式。</span><span class="sxs-lookup"><span data-stu-id="2434d-126">If your cmdlet reads or writes text to or from a binary form, such as writing to or reading from a file in a filesystem, then your cmdlet has to have Encoding parameter that specifies how the text is encoded in the binary form.</span></span>

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a><span data-ttu-id="2434d-127">測試 Cmdlet 應該會傳回布林值 (AD05) </span><span class="sxs-lookup"><span data-stu-id="2434d-127">Test Cmdlets Should Return a Boolean (AD05)</span></span>

<span data-ttu-id="2434d-128">對其資源執行測試的 Cmdlet 應該[會將 system.string 類型傳回](/dotnet/api/System.Boolean)給管線，以便在條件運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="2434d-128">Cmdlets that perform tests against their resources should return a [System.Boolean](/dotnet/api/System.Boolean) type to the pipeline so that they can be used in conditional expressions.</span></span>

## <a name="code-guidelines"></a><span data-ttu-id="2434d-129">程式碼方針</span><span class="sxs-lookup"><span data-stu-id="2434d-129">Code Guidelines</span></span>

<span data-ttu-id="2434d-130">撰寫 Cmdlet 程式碼時，應考慮下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="2434d-130">The following guidelines should be considered when writing cmdlet code.</span></span> <span data-ttu-id="2434d-131">當您找到適用于您情況的指導方針時，請務必查看類似指導方針的設計方針。</span><span class="sxs-lookup"><span data-stu-id="2434d-131">When you find a guideline that applies to your situation, be sure to look at the Design guidelines for similar guidelines.</span></span>

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a><span data-ttu-id="2434d-132">遵循 Cmdlet 類別命名慣例 (AC01) </span><span class="sxs-lookup"><span data-stu-id="2434d-132">Follow Cmdlet Class Naming Conventions (AC01)</span></span>

<span data-ttu-id="2434d-133">藉由遵循標準命名慣例，您可以讓 Cmdlet 更容易找到，並協助使用者瞭解 Cmdlet 的作用。</span><span class="sxs-lookup"><span data-stu-id="2434d-133">By following standard naming conventions, you make your cmdlets more discoverable, and you help the user understand exactly what the cmdlets do.</span></span> <span data-ttu-id="2434d-134">這種作法對於使用 Windows PowerShell 的其他開發人員而言特別重要，因為 Cmdlet 是公用類型。</span><span class="sxs-lookup"><span data-stu-id="2434d-134">This practice is particularly important for other developers using Windows PowerShell because cmdlets are public types.</span></span>

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a><span data-ttu-id="2434d-135">在正確的命名空間中定義 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2434d-135">Define a Cmdlet in the Correct Namespace</span></span>

<span data-ttu-id="2434d-136">您通常會在附加 "的 .NET Framework 命名空間中，定義 Cmdlet 的類別。命令，代表 Cmdlet 執行所在產品的命名空間。</span><span class="sxs-lookup"><span data-stu-id="2434d-136">You normally define the class for a cmdlet in a .NET Framework namespace that appends ".Commands" to the namespace that represents the product in which the cmdlet runs.</span></span> <span data-ttu-id="2434d-137">例如，Windows PowerShell 隨附的 Cmdlet 會定義在 `Microsoft.PowerShell.Commands` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="2434d-137">For example, cmdlets that are included with Windows PowerShell are defined in the `Microsoft.PowerShell.Commands` namespace.</span></span>

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a><span data-ttu-id="2434d-138">將 Cmdlet 類別命名為符合 Cmdlet 名稱</span><span class="sxs-lookup"><span data-stu-id="2434d-138">Name the Cmdlet Class to Match the Cmdlet Name</span></span>

<span data-ttu-id="2434d-139">當您命名執行 Cmdlet 的 .NET Framework 類別時，請將類別命名為 " *\<Verb>**\<Noun>**\<Command>* "，您可以在其中將 *\<Verb>* 和 *\<Noun>* 預留位置取代為用於 Cmdlet 名稱的動詞和名詞。</span><span class="sxs-lookup"><span data-stu-id="2434d-139">When you name the .NET Framework class that implements a cmdlet, name the class "*\<Verb>**\<Noun>**\<Command>*", where you replace the *\<Verb>* and *\<Noun>* placeholders with the verb and noun used for the cmdlet name.</span></span> <span data-ttu-id="2434d-140">例如， [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 是由名為的類別所實 `GetProcessCommand` 。</span><span class="sxs-lookup"><span data-stu-id="2434d-140">For example, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet is implemented by a class called `GetProcessCommand`.</span></span>

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a><span data-ttu-id="2434d-141">如果沒有管線輸入覆寫 BeginProcessing 方法 (AC02) </span><span class="sxs-lookup"><span data-stu-id="2434d-141">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>

<span data-ttu-id="2434d-142">如果您的 Cmdlet 不接受來自管線的輸入，則應該在[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中執行處理。</span><span class="sxs-lookup"><span data-stu-id="2434d-142">If your cmdlet does not accept input from the pipeline, processing should be implemented in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span> <span data-ttu-id="2434d-143">使用此方法可讓 Windows PowerShell 維護 Cmdlet 之間的順序。</span><span class="sxs-lookup"><span data-stu-id="2434d-143">Use of this method allows Windows PowerShell to maintain ordering between cmdlets.</span></span> <span data-ttu-id="2434d-144">管線中的第一個 Cmdlet 一律會傳回其物件，然後管線中的其餘 Cmdlet 就有機會開始處理。</span><span class="sxs-lookup"><span data-stu-id="2434d-144">The first cmdlet in the pipeline always returns its objects before the remaining cmdlets in the pipeline get a chance to start their processing.</span></span>

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a><span data-ttu-id="2434d-145">若要處理停止要求，請覆寫 StopProcessing 方法 (AC03) </span><span class="sxs-lookup"><span data-stu-id="2434d-145">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>

<span data-ttu-id="2434d-146">覆寫[StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法，讓您的 Cmdlet 可以處理停止信號。</span><span class="sxs-lookup"><span data-stu-id="2434d-146">Override the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method so that your cmdlet can handle stop signal.</span></span> <span data-ttu-id="2434d-147">某些 Cmdlet 會花很長的時間來完成其作業，並可讓您在呼叫 Windows PowerShell 執行時間之間進行較長的時間傳遞，例如當 Cmdlet 在長時間執行的 RPC 呼叫中封鎖執行緒時。</span><span class="sxs-lookup"><span data-stu-id="2434d-147">Some cmdlets take a long time to complete their operation, and they let a long time pass between calls to the Windows PowerShell runtime, such as when the cmdlet blocks the thread in long-running RPC calls.</span></span> <span data-ttu-id="2434d-148">這包括對[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法進行呼叫的 Cmdlet、 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，以及其他可能需要很長時間才能完成的意見反應機制，都包含在這種情況下。</span><span class="sxs-lookup"><span data-stu-id="2434d-148">This includes cmdlets that make calls to the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method, to the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, and to other feedback mechanisms that may take a long time to complete.</span></span> <span data-ttu-id="2434d-149">在這些情況下，使用者可能需要傳送停止信號給這些 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2434d-149">For these cases the user might need to send a stop signal to these cmdlets.</span></span>

### <a name="implement-the-idisposable-interface-ac04"></a><span data-ttu-id="2434d-150">執行 IDisposable 介面 (AC04) </span><span class="sxs-lookup"><span data-stu-id="2434d-150">Implement the IDisposable Interface (AC04)</span></span>

<span data-ttu-id="2434d-151">如果您的 Cmdlet 具有未處置 (寫入[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法所) 之管線的物件，您的 Cmdlet 可能需要額外的物件處置。</span><span class="sxs-lookup"><span data-stu-id="2434d-151">If your cmdlet has objects that are not disposed of (written to the pipeline) by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, your cmdlet might require additional object disposal.</span></span> <span data-ttu-id="2434d-152">例如，如果您的 Cmdlet 會在[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中開啟檔案控制代碼，並讓控制碼保持開啟以供[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法使用，則必須在處理結束時關閉此控制碼（handle）。</span><span class="sxs-lookup"><span data-stu-id="2434d-152">For example, if your cmdlet opens a file handle in its [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, this handle has to be closed at the end of processing.</span></span>

<span data-ttu-id="2434d-153">Windows PowerShell 執行時間並不一定會呼叫[system.servicemodel 方法。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)</span><span class="sxs-lookup"><span data-stu-id="2434d-153">The Windows PowerShell runtime does not always call the  [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="2434d-154">例如，如果 Cmdlet 在其作業中途取消，或在 Cmdlet 的任何部分發生終止錯誤，則可能不會呼叫[system.servicemodel 方法。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)</span><span class="sxs-lookup"><span data-stu-id="2434d-154">For example, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method might not be called if the cmdlet is canceled midway through its operation or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="2434d-155">因此，需要物件清除之 Cmdlet 的 .NET Framework 類別應該會執行完整的[IDisposable](/dotnet/api/System.IDisposable)介面模式，包括完成項，讓 Windows PowerShell 執行時間可以在處理結束時同時呼叫 System.web 和[IDisposable](/dotnet/api/System.IDisposable.Dispose)方法，以進行[管理](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)。</span><span class="sxs-lookup"><span data-stu-id="2434d-155">Therefore, the .NET Framework class for a cmdlet that requires object cleanup should implement the complete  [System.IDisposable](/dotnet/api/System.IDisposable) interface pattern, including the finalizer, so that the Windows PowerShell runtime can call both the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>

### <a name="use-serialization-friendly-parameter-types-ac05"></a><span data-ttu-id="2434d-156"> (AC05 使用序列化易懂的參數類型) </span><span class="sxs-lookup"><span data-stu-id="2434d-156">Use Serialization-friendly Parameter Types (AC05)</span></span>

<span data-ttu-id="2434d-157">若要支援在遠端電腦上執行 Cmdlet，請使用可在用戶端電腦上輕鬆序列化，然後在伺服器電腦上解除凍結的類型。</span><span class="sxs-lookup"><span data-stu-id="2434d-157">To support running your cmdlet on remote computers, use types that can be easily serialized on the client computer and then rehydrated on the server computer.</span></span> <span data-ttu-id="2434d-158">下列類型可供序列化。</span><span class="sxs-lookup"><span data-stu-id="2434d-158">The follow types are serialization-friendly.</span></span>

<span data-ttu-id="2434d-159">基本類型：</span><span class="sxs-lookup"><span data-stu-id="2434d-159">Primitive types:</span></span>

- <span data-ttu-id="2434d-160">Byte、SByte、Decimal、Single、Double、Int16、Int32、Int64、Uint16、UInt32 和 UInt64。</span><span class="sxs-lookup"><span data-stu-id="2434d-160">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, and UInt64.</span></span>

- <span data-ttu-id="2434d-161">布林值、Guid、位元組 []、TimeSpan、DateTime、Uri 和版本。</span><span class="sxs-lookup"><span data-stu-id="2434d-161">Boolean, Guid, Byte[], TimeSpan, DateTime, Uri, and Version.</span></span>

- <span data-ttu-id="2434d-162">Char、String、Xml。</span><span class="sxs-lookup"><span data-stu-id="2434d-162">Char, String, XmlDocument.</span></span>

<span data-ttu-id="2434d-163">內建的 rehydratable 類型：</span><span class="sxs-lookup"><span data-stu-id="2434d-163">Built-in rehydratable types:</span></span>

- <span data-ttu-id="2434d-164">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="2434d-164">PSPrimitiveDictionary</span></span>

- <span data-ttu-id="2434d-165">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2434d-165">SwitchParameter</span></span>

- <span data-ttu-id="2434d-166">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="2434d-166">PSListModifier</span></span>

- <span data-ttu-id="2434d-167">PSCredential</span><span class="sxs-lookup"><span data-stu-id="2434d-167">PSCredential</span></span>

- <span data-ttu-id="2434d-168">IPAddress、MailAddress</span><span class="sxs-lookup"><span data-stu-id="2434d-168">IPAddress, MailAddress</span></span>

- <span data-ttu-id="2434d-169">CultureInfo</span><span class="sxs-lookup"><span data-stu-id="2434d-169">CultureInfo</span></span>

- <span data-ttu-id="2434d-170">X509Certificate2、System.security.cryptography.x509certificates.x500distinguishedname</span><span class="sxs-lookup"><span data-stu-id="2434d-170">X509Certificate2, X500DistinguishedName</span></span>

- <span data-ttu-id="2434d-171">System.security.accesscontrol.directorysecurity、System.security.accesscontrol.filesecurity、RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="2434d-171">DirectorySecurity, FileSecurity, RegistrySecurity</span></span>

<span data-ttu-id="2434d-172">其他類型：</span><span class="sxs-lookup"><span data-stu-id="2434d-172">Other types:</span></span>

- <span data-ttu-id="2434d-173">SecureString</span><span class="sxs-lookup"><span data-stu-id="2434d-173">SecureString</span></span>

- <span data-ttu-id="2434d-174">容器 (上述類型的清單和字典) </span><span class="sxs-lookup"><span data-stu-id="2434d-174">Containers (lists and dictionaries of the above type)</span></span>

### <a name="use-securestring-for-sensitive-data-ac06"></a><span data-ttu-id="2434d-175">將 SecureString 用於機密資料 (AC06) </span><span class="sxs-lookup"><span data-stu-id="2434d-175">Use SecureString for Sensitive Data (AC06)</span></span>

<span data-ttu-id="2434d-176">處理敏感性資料時，請一律使用[Securestring](/dotnet/api/System.Security.SecureString)資料類型。</span><span class="sxs-lookup"><span data-stu-id="2434d-176">When handling sensitive data always use the [System.Security.Securestring](/dotnet/api/System.Security.SecureString) data type.</span></span> <span data-ttu-id="2434d-177">這可能包括參數的管線輸入，以及將機密資料傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="2434d-177">This could include pipeline input to parameters, as well as returning sensitive data to the pipeline.</span></span>

## <a name="see-also"></a><span data-ttu-id="2434d-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2434d-178">See Also</span></span>

[<span data-ttu-id="2434d-179">必要的開發指導方針</span><span class="sxs-lookup"><span data-stu-id="2434d-179">Required Development Guidelines</span></span>](./required-development-guidelines.md)

[<span data-ttu-id="2434d-180">強烈建議使用的開發指導方針</span><span class="sxs-lookup"><span data-stu-id="2434d-180">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

[<span data-ttu-id="2434d-181">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2434d-181">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
