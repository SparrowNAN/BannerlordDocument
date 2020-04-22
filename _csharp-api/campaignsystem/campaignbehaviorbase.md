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
(Work in Progress)

 **注意**：我们目前不确定该方法的作用，但是目前我们建议您将其实现为空方法，如下所示： 
```csharp
public override void SyncData(IDataStore dataStore)
{
}
```

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
