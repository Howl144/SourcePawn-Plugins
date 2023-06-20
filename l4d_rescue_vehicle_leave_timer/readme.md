# Description | 內容
When rescue vehicle arrived and a timer will display how many time left for vehicle leaving. If a player is not on rescue vehicle or zone, slay him.

* [Video | 影片展示](https://youtu.be/zC4kZcG8wOA)

* Image | 圖示
	* Nuke explosion
		> 核彈爆炸
		<br/>![l4d_rescue_vehicle_leave_timer_1](image/l4d_rescue_vehicle_leave_timer_1.gif)

* Apply to | 適用於
	```
	L4D2
	```

* <details><summary>Changelog | 版本日誌</summary>

    * v1.7 (2023-6-20)
        * Require lef4dhooks v1.33 or above

	* v1.6 (2023-4-4)
        * Add a cvar to enable or disable AirStrike (explosion, missile, jets, fire)

	* v1.5 (2023-3-21)
        * Support Gamedata, from [End Safearea Teleport by sorallll](https://forums.alliedmods.net/showthread.php?p=2766575)
        * Support All custom map
        * delete data file

	* v1.4
        * [AlliedModder Post](https://forums.alliedmods.net/showpost.php?p=2725525&postcount=7)
	    * Original Request by darkbret.
	    * Thanks to Marttt and Crasher_3637.
	    * Works on l4d1/2 all value maps.
	    * Custom timer for each final map (edit data).
	    * Translation support
	    * The City Will Get Nuked After Countdown Time Passes, Idea from [Nuke | The City Will Get Nuked After Countdown Time Passes by alasfourom](https://forums.alliedmods.net/showthread.php?p=2784677)
	    * Silvers F18 Airstrike
</details>

* Require | 必要安裝
	1. [left4dhooks](https://forums.alliedmods.net/showthread.php?t=321696)
	2. [[INC] Multi Colors](https://github.com/fbef0102/L4D1_2-Plugins/releases/tag/Multi-Colors)

* Similar Plugin | 相似插件
	1. [l4d_elevator_getin_timer](https://github.com/fbef0102/Game-Private_Plugin/blob/main/Plugin_%E6%8F%92%E4%BB%B6/Anti_Griefer_%E9%98%B2%E6%83%A1%E6%84%8F%E8%B7%AF%E4%BA%BA/l4d_elevator_getin_timer): When someone presses the elevator button or enters the CEDA Trailer, a timer will display how many time left. If a player is not inside the evelator/CEDA Trailer, slay him
		> 當有人按下電梯按鈕或是進入CEDA大拖車時，開始倒數計時，未在時間內進入電梯或CEDA大拖車的玩家將處死

* Related | 相關插件
	1. [lockdown_system-l4d2](https://github.com/fbef0102/L4D1_2-Plugins/tree/master/lockdown_system-l4d2): Locks Saferoom Door Until Someone Opens It.
		> 倖存者必須等待時間到並合力對抗屍潮與Tank才能打開終點安全門

* <details><summary>ConVar | 指令</summary>

	* cfg/sourcemod/l4d_rescue_vehicle_leave_timer.cfg
		```php
        // If 1, Enable AirStrike (explosion, missile, jets, fire)
        l4d_rescue_vehicle_leave_timer_airstrike_enable "1"

        // 0=Plugin off, 1=Plugin on.
        l4d_rescue_vehicle_leave_timer_allow "1"

        // Changes how count down tumer hint displays. (0: Disable, 1:In chat, 2: In Hint Box, 3: In center text)
        l4d_rescue_vehicle_leave_timer_announce_type "2"

        // Default time to escape.
        l4d_rescue_vehicle_leave_timer_escape_time_default "60"

        // Turn on the plugin in these game modes, separate by commas (no spaces). (Empty = all).
        l4d_rescue_vehicle_leave_timer_modes ""

        // Turn off the plugin in these game modes, separate by commas (no spaces). (Empty = none).
        l4d_rescue_vehicle_leave_timer_modes_off ""

        // Turn on the plugin in these game modes. 0=All, 1=Coop, 2=Survival, 4=Versus, 8=Scavenge. Add numbers together.
        l4d_rescue_vehicle_leave_timer_modes_tog "0"
		```
</details>

* <details><summary>Command | 命令</summary>

	None
</details>

* <details><summary>Data Example</summary>

    * data/l4d_rescue_vehicle.cfg
        ```php
        "rescue_vehicle"
        {
            "c2m5_concert" // Map name
            {
                "time"       "60" // Set timer to escape (seconds), use l4d_rescue_vehicle_leave_timer_escape_time_default cvar value if does not set this keyvalue
            }
            
            "c7m3_port"
            {
                "num"		"0" // 0=Turn off the plugin in this map
            } 
        }
        ```
</details>

* Notice
    * The plugin supports all valve maps and all custom maps.
    * If the map finale is sacrifice, disable this plugin.

- - - -
# 中文說明
救援來臨之後，未在時間內上救援載具逃亡的玩家將處死

* 原理
	* 當最後一關救援飛機來臨時，顯示逃亡倒數剩餘時間
    * 這段期間會有空軍飛過轟炸地面
    * 逃亡時間到之後，軍方開始投下核彈消滅城市，沒有上飛機的玩家將會被核彈炸死

* 功能
	* 可自行調整關卡，設置每個章節逃亡倒數時間
    * 可以關閉空軍轟炸，避免太lag

* <details><summary>Data設定範例</summary>

    * data/l4d_rescue_vehicle.cfg
        ```php
        "rescue_vehicle"
        {
            "c2m5_concert" //地圖名
            {
                "time"       "60" // 設置逃亡時間，如果未填寫地圖名或者逃亡時間，會使用l4d_rescue_vehicle_leave_timer_escape_time_default的指令值
            }
            
            "c7m3_port" //地圖名
            {
                "num"		"0" // 0=在這張地圖上關閉插件
            } 
        }
        ```
</details>

* 注意事項
    * 此插件適用二代所有官方地圖與三方圖
    * 不適用有犧牲結局的救援地圖
