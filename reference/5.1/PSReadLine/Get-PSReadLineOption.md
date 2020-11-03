---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadline
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlineoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineOption
ms.openlocfilehash: 7f731014e5a240e0c756640144ff7cae5e48f051
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208652"
---
# <span data-ttu-id="048e5-103">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="048e5-103">Get-PSReadLineOption</span></span>

## <span data-ttu-id="048e5-104">概要</span><span class="sxs-lookup"><span data-stu-id="048e5-104">SYNOPSIS</span></span>
<span data-ttu-id="048e5-105">取得可設定之選項的值。</span><span class="sxs-lookup"><span data-stu-id="048e5-105">Gets values for the options that can be configured.</span></span>

## <span data-ttu-id="048e5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="048e5-106">SYNTAX</span></span>

```
Get-PSReadLineOption [<CommonParameters>]
```

## <span data-ttu-id="048e5-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="048e5-107">DESCRIPTION</span></span>

<span data-ttu-id="048e5-108">指令 `Get-PSReadLineOption` 程式會傳回可使用 Cmdlet 設定之設定的目前狀態 `Set-PSReadLineOption` 。</span><span class="sxs-lookup"><span data-stu-id="048e5-108">The `Get-PSReadLineOption` cmdlet returns the current state of the settings that can be configured by using the `Set-PSReadLineOption` cmdlet.</span></span> <span data-ttu-id="048e5-109">您可以使用傳回的物件來變更 **PSReadLine** 選項。</span><span class="sxs-lookup"><span data-stu-id="048e5-109">You can use the returned object to change **PSReadLine** options.</span></span> <span data-ttu-id="048e5-110">這提供了稍微簡單的方法來設定多種 token 的語法色彩選項。</span><span class="sxs-lookup"><span data-stu-id="048e5-110">This provides a slightly simpler way to set syntax coloring options for multiple kinds of tokens.</span></span>

## <span data-ttu-id="048e5-111">範例</span><span class="sxs-lookup"><span data-stu-id="048e5-111">EXAMPLES</span></span>

### <span data-ttu-id="048e5-112">範例1：取得選項及其值</span><span class="sxs-lookup"><span data-stu-id="048e5-112">Example 1: Get options and their values</span></span>

```powershell
Get-PSReadLineOption
```

```Output
EditMode                               : Windows
AddToHistoryHandler                    : System.Func`2[System.String,System.Object]
HistoryNoDuplicates                    : True
HistorySavePath                        : C:\Users\username\AppData\Roaming\Microsoft\Windows\
                                         PowerShell\PSReadLine\ConsoleHost_history.txt
HistorySaveStyle                       : SaveIncrementally
HistorySearchCaseSensitive             : False
HistorySearchCursorMovesToEnd          : False
MaximumHistoryCount                    : 4096
ContinuationPrompt                     : >>
ExtraPromptLineCount                   : 0
PromptText                             : {> }
BellStyle                              : Audible
DingDuration                           : 50
DingTone                               : 1221
CommandsToValidateScriptBlockArguments : {ForEach-Object, %, Invoke-Command, icm...}
CommandValidationHandler               :
CompletionQueryItems                   : 100
MaximumKillRingCount                   : 10
ShowToolTips                           : True
ViModeIndicator                        : None
WordDelimiters                         : ;:,.[]{}()/\|^&*-=+'"---
AnsiEscapeTimeout                      : 100
CommandColor                           : "$([char]0x1b)[93m"
CommentColor                           : "$([char]0x1b)[32m"
ContinuationPromptColor                : "$([char]0x1b)[37m"
DefaultTokenColor                      : "$([char]0x1b)[37m"
EmphasisColor                          : "$([char]0x1b)[96m"
ErrorColor                             : "$([char]0x1b)[91m"
KeywordColor                           : "$([char]0x1b)[92m"
MemberColor                            : "$([char]0x1b)[97m"
NumberColor                            : "$([char]0x1b)[97m"
OperatorColor                          : "$([char]0x1b)[90m"
ParameterColor                         : "$([char]0x1b)[90m"
SelectionColor                         : "$([char]0x1b)[30;47m"
StringColor                            : "$([char]0x1b)[36m"
TypeColor                              : "$([char]0x1b)[37m"
VariableColor                          : "$([char]0x1b)[92m"
```

<span data-ttu-id="048e5-113">此命令會傳回可用 PSReadLine 選項的清單及其目前的值。</span><span class="sxs-lookup"><span data-stu-id="048e5-113">This command returns the list of available PSReadLine options and their current values.</span></span>

## <span data-ttu-id="048e5-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="048e5-114">PARAMETERS</span></span>

### <span data-ttu-id="048e5-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="048e5-115">CommonParameters</span></span>

<span data-ttu-id="048e5-116">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="048e5-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="048e5-117">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="048e5-117">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="048e5-118">輸入</span><span class="sxs-lookup"><span data-stu-id="048e5-118">INPUTS</span></span>

### <span data-ttu-id="048e5-119">無</span><span class="sxs-lookup"><span data-stu-id="048e5-119">None</span></span>

<span data-ttu-id="048e5-120">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="048e5-120">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="048e5-121">輸出</span><span class="sxs-lookup"><span data-stu-id="048e5-121">OUTPUTS</span></span>

### <span data-ttu-id="048e5-122">PSConsoleReadLineOptions</span><span class="sxs-lookup"><span data-stu-id="048e5-122">Microsoft.PowerShell.PSConsoleReadLineOptions</span></span>

<span data-ttu-id="048e5-123">目前選項的實例。</span><span class="sxs-lookup"><span data-stu-id="048e5-123">An instance of the current options.</span></span> <span data-ttu-id="048e5-124">變更這個物件的屬性值會直接更新 PSReadLine 中的設定，而不會叫用 `Set-PSReadLineOption` 。</span><span class="sxs-lookup"><span data-stu-id="048e5-124">Changing the property values of this object updates the settings in PSReadLine directly without invoking `Set-PSReadLineOption`.</span></span>

## <span data-ttu-id="048e5-125">注意</span><span class="sxs-lookup"><span data-stu-id="048e5-125">NOTES</span></span>

## <span data-ttu-id="048e5-126">相關連結</span><span class="sxs-lookup"><span data-stu-id="048e5-126">RELATED LINKS</span></span>

[<span data-ttu-id="048e5-127">移除-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="048e5-127">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="048e5-128">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="048e5-128">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="048e5-129">設定-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="048e5-129">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="048e5-130">設定-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="048e5-130">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
