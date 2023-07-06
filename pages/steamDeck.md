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
	- [官方讨论区](https://steamcommunity.com/groups/steamuniverse/discussions/1/)
	- [官方github问题追踪](https://github.com/ValveSoftware/SteamOS/issues)
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
	- [atelier-sync-fix](https://github.com/doitsujin/atelier-sync-fix) 提高帧率
		- 补丁原网址https://github.com/doitsujin/atelier-sync-fix
		  补丁网盘链接：https://pan.baidu.com/s/1Bc02jE_JAX1-YvvSoPN2Tg 
		  提取码：8888 
		  补丁指令：WINEDLLOVERRIDES="d3d11=n,b" %command%
- [大佬的综合教学帖](https://www.zhihu.com/column/c_1597940398197800960)
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
	- [[steamDeck]] 如果需要一个稳定的帧，可以使用40fps，对于性能和电量来说性价比最高就是40fps
	- steamOS有两个存储库，`brewmaster`正式版和`brewmaster_beta`测试版，测试版每周一更新，正式版每月第一个周三更新
		- 如果想进入测试版，可以尝试`sudo apt-get install steamos-beta-repo`
		  不过警告你，只能恢复[[系统]]分区，或者等brewmaster赶上你这个beta版本，不过第二个应该是不可能
		-
	- steamos root访问权限密码是passwd
	- 续航
		- 如果要高续航，最好是锁3-7w 并且30帧打小[[游戏]]
		- sd 9w 1100，锁45帧玩怪猎世界，可以玩3小时
		-
	- 快捷键
		- ```
		  steam+B 长按=强制游戏关闭
		  steam+X 释放按压=显示键盘
		  steam+L1=切换放大器
		  steam+R1=截图
		  steam+L2=鼠标右键点击
		  steam+R2=鼠标左键点击
		  steam+R2=鼠标左键点击
		  steam+右摇杆 R3=摇杆鼠标
		  steam+右触摸板Trackpad 移动=作鼠标用
		  steam+右触摸板Trackpad 按压=鼠标左键点击
		  steam+左摇杆L3 ↑↓=调高屏幕亮度和降低屏幕亮度
		  steam+十字键 D-pad 右=回车键
		  steam+十字键 D-pad 下=Tab键
		  steam+十字键 D-pad 左=Esc键
		  ```
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
- 不得不说，steam的维护做的很好，听张宁说无人深空一开始口碑很烂，但是后期无偿维护起死回生，我看到steamdeck中一句话很触动，别人问他什么时候考虑发布steamdeck2，我还以为他会说steamdeck2将会很厉害的处理器，很厉害配置等等，谁知他说，暂不考虑，目前只会考虑如何将本世代维护好，这种脚踏实地的责任精神，令我肃然起敬，或许能够延伸到我自己的身上，如何脚踏实地。