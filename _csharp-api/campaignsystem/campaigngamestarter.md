# CampaignGameStarter
This class can be used to introduce behaviours, dialog, menus and models for campaigns, and implements the IGameStarter interface. This is useful in the `OnGameStart` method in [MBSubModuleBase](mbsubmodulebase.md), which is shown in the example.

这个类可以被用来为战役提供自定义的弹框，对话框，菜单和模型，并且可以实现`IGameStarter`接口。可以在[MBSubModuleBase](mbsubmodulebase.md)的`OnGameStart`方法中使用。

## Accessible Methods:
#### `public void ClearEmptyObjects()`
(Work in progress)
#### `public void AddBehavior(CampaignBehaviorBase campaignBehavior)`
把 [Campaign Behavior](campaignbehaviorbase.md) 添加到当前战役
#### `public void AddModel(GameModel model)`
把 [Game Model](../core/gamemodel.md) 添加到当前战役
#### `public void LoadGameTexts(string xmlPath)`
(Work in progress) 在输入的路径中加载XML文件，从而向游戏中引入更多文本。这些文本的格式与*comment_strings.xml*文件的格式相同，其用途目前尚未确定。
#### `public void LoadGameMenus(Type typeOfGameMenusCallbacks, string xmlPath)`
(Work in progress) 在输入的路径中加载XML文件，从而为游戏引入更多菜单。
#### `public void AddGameMenu(string menuId, string menuText, OnInitDelegate initDelegate, GameOverlays.MenuOverlayType overlay = GameOverlays.MenuOverlayType.None, GameMenu.MenuFlags menuFlags = GameMenu.MenuFlags.none, object relatedObject = null)`
See [GameMenu](gamemenu.md) for use.
#### `public void AddWaitGameMenu(string idString, string text, OnInitDelegate initDelegate, OnConditionDelegate condition, OnConsequenceDelegate consequence, OnTickDelegate tick, GameMenu.MenuAndOptionType type, GameOverlays.MenuOverlayType overlay = GameOverlays.MenuOverlayType.None, float targetWaitHours = 0f, GameMenu.MenuFlags flags = GameMenu.MenuFlags.none, object relatedObject = null)`
(Work in progress)
#### `public void AddGameMenuOption(string menuId, string optionId, string optionText, GameMenuOption.OnConditionDelegate condition, GameMenuOption.OnConsequenceDelegate consequence, bool isLeave = false, int index = -1, bool isRepeatable = false)`
See [GameMenu](gamemenu.md) for use.
## Accessible Attributes:
**NOTE**: *所有的都是只读的，不可修改*

#### `public readonly bool IsTutorial`
是否以教程开始。
#### `public ICollection<CampaignBehaviourBase> CampaignBehaviors`
当前战役注册的 [Campaign Behaviours](campaignbehaviorbase.md).
#### `public IEnumerable<GameModel> Models`
当前已注册的 [Game Models](../core/gamemodel.md)

## 举例:
```csharp
protected override void OnGameStart(Game game, IGameStarter gameStarter) 
{
    if(game.GameType is Campaign) 
    {
        //Current game is a campaign, so IGameStarter object must be CampaignGameStarter
        CampaignGameStarter campaignStarter = (CampaignGameStarter) gameStarter;
        //Can now use CampaignGameStarter
    }
}
```