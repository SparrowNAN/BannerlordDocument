# Campaign Behavior Base
这是 [TaleWorlds.CampaignSystem](./README.md)中的一个抽象类,  可以继承该代码来编写游戏战役中的独特行为。 

## Abstract Methods:
#### ```public abstract void RegisterEvents()```
当定义了此方法,可以通过调用`CampaignEvents.On...` 方法，给某些事件添加影响效果。 

简单的例子:

```csharp
public override void RegisterEvents()
{   
    // 在一个家族被消灭之后，展示一条消息
    CampaignEvents.OnClanDestroyedEvent.AddNonSerializedListener(this, new Action<Clan>(
    clan => {
        String clanName = clan.Name.ToString();
        InformationManager.DisplayMessage(new InformationMessage("The " + clanName + " was destroyed!"));
    }));
}
```
 上面的示例注册了一个事件，以便在家族灭亡时，会向聊天室广播一条消息。在`AddNonSerializedListener`方法中需要的第二个参数是一个动作，具体描述[在这里](https://docs.microsoft.com/en-us/dotnet/api/system.action-1?view=netframework-4.8) 。

#### ```public abstract void SyncData(IDataStore dataStore)```

在这里，您可以操作行为需要保存的数据。但是，大多数`Behavior`都不需要它，您可以根据需要将其留空。
 
```csharp
// inside your class
private int _numVillagesRaided;

public override void SyncData(IDataStore dataStore)
{
    dataStore.SyncData("_numVillagesRaided", ref _numVillagesRaided);
}

// 我们可以监听游戏退出事件，如果将需要保存的数据写入`_numVillagesRaided`,下次启动有相关存档的游戏之后，这个`_numVillagesRaided`就能读取到上次游戏退出保存的值。读取值的操作一般可以通过监听游戏启动事件。
```
语法非常简单，第一个参数是要存储的字符串标识符。这可能只需要在给定的`Behavior`类中是唯一的，因此您不必担心与其他人的名字相同`Behavior`。第二个参数是对要保存或加载的变量本身的引用。您无需担心发生了什么，游戏便会处理。如果玩家**加载了保存，它将把它写入该变量**，如果他们**保存了游戏，它将从中读取并保存**。

## Registering Campaign Behaviors:
在 [MBSubModuleBase](../mountandblade/mbsubmodulebase.md) 类中,  您可以利用`OnGameStart`方法将行为添加到战役中。 

简单的例子:

```csharp
protected override void OnGameStart(Game game, IGameStarter gameStarter) 
{
    if(game.GameType is Campaign) 
    {
        //当前游戏类型是战役
        CampaignGameStarter campaignStarter = (CampaignGameStarter) gameStarter;
        campaignStarter.AddBehavior(new ExampleBehavior());
        //ExampleBehavoir 是一个自定义的并且实现 CampaignBehaviorBase的类
    }
}
```
