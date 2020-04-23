# ModuleInfo

`ModuleInfo class` 包含了每一个MOD的信息。


您可以通过执行以下操作来获取所有已**加载的** mod 的列表以及有关它们的详细信息（其ModuleInfo）

```csharp
var loadedMods = new List<ModuleInfo>();
foreach(var moduleName in Utilities.GetModulesNames())
{
    var moduleInfo = new ModuleInfo();
    moduleInfo.Load(moduleName);
    loadedMods.Add(moduleInfo);
}
```
`Utilities class` 是 Talewords.Engine 命名空间的一部分, 它的`GetModulesNames()`方法返回一个已经加载的MOD列表

这可用于确定模块是否已加载，这对于具有可选依赖项的mod很有用。
