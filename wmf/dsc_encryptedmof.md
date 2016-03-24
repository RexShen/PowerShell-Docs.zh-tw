# MOF 文件預設為加密

設定文件包含機密資訊。 在舊版的 DSC 中，您必須先發佈和管理憑證，才能保護設定中的認證。 對許多人來說，即進行了所有所需的工作，這依然是重大的管理負擔，而且您還必須面對一些既沒有被保護，也無法被保護的設定資訊。 

這種情況將不再發生，因為**預設上所有設定 MOF 都受到保護**。 沒有憑證或需要設定中繼設定。 每當在目標節點上本機設定管理員 (LCM) 將設定 MOF 儲存到磁碟時，它會進行加密。 MOF 使用了 [DPAPI](https://msdn.microsoft.com/en-us/library/ms995355.aspx) 進行加密。 **注意︰** 設定指令碼產生的 MOF 並未加密。

**範例︰**Push 模式中的加密
![MOF 加密](images/MOF_Encryption.jpg)

如果您已經使用憑證方法來加密密碼，或您的密碼需要額外的保護，[現有以憑證為基礎的加密方法](https://msdn.microsoft.com/en-us/powershell/dsc/securemof)將繼續運作。 結果就是使用 DPAPIs 完全加密的 MOF 文件，此文件還有使用額外的密碼進行加密。

此加密僅適用於設定 MOF 文件 (pending.MOF、current.MOF、previous.MOF 和部分 MOF)。 因為它們比較不可能包含密碼，所以中繼設定 MOF 仍然以純文字的格式儲存。
<!--HONumber=Mar16_HO2-->
