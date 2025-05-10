---
name: Automatic Stock Trading 
tools: [pyfolio, datetime,numpy]
order: 1
image: /assets/stocks.png
description: Utilized financial indicators with ML and DRL strategies for stock selection and optimized portfolio allocation.
# external_url: https://github.com/yousinix
---
# Automatic Stock Trading 

## Description
The project frames stock trading as a Markov Decision Process (MDP), formulating the trading objective as a maximization problem. The methodology is structured into three primary steps. First, an environment is established, defining the action space, state space, and reward function. Next, three algorithms are trained to execute actions within this environment. Finally, an ensemble strategy is implemented, combining the actions of the three agents based on the Sharpe ratio, a measure of risk-adjusted return. The results highlight the effectiveness of the ensemble strategy, as indicated by its superior Sharpe ratio compared to the minimum-variance portfolio allocation strategy and the Dow Jones Industrial Average (DJIA).
<p align = "center">
    <img src="/assets/strategy.png" width= "60%"/>
</p>

## Dataset 
The Dow Jones 30 constituent stocks (as of 01/01/2016) were selected as the trading stock pool, with data sourced from the Compustat database via the Wharton Research Data Services (WRDS). The dataset includes historical daily data from 01/01/2009 to 05/08/2020 for backtesting, divided into an in-sample period for training and validation and an out-of-sample period for trading. To enhance adaptability to market dynamics, the agent undergoes continued training during the trading stage.
<p align = "center">
    <img src="/assets/stockdata.png" width= "60%"/>
</p>

## Deep Reinforcement Learning Strategy
An ensemble method selects the best-performing agent among PPO, A2C, and DDPG based on the Sharpe ratio.
- Advantage Actor-Critic (A2C): Combines policy-based (Actor) and value-based (Critic) approaches. The Actor proposes actions, while the Critic evaluates them using a value function. The advantage, calculated as the difference between observed and expected rewards, guides simultaneous updates to both policy and value function for improvement.
- Proximal Policy Optimization (PPO): Focuses on stabilizing policy optimization by employing a trust region to constrain significant policy updates. This approach balances exploration and exploitation while avoiding drastic policy changes that could harm performance.
- Deep Deterministic Policy Gradients (DDPG): Extends the Actor-Critic framework to continuous action spaces with a deterministic policy for direct action output. Stability is maintained through target networks, experience replay, and Ornstein-Uhlenbeck noise, enhancing exploration and convergence.
The ensemble process operates as follows:
1. A growing window of n months is used to retrain all three agents every 3 months.
2. A 12-month rolling validation window evaluates performance, followed by a growing window for training. The agent with the highest Sharpe ratio is selected, with risk aversion adjusted via the turbulence index during validation.
3. The selected agent, based on the highest Sharpe ratio, is used for predictions and trading in the next quarter.

## Performance Evaluation
Backtesting was performed for the three individual agents and our ensemble strategy.
<p align = "center">
    <img src="/assets/performance.png" width= "60%"/>
</p>
Five metrics were used to evaluate results:
- Cumulative Return: Calculated by subtracting the portfolio’s final value from its initial value and then dividing by the initial value.
- Annualized Return: The geometric average amount of money earned by the agent each year over the time period.
- Annualized Volatility: The annualized standard deviation of portfolio return.
- Sharpe Ratio: Calculated by subtracting the annualized risk-free rate from the annualized return and then dividing by the annualized volatility.
- Max Drawdown: The maximum percentage loss during the trading period.

## Analysis
The A2C agent is more adaptive to risk. It has the lowest annual volatility and max drawdown among the three agents. So A2C is good at handling a bearish market. PPO agent is good at following trend and acts well in generating more returns, it has the highest annual return and cumulative return among the three agents. So PPO is preferred when facing a bullish market. DDPG performs similar but not as good as PPO, it can be used as a complementary strategy to PPO in a bullish market.
The ensemble strategy and the three agents perform well in the 2020 stock market crashevent. When the turbulence index reaches a threshold, it indicates an extreme market situation. Thenthe agents will sell off all currently held shares and wait for the market to return to normal to resume
trading. By incorporating the turbulence index, the agents are able to cut losses and successfully survive the stock market crash in March 2020. 
<p align = "center">
    <img src="/assets/marketcrash.png" width= "60%"/>
</p>
