# GameMenu - 游戏菜单

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

可以通过将其设置`optionLeaveType`为适当的值来更改图标。使用的图像位于下，`Mount & Blade II Bannerlord\GUI\GauntletUI\SpriteParts\ui_group1\GameMenu`并且可以在中查看对应关系`Mount & Blade II Bannerlord\Modules\Native\GUI\Brushes\GameMenu.xml`。当然，可以在您自己的模块中覆盖它，但`LeaveTypes`不能进行其他操作。

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