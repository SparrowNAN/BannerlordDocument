# ChangeOwnerOfSettlementAction

这个类中的函数主要是设置/改变定居点的所有者

## Functions

这里有一个改变定居点所有者的函数列表:
- `ApplyByDefault(`[Hero](../hero.md)`hero, `[Settlement](../settlement.md)`settlement)` - 当战役看是阶段，或者玩家作弊获得定居点时调用
- `ApplyByKingDecision(`[Hero](../hero.md)`hero, `[Settlement](../settlement.md)`settlement)` - 当国王分封时调用
- `ApplyBySiege(`[Hero](../hero.md)`newOwner, `[Hero](../hero.md)`capturerHero, `[Settlement](../settlement.md)`settlement)` - 当军队围攻时
- `ApplyByRevolt(`[Hero](../hero.md)`hero, `[Settlement](../settlement.md)`settlement)` - 当反叛时调用
- `ApplyByLeaveFaction(`[Hero](../hero.md)`hero, `[Settlement](../settlement.md)`settlement)` - 当离开派系时调用
- `ApplyByBarter(`[Hero](../hero.md)`hero, `[Settlement](../settlement.md)`settlement)` - 当交易时调用
- `ApplyByRemoveFaction(`[Settlement](../settlement.md)`settlement)` - 当移除派系时调用
- `ApplyByDestroyClan(`[Settlement](../settlement.md)`settlement, `[Hero](../hero.md)`newOwner)` -  当拥有者去世时调用，当这种情况发生时，将封地转移给前一个拥有者的随机子代 
