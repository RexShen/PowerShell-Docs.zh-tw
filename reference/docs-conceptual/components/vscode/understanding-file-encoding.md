---
title: 了解 VSCode 與 PowerShell 中的檔案編碼
description: 設定檔案的編碼方式在 VSCode 和 PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 9cf445ebd0c2bb2dbdf4438f02dafe3df3a5d1e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429800"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="f796e-103">了解 VSCode 與 PowerShell 中的檔案編碼</span><span class="sxs-lookup"><span data-stu-id="f796e-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="f796e-104">當使用 VS Code 來建立和編輯 PowerShell 指令碼時，務必檔案使用正確的字元編碼格式儲存。</span><span class="sxs-lookup"><span data-stu-id="f796e-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="f796e-105">什麼是檔案的編碼方式，以及它為何如此重要？</span><span class="sxs-lookup"><span data-stu-id="f796e-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="f796e-106">VSCode 會管理人力的輸入字串的緩衝區的字元與位元組到檔案系統讀取/寫入區塊之間的介面。</span><span class="sxs-lookup"><span data-stu-id="f796e-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="f796e-107">當 VSCode 儲存檔案時，它會使用文字編碼來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="f796e-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="f796e-108">同樣地，PowerShell 執行指令碼時它必須將檔案中的位元組轉換為字元來重建檔案到 PowerShell 程式。</span><span class="sxs-lookup"><span data-stu-id="f796e-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="f796e-109">因為 VSCode 將檔案寫入，且 PowerShell 會讀取檔案，他們需要使用相同的編碼系統。</span><span class="sxs-lookup"><span data-stu-id="f796e-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="f796e-110">剖析的 PowerShell 指令碼的這個程序發生：*位元組* -> *字元* -> *權杖* ->  *抽象語法樹狀結構* -> *執行*。</span><span class="sxs-lookup"><span data-stu-id="f796e-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="f796e-111">VSCode 和 PowerShell 會安裝以合理的預設編碼設定。</span><span class="sxs-lookup"><span data-stu-id="f796e-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="f796e-112">不過，使用 PowerShell 的預設編碼方式已變更的 PowerShell Core (v6.x) 版本。</span><span class="sxs-lookup"><span data-stu-id="f796e-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="f796e-113">若要確保在 VSCode 中使用 PowerShell 或 PowerShell 延伸模組時沒有發生問題，您需要設定 VSCode 和 PowerShell 設定正確。</span><span class="sxs-lookup"><span data-stu-id="f796e-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="f796e-114">編碼問題常見原因</span><span class="sxs-lookup"><span data-stu-id="f796e-114">Common causes of encoding issues</span></span>

<span data-ttu-id="f796e-115">VSCode 或指令碼檔案的編碼方式不符合預期的編碼的 PowerShell 時，會發生編碼的問題。</span><span class="sxs-lookup"><span data-stu-id="f796e-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="f796e-116">沒有任何方法，適用於 PowerShell 來自動判斷檔案的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="f796e-117">您是有可能已經編碼問題，當您使用不在字元[7 位元 ASCII 字元集](https://ascii.cl/)。</span><span class="sxs-lookup"><span data-stu-id="f796e-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="f796e-118">例如：</span><span class="sxs-lookup"><span data-stu-id="f796e-118">For example:</span></span>

- <span data-ttu-id="f796e-119">加重音拉丁字元 (`É`， `ü`)</span><span class="sxs-lookup"><span data-stu-id="f796e-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="f796e-120">非拉丁字元像是斯拉夫文 (`Д`， `Ц`)</span><span class="sxs-lookup"><span data-stu-id="f796e-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="f796e-121">Han 中文 (`脚`， `本`)</span><span class="sxs-lookup"><span data-stu-id="f796e-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="f796e-122">編碼問題的常見原因如下：</span><span class="sxs-lookup"><span data-stu-id="f796e-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="f796e-123">VSCode 和 PowerShell 的編碼不從其預設值已變更。</span><span class="sxs-lookup"><span data-stu-id="f796e-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="f796e-124">PowerShell 5.1 及之前的版本的預設編碼是從 VSCode 的不同。</span><span class="sxs-lookup"><span data-stu-id="f796e-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="f796e-125">另一個編輯器已開啟，並覆寫的檔案，以新的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="f796e-126">這通常發生在 ISE。</span><span class="sxs-lookup"><span data-stu-id="f796e-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="f796e-127">檔案已簽入不同的原始檔控制中的編碼方式從哪些 VSCode 或 PowerShell 預期。</span><span class="sxs-lookup"><span data-stu-id="f796e-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="f796e-128">發生此情況的共同作業者使用不同編碼的組態編輯器。</span><span class="sxs-lookup"><span data-stu-id="f796e-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="f796e-129">如何分辨您有編碼的問題</span><span class="sxs-lookup"><span data-stu-id="f796e-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="f796e-130">通常編碼錯誤呈現為剖析指令碼中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f796e-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="f796e-131">如果您發現您的指令碼中的奇怪字元序列，這可以是問題。</span><span class="sxs-lookup"><span data-stu-id="f796e-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="f796e-132">在下列範例中，短破折號 (`–`) 會顯示為字元`â€“`:</span><span class="sxs-lookup"><span data-stu-id="f796e-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="f796e-133">因為 VSCode 編碼字元，就會發生這個問題`–`做為位元組的 utf-8 `0xE2 0x80 0x93`。</span><span class="sxs-lookup"><span data-stu-id="f796e-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="f796e-134">這些位元組會解碼時作為 Windows 1252，它們會被解譯為字元`â€“`。</span><span class="sxs-lookup"><span data-stu-id="f796e-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="f796e-135">您可能會看到一些奇怪的字元序列包括：</span><span class="sxs-lookup"><span data-stu-id="f796e-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="f796e-136">`â€“`，而非 `–`</span><span class="sxs-lookup"><span data-stu-id="f796e-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="f796e-137">`â€”`，而非`—`</span><span class="sxs-lookup"><span data-stu-id="f796e-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="f796e-138">`Ã„2`，而非`Ä`</span><span class="sxs-lookup"><span data-stu-id="f796e-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="f796e-139">`Â` 而不是` `（不分行空格）</span><span class="sxs-lookup"><span data-stu-id="f796e-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="f796e-140">`Ã©`，而非`é`</span><span class="sxs-lookup"><span data-stu-id="f796e-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="f796e-141">這很方便[參考](https://www.i18nqa.com/debug/utf8-debug.html)列出表示 UTF-8/Windows-1252年編碼問題的常見模式。</span><span class="sxs-lookup"><span data-stu-id="f796e-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="f796e-142">在 VSCode 中的 PowerShell 延伸模組與編碼之間的互動方式</span><span class="sxs-lookup"><span data-stu-id="f796e-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="f796e-143">PowerShell 延伸模組互動數種方式中的指令碼：</span><span class="sxs-lookup"><span data-stu-id="f796e-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="f796e-144">當在 VSCode 中編輯指令碼時，就會 vscode 將內容傳送至延伸模組。</span><span class="sxs-lookup"><span data-stu-id="f796e-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="f796e-145">[語言伺服器通訊協定][]規定，在 utf-8 中傳送此內容。</span><span class="sxs-lookup"><span data-stu-id="f796e-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="f796e-146">因此，不可能進行擴充，以取得錯誤的編碼。</span><span class="sxs-lookup"><span data-stu-id="f796e-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="f796e-147">當指令碼會直接在整合式主控台中執行時，它們是從檔案讀取 powershell 直接。</span><span class="sxs-lookup"><span data-stu-id="f796e-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="f796e-148">如果 PowerShell 的編碼方式和 VSCode 的不同，可以發生錯誤了這裡。</span><span class="sxs-lookup"><span data-stu-id="f796e-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="f796e-149">當在 VSCode 中開啟的指令碼參考另一個不是在 VSCode 中開啟的指令碼時，延伸模組會回復成從檔案系統載入該指令碼的內容。</span><span class="sxs-lookup"><span data-stu-id="f796e-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="f796e-150">PowerShell 延伸模組會預設為 utf-8 編碼，但會使用[位元組順序標記][]，或 BOM，偵測，以選取正確的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="f796e-151">假設無 BOM 格式的編碼方式時，就會發生問題 (例如[utf-8][]不含 bom 並[Windows-1252][])。</span><span class="sxs-lookup"><span data-stu-id="f796e-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="f796e-152">PowerShell 延伸模組會預設為 utf-8。</span><span class="sxs-lookup"><span data-stu-id="f796e-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="f796e-153">延伸模組不能變更 VSCode 的編碼設定。</span><span class="sxs-lookup"><span data-stu-id="f796e-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="f796e-154">如需詳細資訊，請參閱 <<c0> [ 發出 #824](https://github.com/Microsoft/vscode/issues/824)。</span><span class="sxs-lookup"><span data-stu-id="f796e-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="f796e-155">選擇正確的編碼方式</span><span class="sxs-lookup"><span data-stu-id="f796e-155">Choosing the right encoding</span></span>

<span data-ttu-id="f796e-156">不同系統和應用程式可以使用不同的編碼：</span><span class="sxs-lookup"><span data-stu-id="f796e-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="f796e-157">在.NET Standard 中，在 web 上，並在 Linux 環境中，utf-8 是現在主控項的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="f796e-158">許多.NET Framework 應用程式使用[utf-16][]。</span><span class="sxs-lookup"><span data-stu-id="f796e-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="f796e-159">基於歷史原因，這有時稱為"Unicode"，現在的詞彙是指網羅[標準](https://en.wikipedia.org/wiki/Unicode)包含 utf-8 和 utf-16。</span><span class="sxs-lookup"><span data-stu-id="f796e-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="f796e-160">Windows 中，許多比 Unicode 的原生應用程式繼續依預設會使用 Windows 1252。</span><span class="sxs-lookup"><span data-stu-id="f796e-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="f796e-161">Unicode 編碼方式也有位元組順序標記 (BOM) 的概念。</span><span class="sxs-lookup"><span data-stu-id="f796e-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="f796e-162">Bom 會告訴解碼器文字使用哪種編碼文字的開頭發生。</span><span class="sxs-lookup"><span data-stu-id="f796e-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="f796e-163">針對多位元組編碼，BOM 也會指出[位元組序](https://en.wikipedia.org/wiki/Endianness)編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="f796e-164">Bom 被設計成很少會發生在非 Unicode 文字，讓文字在 BOM 存在時，會是 Unicode 合理猜測的位元組。</span><span class="sxs-lookup"><span data-stu-id="f796e-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="f796e-165">Bom 是選擇性的其採用不受歡迎 Linux 世界中，因為在各處使用可靠的 utf-8 慣例。</span><span class="sxs-lookup"><span data-stu-id="f796e-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="f796e-166">大部分的 Linux 應用程式會假設文字輸入以 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="f796e-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="f796e-167">雖然許多 Linux 應用程式會辨識並正確處理 BOM，數字未這麼做，導致操作與這些應用程式的文字中的成品。</span><span class="sxs-lookup"><span data-stu-id="f796e-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="f796e-168">**因此**：</span><span class="sxs-lookup"><span data-stu-id="f796e-168">**Therefore**:</span></span>

- <span data-ttu-id="f796e-169">如果您主要是使用 Windows 應用程式和 Windows PowerShell，您應該會偏好使用如 utf-8 BOM 或 utf-16 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="f796e-170">如果您使用跨平台，您應該會偏好使用以 BOM 的 utf-8。</span><span class="sxs-lookup"><span data-stu-id="f796e-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="f796e-171">如果您主要是在 Linux 相關聯的內容中，您應該會偏好使用不具有 BOM 的 utf-8。</span><span class="sxs-lookup"><span data-stu-id="f796e-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="f796e-172">Windows-1252年和拉丁文-1。 如果可能的話，您應該避免基本上是舊版的編碼</span><span class="sxs-lookup"><span data-stu-id="f796e-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="f796e-173">不過，某些較舊的 Windows 應用程式可能取決於它們。</span><span class="sxs-lookup"><span data-stu-id="f796e-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="f796e-174">也很值得一提，簽署指令碼[編碼相依](https://github.com/PowerShell/PowerShell/issues/3466)，這表示變更已簽署的指令碼的編碼方式，將需要重新簽署。</span><span class="sxs-lookup"><span data-stu-id="f796e-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="f796e-175">設定 VSCode</span><span class="sxs-lookup"><span data-stu-id="f796e-175">Configuring VSCode</span></span>

<span data-ttu-id="f796e-176">VSCode 的預設編碼是不具有 BOM 的 utf-8。</span><span class="sxs-lookup"><span data-stu-id="f796e-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="f796e-177">若要設定[VSCode 的編碼方式][]，請移至 VSCode 設定 (<kbd>Ctrl<kbd>+</kbd>，</kbd>)，並設定`"files.encoding"`設定：</span><span class="sxs-lookup"><span data-stu-id="f796e-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="f796e-178">一些可能的值為：</span><span class="sxs-lookup"><span data-stu-id="f796e-178">Some possible values are:</span></span>

- <span data-ttu-id="f796e-179">`utf8`: [Utf-8]不加 BOM</span><span class="sxs-lookup"><span data-stu-id="f796e-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="f796e-180">`utf8bom`: [Utf-8] bom</span><span class="sxs-lookup"><span data-stu-id="f796e-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="f796e-181">`utf16le`: Little endian [utf-16]</span><span class="sxs-lookup"><span data-stu-id="f796e-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="f796e-182">`utf16be`: Big endian [utf-16]</span><span class="sxs-lookup"><span data-stu-id="f796e-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="f796e-183">`windows1252`：[Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="f796e-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="f796e-184">應該在下拉式清單中取得，這在 GUI 檢視中，或自動完成，在 JSON 中的檢視。</span><span class="sxs-lookup"><span data-stu-id="f796e-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="f796e-185">您也可以將下列加入盡可能的編碼方式的自動偵測中：</span><span class="sxs-lookup"><span data-stu-id="f796e-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="f796e-186">如果您不想讓這些設定會影響所有的檔案類型，VSCode 也可讓每個語言設定。</span><span class="sxs-lookup"><span data-stu-id="f796e-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="f796e-187">建立特定語言的設定將設定放入`[<language-name>]`欄位。</span><span class="sxs-lookup"><span data-stu-id="f796e-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="f796e-188">例如：</span><span class="sxs-lookup"><span data-stu-id="f796e-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="f796e-189">設定 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f796e-189">Configuring PowerShell</span></span>

<span data-ttu-id="f796e-190">PowerShell 的預設編碼方式會根據版本而有所不同：</span><span class="sxs-lookup"><span data-stu-id="f796e-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="f796e-191">在 PowerShell 6 + 中，預設的編碼方式是不具有 BOM 的 utf-8 所有平台上。</span><span class="sxs-lookup"><span data-stu-id="f796e-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="f796e-192">在 Windows PowerShell 中，預設的編碼方式通常是 Windows-1252 的延伸模組[latin-1][]，也稱為 ISO 8859-1。</span><span class="sxs-lookup"><span data-stu-id="f796e-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="f796e-193">在 PowerShell 5 + 中，您可以找到與此編碼預設值：</span><span class="sxs-lookup"><span data-stu-id="f796e-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="f796e-194">下列[指令碼](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)可用來判斷什麼編碼您的 PowerShell 工作階段會推斷不具有 BOM 的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f796e-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="f796e-195">可以將 PowerShell 設為使用指定的編碼方式更廣泛使用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="f796e-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="f796e-196">查看下列文章：</span><span class="sxs-lookup"><span data-stu-id="f796e-196">See the following articles:</span></span>

- <span data-ttu-id="f796e-197">[@mklement0][StackOverflow 上的 PowerShell 編碼方式相關的答案](https://stackoverflow.com/a/40098904)。</span><span class="sxs-lookup"><span data-stu-id="f796e-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="f796e-198">[@rkeithhill][有關在 PowerShell 中的無 BOM 的 utf-8 輸入處理的部落格文章](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)。</span><span class="sxs-lookup"><span data-stu-id="f796e-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="f796e-199">您不可能強制 PowerShell 以使用特定的輸入編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="f796e-200">PowerShell 5.1 和以下版本設為 Windows 1252 時沒有 BOM 編碼的預設值。</span><span class="sxs-lookup"><span data-stu-id="f796e-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="f796e-201">基於互通性考量，最好是以包含 BOM 以 Unicode 格式儲存指令碼。</span><span class="sxs-lookup"><span data-stu-id="f796e-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f796e-202">任何其他工具您有該觸控式 PowerShell 指令碼可能會受到您的編碼選項，或重新編碼您的指令碼，以其他編碼。</span><span class="sxs-lookup"><span data-stu-id="f796e-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="f796e-203">現有的指令碼</span><span class="sxs-lookup"><span data-stu-id="f796e-203">Existing scripts</span></span>

<span data-ttu-id="f796e-204">已在檔案系統上的指令碼可能需要重新編碼，您新的選擇編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="f796e-205">下方列的在 VSCode 中，您會看到 [utf-8] 標籤。</span><span class="sxs-lookup"><span data-stu-id="f796e-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="f796e-206">按一下以開啟 [動作] 列，然後選取**以編碼方式儲存**。</span><span class="sxs-lookup"><span data-stu-id="f796e-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="f796e-207">您現在可以選擇以新的編碼方式，就該檔案。</span><span class="sxs-lookup"><span data-stu-id="f796e-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="f796e-208">請參閱[VSCode 的編碼方式][]的完整指示。</span><span class="sxs-lookup"><span data-stu-id="f796e-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="f796e-209">如果您需要重新編碼多個檔案，您可以使用下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="f796e-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="f796e-210">PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="f796e-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="f796e-211">如果您也會編輯使用 PowerShell ISE 指令碼，您需要同步處理您的編碼設定。</span><span class="sxs-lookup"><span data-stu-id="f796e-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="f796e-212">ISE 應該接受 BOM，但也可以使用反映來[設定的編碼方式](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)。</span><span class="sxs-lookup"><span data-stu-id="f796e-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="f796e-213">請注意這不會在新創公司之間保存。</span><span class="sxs-lookup"><span data-stu-id="f796e-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="f796e-214">原始檔控制軟體</span><span class="sxs-lookup"><span data-stu-id="f796e-214">Source control software</span></span>

<span data-ttu-id="f796e-215">某些原始檔控制工具，例如 git 忽略編碼;git 只會追蹤位元組。</span><span class="sxs-lookup"><span data-stu-id="f796e-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="f796e-216">例如 TFS 或 Mercurial，卻不然。</span><span class="sxs-lookup"><span data-stu-id="f796e-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="f796e-217">解碼的文字依賴甚至一些 git 為基礎的工具。</span><span class="sxs-lookup"><span data-stu-id="f796e-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="f796e-218">這種情況時，請確定您：</span><span class="sxs-lookup"><span data-stu-id="f796e-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="f796e-219">設定以符合您的 VSCode 設定原始檔控制中的編碼的文字。</span><span class="sxs-lookup"><span data-stu-id="f796e-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="f796e-220">請確定您的檔案已簽入原始檔控制相關的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="f796e-221">請小心變更，以透過原始檔控制所收到的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f796e-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="f796e-222">索引鍵的符號是差異變更，但沒有似乎已變更 （因為有個位元組，但字元不具有） 表示。</span><span class="sxs-lookup"><span data-stu-id="f796e-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="f796e-223">共同作業者的環境</span><span class="sxs-lookup"><span data-stu-id="f796e-223">Collaborators' environments</span></span>

<span data-ttu-id="f796e-224">頂端設定原始檔控制，請確定在您共用的任何檔案上共同作業者沒有覆寫編碼方式，藉由重新編碼 PowerShell 檔案的設定。</span><span class="sxs-lookup"><span data-stu-id="f796e-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="f796e-225">其他程式</span><span class="sxs-lookup"><span data-stu-id="f796e-225">Other programs</span></span>

<span data-ttu-id="f796e-226">可讀取或寫入的 PowerShell 指令碼的其他程式可能會重新加以編碼。</span><span class="sxs-lookup"><span data-stu-id="f796e-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="f796e-227">以下列出一些範例：</span><span class="sxs-lookup"><span data-stu-id="f796e-227">Some examples are:</span></span>

- <span data-ttu-id="f796e-228">使用剪貼簿複製並貼上指令碼。</span><span class="sxs-lookup"><span data-stu-id="f796e-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="f796e-229">這是常見的案例，例如：</span><span class="sxs-lookup"><span data-stu-id="f796e-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="f796e-230">將指令碼複製到 VM</span><span class="sxs-lookup"><span data-stu-id="f796e-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="f796e-231">複製出電子郵件或網頁的指令碼</span><span class="sxs-lookup"><span data-stu-id="f796e-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="f796e-232">複製指令碼，傳入或傳出的 Microsoft Word 或 PowerPoint 文件</span><span class="sxs-lookup"><span data-stu-id="f796e-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="f796e-233">其他文字編輯器，例如：</span><span class="sxs-lookup"><span data-stu-id="f796e-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="f796e-234">在 [記事本]</span><span class="sxs-lookup"><span data-stu-id="f796e-234">Notepad</span></span>
  - <span data-ttu-id="f796e-235">vim</span><span class="sxs-lookup"><span data-stu-id="f796e-235">vim</span></span>
  - <span data-ttu-id="f796e-236">任何其他的 PowerShell 指令碼編輯器</span><span class="sxs-lookup"><span data-stu-id="f796e-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="f796e-237">文字編輯公用程式，例如：</span><span class="sxs-lookup"><span data-stu-id="f796e-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="f796e-238">之類的 PowerShell 重新導向運算子`>`和 `>>`</span><span class="sxs-lookup"><span data-stu-id="f796e-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="f796e-239">檔案傳輸的程式，例如：</span><span class="sxs-lookup"><span data-stu-id="f796e-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="f796e-240">Web 瀏覽器中，但是，要下載指令碼時</span><span class="sxs-lookup"><span data-stu-id="f796e-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="f796e-241">檔案共用</span><span class="sxs-lookup"><span data-stu-id="f796e-241">A file share</span></span>

<span data-ttu-id="f796e-242">其中部分工具處理的位元組，而不是文字，但其他人提供編碼的組態。</span><span class="sxs-lookup"><span data-stu-id="f796e-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="f796e-243">在這些情況下，您要設定的編碼方式，您需要使其與您的編輯器以避免發生問題的編碼方式相同。</span><span class="sxs-lookup"><span data-stu-id="f796e-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="f796e-244">在 PowerShell 中的編碼方式的其他資源</span><span class="sxs-lookup"><span data-stu-id="f796e-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="f796e-245">有幾個其他好用文章有關編碼方式和設定 PowerShell 中的編碼值得讀取：</span><span class="sxs-lookup"><span data-stu-id="f796e-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="f796e-246">[@mklement0][PowerShell 編碼 StackOverflow 上的摘要](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="f796e-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="f796e-247">在 vscode-PowerShell 編碼問題上，開啟上一個問題：</span><span class="sxs-lookup"><span data-stu-id="f796e-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="f796e-248">#1308</span><span class="sxs-lookup"><span data-stu-id="f796e-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="f796e-249">#1628</span><span class="sxs-lookup"><span data-stu-id="f796e-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="f796e-250">#1680</span><span class="sxs-lookup"><span data-stu-id="f796e-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="f796e-251">#1744</span><span class="sxs-lookup"><span data-stu-id="f796e-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="f796e-252">#1751</span><span class="sxs-lookup"><span data-stu-id="f796e-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="f796e-253">傳統*Joel on Software*寫 Unicode</span><span class="sxs-lookup"><span data-stu-id="f796e-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="f796e-254">.NET Standard 中的編碼</span><span class="sxs-lookup"><span data-stu-id="f796e-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[位元組順序標記]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[語言伺服器通訊協定]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode 的編碼方式]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
