There are many kinds of decentrialize exchanger, the most popular one are those base on Automated market maker (AMM). In this section we will dive deep into its financial model and trading logic. All DEX base on AMM are composite of so called
"liquidity pool", "liquidity pool" is made up by a pair of tokens and the number of each kind of token in the pair need to satisfy a kind of constrain. And the total amount of tokens in the pool is called "reserve". For example a pool is
made up of two kinds of token: ETH and USTD, if the number of USDT is 10000 and the number of ETH is 5, the the amount of "reserve" of USDT in the pool is 10000 and "reserve" of ETH is 5.

Besides tokens in the pool, there is another token which is created to represent the share of tokens in the pool which has name "liquidity pool token" which is called LP token, compare with normal stock exchange,
you can take the tokens in the pool as stocks and the LP token is the us dollar which you can use to buy stocks, or you can sell the stocks back and get back us dolloars.

For example if the pool has token pair of BTC/ETH with BTC has number 100 and ETC has number 1600, and the total number of LP token is 400, then if you hold 40 LP tokens, then you can use thsese LP token to exchange 10% of the tokens from the
pool. But you can't change any number of BTC or ETH as your own will, since 40 LP tokens is 10% of total LP tokens, therefore you can get back 10% * 100 = 10 BTC tokens and 10 % 1600 tokens. Using LP tokens to take out tokens from the pool
is called "liquidity removal".

For AMM type of exchange. The trading of tokens in the pool need to confined to some restrain. The most popular restrain is the product of number of token for each type need to keep as a constant. This means for a pool with two kinds of token
A and B, if you want to take some number of token A out from the pool, then you need to put some number of token B back into the pool. This type of restrain is called constant product market maker(CPMM). For eample if the constant number
is 600, and number of token A is 20 and number of token B is 30, which statisfy the constrain that is 20 * 30 = 600. If you want to take 10 tokens of type A out from the pool, you need to put 30 tokens of B back into the pool then the 
number of tokens of type A multiply with number of token B is still 10 * 60 = 600.

For CMMP kind of trading, the number of each token will satisfy the following curve:



![截屏2024-12-11 17 38 17](https://github.com/user-attachments/assets/5e5dc593-2d81-4e7a-bcdd-315af39e522a)

For above image, if the trading from the blue point move to red point, which means increase the number of token A and decrease the number of token B, that is selling token A to buy token B. If the blue point move to green point. Which means
the number of token B is increased and the number of token A is reduced, then we are selling token B to buy token A. Therefore the trading for CPMM is always using one kind of token to exchange other kind of token and we need to following the
given ratio that is when you taken some amount of token A out from the pool you need to put back amount of token B back and make sure the product of number of two kind of token still equals to the given constant.

What need to notified is that, the constant constrain is for trading. Any one can add more token to the pool and change the value of constant. For example for the pool has 20 tokens of type A and 30 tokens of type B, then you can add
2 tokens of type A with 3 tokens of type B, that is when adding tokens to the pool you need to following the ratio of two type of tokens in the pool. Then the exchanger will given some amount of LP tokens(this is called LP token mint), 
and at later time you can use the given amount of LP tokens to get some amount of tokens of type A and B from the pool(this is called LP token burn). 
Need to noticed that the amount of tokens you get back will not equal to the amount of tokens when you provide them to the pool.

For exchanger, it may has several pools such as (tokenA, tokenB), (tokenB, tokenC), (tokenC, tokenD), then there is rout from tokenA to tokenD, then you can trading tokenA with tokenD, or tokenD with tokenA, if there is not route for
tokenA to tokenD, such as pools like: (tokenA, tokenB), (tokenC, tokenD), then you can't trade tokenA for tokenD in the given exchange.

Finally let's see the architecture we will build for the exchanger as following:

<img width="1078" alt="截屏2024-12-11 18 20 11" src="https://github.com/user-attachments/assets/41714cb3-1d47-4468-ac2d-e5472317fd2f">

In the image above, the AMM caller is the frontend page the is used by users, and the AMM router is a smart contract act as proxy between frontend page and the lower level smart contract. It takes commands or requests from the frontend, 
do some checking then same convert the requests to commands such as minting LP tokens, swaping tokenA with tokenB for lower smart contracts.
