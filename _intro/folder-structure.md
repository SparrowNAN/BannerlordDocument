# Mod的结构

>  所有文件夹都是可选的，启动程序检测子模块的唯一要求是子模块的基本目录本身和有效的 [SubModule.xml](../_xmldocs/submodule.md)

注意：我们制作的MOD其实就是游戏的一个子模块。

一个子模块的举例
`Drive:\\InstallLocation\Mount & Blade II Bannerlord\Modules\Native\` 

## 文件夹 & 文件示例

* `AssetPackages` - 开发MOD时未知的文件 （// TODO 此处需要优化）
  *  `someasset.tpac`
* `Atmospheres` -  [Refer to [Atmosphere]](../_xmldocs/atmosphere.md)
  * `Interpolated` 
    * `interpolatedatmosphere.xml`
  * `atmosphere.xml`
* `bin` - 编译好的DLL文件需要放置的地方 - [Refer to [Basic C# Mod]](../_tutorials/basic-csharp-mod.md)
  * `Win64_Shipping_Client`
    * `MyModule.dll`
* `GUI` -UI相关的文件
  * `Brushes` - 一些提示框之类的UI
  * `Prefabs` - 动画
* `ModuleData` - 任何MOD需要加载的数据，需要是XML格式的文件 \(e.g. items/cultures/gametexts\).
* `SceneObj` - 场景/事件

```text
- MyModule
	- AssetPackages
		-- assetpackage.tpac
	- Atmospheres
		- Interpolated
			-- interpolatedatmosphere.xml
		-- atmosphere.xml
	- bin
		- Win64_Shipping_Client
			-- MyModule.dll
    - GUI
        - Brushes
        - Prefabs
    - ModuleData
    - SceneObj
    - SubModule.xml
```

