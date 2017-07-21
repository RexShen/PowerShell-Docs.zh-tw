# <a name="style-guide-for-powershell-docs"></a><span data-ttu-id="6618e-101">PowerShell-Docs 的樣式指南</span><span class="sxs-lookup"><span data-stu-id="6618e-101">Style guide for PowerShell-Docs</span></span>


## <a name="titlesheadings"></a><span data-ttu-id="6618e-102">標題/標頭</span><span class="sxs-lookup"><span data-stu-id="6618e-102">Titles/Headings</span></span>

* <span data-ttu-id="6618e-103">標題/標頭 (任何在前方加上 \# 的項目) 後方應接著新行字元</span><span class="sxs-lookup"><span data-stu-id="6618e-103">Titles/headings (anything preprended by \#) should be followed with a newline</span></span>
* <span data-ttu-id="6618e-104">只有標題及該標題中所有專有名詞的第一個字母才應大寫</span><span class="sxs-lookup"><span data-stu-id="6618e-104">Only the first letter of a title and any proper nouns in that title should be capitalized</span></span>
* <span data-ttu-id="6618e-105">每個文件只能有一個 H1</span><span class="sxs-lookup"><span data-stu-id="6618e-105">Only 1 H1 per document</span></span>
* <span data-ttu-id="6618e-106">編輯參考內容時，H2 是由 platyPS 所指定，且不應新增或移除，因為那會導致建置中斷</span><span class="sxs-lookup"><span data-stu-id="6618e-106">When editing reference content, the H2s are prescribed by platyPS and should not be added or removed as it will cause a build break</span></span>
* <span data-ttu-id="6618e-107">僅使用 \# 樣式標頭 (而非 = 或 \- 樣式標頭)</span><span class="sxs-lookup"><span data-stu-id="6618e-107">Only use \# style headers (as opposed to = or \- style headers)</span></span>

### <a name="correct"></a><span data-ttu-id="6618e-108">正確</span><span class="sxs-lookup"><span data-stu-id="6618e-108">Correct</span></span>

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a><span data-ttu-id="6618e-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="6618e-109">Incorrect</span></span>

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a><span data-ttu-id="6618e-110">語法</span><span class="sxs-lookup"><span data-stu-id="6618e-110">Syntax</span></span>

* <span data-ttu-id="6618e-111">在段落中說明 Cmdlet 時，請使用 \\` 以將 Cmdlet 名稱醒目提示</span><span class="sxs-lookup"><span data-stu-id="6618e-111">When talking about a cmdlet in paragraph, use \\` to highlight cmdlet names</span></span>
  * <span data-ttu-id="6618e-112">正確的範例：這個 `Write-Host` Cmdlet 可以 ...</span><span class="sxs-lookup"><span data-stu-id="6618e-112">Correct Example: This `Write-Host` Cmdlet can ...</span></span>
  * <span data-ttu-id="6618e-113">不正確的範例：這個 **Write-Host** Cmdlet 可以 ... 並以管線方式處理至 out-file Cmdlet 以 ...</span><span class="sxs-lookup"><span data-stu-id="6618e-113">Incorrect Example: This **Write-Host** Cmdlet can ... and pipeline to out-file Cmdlet to ...</span></span>
* <span data-ttu-id="6618e-114">撰寫文章 (而非撰寫參考內容) 時，第一個 Cmdlet 名稱實例應該是該 Cmdlet 文件的連結</span><span class="sxs-lookup"><span data-stu-id="6618e-114">When writing an article (as opposed to reference content), the first instance of a cmdlet name should be a link to the cmdlet documentation</span></span>
* <span data-ttu-id="6618e-115">所有的 PowerShell 語法區塊都應該使用 &#96;&#96;&#96;powershell</span><span class="sxs-lookup"><span data-stu-id="6618e-115">All PowerShell syntax blocks should use &#96;&#96;&#96;powershell</span></span>
* <span data-ttu-id="6618e-116">PowerShell 命令的開頭請勿使用 "`PS C:\>`"</span><span class="sxs-lookup"><span data-stu-id="6618e-116">Do not start PowerShell commands with "`PS C:\>`"</span></span>
  * <span data-ttu-id="6618e-117">正確的範例：</span><span class="sxs-lookup"><span data-stu-id="6618e-117">Correct Example:</span></span>
  ```powershell
  Get-Process
  ```
  * <span data-ttu-id="6618e-118">不正確的範例：</span><span class="sxs-lookup"><span data-stu-id="6618e-118">Incorrect Example:</span></span>
  ```powershell
  PS C:\> Get-Process
  ```
* <span data-ttu-id="6618e-119">PowerShell 命令發出的輸出應該加上註解，以防止它接收語法醒目提示</span><span class="sxs-lookup"><span data-stu-id="6618e-119">Output emitted by PowerShell commands should be commented to prevent it from recieving syntax highlighting</span></span>
* <span data-ttu-id="6618e-120">屬性名稱和參數名稱應使用「粗體」</span><span class="sxs-lookup"><span data-stu-id="6618e-120">Property names and parameter names should be in **bold**</span></span>
* <span data-ttu-id="6618e-121">PowerShell Cmdlet 使用「[帕斯卡命名法 (英文)](https://en.wikipedia.org/wiki/PascalCase)」。</span><span class="sxs-lookup"><span data-stu-id="6618e-121">PowerShell cmdlets are "[Pascal Cased](https://en.wikipedia.org/wiki/PascalCase)".</span></span> <span data-ttu-id="6618e-122">使用連字號分隔動詞和名詞。</span><span class="sxs-lookup"><span data-stu-id="6618e-122">Verbs are seperated from nouns by a hyphen.</span></span>

## <a name="lists"></a><span data-ttu-id="6618e-123">清單</span><span class="sxs-lookup"><span data-stu-id="6618e-123">Lists</span></span>

* <span data-ttu-id="6618e-124">清單的結尾請勿使用句號 (除非它們包含多個句子)</span><span class="sxs-lookup"><span data-stu-id="6618e-124">Do not end list items with a period (unless they contain multiple sentences)</span></span>
* <span data-ttu-id="6618e-125">如果您的清單包含多個句子，請考慮在您的主要想法下使用標頭 3/4/5 (視情況而定)</span><span class="sxs-lookup"><span data-stu-id="6618e-125">If your list contains multiple sentences, consider using a header 3/4/5 (as applicable) underneath your primary idea</span></span>

## <a name="links"></a><span data-ttu-id="6618e-126">連結</span><span class="sxs-lookup"><span data-stu-id="6618e-126">Links</span></span>

* <span data-ttu-id="6618e-127">連結一律使用 MarkDown 語法 `[friendlyname](url)` 標記</span><span class="sxs-lookup"><span data-stu-id="6618e-127">Links are always marked up using MarkDown syntax `[friendlyname](url)`</span></span>
* <span data-ttu-id="6618e-128">連結應視情況提供易記名稱，通常是所連結之頁面的標題</span><span class="sxs-lookup"><span data-stu-id="6618e-128">Links should have a a friendly name when applicable, most likely the title of the linked page</span></span>
  * <span data-ttu-id="6618e-129">**例外狀況**：非 Microsoft 網站的連結應只使用 URL</span><span class="sxs-lookup"><span data-stu-id="6618e-129">**Exception**: Links going towards non-Microsoft sites should only have a URL</span></span>
* <span data-ttu-id="6618e-130">位於底部＜相關連結＞一節中的所有項目，都應該是超連結。</span><span class="sxs-lookup"><span data-stu-id="6618e-130">All items in the "related links" section at the bottom should be hyperlinked.</span></span> 

## <a name="line-breaks"></a><span data-ttu-id="6618e-131">分行符號</span><span class="sxs-lookup"><span data-stu-id="6618e-131">Line breaks</span></span>

* <span data-ttu-id="6618e-132">您必須包含語意分行符號</span><span class="sxs-lookup"><span data-stu-id="6618e-132">You must include semantic line breaks</span></span>
* <span data-ttu-id="6618e-133">您應該將行的長度限制為 100 個字元 (開放項目：協助我們驗證此項目的工具)</span><span class="sxs-lookup"><span data-stu-id="6618e-133">You should limit lines to 100char (Open item: tooling to help us validate this)</span></span>
* <span data-ttu-id="6618e-134">您「可以」移除 PS4 及更新版本的額外分行符號，但針對 ps3 則「不可以」(需要驗證)</span><span class="sxs-lookup"><span data-stu-id="6618e-134">You CAN remove additional line breaks for PS4+, NOT ps3 (needs validation)</span></span>
