---
標題︰Pester 更新至 3.4.0 版作者︰jaimeo 參與者︰jkeithb 參與者︰Keith Bankston (專家是 Jim Truher)
---

在 5.1 版中，PowerShell 隨附的 Pester 版本已從 3.3.5 更新至 3.4.0，加上認可 https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e，讓 Pester 在 Nano 上有更好的表現。 


您可以檢查 https://github.com/pester/Pester/blob/master/CHANGELOG.md 的 ChangeLog.md 檔案，檢閱 3.3.5 版至 3.4.0 版的變更。

Pester 在 Nano 上的**已知問題** 
* 因為完整 CLR 和核心 CLR 之間的差異，針對 Pester 本身執行測試仍會產生某些失敗，特別是 XmlDocument 類型不提供驗證方法時。 嘗試驗證 NUnit 輸出記錄檔結構描述的 6 項測試已失敗。 
* 目前一項程式碼涵蓋範圍測試失敗，因為 Nano 上沒有 *WindowsFeature* DSC 資源。 這些失敗是通常是無害的。


<!--HONumber=Jul16_HO3-->


