# MBSubModuleBase

您可以从`MBSubModuleBase`类继承来处理模块的加载，它实质上是代码的入口点。有一些有用的可重写的方法，例如`OnSubModuleLoad()`和`OnApplicationTick()`您可以利用。

**重要的是要注意，您必须在模块的引用中引用类的完全限定名称，`SubModule.xml`才能使其正常工作。**

`SubModule.xml`中的`ExampleMod.MySubModule`就是一个继承MBSubModuleBase的全限定名。[SubModule.xml](../../_xmldocs/submodule.md)

## Overrides - 重写

这是一个可重写方法的完整列表，通常（按调用顺序）列出。这是一个粗略的指南，当您遇到执行顺序问题时，不能替代调试。

- `OnSubModuleLoad()` - 在游戏的第一个加载屏幕上调用，始终是第一个要调用的替代，这是您应进行大部分初始设置的地方。
- `OnApplicationTick(float)` - 每帧调用一次，应避免在此处直接调用昂贵的操作，而由于性能原因，应尽可能少地工作。
  - `float` - 帧完成所需的时间（以毫秒为单位）。
- `OnBeforeInitialModuleScreenSetAsRoot()` - 在主菜单首次出现之前调用，如果您的mod依赖于初始加载期间设置的其他内容，则很有用。
- `OnGameStart(Game, IGameStarter)` - 从主菜单中选择游戏模式（子模块）后，在加载后立即调用。
  - `Game` - [See: Game](../core/game.md)
  - `IGameStarter` - N/A
- `BeginGameStart(Game)` - 加载所选游戏模式（子模块）完成后立即调用。
  - `Game` - [See: Game](../core/game.md)
- `OnGameLoaded(Game, object)` - 仅在加载保存后调用。
  - `Game` - [See: Game](../core/game.md)
  - `object` - N/A
- `OnCampaignStart(Game, object)` - 在任何游戏模式启动后调用。
  - `Game` - [See: Game](../core/game.md)
  - `object` - N/A
- `OnGameInitializationFinished(Game)` - 游戏模式的初始化完成后调用。
  - `Game` - [See: Game](../core/game.md)
- `DoLoading(Game)` -  似乎是在加载即将结束时调用的，因此无法完全确定这一步。
  - `Game` - [See: Game](../core/game.md)
- `OnNewGameCreated(Game, object)` - 特别是在战役模式下开始新保存时调用。
  - `Game` - [See: Game](../core/game.md)
  - `object` - N/A
- `OnMissionBehaviourInitialize(Mission)` - 一旦任务开始并且要初始化行为，则调用该方法。
  - `Mission` - [See: Mission](mission.md)
- `OnGameEnd(Game)` - 要求退出任务/活动。
  - `Game` - [See: Game](../core/game.md)
- `OnSubModuleUnloaded()` - 完全退出Bannerlord时调用。



- `OnMultiplayerGameStart(Game, object)` - 与多人游戏相关，尚未测试。
  - `Game` - [See: Game](../core/game.md)
  - `object` - N/A