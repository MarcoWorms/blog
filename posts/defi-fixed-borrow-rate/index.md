# How Spark fixes DeFi borrow rates

![image](https://github.com/MarcoWorms/blog/assets/7863230/8436731a-bea5-403c-a493-6b214ae1b274)

Lending and borrowing are one of DeFi's strongest use cases, and we have come a long way in experimenting with different types of collateral assets and risk parameters. This article will recap how borrow interest has been set across many protocols and how Maker and Spark work on a less volatile alternative for all parties involved.

# Why do people use DeFi lending and borrowing?

## Borrow

DeFi borrowing is very straightforward:

1. The borrower deposits collateral assets.
2. The borrower takes a loan from lenders.
3. If the borrower fails to pay back, the protocol liquidates collateral to pay lenders.

This is a very simple mechanic but it can be used in powerful ways, most notably:

- To capture some upside of selling without actually selling. Borrowers can obtain liquidity (working capital) without selling their assets, allowing them to retain their collateral's potential upside value gain.
- To leverage their positions. Borrowers can deposit an asset and take out a loan to purchase more of that asset, effectively increasing their exposure to the asset's price movements. If the asset's value increases, it can gain more than it would without borrowing.

## Lend 

Lenders are attracted to DeFi for the sweet, sweet yield. Lenders can earn interest on their deposits by supplying assets to be borrowed by other users. Interest is generated from the borrowing demand and is algorithmically adjusted based on the current supply and demand within the pool.

# How does DeFi lending interest rate work?

DeFi lending protocols will often plot the interest rate curve like this:

1. There is a total supply of assets to be borrowed (which is the total supply deposited by lenders)
2. The protocol wants borrowers to borrow up to ~80% of the supply (which is called the optimal point, which can change per asset type)
3. Because the other ~20% needs to be available for lenders to withdraw (and not get stuck waiting for borrowers to pay back)

To achieve the optimal balance protocols will often have formulas that lower the borrow rates when demand is below the optimal point and exponentially increase the rate if demand is above. Here is an example of wETH AAVE market interest curve:

![image](https://github.com/MarcoWorms/blog/assets/7863230/93f9087f-0107-4425-a4b0-a75a98543e0e)

The issue with this traditional interest rate model is capital inefficiency because you can't just use 100% of the supplied amount. But there is a way to allow this to happen!

# How does Maker provide a fixed interest through Spark and allow for 100% supply usage

In collaboration with Spark, Maker is pioneering a fixed interest rate model. Spark's model provides a stable rate that, while fixed in the short term, can be adjusted by Maker governance in the long term to reflect market conditions.

Maker fixes the rate through governance and increases supply in batches of $30M as needed. If the fixed rate needs to change, borrowers and lenders have at least 2 weeks to adjust before the change happens. The fixed-rate means that Maker is willing to lend DAI at that rate, and Maker will also increase supply for borrowing if demand tops 100% for the current rate.

![image](https://github.com/MarcoWorms/blog/assets/7863230/4184bdb3-8784-47d4-9f12-17def7c80506)
