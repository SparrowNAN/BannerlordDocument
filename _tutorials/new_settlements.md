## 创建新的定居点

> 游戏添加定居点的方式是通过结合两个基于XML的文件：一个定义定居点的类型（藏身处，村庄，城镇，城堡等），定居点的`所有者`以及其他`相关参数`，例如繁荣，特产，村庄属于哪个城镇等等。这些数据维护在游戏中的`Modules / SandBox / ModuleData / settlements.xml`文件中。在此文件旁边是一个距离缓存文件`Modules / SandBox / ModuleSata / Settlements_distance_cache.bin`，可以用代码生成。

> 定居点的`视觉效果`的描述维护在在`Modules / SandBox / SceneObj / Main_map / scene.xscene`文件中。

## 有关将来的SDK支持的说明

从目前可用的DLL中的代码中可以明显看出，应该使用编辑器来进行修改定居点。该编辑器可帮助放置定居点，定义其视觉效果并生成上述距离缓存。到目前为止，这还不存在，因此必须诉使用修改XML文件的方式修改定居点。

## 有关距离缓存的说明

目前尚不清楚距离缓存的实际作用。如果不进行更新，AI似乎可以访问更多的定居点，在那里征募部队， 关押囚犯并购买物品。玩家也可以输入新的定居点。距离缓存可能与某些AI决策有关，但尚不清楚。距离缓存是由`SettlementPositionScript`中的`SaveSettlementDistanceCache()`方法创建的，该方法是当前未在游戏中使用的类，该类可能源自上述地图编辑器。可以在`SandBox.View.dll`中找到该类。

## 如何覆盖游戏中默认的定居点

> 创建MOD的时候，可以覆盖`SandBox`模块中的定居点的数据，但是不能进行增量的修改，只能进行全部的覆盖。

1. 首先将 ```Modules / SandBox / ModuleData / settlements.xml``` 复制到 `Modules / 你的MOD目录 / ModuleData / settlements.xml` 以及复制 `Modules / SandBox / SceneObj / Main_map（一个文件夹）` 到 `Modules / 你的MOD目录 / SceneObj / Main_map`。

Tips: 请不要使用常规的记事本进行XML编辑（对的，说的就是windows的记事本），而是使用适当的XML编辑工具或功能更强大的文本编辑器(如[`Notepad++`](https://notepad-plus.en.softonic.com/))

2. 修改MOD的`submodule.xml`
```xml
    -- 直接添加，不需要修改任何内容（除了这句注释）
	<XmlNode>
			<XmlName id="Settlements" path="settlements"/>
			<IncludeGameTypes>
				<GameType value = "Campaign"/>
				<GameType value = "CampaignStoryMode"/>
			</IncludeGameTypes>
	</XmlNode> 	
```
现在你可以根据自己的想法在复制出来的`settlements.xml`文件中添加/修改定居点的相关配置了，**但是要保证文件中每个条目都要有一个独一无二的ID**。

在您的mods`Main_map / scene.xscene`文件中，对`settlements.xml`文件中的每个条目都需要一个`game_entity`，仍然要确保没有重复的ID。

>举个🌰 -- [添加一个城镇和两个村庄](https://pastebin.com/BuSbQ6x2) 以及[scene.xscene中添加game_entity](https://pastebin.com/dXcKT7wf)

3. 其它说明

```shell
# 村庄被绑定到一个城镇
trade_bound="Settlement.town_M1" bound="Settlement.town_M1"
# 现在还不清楚`trade_bound`和`bound`有什么区别，安全起见，请设置成相同的一个

# 指定村庄的特产
# 村庄类型在`Modules / SandBox / ModuleData / spprojects.xml`中定义
village_type="VillageType.fisherman"
```
