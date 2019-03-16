---
title: 諮詢開發指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 871a74a084da3c7ec36767b7195461e0e7290cb9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056561"
---
# <a name="advisory-development-guidelines"></a><span data-ttu-id="39968-102">建議性開發指導方針</span><span class="sxs-lookup"><span data-stu-id="39968-102">Advisory Development Guidelines</span></span>

<span data-ttu-id="39968-103">本章節描述您應該考慮以確保良好的開發和使用者體驗的指導方針。</span><span class="sxs-lookup"><span data-stu-id="39968-103">This section describes guidelines that you should consider to ensure good development and user experiences.</span></span> <span data-ttu-id="39968-104">有時它們可能適用，而有時不可能。</span><span class="sxs-lookup"><span data-stu-id="39968-104">Sometimes they might apply, and sometimes they might not.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="39968-105">設計指導方針</span><span class="sxs-lookup"><span data-stu-id="39968-105">Design Guidelines</span></span>

- [<span data-ttu-id="39968-106">支援的 InputObject 參數 (AD01)</span><span class="sxs-lookup"><span data-stu-id="39968-106">Support an InputObject Parameter (AD01)</span></span>](./advisory-development-guidelines.md#AD01)

- [<span data-ttu-id="39968-107">Force 參數 （ad02 移） 的支援</span><span class="sxs-lookup"><span data-stu-id="39968-107">Support the Force Parameter (AD02)</span></span>](./advisory-development-guidelines.md#AD02)

- [<span data-ttu-id="39968-108">處理透過 Windows PowerShell (AD03) 的認證</span><span class="sxs-lookup"><span data-stu-id="39968-108">Handle Credentials Through Windows PowerShell (AD03)</span></span>](./advisory-development-guidelines.md#AD03)

- [<span data-ttu-id="39968-109">支援編碼的參數 (AD04)</span><span class="sxs-lookup"><span data-stu-id="39968-109">Support Encoding Parameters (AD04)</span></span>](./advisory-development-guidelines.md#AD04)

- [<span data-ttu-id="39968-110">測試 Cmdlet 應該會傳回布林值 (AD05)</span><span class="sxs-lookup"><span data-stu-id="39968-110">Test Cmdlets Should Return a Boolean (AD05)</span></span>](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a><span data-ttu-id="39968-111">程式碼的指導方針</span><span class="sxs-lookup"><span data-stu-id="39968-111">Code Guidelines</span></span>

- [<span data-ttu-id="39968-112">請依照下列 Cmdlet 類別命名慣例 (AC01)</span><span class="sxs-lookup"><span data-stu-id="39968-112">Follow Cmdlet Class Naming Conventions (AC01)</span></span>](./advisory-development-guidelines.md#AC01)

- [<span data-ttu-id="39968-113">如果沒有管線輸入覆寫 BeginProcessing 方法 (AC02)</span><span class="sxs-lookup"><span data-stu-id="39968-113">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>](./advisory-development-guidelines.md#AC02)

- [<span data-ttu-id="39968-114">若要處理停止要求覆寫 StopProcessing 方法 (AC03)</span><span class="sxs-lookup"><span data-stu-id="39968-114">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>](./advisory-development-guidelines.md#AC03)

- [<span data-ttu-id="39968-115">實作 IDisposable 介面 (AC04)</span><span class="sxs-lookup"><span data-stu-id="39968-115">Implement the IDisposable Interface (AC04)</span></span>](./advisory-development-guidelines.md#AC04)

- [<span data-ttu-id="39968-116">使用序列化參數型別 (AC05)</span><span class="sxs-lookup"><span data-stu-id="39968-116">Use Serialization-friendly Parameter Types (AC05)</span></span>](./advisory-development-guidelines.md#AC05)

- [<span data-ttu-id="39968-117">使用 SecureString，機密資料 (AC06)</span><span class="sxs-lookup"><span data-stu-id="39968-117">Use SecureString for Sensitive Data (AC06)</span></span>](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a><span data-ttu-id="39968-118">設計指導方針</span><span class="sxs-lookup"><span data-stu-id="39968-118">Design Guidelines</span></span>

<span data-ttu-id="39968-119">設計 cmdlet 時，就應該考慮下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="39968-119">The following guidelines should be considered when designing cmdlets.</span></span> <span data-ttu-id="39968-120">當您找到適用於您情況的設計指導方針時，請務必查看類似的指導方針中的程式碼的方針。</span><span class="sxs-lookup"><span data-stu-id="39968-120">When you find a Design guideline that applies to your situation, be sure to look at the Code guidelines for similar guidelines.</span></span>

### <a name="support-an-inputobject-parameter-ad01"></a><span data-ttu-id="39968-121">支援的 InputObject 參數 (AD01)</span><span class="sxs-lookup"><span data-stu-id="39968-121">Support an InputObject Parameter (AD01)</span></span>

<span data-ttu-id="39968-122">Windows PowerShell 會直接使用 Microsoft.NET Framework 物件，因為.NET Framework 物件通常會提供完全符合類型的使用者需要執行特定作業。</span><span class="sxs-lookup"><span data-stu-id="39968-122">Because Windows PowerShell works directly with Microsoft .NET Framework objects, a .NET Framework object is often available that exactly matches the type the user needs to perform a particular operation.</span></span> <span data-ttu-id="39968-123">`InputObject` 會接受這類物件做為輸入參數的標準名稱。</span><span class="sxs-lookup"><span data-stu-id="39968-123">`InputObject` is the standard name for a parameter that takes such an object as input.</span></span> <span data-ttu-id="39968-124">比方說，此範例**停止程序**中的 cmdlet [StopProc 教學課程](./stopproc-tutorial.md)定義`InputObject`類型支援從管線輸入處理序的參數。</span><span class="sxs-lookup"><span data-stu-id="39968-124">For example, the sample **Stop-Proc** cmdlet in the [StopProc Tutorial](./stopproc-tutorial.md) defines an `InputObject` parameter of type Process that supports the input from the pipeline.</span></span> <span data-ttu-id="39968-125">使用者可以取得一組處理程序物件的、 操作這些選取的確切的物件，若要停止，並再將其傳遞給**停止處理序**直接 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="39968-125">The user can get a set of process objects, manipulate them to select the exact objects to stop, and then pass them to the **Stop-Proc** cmdlet directly.</span></span>

### <a name="support-the-force-parameter-ad02"></a><span data-ttu-id="39968-126">Force 參數 （ad02 移） 的支援</span><span class="sxs-lookup"><span data-stu-id="39968-126">Support the Force Parameter (AD02)</span></span>

<span data-ttu-id="39968-127">有時候，指令程式必須保護使用者不會執行要求的作業。</span><span class="sxs-lookup"><span data-stu-id="39968-127">Occasionally, a cmdlet needs to protect the user from performing a requested operation.</span></span> <span data-ttu-id="39968-128">這類指令程式應該支援`Force`參數，以允許使用者覆寫該保護，如果使用者具有權限來執行此作業。</span><span class="sxs-lookup"><span data-stu-id="39968-128">Such a cmdlet should support a `Force` parameter to allow the user to override that protection if the user has permissions to perform the operation.</span></span>

<span data-ttu-id="39968-129">例如， [Remove-item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet 通常也不會移除唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="39968-129">For example, the [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet does not normally remove a read-only file.</span></span> <span data-ttu-id="39968-130">不過，此 cmdlet 支援`Force`參數讓使用者可以強制移除唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="39968-130">However, this cmdlet supports a `Force` parameter so a user can force removal of a read-only file.</span></span> <span data-ttu-id="39968-131">如果使用者已修改的唯讀屬性，權限，而且使用者會移除檔案，使用`Force`參數可簡化此作業。</span><span class="sxs-lookup"><span data-stu-id="39968-131">If the user already has permission to modify the read-only attribute, and the user removes the file, use of the `Force` parameter simplifies the operation.</span></span> <span data-ttu-id="39968-132">不過，如果使用者沒有權限可移除檔案，`Force`參數沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="39968-132">However, if the user does not have permission to remove the file, the `Force` parameter has no effect.</span></span>

### <a name="handle-credentials-through-windows-powershell-ad03"></a><span data-ttu-id="39968-133">處理透過 Windows PowerShell (AD03) 的認證</span><span class="sxs-lookup"><span data-stu-id="39968-133">Handle Credentials Through Windows PowerShell (AD03)</span></span>

<span data-ttu-id="39968-134">Cmdlet 應該定義`Credential`參數表示的認證。</span><span class="sxs-lookup"><span data-stu-id="39968-134">A cmdlet should define a `Credential` parameter to represent credentials.</span></span> <span data-ttu-id="39968-135">這個參數必須是型別[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) ，且必須使用的認證屬性宣告中定義。</span><span class="sxs-lookup"><span data-stu-id="39968-135">This parameter must be of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) and must be defined using a Credential attribute declaration.</span></span> <span data-ttu-id="39968-136">這項支援未直接提供完整的認證時，會自動提示使用者的使用者名稱、 密碼，或兩者。</span><span class="sxs-lookup"><span data-stu-id="39968-136">This support automatically prompts the user for the user name, for the password, or for both when a full credential is not supplied directly.</span></span> <span data-ttu-id="39968-137">如需有關認證屬性的詳細資訊，請參閱[認證屬性宣告](./credential-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="39968-137">For more information about the Credential attribute, see [Credential Attribute Declaration](./credential-attribute-declaration.md).</span></span>

### <a name="support-encoding-parameters-ad04"></a><span data-ttu-id="39968-138">支援編碼的參數 (AD04)</span><span class="sxs-lookup"><span data-stu-id="39968-138">Support Encoding Parameters (AD04)</span></span>

<span data-ttu-id="39968-139">如果您的 cmdlet 會讀取或寫入的文字或二進位格式，例如寫入或讀取的檔案中的檔案系統中，從您的 cmdlet 就必須要有 Encoding 參數，指定文字以二進位格式的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="39968-139">If your cmdlet reads or writes text to or from a binary form, such as writing to or reading from a file in a filesystem, then your cmdlet has to have Encoding parameter that specifies how the text is encoded in the binary form.</span></span>

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a><span data-ttu-id="39968-140">測試 Cmdlet 應該會傳回布林值 (AD05)</span><span class="sxs-lookup"><span data-stu-id="39968-140">Test Cmdlets Should Return a Boolean (AD05)</span></span>

<span data-ttu-id="39968-141">執行測試，針對其資源的指令程式應該會傳回[System.Boolean](/dotnet/api/System.Boolean)類型至管線，以便它們可以用於條件運算式。</span><span class="sxs-lookup"><span data-stu-id="39968-141">Cmdlets that perform tests against their resources should return a [System.Boolean](/dotnet/api/System.Boolean) type to the pipeline so that they can be used in conditional expressions.</span></span>

## <a name="code-guidelines"></a><span data-ttu-id="39968-142">程式碼的指導方針</span><span class="sxs-lookup"><span data-stu-id="39968-142">Code Guidelines</span></span>

<span data-ttu-id="39968-143">撰寫 cmdlet 程式碼時，應該考慮下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="39968-143">The following guidelines should be considered when writing cmdlet code.</span></span> <span data-ttu-id="39968-144">當您找到適用於您情況的指導方針時，請務必查看類似的指導方針的設計方針。</span><span class="sxs-lookup"><span data-stu-id="39968-144">When you find a guideline that applies to your situation, be sure to look at the Design guidelines for similar guidelines.</span></span>

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a><span data-ttu-id="39968-145">請依照下列 Cmdlet 類別命名慣例 (AC01)</span><span class="sxs-lookup"><span data-stu-id="39968-145">Follow Cmdlet Class Naming Conventions (AC01)</span></span>

<span data-ttu-id="39968-146">根據下列標準的命名慣例，讓您的 cmdlet 更容易被找到，而幫助使用者了解完全指令程式做什麼。</span><span class="sxs-lookup"><span data-stu-id="39968-146">By following standard naming conventions, you make your cmdlets more discoverable, and you help the user understand exactly what the cmdlets do.</span></span> <span data-ttu-id="39968-147">這種做法是使用 Windows PowerShell，因為 cmdlet 是公用類型的其他開發人員特別重要。</span><span class="sxs-lookup"><span data-stu-id="39968-147">This practice is particularly important for other developers using Windows PowerShell because cmdlets are public types.</span></span>

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a><span data-ttu-id="39968-148">定義正確的命名空間中的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="39968-148">Define a Cmdlet in the Correct Namespace</span></span>

<span data-ttu-id="39968-149">您通常會將附加至.NET Framework 命名空間中定義 cmdlet 類別 」。命令"代表的產品 cmdlet 執行所在之命名空間。</span><span class="sxs-lookup"><span data-stu-id="39968-149">You normally define the class for a cmdlet in a .NET Framework namespace that appends ".Commands" to the namespace that represents the product in which the cmdlet runs.</span></span> <span data-ttu-id="39968-150">比方說，隨附於 Windows PowerShell 的 cmdlet 定義於`Microsoft.PowerShell.Commands`命名空間。</span><span class="sxs-lookup"><span data-stu-id="39968-150">For example, cmdlets that are included with Windows PowerShell are defined in the `Microsoft.PowerShell.Commands` namespace.</span></span>

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a><span data-ttu-id="39968-151">名稱比對 Cmdlet 名稱在 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="39968-151">Name the Cmdlet Class to Match the Cmdlet Name</span></span>

<span data-ttu-id="39968-152">當您命名實作指令程式的.NET Framework 類別時，將類別命名為"*\<動詞 >**\<名詞 >**\<命令 >*」，您用來取代*\<動詞 >* 並*\<名詞 >* 預留位置取代為用於的 cmdlet 名稱的名詞與動詞命令。</span><span class="sxs-lookup"><span data-stu-id="39968-152">When you name the .NET Framework class that implements a cmdlet, name the class "*\<Verb>**\<Noun>**\<Command>*", where you replace the *\<Verb>* and *\<Noun>* placeholders with the verb and noun used for the cmdlet name.</span></span> <span data-ttu-id="39968-153">例如， [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式藉由呼叫類別`GetProcessCommand`。</span><span class="sxs-lookup"><span data-stu-id="39968-153">For example, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet is implemented by a class called `GetProcessCommand`.</span></span>

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a><span data-ttu-id="39968-154">如果沒有管線輸入覆寫 BeginProcessing 方法 (AC02)</span><span class="sxs-lookup"><span data-stu-id="39968-154">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>

<span data-ttu-id="39968-155">如果您的 cmdlet 不接受來自管線的輸入，應該在實作處理[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="39968-155">If your cmdlet does not accept input from the pipeline, processing should be implemented in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span> <span data-ttu-id="39968-156">使用這個方法可讓 Windows PowerShell 來維護 cmdlet 之間的順序。</span><span class="sxs-lookup"><span data-stu-id="39968-156">Use of this method allows Windows PowerShell to maintain ordering between cmdlets.</span></span> <span data-ttu-id="39968-157">在管線中的其餘 cmdlet 有機會開始其處理之前，管線中的第一個 cmdlet 一律會傳回其物件。</span><span class="sxs-lookup"><span data-stu-id="39968-157">The first cmdlet in the pipeline always returns its objects before the remaining cmdlets in the pipeline get a chance to start their processing.</span></span>

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a><span data-ttu-id="39968-158">若要處理停止要求覆寫 StopProcessing 方法 (AC03)</span><span class="sxs-lookup"><span data-stu-id="39968-158">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>

<span data-ttu-id="39968-159">覆寫[System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法，使您的 cmdlet 能夠處理停止訊號。</span><span class="sxs-lookup"><span data-stu-id="39968-159">Override the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method so that your cmdlet can handle stop signal.</span></span> <span data-ttu-id="39968-160">某些 cmdlet 需要一些時間才能完成其作業，並可讓 Windows PowerShell 執行階段，例如當此 cmdlet 會封鎖長時間執行的 RPC 呼叫的執行緒的呼叫之間傳遞很長的時間。</span><span class="sxs-lookup"><span data-stu-id="39968-160">Some cmdlets take a long time to complete their operation, and they let a long time pass between calls to the Windows PowerShell runtime, such as when the cmdlet blocks the thread in long-running RPC calls.</span></span> <span data-ttu-id="39968-161">這包括對進行呼叫的 cmdlet [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法，以[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，以及其他意見反應可能需要很長的時間才能完成的機制。</span><span class="sxs-lookup"><span data-stu-id="39968-161">This includes cmdlets that make calls to the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method, to the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, and to other feedback mechanisms that may take a long time to complete.</span></span> <span data-ttu-id="39968-162">在這些情況下可能需要使用者將停止訊號傳送至這些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="39968-162">For these cases the user might need to send a stop signal to these cmdlets.</span></span>

### <a name="implement-the-idisposable-interface-ac04"></a><span data-ttu-id="39968-163">實作 IDisposable 介面 (AC04)</span><span class="sxs-lookup"><span data-stu-id="39968-163">Implement the IDisposable Interface (AC04)</span></span>

<span data-ttu-id="39968-164">如果您的 cmdlet 未處置的物件 （寫入管線） 所[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法中，您的 cmdlet 可能會需要額外的物件可供使用。</span><span class="sxs-lookup"><span data-stu-id="39968-164">If your cmdlet has objects that are not disposed of (written to the pipeline) by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, your cmdlet might require additional object disposal.</span></span> <span data-ttu-id="39968-165">例如，如果您的指令程式會開啟檔案控制代碼，以其[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，並維持控制代碼開啟以供[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，這個控制代碼已關閉結尾的處理。</span><span class="sxs-lookup"><span data-stu-id="39968-165">For example, if your cmdlet opens a file handle in its [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, this handle has to be closed at the end of processing.</span></span>

<span data-ttu-id="39968-166">Windows PowerShell 執行階段不會一律呼叫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="39968-166">The Windows PowerShell runtime does not always call the  [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="39968-167">例如， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)如果 cmdlet 可透過其作業中途取消或終止錯誤發生在 cmdlet 的任何部分，可能不會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="39968-167">For example, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method might not be called if the cmdlet is canceled midway through its operation or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="39968-168">因此，需要物件清除指令程式的.NET Framework 類別應實作完整[System.IDisposable](/dotnet/api/System.IDisposable)介面模式，包括完成項，可讓 Windows PowerShell 執行階段呼叫兩者[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)並[System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose)結尾的處理方法。</span><span class="sxs-lookup"><span data-stu-id="39968-168">Therefore, the .NET Framework class for a cmdlet that requires object cleanup should implement the complete  [System.IDisposable](/dotnet/api/System.IDisposable) interface pattern, including the finalizer, so that the Windows PowerShell runtime can call both the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>

### <a name="use-serialization-friendly-parameter-types-ac05"></a><span data-ttu-id="39968-169">使用序列化參數型別 (AC05)</span><span class="sxs-lookup"><span data-stu-id="39968-169">Use Serialization-friendly Parameter Types (AC05)</span></span>

<span data-ttu-id="39968-170">若要支援在遠端電腦上執行您的 cmdlet，使用型別，可以輕鬆地序列化用戶端電腦上，並接著解除凍結伺服器電腦上。</span><span class="sxs-lookup"><span data-stu-id="39968-170">To support running your cmdlet on remote computers, use types that can be easily serialized on the client computer and then rehydrated on the server computer.</span></span> <span data-ttu-id="39968-171">下列型別會序列化。</span><span class="sxs-lookup"><span data-stu-id="39968-171">The follow types are serialization-friendly.</span></span>

<span data-ttu-id="39968-172">基本類型：</span><span class="sxs-lookup"><span data-stu-id="39968-172">Primitive types:</span></span>

- <span data-ttu-id="39968-173">位元組、 SByte、 Decimal、 單一、 Double、 Int16、 Int32、 Int64、 Uint16、 UInt32 和 UInt64。</span><span class="sxs-lookup"><span data-stu-id="39968-173">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, and UInt64.</span></span>

- <span data-ttu-id="39968-174">布林值、 Guid、 Byte []、 TimeSpan、 DateTime、 Uri 和版本。</span><span class="sxs-lookup"><span data-stu-id="39968-174">Boolean, Guid, Byte[], TimeSpan, DateTime, Uri, and Version.</span></span>

- <span data-ttu-id="39968-175">Char、 String，XmlDocument。</span><span class="sxs-lookup"><span data-stu-id="39968-175">Char, String, XmlDocument.</span></span>

<span data-ttu-id="39968-176">內建的 rehydratable 類型：</span><span class="sxs-lookup"><span data-stu-id="39968-176">Built-in rehydratable types:</span></span>

- <span data-ttu-id="39968-177">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="39968-177">PSPrimitiveDictionary</span></span>

- <span data-ttu-id="39968-178">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="39968-178">SwitchParameter</span></span>

- <span data-ttu-id="39968-179">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="39968-179">PSListModifier</span></span>

- <span data-ttu-id="39968-180">PSCredential</span><span class="sxs-lookup"><span data-stu-id="39968-180">PSCredential</span></span>

- <span data-ttu-id="39968-181">Ip 位址 MailAddress</span><span class="sxs-lookup"><span data-stu-id="39968-181">IPAddress, MailAddress</span></span>

- <span data-ttu-id="39968-182">CultureInfo</span><span class="sxs-lookup"><span data-stu-id="39968-182">CultureInfo</span></span>

- <span data-ttu-id="39968-183">X509Certificate2, X500DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="39968-183">X509Certificate2, X500DistinguishedName</span></span>

- <span data-ttu-id="39968-184">DirectorySecurity，FileSecurity，RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="39968-184">DirectorySecurity, FileSecurity, RegistrySecurity</span></span>

<span data-ttu-id="39968-185">其他類型：</span><span class="sxs-lookup"><span data-stu-id="39968-185">Other types:</span></span>

- <span data-ttu-id="39968-186">SecureString</span><span class="sxs-lookup"><span data-stu-id="39968-186">SecureString</span></span>

- <span data-ttu-id="39968-187">容器 （list 和 dictionary 的上述類型）</span><span class="sxs-lookup"><span data-stu-id="39968-187">Containers (lists and dictionaries of the above type)</span></span>

### <a name="use-securestring-for-sensitive-data-ac06"></a><span data-ttu-id="39968-188">使用 SecureString，機密資料 (AC06)</span><span class="sxs-lookup"><span data-stu-id="39968-188">Use SecureString for Sensitive Data (AC06)</span></span>

<span data-ttu-id="39968-189">永遠處理敏感性資料時使用[System.Security.Securestring](/dotnet/api/System.Security.SecureString)資料型別。</span><span class="sxs-lookup"><span data-stu-id="39968-189">When handling sensitive data always use the [System.Security.Securestring](/dotnet/api/System.Security.SecureString) data type.</span></span> <span data-ttu-id="39968-190">這可能包括參數，以及將機密資料傳回至管線的管線輸入。</span><span class="sxs-lookup"><span data-stu-id="39968-190">This could include pipeline input to parameters, as well as returning sensitive data to the pipeline.</span></span>

## <a name="see-also"></a><span data-ttu-id="39968-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39968-191">See Also</span></span>

[<span data-ttu-id="39968-192">所需的開發指導方針</span><span class="sxs-lookup"><span data-stu-id="39968-192">Required Development Guidelines</span></span>](./required-development-guidelines.md)

[<span data-ttu-id="39968-193">極力建議您的開發指導方針</span><span class="sxs-lookup"><span data-stu-id="39968-193">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

[<span data-ttu-id="39968-194">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="39968-194">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
