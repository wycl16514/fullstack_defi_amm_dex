There are many kinds of decentrialize exchanger, the most popular one are those base on Automated market maker (AMM). In this section we will dive deep into its financial model and trading logic. All DEX base on AMM are composite of so called
"liquidity pool", "liquidity pool" is made up by a pair of tokens and the number of each kind of token in the pair need to satisfy a kind of constrain. And the total amount of tokens in the pool is called "reserve". For example a pool is
made up of two kinds of token: ETH and USTD, if the number of USDT is 10000 and the number of ETH is 5, the the amount of "reserve" of USDT in the pool is 10000 and "reserve" of ETH is 5.

Besides tokens in the pool, there is another token which is created to represent the share of tokens in the pool which has name "liquidity pool token" which is called LP token, compare with normal stock exchange,
you can take the tokens in the pool as stocks and the LP token is the us dollar which you can use to buy stocks, or you can sell the stocks back and get back us dolloars.

For example if the pool has token pair of BTC/ETH with BTC has number 100 and ETC has number 1600, and the total number of LP token is 400, then if you hold 40 LP tokens, then you can use thsese LP token to exchange 10% of the tokens from the
pool. But you can't change any number of BTC or ETH as your own will, since 40 LP tokens is 10% of total LP tokens, therefore you can get back 10% * 100 = 10 BTC tokens and 10 % 1600 tokens. Using LP tokens to take out tokens from the pool
is called "liquidity removal".


