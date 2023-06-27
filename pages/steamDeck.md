- todo
	- [[硬件]]list
		- 加速器
		- sd卡
	- [[软件]]list
		- [折腾教程](https://bbs.a9vg.com/thread-8869286-1-1.html)
		- 下载镜像修改
		- 装window
		- 桌面汉化
		- 两个兼容[[软件]]
		-
-
- 各种折腾
	- [官方指南](https://partner.steamgames.com/doc/steamdeck)
		- proton他是允许window和linux运行的兼容层，通过使用修改的wine版本和高性能api实现的，只是说覆盖率很广
			- 如果测试[[游戏]]是否支持proton，可以在linux上装steam测试或者使用开发者套件
		- 可玩
			- ![Replaced by Image Uploader](https://s2.loli.net/2023/06/26/SOT8r3uUHAyt5FQ.png)
		-
	- [Steam-Deck-Guide](https://github.com/mikeroyal/Steam-Deck-Guide)三方steamdeck的指南包括插件，配件等等
	- [steamdeck-emulation](https://github.com/n1ckoates/steamdeck-emulation) 能够安装各大平台的模拟器
	- [decky-loader](https://github.com/SteamDeckHomebrew/decky-loader) 扩展插件，更改[[系统]]声音，调整饱和度等等
	- [steamtinkerlaunch](https://github.com/sonic2kk/steamtinkerlaunch)极致细化的自定义[[游戏]]配置，可以使用mode，切换修改各种设置
	- [ludusavi](https://github.com/mtkennerly/ludusavi) 支持window存档
	-
- 很多教程贴吧可能找不到，最好去酷安看看，[github](https://github.com/search?q=steamdeck&type=topics)
- ## 常用解答
	- [关于ssd和tf卡的速度对比](https://g.nga.cn/read.php?tid=35068555&rand=729)
		- 结果，差距几乎在2-s10s内左右
	- [Steam Deck完全没必要买贵的TF卡](https://tieba.baidu.com/p/8052545313)
		- 结果，a1红卡就够
	- [steam deck安装第三方游戏](https://bbs.a9vg.com/thread-8869286-1-1.html)
	- [如何装epic](https://www.coolapk.com/feed/42469989?shareKey=MzA4OTQ3ODdhZDExNjQ3NTU3MDc~&shareUid=25102075&shareFrom=com.coolapk.market_13.1.3)
	-
-
- ### 小技巧
	- 如果使用unity或虚幻引擎，使用Vulkan图形api可以获得最佳性能和续航（注意：Proton 包括一个 DirectX 至 Vulkan 转译层。 如果您的[[游戏]]或引擎具有高质量的 DirectX 支持却没有 Vulkan 支持，那么使用此自动转译层很可能会比使用自定义 Vulkan 实现获得更好的性能。）
	- 建议使用独立解码器vP9，而不是wmf
	- Steam Deck 会因使用外接电源或电池而有任何性能差异吗？我们将精力放在为您提供 APU 的完整可用性能，无论是使用电池还是接入电源。 我们期望在两种配置下，性能表现全都相同。
	-
- ## [[steamDeck]] 介绍
	- ### 缺点
	  collapsed:: true
		- 体积
			- 重，600g
			- 大
			- 可视屏幕小
		- 续航
			- 不行 2-3小时大作，须带充电宝
			- 充电慢
		- 屏幕
			- 分辨率只能800但比switch强
		- 网络
			- 需要加速器
		- 底层是linux，window须加兼容层
		- 只能玩steam上[[购买]]的[[游戏]]，想要白嫖[[游戏]]还是比较麻烦
	- ### 优点
	  collapsed:: true
		- 可以玩pc上[[游戏]]，替代需要背[[电脑]]的短板
		- 可以装win[[系统]]
		- 一些老大作可以开60帧
		- 声音比较小
- ## [[购买]]
	- 主机 3100
	- 1t ssd+双[[系统]]盘 350
	- 扩展坞 100
	- 贴膜
	- ###  [[硬件]]
	  collapsed:: true
		- ### 固态
			- ## 介绍
			  collapsed:: true
				- 原装的是pcle2*1
				- steamdeck并不需要高性能的ssd，一般来说pcle3*2就行
				- 推荐低功耗
				- 支持固态的型号2230
			- 品牌
				- 镁光2400
				- 西数 sn740 2t 推荐1400入手
				- SN530 推荐450入手
				- 东芝铠侠bg4 512g 不如740功耗高，比530快，但买1t就不值了
				- 收藏的那个伊芯可能是矿
				- SN520功耗2.6W（512G），SN530功耗3.4W(1T），SN740功耗4.3W（1T）
				-
- ## 必备[[软件]]
	- uu加速器
	- ### 折腾思路1
		- 折腾了一天，终于搞到能玩的程度了[受虐滑稽]这是这几天折腾sd的思路，刚入手的玩家可以参考下。
		  1.换1T固态，制作[[系统]]盘
		  2.硬盘分区，制作Windows双[[系统]]
		  2.UU加速第一次[[系统]]安装
		  3.把所有兼容层都更新一遍
		  4.配置archLinux的用户密码和[[软件]]源
		  5.配置双[[系统]]开机引导
		  6.安装to moon
		  7.通过discovery商店安装第三方epicgames商店
		  8.下载emudeck，安装各种模拟器
-
-