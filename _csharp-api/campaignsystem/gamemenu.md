# GameMenu - 游戏菜单

All the menus in the campaign are handled by the `GameMenuManager`. To add new menus however you must use the provided methods by the `Campaign` class.

战役中所有的`menus`都被`GameMenuManager`管理着。但是如果要添加新菜单，必须使用`Campaign`该类提供的方法。

添加一个新的`menu`:
```csharp
CampaignGameStarter.AddGameMenu(string menuId, string menuText, OnInitDelegate initDelegate, MenuOverlayType overlay = MenuOverlayType.None, MenuFlags menuFlags = GameMenu.MenuFlags.none, object relatedObject = null)

// `menu`初始化之后会调用这个方法
delegate void OnInitDelegate(MenuCallbackArgs args);
```

// The overlay defines if for example the upper right characters list is visible or not. （// TODO 这里需要再琢磨一下）

`menu`中新增一个选项：

```csharp
CampaignGameStarter.AddGameMenuOption(string menuId, string optionId, string optionText, OnConditionDelegate condition, OnConsequenceDelegate consequence, bool isLeave = false, int index = -1)

bool OnConditionDelegate(MenuCallbackArgs args);
void OnConsequenceDelegate(MenuCallbackArgs args);
```

你可以往已经存在的`menu`中新增`options`，并且也可以根据索引很方便的调整`option`的顺序。（默认会在最后`menu`添加）

* 提供的条件方法具有双重职责：
  - 启用/禁用选项（通过其返回值）
  - 设置图标（通过提供的参数）

The icon can be changed by setting `optionLeaveType` to something appropriate. The used images are found under `Mount & Blade II Bannerlord\GUI\GauntletUI\SpriteParts\ui_group1\GameMenu` and the correspondence can be viewed in `Mount & Blade II Bannerlord\Modules\Native\GUI\Brushes\GameMenu.xml`. This can of course be overrides in your own module, but additional `LeaveTypes` are not possible.

| Type                | Image |
| ------------------- | ----- |
| Default             |       |
| Mission             |       |
| Submenu             |       |
| BribeAndEscape      |       |
| Escape              |       |
| Craft               |       |
| ForceToGiveGoods    |       |
| ForceToGiveTroops   |       |
| RansomAndBribe      |       |
| LeaveTroopsAndFlee  |       |
| OrderTroopsToAttack |       |
| Raid                |       |
| HostileAction       |       |
| Recruit             |       |
| Trade               |       |
| Wait                |       |
| Leave               |       |
| Continue            |       |
| Manage              |       |
| WaitQuest           |       |
| Surrender           |       |
| Conversation        |       |
| DefendAction        |       |