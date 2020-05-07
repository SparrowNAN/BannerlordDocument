# 为Vortex打包您的mod


## 简介

[Vortex](https://www.nexusmods.com/about/vortex/)是Nexus Mods强大的开源Mod管理器。它支持安装和管理适用于100多种游戏的mod，包括Mount＆Blade 2：Bannerlord。共享您的mod时，应注意几个事项，以确保其结构与Vortex兼容。


## MOD

MOD是自动检测的，它们的特征在于包含在“Modules”文件夹中，并且包含Submodule.xml文件。Vortex抓取了包含Submodule.xml的整个文件夹，并将其放入游戏的“Modules”文件夹中。

开始游戏时，请不要忘记在启动器中启用这些mod！


## XML编辑

当前，任何其他类型的Mod都需要您相对于游戏库文件夹进行简单打包。例如，如果我有文件`BannerEditor.xml`需要进入`Modules \ Native \ GUI \ Prefabs \ Bannereditor`文件夹，则需要在上传的文件上包含这些文件夹的路径`GUI \ Prefabs \ Bannereditor`。

这将允许正确且一致地安装包括XML编辑，视频/声音编辑和Reshade预设在内的所有内容。

## 使用工具创建可上传的Vortex MOD

[FOMOD Creation Tool](https://www.nexusmods.com/fallout4/mods/6821/?tab=files)
