# 入门

## ！！！重要

在开始之前，需要去了解一下[SubModule.xml](../_xmldocs/submodule.md) 文件，这个文件指引游戏去加载勾选的相关MOD。

## 工具

### C\# IDE

* [Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/) \(not required for basic mods\)

### 文本编辑器

* [Visual Studio Code](https://code.visualstudio.com/download)
* [Sublime Text](https://www.sublimetext.com/)  
* Others

## Modding without C\#

游戏中有几个方面你可以`不通过编程`来修改。这包括`事件`、`物品`、`文化`、`性格`、`UI`等等。

## Modding with C\#

Bannerlord的MOD系统是基于模块的，所以制作MOD会比之前的系列更加方便，并且可以制作M更复杂的MOD。

## 创建一个模块

在Bannerlord中，一个单独的mod被称为一个`模块`， 模块是通过文件夹的形式创建的，必定包括一个`SubModule.xml`文件（它通知启动程序加载您的mod）。

2. 在`Modules`文件夹下面创建一个新的文件夹，文件夹的名称必须是你MOD的名称（MOD的名称会在`SubModule.xml`中定义）。
2. 在文件夹中创建`SubModule.xml` 文件。 你可以 [查看一个简单版本](../_xmldocs/submodule.md) 或者 [查看SubModule.xml的详细文档](../_xmldocs/submodule.md)

## Next Steps

- Refer to the [Folder Structure](folder-structure.md) page for additional information on what additional directories to add depending on the intended content of your mod.
- Refer to the [Basic C# Mod](../_tutorials/basic-csharp-mod.md) page for an example of how to set up, build and run code in Bannerlord.
- Refer to the [Modding Gauntlet UIs Without C#](../_tutorials/modding-gauntlet-without-csharp.md) page for information on how to mod Gauntlet UIs without using any C#.

