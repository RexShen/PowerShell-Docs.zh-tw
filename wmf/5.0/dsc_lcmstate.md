# <a name="detailed-information-about-lcm-state"></a>LCM 狀態的詳細資訊

我們在公開有關 LCM 狀態詳細資料的方面上進行了改善。 由 Get-DscLocalConfigurationManager 傳回的 LCMState 現在可包含下列值︰

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

我們也加入了 LCMStateDetail 屬性，其中包含狀態的詳細資訊。
