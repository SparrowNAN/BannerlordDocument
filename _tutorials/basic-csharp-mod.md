# 基础 C\# Mod

## 简介

接下来会一步一步引导制作出一个基础的 C\# mod。 这个`Mod`将在单人游戏标题屏幕上添加一个名为“Messa ge”的按钮。单击后，此按钮将输出“Hello World”。 

## 准备

#### 针对这个教程我们将将要制作的`Mod`命名为 `ExampleMod`.

### 设置Module \(SubModule.xml\)

1. 进入到游戏的 `Modules` 文件夹

2. 创建一个文件夹并且命名为 `ExampleMod` (一定要和`SubModule.xml`中的`Id`保持一致)

3. 在Mod文件夹下创建`/bin/Win64_Shipping_Client`文件夹

4. 在Mod文件夹下创建一个 `SubModule.xml` 文件 (必须是这个名字) 

   ```xml
    <Module>
        <Name value="Example Mod"/>
        <Id value="ExampleMod"/>
        <Version value="v1.0.0"/>
        <SingleplayerModule value="true"/>
        <MultiplayerModule value="false"/>
        <DependedModules>
            <DependedModule Id="Native"/>
            <DependedModule Id="SandBoxCore"/>
            <DependedModule Id="Sandbox"/>
            <DependedModule Id="CustomBattle"/>
            <DependedModule Id="StoryMode" />
        </DependedModules>
        <SubModules>
            <SubModule>
                <Name value="ExampleMod"/>
                <DLLName value="ExampleMod.dll"/>
                <!-- MySubModule 是将要在教程编程章节创建的类名称 -->
                <SubModuleClassType value="ExampleMod.MySubModule"/>
                <Tags>
                    <Tag key="DedicatedServerType" value="none" />
                    <Tag key="IsNoRenderModeElement" value="false" />
                </Tags>
            </SubModule>
        </SubModules>
        <Xmls/>
    </Module>
   ```

5. 如果您使用其他名称，请更改上述值以匹配您的Module / SubModule的值。

6. 启动启动器，并确保您的mod出现 `Singleplayer` &gt; `Mods`中。

[有关Mod结构的更多信息](../_intro/folder-structure.md).

### Setting up your Project

Before setting up a project, it is important to know that **this is not required for basic mods** \(e.g. changing or adding items/characters/scenes\).

1. Start Microsoft Visual Studio and select `Create New Project`.
2. Choose `Class Library (.NET Framework)`.
3. Name your project `ExampleMod` (if you choose another name make sure that your namespace and assembly name are correct) `.NET Framework 4.7.2` as the `Framework`.  If this option is not available for you, [Download it here](https://dotnet.microsoft.com/download/dotnet-framework/net472) \(Developer Pack\).
4. Now that your project is setup, [set your build path](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-change-the-build-output-directory?view=vs-2019) to the `Modules/ExampleMod/bin/Win64_Shipping_Client` directory in your game files.
5. [Reference](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager?view=vs-2019) the `TaleWorlds.*` DLLs in the `bin\Win64_Shipping_Client` directory of your game files \(not your module directory\). Also reference the `TaleWorlds.*` DLLs for each official module in `Modules\ModuleName\bin\Win64_Shipping_Client`.

### Debugging your Project (Optional)

#### Way 1 (Preferred)
1. Open your project properties and go to the `Debug` tab.
2. Select the `Start external program` option and then browse for `Bannerlord.exe` located in the `bin\Win64_Shipping_Client` directory in your game files \(not your module directory\).
3. Set your working directory to the `bin\Win64_Shipping_Client` directory in your game files \(not your module directory\).
4. Add the following command line arguments \(be sure to replace ExampleMod with the name of your module\):
   * `/singleplayer _MODULES_*Native*SandBoxCore*CustomBattle*SandBox*StoryMode*ExampleMod*_MODULES_`

#### Way 2 (If you want to start your debugging from launcher window)
1. Open your project properties and go to the `Debug` tab.
2. Select the `Start external program` option and then browse for `TaleWorlds.MountAndBlade.Launcher.exe` located in the `bin\Win64_Shipping_Client` directory in your game files \(not your module directory\).
3. Set your working directory to the `bin\Win64_Shipping_Client` directory in your game files \(not your module directory\).

## Programming

1. Create a new class in your VS Project and name it `MySubModule`, then open it.
2. Add the following using directives to your class:

   ```csharp
    using TaleWorlds.Core;
    using TaleWorlds.Localization;
    using TaleWorlds.MountAndBlade;
   ```

3. Inherit from the `MBSubModuleBase` class.
4. Setup an override for the `OnSubModuleLoad()` inherited method.
5. Add the following code to your override method:

   ```csharp
    Module.CurrentModule.AddInitialStateOption(new InitialStateOption("Message",
        new TextObject("Message", null),
        9990,
        () => { InformationManager.DisplayMessage(new InformationMessage("Hello World!")); },
        false));
   ```

6. Compile your project and confirm that it was outputted to `Modules\ExampleMod\bin\Win64_Shipping_Client`.
7. Open the Bannerlord launcher and navigate to `Singleplayer` &gt; `Mods` then make sure that your mod is ticked and start the game.
8. On the title screen, you should now see a button called `Message`, click it and you should see `Hello World` displayed in the bottom-left corner of your screen \(in chat\).
9. You have now successfully created your first Bannerlord mod!

