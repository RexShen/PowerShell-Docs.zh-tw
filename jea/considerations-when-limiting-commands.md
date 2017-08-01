---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "限制命令時的考量"
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-TW
---
### <a name="considerations-when-limiting-commands"></a><span data-ttu-id="c14ed-103">限制命令時的考量</span><span class="sxs-lookup"><span data-stu-id="c14ed-103">Considerations When Limiting Commands</span></span>
<span data-ttu-id="c14ed-104">此步驟還有一個值得提出的重點。</span><span class="sxs-lookup"><span data-stu-id="c14ed-104">There is one important point to make about this step.</span></span>
<span data-ttu-id="c14ed-105">所有透過 JEA 公開的功能都必須位於系統管理員限制的區域中。</span><span class="sxs-lookup"><span data-stu-id="c14ed-105">It is critical that all capabilities exposed through JEA are located in administrator-restricted areas.</span></span>
<span data-ttu-id="c14ed-106">非系統管理員使用者不應該具有修改透過 JEA 端點使用之指令碼的能力。</span><span class="sxs-lookup"><span data-stu-id="c14ed-106">Non-administrator users should not have the capability to modify the scripts used through JEA endpoints.</span></span>

<span data-ttu-id="c14ed-107">另一個相關注意事項是，請務必不要讓 JEA 使用者可以覆寫 JEA 設定，以及將其 JEA 工作階段中的指令碼列入允許清單。</span><span class="sxs-lookup"><span data-stu-id="c14ed-107">On a related note, it is critical that you do not give JEA users the ability to overwrite JEA configurations and whitelisted scripts within their JEA sessions.</span></span>
<span data-ttu-id="c14ed-108">公開 `Copy-Item` 等命令時請格外小心！</span><span class="sxs-lookup"><span data-stu-id="c14ed-108">Be extremely careful when exposing commands like `Copy-Item`!</span></span>

