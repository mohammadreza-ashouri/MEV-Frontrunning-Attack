
# What the F**K is Front-Running Attack?

## What the hell is MEV ?

When a user broadcasts an Ethereum transaction, it doesn't become part of the blockchain until a miner puts it in a block. This process takes some time. Note that, DeFi has to supply some incentives for all partners. Mining grants and transaction fees allow miners to earn rewards for the work completed. They randomly pick transactions from mempool to be held in the block, and those with a higher fee probably have more potential to be selected shortly. However, they can reorder, exclude, or censor transactions within specific blocks to boost their revenue. The value extracted in this way is called Maximal Extractable Value (MEV), and malicious participants can also profit from their knowledge of the future inclusion of the transaction at the user's expense. This is called front-running.
Note that DeFi projects such as Bancor (a reputable DEX) were vulnerable to front-running.
An Attack Scenario
Let's suppose that Alice will swap TokenX for TokenY from a liquidity pool. Meanwhile, Bob is scanning mempool, finds the transaction, and places two other ones:
- TX2 transaction - the same TokenX for TokenY swap, with fewer assets (to evade causing a significant price slippage) and with little more gas fee,
- TX3 transaction - TokenY for TokenX swap, with a slightly lower gas fee.

The first malicious transaction TX2 will be validated and executed before Alice's TX1 transaction. To the best of Bob's knowledge, Alice's transaction raises the price of TokenY. Therefore, the TX3 transaction will become profitable for Bob.
This class of front-running is called 'sandwiching', and is an example of how someone can exploit MEV.
Miners - Due to their power to control and control the order of transactions. They are not mandated to propose a higher gas price to manipulate the transaction sequence. Furthermore, miners can only front-run in the blocks that they mine.
Nodes - They are considered as users watching transactions in the mempool where they can select unconfirmed transactions to front-run. The higher the gas price they put in, the higher chance the transaction is selected first. And if the user can front-run any transaction in the protocol, evil things can occur.

## Okay now what!?
This attack is a bit complicated so any suggested solution has to address two challenges:
Lack of transactions confidentiality: All information about transactions is transparent to each participant,
Miners' knowledge: Knowing about transaction orders is usually based on the provided gas fee.

Potential solutions have to take these two issues into account, so the followings are potential solutions that we can make use of in order to mitigate the attack:

- Transaction sequencing → Assigning a counter to transactions in the protocol to keep order of the execution process.
- Commit & reveal strategy → Relying on limiting the transaction's visibility.
- Off-Chain Ordering → Relying on a third-party trust.
- Limit the gas price → Accepting transactions with a gas price below the appointed threshold only.
- Determine minimal expected value → Forcing users to specify transaction minimal expected value or an acceptable price slippage.
