# MBInitialScreenBase

您可以通过继承`MBInitialScreenBase`来创建自定义的过场动画，然后将GameStateScreen属性应用于您的类。

这是你实现`MBInitialScreenBase`类的基本骨架:

```csharp
[GameStateScreen(typeof(InitialState))]
public class MyInitialScreen : MBInitialScreenBase
{
    private GauntletLayer _gauntletLayer;
    private InitialMenuVM _dataSource;

    public MBInitialScreen(InitialState initialState) : base(initialState) { }

    protected override void OnInitialize()
    {
        base.OnInitialize();
        this._dataSource = new InitialMenuVM();
        this._gauntletLayer = new GauntletLayer(1, "GauntletLayer");
        this._gauntletLayer.LoadMovie("InitialScreen", this._dataSource);
        this._gauntletLayer.InputRestrictions.SetInputRestrictions(true, InputUsageMask.Mouse);
        base.AddLayer(this._gauntletLayer);
        GameNotificationManager.Current?.LoadMovie(false);
        ChatLog.Current?.LoadMovie(false);
        InformationManager.ClearAllMessages();
    }
}
```

将字符串替换为[Movie](https://docs.bannerlordmodding.com/_gauntlet/movie.html)的XML文件`InitialScreen`的名称。
