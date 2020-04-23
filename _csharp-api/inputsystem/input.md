# Input

此静态类型为您提供输入功能，基本输入系统没有绑定事件的功能，仅支持轮询。可能有很少的BUG。

## Key Polling

使用最多的是`GetKeyDown(KeyCode)` | `GetKeyPressed(KeyCode)` | `GetKeyReleased(KeyCode)` 

- `GetKeyDown` ：只有有一个键是按下的状态，就会返回
- `GetKeyPressed`：如果有键被按下，就返回
- `GetKeyReleased`：如果有按键被松开，就返回
- These are likely to be the most commonly used methods, `GetKeyDown` will return true on any number of frames so long as a key is down, this can cause undesired behaviour. If you only want to read an input once, use `GetKeyPressed` or `GetKeyReleased`.

您还可以使用扩展方法 `IsDown`/`IsPressed`/`IsReleased` 比如： `KeyCode.A.IsPressed()`