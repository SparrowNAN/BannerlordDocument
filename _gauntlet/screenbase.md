# ScreenBase

你可以使用`screens`来组织和实例化 [ViewModels](viewmodel.md) 和 [Movies](movie.md) 。

为了防止出现任何问题，建议您在创建`screen`时使用以下模板。

```csharp
public class MyExampleScreen : ScreenBase
{

    private MyExampleVM _dataSource;
    private GauntletLayer _gauntletLayer;
    private GauntletMovie _movie;

    protected override void OnInitialize()
    {
        base.OnInitialize();
        _dataSource = new MyExampleVM();
        _gauntletLayer = new GauntletLayer(100)
        {
            IsFocusLayer = true
        };
        AddLayer(_gauntletLayer);
        _gauntletLayer.InputRestrictions.SetInputRestrictions();
        _movie = _gauntletLayer.LoadMovie("MyExampleMovie", _dataSource);
    }

    protected override void OnActivate()
    {
        base.OnActivate();
        ScreenManager.TrySetFocus(_gauntletLayer);
    }

    protected override void OnDeactivate()
    {
        base.OnDeactivate();
        _gauntletLayer.IsFocusLayer = false;
        ScreenManager.TryLoseFocus(_gauntletLayer);
    }

    protected override void OnFinalize()
    {
        base.OnFinalize();
        RemoveLayer(_gauntletLayer);
        _dataSource = null;
        _gauntletLayer = null;
    }
}
```

## Pushing your Screen

要将屏幕推到屏幕堆栈上，可以执行以下操作：

```csharp
ScreenManager.PushScreen(ViewCreatorManager.CreateScreenView<MyExampleScreen>());
```

