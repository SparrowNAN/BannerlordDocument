# Widget - 小部件

小部件是一种为UI创建可交互内容的好方法。这可能包括滚动条，按钮，工具提示等。

## Common Predefined Widgets Include

* ButtonWidget -- 按钮
* ImageWidget -- 图片
* ListPanel -- 列表
* RichTextWidget -- 富文本
* ScrollablePanel -- 可以滚动的窗口
* ScrollBarWidget -- 多格式文本（// TODO）
* TextWidget -- 文本
* TooltipWidget -- 提示
* Widget -- 小部件

### Note

还有更多的小部件；以上只是最常用的小部件。您可以通过反编译`TaleWorlds.GauntletUI.dll`和`TaleWorlds.MountAndBlade.GauntletUI.dll`DLL 找到其他小部件。小部件继承了`Widget`该类，该小部件的标签名称将与类名称相同。

## Widgets 中常见的属性

* Brush
* Command.Click _\(Command.YourKeyHere\)_
* DataSource _\(Properties with DataSourceProperty Attribute in C\#\)_
* DoNotAcceptEvents
* HorizontalAlignment / VerticalAlignment
* Id
* MarginLeft / MarginRight / MarginTop / MarginBottom
* Sprite
* SuggestedWidth / SuggestedHeight
* Text _\(Text Widgets only\)_
* WidthSizePolicy / HeightSizePolicy

## Creating a Custom Widget

您可以通过简单地创建一个继承类来创建自定义窗口小部件`Widget`。之后，您可以在任何[Movie中](https://docs.bannerlordmodding.com/_gauntlet/movie.html)使用您的Widget 。小部件的标签名称将与您使用的标签名称相同。

