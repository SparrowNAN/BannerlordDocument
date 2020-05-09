# Input - 输入

此静态类型为您提供输入功能，基本输入系统没有绑定事件的功能，仅支持轮询。可能有一些BUG。

## 方法说明

> 有许多有用的方法可以检测以不同方式按下的键，所有这些方法都返回`Boolean`。使用最多的是`IsKeyDown`，`IsKeyPressed` 和 `IsKeyReleased`

### 使用方法

```c#
using TaleWorlds.InputSystem.
......

protected override void OnApplicationTick(float dt)
{
  int x = 0;
  int y = 0;
  int z = 0;
  //If X has been pressed, increment x by 1
  if(Input.IsKeyPressed(InputKey.X))
    x++;
  //For each tick that X is being held down, increment y by 1
  if(Input.IsKeyDown(InputKey.X))
    y++;
  //For each tick that X is untouched, increment z by 1
  if(Input.IsKeyReleased(InputKey.X))
    z++;
}  
```

### 常用方法列表

|方法名|作用|
|--|--|
|IsKeyDown|检查当前是否按下了指定的`key`，只要按住`key`，它就会返回true|
|IsKeyDownImmediate|`IsKeyDown`和`IsKeyPressed`的中间状态的检查|
|IsKeyPressed|检查是否已按下指定的`key`，它会一次返回布尔值|
|IsKeyReleased|检查当前是否未按下指定的`key`，它将返回布尔值|
|IsControlOrShiftNotDown|当Control或Shift均未按下时返回true|
|GetKeyboardText|以字符串形式返回当前存在于用户剪贴板中的文本|
|IsMouseActive|检查鼠标当前是否处于活动状态|
|IsMouseScrollChanged|检查鼠标滚轮当前是否正在旋转|
|MouseMoveX|以浮点数的形式返回鼠标的水平位置|
|MouseMoveY|以浮点数的形式返回鼠标的垂直位置|

### 可监听的按键

```c#
public enum InputKey
{
    Invalid,
    Escape,
    D1,
    D2,
    D3,
    D4,
    D5,
    D6,
    D7,
    D8,
    D9,
    D0,
    Minus,
    Equals,
    BackSpace,
    Tab,
    Q,
    W,
    E,
    R,
    T,
    Y,
    U,
    I,
    O,
    P,
    OpenBraces,
    CloseBraces,
    Enter,
    LeftControl,
    A,
    S,
    D,
    F,
    G,
    H,
    J,
    K,
    L,
    SemiColon,
    Apostrophe,
    Tilde,
    LeftShift,
    BackSlash,
    Z,
    X,
    C,
    V,
    B,
    N,
    M,
    Comma,
    Period,
    Slash,
    RightShift,
    NumpadMultiply,
    LeftAlt,
    Space,
    CapsLock,
    F1,
    F2,
    F3,
    F4,
    F5,
    F6,
    F7,
    F8,
    F9,
    F10,
    Numpad7,
    Numpad8,
    Numpad9,
    NumpadMinus,
    Numpad4,
    Numpad5,
    Numpad6,
    NumpadPlus,
    Numpad1,
    Numpad2,
    Numpad3,
    Numpad0,
    NumpadPeriod,
    Extended,
    F11,
    F12,
    NumpadEnter,
    RightControl,
    NumpadSlash,
    RightAlt,
    NumLock,
    Home,
    Up,
    PageUp,
    Left,
    Right,
    End,
    Down,
    PageDown,
    Insert,
    Delete,
    ControllerLStick,
    ControllerRStick,
    LeftMouseButton,
    RightMouseButton,
    MiddleMouseButton,
    X1MouseButton,
    X2MouseButton,
    MouseScrollUp,
    MouseScrollDown,
    ControllerLStickUp,
    ControllerLStickDown,
    ControllerLStickLeft,
    ControllerLStickRight,
    ControllerRStickUp,
    ControllerRStickDown,
    ControllerRStickLeft,
    ControllerRStickRight,
    ControllerLUp,
    ControllerLDown,
    ControllerLLeft,
    ControllerLRight,
    ControllerRUp,
    ControllerRDown,
    ControllerRLeft,
    ControllerRRight,
    ControllerLBumper,
    ControllerRBumper,
    ControllerLOption,
    ControllerROption,
    ControllerLThumb,
    ControllerRThumb,
    ControllerLTrigger,
    ControllerRTrigger,
}
```