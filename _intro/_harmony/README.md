# Harmony文档翻译

> `Harmony`是一个可以在运行时对`.NET方法`进行打补丁，扩展，替换操作的一个Library

## 使用条件

> `Harmony`适用于所有编译为CIL的语言。最具代表性的就是`.NET Framework` 和 `Mono`。
此外，您需要找到自己的注入方法或选择支持用户dll加载（通常称为Mods）的游戏，例如RimWorld或者Bannerlord.

## 依赖关系

它没有其他依赖关系，很可能也会在其他环境中工作。Harmony已在PC，Mac和Linux上进行了测试，并支持32位和64位。对于典型的Unity目标，只需将项目设置为.Net 3.5或Mono 2.x，并包含Harmony dll。

## 工作原理

在其他修补程序库仅允许您替换原始方法的情况下，Harmony更进一步为您提供：
* 一种保持原始方法完好无损的方法
* 在原始方法之前和/或之后执行代码
* 用IL代码处理器修改原始文件
* 多个Harmony补丁共存且彼此不冲突

![工作原理](https://raw.githubusercontent.com/pardeike/Harmony/master/Harmony/Documentation/images/patch-logic.svg?sanitize=true)

Tips:
1. 使用Harmony，您只需操纵方法。这包括构造函数和getter / setter。
2. 您只能使用具有实际IL代码主体的方法，这意味着它们会出现在dnSpy之类的反汇编程序中。
3. 太小的方法可能会内联并且您的补丁程序将无法运行。
4. 您不能将字段添加到类中，也不能扩展枚举（它们会被编译为ints）。
5. 修补通用方法或通用类中的方法很困难，并且可能无法按您期望的那样工作。
