# 存档系统 - Save System

### Warning!  
从e1.0.10 / e1.1.0版本开始，定义继承游戏基本类型的自定义数据时，请格外小心。
如果数据将保存到游戏的内部存储中，则删除您的模块后，由于缺少自定义数据，将无法加载保存内容。在定义自定义LogEntry类型并将其传递给游戏时，就会出现这种情况LogEntry.AddLogEntry(customLog);。
一种解决方法，您应该包括从游戏中完全删除自定义数据的功能，或者为其提供一个mod。


## SaveableTypeDefiner
通过继承``TaleWorlds.SaveSystem.SaveableTypeDefiner``，来保存自定义的类/结构。
您不需要在某个地方注册它，游戏会通过反射机制找到。
```csharp
    public class CustomSaveDefiner : SaveableTypeDefiner
    {
        // 使用一个比较大的数字，并且确保其它模组没有使用相近的数字
        public CustomSaveDefiner() : base(2 _333_000) { }

        protected override void DefineClassTypes()
        {
            //这里的ID是本地的，并且与传递给构造函数的ID有关
            AddClassDefinition(typeof(CustomMapNotification), 1);
            AddStructDefinition(typeof(ExampleStruct), 2);
            AddClassDefinition(typeof(ExampleNested), 3);
            AddStructDefinition(typeof(NestedStruct), 4);
        }

        protected override void DefineContainerDefinitions()
        {
            ConstructContainerDefinition(typeof(List<ExampleStruct>));
        }
    }
```
  
## SaveableField and SaveableProperty

要将自定义类/结构中的数据标记为可保存，请使用`TaleWorlds.SaveSystem.SaveableFieldAttribute`和`TaleWorlds.SaveSystem.SaveablePropertyAttribute`.它们直接没有真正的区别，但是如果您使用了其中一个，请坚持使用该类型。它们不可互换，并且如果改变类型，将不会加载数据。

```csharp
    public struct ExampleStruct
    {
        // 如果类/结构未从任何具有可保存数据的游戏类型继承，则本地ID从1开始
        [SaveableField(1)]
        public PartyBase Attacker;
    }

    public class CustomMapNotification : InformationData
    {
        // InformationData中已经定义了5个，所以下一个ID应该从6开始
        [SaveableProperty(6)]
        public Hero Mercenary { get; set; }

        [SaveableProperty(7)]
        public bool IsHandled { get; set; }
    }
    
    public struct NestedStruct
    {
        [SaveableField(1)]
        public bool Flag;
    }
    public class ExampleNested
    {
        [SaveableField(1)]
        public NestedStruct Data;
    }
```
  
## CampaignBehaviorBase.SyncData

这个方法可以在多个`CampaignBehaviorBase`之间共享数据。

也可以使用这个方法存储自定义的集合类数据，比如：
* Array
* List
* Dictionary
* Queue
```csharp
    public class CustomBehavior : CampaignBehaviorBase
    {
        private List<ExampleStruct> _customDataMap = new List<ExampleStruct>();

        public override void SyncData(IDataStore dataStore)
        {
            dataStore.SyncData("customDataMap", ref _customDataMap);
        }
    }
```
  
  
### Tips:

社区应决定如何处理saveBaseId冲突
