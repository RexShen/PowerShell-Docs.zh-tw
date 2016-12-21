---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "物件管線"
ms.technology: powershell
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 531c3c00ddcc0cc8299875392832fb1dad9f49d8
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="object-pipeline"></a>物件管線
管線就像是一系列連接的管道區段。 沿著管線移動的項目會通過每個區段。 若要在 Windows PowerShell 中建立管線，您可以將命令與管道運算子 "|" 連接在一起。 每個命令的輸出可作為下一個命令的輸入。

管線可說是用於命令列介面中最重要的概念。 管線若使用得宜，不僅可以減輕輸入複雜命令所涉及的工作，也可以讓您更輕鬆地查看命令中的工作流程。 管線的相關實用特性在於，由於它們會在每個項目上分開運作，因此您不需要根據管線中將有零個、一個或多個項目對其進行修改。 此外，管線中的每個命令 (稱為管線項目) 通常會將其輸出逐項目傳遞至管線中的下一個命令。 這通常會減少複雜命令的資源需求，讓您立即開始取得輸出。

在本章中，我們將說明 Windows PowerShell 管線與最熱門殼層管線的不同之處，接著示範您可以用來協助控制管線輸出及查看管線運作方式的一些基本工具。

