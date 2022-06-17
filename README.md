# Ton Nominators Pool

Nominator pool source code for TON.

## Add stake
Adding stake is two step process: first you send a stake and eventually pool need accept it. Nominator Pool is free to NOT accept your stake for any reason.

All pools have different deposit fees and minimum stake amounts, check out information about current deposit fees.

To send stake send a message with a comment `Stake` (capitalization is important) with value of `desired stake` + `deposit fee`.

## Withdraw stake
Withdrawal also two step process: first you need to request withdrawal and then when withdrawal solidify, you can repeat command to withdraw result. Sometimes you can withdraw immediatelly.

All pools have different withdraw fees, check out information about current withdraw fees.

To withdraw stake send a message with a comment `Withdraw` (capitalization is important) with value of `withdraw fee`.

## Testing

This contract has almost full testing coverage, but it is not open source.

## Deployment

Nominator pool is combination of several contracts:
* Owner - owner is a arbitrary contract (wallet or dao) that could make critical updates to the contract: change fees, start/stop pool and even update code. Owner also receives all profits from fees.
* Controller - controller is arbitrary contract (wallet or dao) that issue staking commands for validation and/or voting. Controller pays for this operations and can get "unowned" balances to restore it's balance and continue working. We recommend to top ~1000 TONs for uninterrupted work.
* Proxy - proxy contract is the only one that is masterchain and represent validation pool there. It performs simple proxying between pool and elector.
* 池 - 包含所有權益的所有記錄並自行執行權益的主合約。
 
在部署之前，您需要準備好並部署所有者和控制器合約，並生成兩個虛合約 - 一個用於主鏈中的代理，另一個用於基本工作鏈中的池。

## License

GNU v3
