# MBObjectManager

这个对象管理器是在制作MOD过程中会经常使用到的，因此熟悉它很重要。

`MBObjectManager`可用于获取游戏中当前从XML加载的任何对象。

These include:

* [BasicCharacterObjects](basiccharacterobject.md) - 角色对象
* CharacterAttributes - 角色属性
* CraftingPieces - 工艺品
* CraftingTemplates - 物品模版
* Cultures - 文化
* ItemModifierGroups
* ItemCategories
* ItemComponents
* [ItemObjects](itemobject.md)
* SkillObjects - 技能
* SiegeEngineTypes - 攻城器械类型

获取 [BasicCharacterObject](basiccharacterobject.md) 的例子：

```csharp
MBObjectManager.Instance.GetObject<BasicCharacterObject>("example_troop_id");
```

