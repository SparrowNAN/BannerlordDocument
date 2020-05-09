# Mission

> 此处翻译需要推到重来

可以将`Mission` 当作 GameModes\(Battles/TeamDeathMatch\) etc.  ？？？ //TODO optimization

`Missions`会随着 [Scene](../engine/scene.md), [MissionViews](missionbehaviour/missionview.md), and [MissionBehaviours](missionbehaviour/README.md) 进行初始化。

一旦获得`CampaignSystem`DLL的访问权限，即可获得有关`Mission`的更多信息。

## Tips

* 您可以使用`Mission.Current`属性获取当前任务实例（如果有）。

