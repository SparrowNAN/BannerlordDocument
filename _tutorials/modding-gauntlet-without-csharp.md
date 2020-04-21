# Modding Gauntlet UI

## 重要
### 在本教程中可以不依赖任何模块。

## 简介

以下指南将逐步指导您如何创建一个无需使用任何C＃即可覆盖任何Gauntlet UI的mod。对于此示例，我们将使用一些自定义标题文本覆盖Quests UI。

## 准备

#### 我们将把教程创建的Mod命名为 `ExampleUIMod`.

### 设置你的模块 \(SubModule.xml\)

1. 定位到你游戏文件的`Modules`目录

2. 创建 `ExampleUIMod` 文件夹(必须和第五步中的ID一致).

3. 在`ExampleUIMod`下建一个`GUI`目录

4. 在`GUI `目录下创建一个`Prefabs`文件夹（`/ExampleUIMod/GUI/Prefabs/`）

5. 回到`ExampleUIMod`目录下创建`SubModule.xml`文件

    ```xml
    <Module>
        <Name value="Example UI Mod"/>
        <Id value="ExampleUIMod"/>
        <Version value="v1.0.0"/>
        <SingleplayerModule value="true"/>
        <MultiplayerModule value="false"/>
        <DependedModules/>
        <SubModules/>
        <Xmls/>
    </Module>
    ```

6. 开始游戏，查看启动器的 `Singleplayer` &gt; `Mods`下是否有`ExampleUIMod`

## 重写一个 Gauntlet UI

Tips：你可以重写任何的`Gauntlet UI`。这这个教程汇总，我们将重写`Quests UI`（任务UI）

1. 进入 `Modules\SandBox\GUI\Prefabs\QuestsScreen` ，复制 `QuestsScreen.xml`文件
2. 进入 `Prefabs` 文件夹（上面第4步创建的），把`QuestsScreen.xml`文件复制到这里
3. 使用文本编辑器打开文件，不要使用记事本，使用`VS code`之类的文本编辑器
4. 查找 `Text="@QuestTitleText"` 
5. 替换 `@QuestTitleText` (也包括@符号) 为你想要的任何文本
6. 保存文件
7. 打开游戏加载器 `Singleplayer` &gt; `Mods` ，确认勾选你的Mod，启动游戏
8. 打开任务UI界面，你应该就可以看到你输入的文本在顶部中间显示了
9. 恭喜，创建了第一个`Bannerlord Gauntlet mod`!!!

##  如何启用和使用实时UI编辑

游戏中，实时编辑UI，会让创作更加容易，但是仅仅依靠游戏本体是无法实现的。

要启用实时编辑，需要下载 [DeveloperConsole Mod](https://www.nexusmods.com/mountandblade2bannerlord/mods/4).

下载并安装了Developer Console Mod后，请按照以下步骤为游戏会话启用实时编辑。

1. 打开加载器，确保 `Developer Console` ，和你的`UI Mod`都被勾选
2. `Developer Console`使用快捷键`CTRL`+ `~`（波浪号）启用控制台。如果此快捷方式对您不起作用，请尝试按CTRL，然后按键盘上Tab上方和Esc下方的键
3. 现在您可以看到控制台，您将需要键入命令`ui.toggle_debug_mode`以启用实时UI编辑功能
4. 您对UI所做的任何更改现在都应该在游戏中自动更新
