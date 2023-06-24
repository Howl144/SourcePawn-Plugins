# Description | 內容
L4D2 coop save weapon when map transition if more than 4 players

* Video | 影片展示
<br/>None

* Image | 圖示
<br/>None

* Apply to | 適用於
	```
	L4D2 Coop/Realism
	```

* <details><summary>Changelog | 版本日誌</summary>

	* v6.0 (2023-6-25)
        * Fixed melee disapear after map transition

	* v5.9 (2022-9-17)
        * [AlliedModder Post](https://forums.alliedmods.net/showpost.php?p=2757629&postcount=113)
        * Remake code
        * Add the last stand two melee
        * Add ConVar and generate cfg
        * Save health
        * Save Character Model
        * Support Bots
        * Support custom melee save
        * Doesn't save if change map in game (ex. vote change new campaign)
        * Compatible with the [[ANY] Cheats](https://forums.alliedmods.net/showthread.php?t=195037)

	* v4.1
        * [Original Post by maks](https://forums.alliedmods.net/showthread.php?t=263860)
</details>

* Require | 必要安裝
	1. [left4dhooks](https://forums.alliedmods.net/showthread.php?t=321696)

* Related Plugin | 相關插件
	1. [l4dmultislots](https://github.com/fbef0102/L4D1_2-Plugins/tree/master/l4dmultislots): Allows additional survivor players in server when 5+ player joins the server
	    > 創造5位以上倖存者遊玩伺服器

* <details><summary>ConVar | 指令</summary>

	* cfg\sourcemod\l4d2_ty_saveweapons.cfg
		```php
        // Do not restore weapons and health to a player after survivors have left start safe area for at least x seconds. (0=Always restore)
        l4d2_ty_saveweapons_game_seconds_block "60"

        // If 1, restore 100 full health when end of chapter.
        l4d2_ty_saveweapons_health "0"

        // If 1, save weapons and health for bots as well.
        l4d2_ty_saveweapons_save_bot "1"

        // If 1, save character model and restore.
        l4d2_ty_saveweapons_save_character "0"

        // If 1, save health and restore. (can save >100 hp)
        l4d2_ty_saveweapons_save_health "1"
		```
</details>

* <details><summary>Command | 命令</summary>

	None
</details>

* <details><summary>API | 串接</summary>

	```c++
    /**
    * @brief Called when restore and give weapons, health to a player
    *
    * @param client    the client who is given to.
    *
    * @noreturn
    */
    forward void L4D2_OnSaveWeaponHxGiveC(int client);
	```
</details>

* <details><summary>Related Official ConVar</summary>

	* Write down the follong cvars in cfg/server.cfg
		```php
		// If 1, survivor bots will be used as placeholders for survivors who are still changing levels
        // If 0, prevent bots from moving, changing weapons, using kits while human survivors are still changing levels
        // Default: 1
		sm_cvar sb_transition 0 
		```
</details>

- - - -
# 中文說明
當伺服器有5+以上玩家遊玩戰役、寫實時，保存他們過關時的血量以及攜帶的武器、物品

> __Note__ 只有當伺服器有5+以上玩家時才需要安裝此插件

* 原理
    * 抵達終點關下安全門時，插件會保存每一位玩家的資料
        * 武器、物品
        * 人物角色
        * 血量與黑白狀態
    * 當玩家載入到下一關之後，恢复所有資料

* 功能
    * 可設置過關時是否恢复滿血
    * 可設置是否保存血量與黑白狀態
    * 可設置是否保存人物角色
    * 可設置是否Bot也要保存並恢复
    * 可設置出安全室一段時間之後不能恢复 (避免有人載入關卡太慢)


* <details><summary>相關的官方指令中文介紹 (點我展開)</summary>

	* 以下指令寫入文件 cfg/server.cfg，可自行調整
		```php
		// 為1時, 過關後玩家的Bot會走動並更換身上的武器與物品
        // 為0時, 過關後玩家的Bot不會走動也不會更換身上的武器與物品 (推薦使用)
        // 預設值: 1
		sm_cvar sb_transition 0
		```
</details>