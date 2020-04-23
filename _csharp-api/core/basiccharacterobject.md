# BasicCharacterObject

BasicCharacterObjects 包含了从 `npccharacters` XML 文件序列化出来的角色信息。 包含了角色的属性，装备，等级，技能，威化。

BasicCharacterObjects  是构建 [Agents](../mountandblade/agent.md) 的组成部分。

可以使用 [MBObjectManager](mbobjectmanager.md) 获得一个已经加载的 BasicCharacterObject

```csharp
MBObjectManager.Instance.GetObject<BasicCharacterObject>("example_troop_id");
```

