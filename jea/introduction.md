---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "簡介"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6b5107b7222708dcceff14bc26f0e12ef98d728
ms.openlocfilehash: 00d568234b1453b9161b60d20117374ee4111ab3

---

# 簡介

##  **動機**  
當您將系統的特殊權限存取授與某人時，就是將您的信任界限延伸到該人員。
這會帶來風險，因為系統管理員是受攻擊面。
內部攻擊和認證遭竊是常見的真實情況。

##  **不是新問題**  
您可能很熟悉最低權限原則，並可能透過應用程式使用其提供的某種角色型存取控制 (RBAC)。
不過，這些解決方案的效率和管理能力通常因其廣泛的範圍和不精確而受到限制。
此外，RBAC 涵蓋範圍也有間隙。
例如，在 Windows 中，特殊權限存取主要是二元切換參數，迫使您在將使用者加入 Administrators 群組時，授與不必要的權限。

##  **Just Enough Administration (JEA)** 
透過 PowerShell 遠端提供角色型存取控制 (RBAC) 平台。
*它可讓特定使用者在伺服器上執行特定管理工作，而不需要授與系統管理員權限。*
這可讓您填滿現有 RBAC 解決方案的間隙，並簡化這些設定的管理工作。




<!--HONumber=Jul16_HO1-->


