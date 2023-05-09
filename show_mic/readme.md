
# Description | 內容
Voice Announce in centr text + create hat to Show Who is speaking.
(```sv_alltalk 1``` support)

* Video | 影片展示
<br/>None

* Image | 圖示
	* hat + text
        > MIC說話的玩家頭上會有對話框
        <br/>![show_mic_1](image/show_mic_1.jpg)

* Apply to | 適用於
    ```
    L4D2
    ```

* <details><summary>Changelog | 版本日誌</summary>

	* v1.9 (2023-1-11)
        * Fixed center text disappear when show_mic_center_hat_enable is 0

	* v1.8 (2022-12-1)
        * Remove voicehook (voicehook is now included with SourceMod 1.11)

	* v1.7
        * Remake Code

	* v1.8
        * [foxhound27's fork](https://forums.alliedmods.net/showpost.php?p=2671963&postcount=7)
</details>

* Require | 必要安裝
	1. [left4dhooks](https://forums.alliedmods.net/showthread.php?t=321696)
	2. [[INC] Multi Colors](https://github.com/fbef0102/L4D1_2-Plugins/releases/tag/Multi-Colors)
	3. [ThirdPersonShoulder_Detect](https://forums.alliedmods.net/showthread.php?p=2529779)

* Related Plugin | 相關插件
    1. [l4d_versus_specListener](https://github.com/fbef0102/Game-Private_Plugin/tree/main/Plugin_%E6%8F%92%E4%BB%B6/Spectator_%E6%97%81%E8%A7%80%E8%80%85/l4d_versus_specListener): Allows spectator listen others team voice and see others team chat for l4d
	    > 旁觀者可以透過聊天視窗看到倖存者和特感的隊伍對話，亦可透過音頻聽到隊伍談話

* <details><summary>ConVar | 指令</summary>

	* cfg\sourcemod\show_mic.cfg
        ```php
        // If 1, display hat on player's head if player is speaking
        show_mic_center_hat_enable "1"

        // If 1, display player speaking message in center text
        show_mic_center_text_enable "1"
        ```
</details>

* <details><summary>Command | 命令</summary>

	None
</details>

- - - -
# 中文說明
顯示誰在語音並且在說話的玩家頭上帶帽子

* 原理
    * 當玩家在遊戲中使用麥克風說話時，顯示提示在螢幕中心
        * 只有相同的隊伍才能知道誰使用麥克風說話
        * 如果伺服器開啟```sv_alltalk 1```，則所有人都能知道誰使用麥克風說話
    * 當倖存者在遊戲中使用麥克風說話時，頭上產生對話框的模組   
        * 只有相同的倖存者隊伍才看得到頭上對話框的模組
        * 如果伺服器開啟```sv_alltalk 1```，則所有人都能看到倖存者頭上對話框的模組
    * 可以搭配[l4d_versus_specListener插件](https://github.com/fbef0102/Game-Private_Plugin/tree/main/Plugin_%E6%8F%92%E4%BB%B6/Spectator_%E6%97%81%E8%A7%80%E8%80%85/l4d_versus_specListener)，旁觀者可以透過聊天視窗看到倖存者和特感的隊伍對話，亦可透過音頻聽到隊伍談話
    * 戰役模式也適用

* 功能
    * 可開啟或關閉帽子模組
    * 可開啟或關閉語音提示