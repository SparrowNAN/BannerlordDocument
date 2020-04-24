1.TaleWorlds.CampaignSystem.SandBox.GameComponents.DefaultClanFinanceModel

2.TaleWorlds.CampaignSystem.SandBox.CampaignBehaviors.ClanVariablesCampaignBehavior.DailyTickClan

3.GiveGoldAction.ApplyBetweenCharacters((Hero) null, clan.Leader, MathF.Floor(Campaign.Current.Models.ClanFinanceModel.CalculateClanGoldChange(clan, explanation, true)), true);
// 这里调用的是接口的方法，所以说肯定有地方可以配置这个接口方法

4.TaleWorlds.Core.GameModelsManager

5.  public sealed class GameModels : GameModelsManager 发现了一个被封闭的类

6. this._gameModels = this.CurrentGame.AddGameModelsManager<GameModels>(campaignGameStarter.Models);
// 游戏初始化的时候

7. this._gameModels = this.CurrentGame.AddGameModelsManager<GameModels>(campaignGameStarter.Models);
//  获取游戏模型

TaleWorlds.CampaignSystem.CampaignGameStarter.CampaignGameStarter

8. CampaignGameStarter.AddModel()

9. TaleWorlds.CampaignSystem.SandBox.SandBoxManager.OnGameStart 是在这个方法中，加载了经济模型


OnSettlementOwnerChanged //定居点发生变化的事件

OnBeforeSave

      this.TradeTaxAccumulated = (int) ((double) num * (0.600000023841858 + 0.300000011920929 * (double) MBRandom.RandomFloat) * (double) Campaign.Current.Models.ClanFinanceModel.RevenueSmoothenFraction());
	  // 村庄计算税收

public abstract class SettlementProsperityModel : GameModel
// 找到了计算增加health的方法

