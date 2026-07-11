# BRAIN FAQ Extracts

## An Alpha expression is executed on each instrument and assigns weight to the instrument, right?

[{"type": "TEXT", "value": " Yes, the expression creates a weighted vector of instruments. Instrument here could be stocks or future contracts.

", "id": "09ae9d99-594f-444b-b526-ca1ce908411d"}]

## Are Alphas one line or full codes?

[{"type": "TEXT", "value": "An Alpha is basically a mathematic trading model. It is a very generic term and can be realized as a flow chart, formula, code in Python, C++, R, etc. In BRAIN platform, they can be represented in the form of expressions.

", "id": "98d26a67-59f9-41f9-a41e-e29d69eb4120"}]

## How the technical indicator and the market indicators are different from each other and which one of them we can use to make Alphas?

[{"type": "TEXT", "value": " The\u00a0[technical indicators](\"http://www.investopedia.com/terms/t/technicalindicator.asp\")\u00a0that are generally aimed at specific stocks. It can also be used on\u00a0[market indexes](\"http://www.investopedia.com/terms/m/marketindex.asp\"). However, there is also a series of indicators, which were formulated specifically for gauging the direction of the major market indexes and are not used to analyze individual securities.\u00a0

The main difference between market indicators and technical indicators is that market indicators are not plotted on the same chart as a security but are plotted on a chart by themselves. The market indicators do not reflect just one security but a large array of securities in the market and vary from measuring market sentiment to the current\u00a0[volatility](\"http://www.investopedia.com/terms/m/marketindex.asp\")\u00a0in the market.

You can use both technical and market indicators to make Alphas.

", "id": "6226ef9b-e72d-46ca-94d3-1bf7ef5eb9f9"}]

## I wanted to request extra study material (if possible) regarding the Alpha generation and how to get higher Sharpe for generated Alphas.

[{"type": "TEXT", "value": " Alpha research is a very broad field and you can apply ideas from various backgrounds to achieve a good signal. You can refer to various papers and articles available over net concerning to alpha research. You can search for papers at SSRN site. You could also start with some technical indicators to get some idea and [stockcharts.com](\"http://www.stockcharts.com/\") is a very good starting point for this.

If the idea is good, the alpha Sharpe will be high. A good idea is an idea which is robust and which performs well consistently over all the years. As such an alpha will have less standard deviation it will have a higher Sharpe ratio and will be considered a good alpha. Thus try to make alphas which work in all situations.

", "id": "79cdf882-f02a-4065-9b1d-bad845ff3c01"}]

## Why am I getting "0" PnL for Alpha = ts_decay_exp_window(close, 5, 1)- ts_decay_exp_window(close, 20, 1). This should not be the case.  I am trying MACD oscillator.

[{"type": "TEXT", "value": " ts_decay_exp_window (close, 5, 1) and  ts_decay_exp_window p(close, 20, 1) are highly correlated with each other and that's why on subtraction, you are getting 0 PnL. If smoothing factor=1, then correlation would be infinite. Try lowering it to 0.5. It should be <1.
You will get a PnL graph for  ts_decay_exp_window (close, 5, 0.5) -  ts_decay_exp_window p(close, 20, 0.5)

", "id": "fd28f16c-c7ab-451c-9622-3fa1343bd401"}]

## Could you please throw some light on meta score and meta alpha count?

[{"type": "TEXT", "value": "

The Meta Score looks at each user's alpha  pool as a whole and assigns a score based on the Sharpe of the  combination, the average turnover of the alphas in your alpha pool and  correlation.

You should keep the following points in your mind while developing alphas:

- Spend time improving the signal,  lowering the turnover to the appropriate range for the delay and  ensuring the idea is unique enough.

- Submitting alphas with noise, variation of the same idea or fitting the data will not really help in improving the meta score.

- Diversifying the alpha pool by developing lesser correlated ideas (self-correlation<= 0.5)\u00a0 will improve your meta score.

- Develop alphas with high sharpe and try to keep the turnover less than 50%.
Meta Score will increase as you add value  to the pool where value comes from signals (alphas) that are different  (low self correlations) and performance is high. Meta alpha count is the  number of alphas that are included in the meta for calculating the meta  score.\u00a0We apply few tests on the entire pool of your submitted alphas  to filter them\u00a0for meta scoring. Based on these tests, the alphas are  selected for meta\u00a0scores. Metas can include the un-scored alphas too.\u00a0

", "id": "fbcce9eb-4729-44e7-b26c-3c0ffb15b48d"}]

## Do you measure risk of the Alpha just by the drawdown or are there other indicators? Is turnover one of them?

[{"type": "TEXT", "value": " All the performance parameters (IR, return, drawdown, margin, turnover)  all are important. You have to optimize all. (Mean Ret)/ (max  Drawdown)>1 is good.

", "id": "5c392eed-541a-41e6-af2b-9b0077156111"}]

## Does positive PnL mean a profit?

[{"type": "TEXT", "value": " Yes, it does not include transaction costs, which is why Turnover is  also important.\u00a0 For example, high PnL with high turnover may result in  much lower gain or even loss based on the full cost.

", "id": "a9bb5b54-53b3-434b-93ab-a3891522ad81"}]

## Does the simulation include trading costs?

[{"type": "TEXT", "value": " No. But turnover is a good proxy to judge transaction cost.

", "id": "7150d838-347e-446e-bf8a-173d234b4c23"}]

## I have felt a lack of information on the fitness of an Alpha. There has been a scant info in the help vids and the documents. If you can help out with the parameters that affect and change the fitness of an Alpha, I could improve the quality of my Alphas substantially.

[{"type": "TEXT", "value": "The fitness of an Alpha is a function of return, turnover and Sharpe. Good Alphas have high fitness. So please make sure the return and Sharpe are high and the turnover is low.
 Return: Annual Return = annualized PnL / Size. It signifies the amount you made or lost during the period observed and is expressed in %
 Turnover: It signifies how often one trades. Daily Turnover=Trading_volume / 2 * Size. Good Alphas have low turnover (Less than 40% is better).
 Sharpe: Sharpe = Avg(return)/Std_dev(return) over the observed time period. An Alpha should have a minimum Sharpe of 2 for delay 0 Alphas and around 1.25 for delay 1 Alphas to be eligible for Out of Sample testing.

", "id": "f6eeeb61-2142-403c-9915-36e677799583"}]

## I want to smooth the PnL curve such that the sudden fluctuations in curve are minimized. What factors shall I focus on to do so?

[{"type": "TEXT", "value": "

There can be some reasons for sudden jumps.

1) Because the Alpha values are frequently  changing from NAN to non-NAN or vice versa. You can use backfill  function to take care of this.\u00a0
 2) The other reason is that the Alpha values change rapidly from time to  time. Thus decay or taking average in Alpha formula can help you in  making the curve smoother.
 3) It also may be because of too much money on one stock and if the  stock value has a jump then the PNL will also have a jump in it. To  tackle this you can set stock weight in sim settings to non-zero value  between 0 and 1, preferably less than 0.1.

", "id": "42fe4708-9426-405e-8edc-5a038a6d0007"}]

## Is it necessary to have turnover <40% for the Alpha to be evaluated?

[{"type": "TEXT", "value": "  It is not necessary, but it is advisable. High turnover Alphas are hard  to trade in the real world where transaction costs are involved. \u00a0I  think you should focus on Alphas with decent Sharpe (>2.5) and  reasonable turnover (< 40%). And you should always remember to keep  trying out new ideas.

", "id": "d791e51d-9215-4e6c-9132-1fc332372b0c"}]

## Is the PNL shown for all 2000 stocks together or individual stocks?

[{"type": "TEXT", "value": " All the results (PnL, Sharpe, etc.) of all 2000 stocks together. The  cumulative PnL graph shows PnL of all shares in selected Universe  against time period.

", "id": "b489809e-44c1-470f-84c5-f95a6abdffad"}]

## The simulation is ranked by five levels, Spectacular, Excellent, Good, Average, Inferior. What are the criteria that an Alpha must satisfy?

[{"type": "TEXT", "value": "

There is an internal threshold which is configurable in terms of Sharpe.

However, the levels given above are another measurement independent of this.

", "id": "a6f9d5e0-7d02-4835-9f48-9ab28a231c9b"}]

## What are the characteristics of a good Alpha? How can I maximize my result?

[{"type": "TEXT", "value": "

Originality of idea is essential. The Alpha should be robust. An Alpha should have a minimum Sharpe of 2.00 for delay 0 Alphas and 1.25 for delay 1 Alphas to be eligible for Out of Sample testing. Along with having a minimum Sharpe, the alpha must fulfil the [Fitness criteria](\"https://websim.worldquantchallenge.com/en/cms/interpreting-results/alpha-performance/\"). Also make sure the Returns are high and Turnover is less than 40% and Drawdown should be kept to a minimum. It\u2019s not just about PnL, but also about the impact. Robust performance in liquid universes is needed. OS Sharpe, as well as the drop in performance of IS vs. OS Sharpe are important

Alphas with good performance are valuable to us. If you see an Alpha in the Out-Sample tab, you can be sure it is valuable.

Think of ideas in arbitrage view. Try different operations (decay, neutralization, etc.). Try new formulas instead of changing one formula. Don\u2019t try putting together nonsensical expressions. E.g.: adv20 + close, which is essentially volume + price which doesn\u2019t make sense.

Do not over-fit parameters. Doing this hurts performance

Note: Over-fitting here refers to changing the Alpha expression slightly in a nonsensical way, just to get a good IS Sharpe; e.g.: slightly changing the constants in the expression, changing the power of a parameter from 2 to 2.5, static flip sign of some sectors etc. This shouldn\u2019t be done since it will inevitably fail the OS test constraints.

", "id": "f1423c3e-627f-4790-84ab-a354922bafe1"}]

## What does the grey line in PnL graph indicate?

[{"type": "TEXT", "value": " Sharpe is indicated by the grey\u00a0line along with the cumulative profits graph if you\u00a0turn it on.\u00a0

", "id": "144bcf01-0c75-4e50-9538-97eb8f36c7c5"}]

## What is transaction cost? And is it important?

[{"type": "TEXT", "value": " Transaction cost is the amount of money one need to pay to the broker to  provide the trade. T-cost should be kept to a minimum and strongly  affected by the Turnover of alpha. Thus it is a good practice\u00a0to keep  the Turnover as small as possible when developing alphas.

", "id": "09da0533-e66e-4713-9f52-b361e553ef8d"}]

## Where's the Alpha output vector generated?

[{"type": "TEXT", "value": "BRAIN platform does not show the contents of the Alpha vector in the simulation result page.

", "id": "3ed7c66e-76f9-4a7a-8fc2-370d6fbe15ec"}]

## Aren’t we supposed to focus on short term trading? Why is the time interval of several years? Is that just for demonstration purposes?

[{"type": "TEXT", "value": "Such time frames are for simulation purposes and it helps us conceptualize what would have happened if this Alpha was put into a strategy during that time period with daily activity, for daily frequency trading.

", "id": "4003558b-404c-40ea-b9ca-5cf265dea278"}]

## Even after searching a lot, I am unable to find out more information about stock weights. Can you please provide more information about the same?

[{"type": "TEXT", "value": "

Alpha value for a stock represents the weight of that particular stock in the complete portfolio. This is how it works:

1) You use an Alpha expression to assign Alpha values for each stock in the universe.
2) Operations like neutralization, decay are then applied on these Alpha values as specified by the user.
3) These new Alpha values assigned to each stock are then converted to the amount of money allocated to a stock by scaling it to booksize.

This stock weight is thus nothing but the weight of the stock in the overall portfolio.

Let me give you a simple example, when Alpha = close.
Suppose you have a universe, with just 5 stocks (A, B, C, D,E) and on a particular date (20100104) they have the following close prices (in USD):

Instruments: A B C D E

close: 6 5 2 8 4

Now, you want to use the value of these close prices to calculate Alpha weights on the next trading day. You first start with the Alpha expression, which is Alpha = close. So you first make a vector of "close". i.e. (6, 5, 2, 8, 4). [Note: If your expression were Alpha = 1 / close, you'd have made a vector of "1 / close", i.e. (1/6, 1/5, 1/2, 1/8, 1/4) = (0.167, 0.2, 0.5, 0.125, 0.25). ]

Now you have the vector (6, 5, 2, 8, 4), this is not a vector of weights. A vector of weights needs to be normalized to 1. So we divide each element by the sum (= 25), so the sum of the elements equals 1.
So the new vector is: (6 / 25, 5 / 25, 2 / 25, 8 / 25, 4 / 25) = (0.24, 0.20, 0.08, 0.32, 0.16). The sum of this vector is 1. And this is our portfolio. We multiply this by the booksize (20 Million), and we get the amount of money we want to bet on each of the stocks.

This was the case when we have set Neutralization = "None". But this makes our strategy ride on market-risk. So, we select Neutralization = "Market". In this case again, we start out by creating a vector of "close" = (6, 5, 2, 8, 4).
Now we make it "mean-neutral", i.e subtract the mean (= 5) from each of the elements, making the sum of the vector = 0.
So the mean-neutral vector is: (1, 0, -3, 3, -1). You can see the sum of the elements is zero.

Now, in order to normalize, we need to ignore the sign and make the sum of elements = 1. So we calculate the sum of absolute values (= 1 + 0 + 3 + 3 + 1 = 8). Now we divide each element by this sum, giving us (1 / 8, 0 / 8, -3 / 8, 3 / 8, -1 / 8) = (+0.125, 0, -0.375, +0.375, -0.125).
Now this is a normalized mean-neutral vector of weights. We multiply this by the booksize of 20 Million USD to get the amount we want to invest on each of the stocks, where a positive sign indicates taking long position and negative sign indicates taking short position. Also, since the positive values add up to +0.5 and the negative values add up to -0.5, we end up investing 10 Million in long and 10 Million in short positions, making the strategy dollar neutral as required.

", "id": "e75b4aad-5659-402a-baab-de6bab08b1ad"}]

## I am wondering if it is possible to abort a running simulation?

[{"type": "TEXT", "value": " We have a cancel simulation button that appears after simulating an alpha.

", "id": "ac354378-4269-4e6d-9380-e887e235111c"}]

## What's the actual definition of signal? How much Sharpe increasing could be reached when improving the signal?

[{"type": "TEXT", "value": " Signal is a loosely defined term and so does not have any rigorous definition as such. In our talk we call any elementary model which on backtest shows a glimmer of a possible Alpha as signal. Filtering, weighing with different factors, improving the basic expressions of the signal etc. can help you achieve good performance improvement over the signal.

", "id": "d860a368-8222-4423-99b0-0283f1a1a6dd"}]

## When I type into the expression box, I see some suggestions. Do they come from my own history or from all users’ history?

[{"type": "TEXT", "value": " The textbox contains available data and operators: it provides the corresponding expression when you are typing.

", "id": "140435ff-f65f-4c7c-9250-0b0f7e72b458"}]

## Would it be possible to provide an API so that I can use OAuth or something similar to send an Alpha to the server, and get a json style response on how well it performed, so that I could then parse it and adjust my algorithm automatically?

[{"type": "TEXT", "value": "I am afraid BRAIN platform cannot support API to send an Alpha to server. Your suggestion is appreciated. We will forward to develop team for further discussion.

", "id": "2ce85870-2e18-4b88-b0fe-5c9f701299f4"}]

## Can a quant have a part-time internet based consultant position permanently? Or if one doesn't get promoted for full time, it means you are out of the position?

[{"type": "TEXT", "value": " Since this is new, there is no precedence.\u00a0 If someone is effective as a  part time Quant and wants to stay that way, it may be a good win-win  for all.

", "id": "e4274a8d-724b-4171-84b1-043076f78991"}]

## Do alphas backtested over a 10-year period have priority when used to calculate payout or increasing weight or a higher Discretionary Payment over alphas that are backtested over a 5-year period? Since an alpha backtested over 10 years is harder than 5 years would I receive a larger payout per alpha submitted under the new rule?

[{"type": "TEXT", "value": "No. Previously, the production system (after you submitted an alpha) always simulated your alphas over 10 years even though you submitted the alpha in a 5 year simulation system. Thus, nothing has changed from the production perspective. The new submission rule makes the alpha simulation on cloud closer to the test run internally on consultants\u2019 alphas and hence will greatly improve the PROD rate of each consultant\u2019s alphas. Therefore, while you are seeing a different simulation period, the overall process for testing has not changed, so there is no change in the payout either.

", "id": "f17d39ec-b753-4078-ba4b-79b99f938077"}]

## How is Prod rate affected? Is it possible for an alpha to be PROD_DECM when all subuniverse, weight, correlation in 10 years had been checked during alpha’s simulation?

[{"type": "TEXT", "value": " The PROD rate is expected to greatly improve as the new submission rule becomes closer to the production test. There is always a possibility that an alpha passing all the initial submission tests may fail the production test, but we anticipate that percentage to be much lower than it is currently. Such a failure is more likely to occur if the volatility of the alpha is high around the testing period especially for the alpha that barely passed the threshold.

", "id": "5987ba31-b9a5-4e34-b72c-f52d271d1965"}]

## How is the growth rate factor affected when applied to the new rules? The number of my alphas will likely reduce dramatically in the first 1-2 months after releasing new rules. Would my payout be reduced?

[{"type": "TEXT", "value": "No. We expect some difficulties for consultants at the beginning when they are familiarizing themselves with the new (more demanding) rule of submission, however, we know each and every research consultant is intelligent and resourceful and we have no doubt that each of you will adapt quickly. This change is essential for the continued growth and progress of BRAIN as we concentrate more on quality.
 Additionally, with the introduction of new Fast Expression simulation will increase the number of simulations at a higher order hence the total number of submission will be expected to grow over time. At the beginning, however, a short-time decline in the number of submissions is expected to be observed.
As all consultants are influenced in the same way, the payout is expected to be stable.

", "id": "4fa14470-c3b5-46d7-b231-5504676a449c"}]

## Can a user check correlation among his own Alphas?

[{"type": "TEXT", "value": "To check the correlation of your own alphas use the 'Alpha to list' and 'Alpha lists' tools available on Alphas page and Simulate page in the right upper corner.

", "id": "0f3c0ff6-b275-467b-9b18-4b20769b04b1"}]

## I have an Alpha expression which is showing GOOD Sharpe for both delay1 and delay 0; so i want to know are they correlated to each other?

[{"type": "TEXT", "value": " Correlation here doesn't mean correlation of formulas, but correlation of PnL graphs and hence can be found by comparing the PnL graphs of the 2 Alphas(one with delay 0 and other delay 1).

", "id": "d2fcd103-51b9-470e-add3-0c23dd0ed263"}]

## Is correlation being tested with all user’s Alphas or just with my Alphas? What is the correlation in out-sample testing webpage.

[{"type": "TEXT", "value": " It is tested and compared with your own Alphas until you become a Consultant. Then the whole alpha pool will be used to measure the correlation.

", "id": "295f42fa-2239-48c1-bca1-13f3d863b03e"}]

## When we improve an idea, we want to check its correlation with the original idea ASAP.

[{"type": "TEXT", "value": "In order to do so, please use the 'Alpha to list' and 'Alpha lists' tools available on Alphas page and Simulate page in the right upper corner. You can also use 'Generate Self Correlation' button to see the top 5 alphas submitted by you before.

", "id": "8dac732b-ac14-4dd1-8581-f648a2d67c24"}]

## First, what the difference between debt and liabilities defined in your system? and what is the difference between cashflow_sales and cashflow_operations? It seems that cashflow_operation has included cashflow_sales?
    Second, how to get the past values of some data. For example, cashflow is said to be quarterly cashflow. So, should the value of cashflow in the last quarter be written as ts_delay(cashflow,1) or as ts_delay(cashflow, 256/4)?
    Similarly, is the data, such as eps, bookvalue_ps, debt, asset, operating_income, calculated daily or yearly? For example, to get the value of assets last year, is it be written as ts_delay(asset,1) or as ts_delay(asset, 256)?
    Last, how can I get the data of  issued shares (Shares outstanding plus treasury share) in BRAIN platform?

[{"type": "TEXT", "value": "(1) Debt vs Liability
Liability means more than debt. For instance, deferred income tax, unearned rev blanks are also included in calculating liability.
(2). Cashflow_sales vs Cashflow_Operation
Cashflow_Operation is the cash flow provided by operations. Operation activities include not only sales activity but also the production and delivery of the company's product as well as collecting payment from its customers. This could include purchasing raw materials, building inventory, advertising, and shipping the product. Hence, Cashflow_sales is a part of Cashflow_Operation since it only provides cash flow generated by sales activity.
(3). You could use ts_delay(fundamental data, 60) to get last quarter\u2019s value since we could have 20 as work day for one month.
(4). Same question. This should be ts_delay(asset, 250). You could keep simple parameter like 20/60/250 to save your time rather than fit for parameter like 20 to 22.
(5). All available data are provided in the guide document and help section.

", "id": "ee363b0b-c57c-428e-9d6d-9a065e5a3896"}]

## How often does the data cache get refreshed?

[{"type": "TEXT", "value": "The data gets refreshed every week. Once it is refreshed, you will be able to work with the most recently available data.

", "id": "d01cb502-5291-4991-99f8-72365b227d29"}]

## I feel there are limited financial ratios, EBITDA, ROE, ROA, etc.  Is there any other financial ratio provided, or do we have to calculate it by ourselves?

[{"type": "TEXT", "value": "All the data series that are available currently are listed on the Help page. More are going to be released in the coming months.

", "id": "541ce43d-2679-4088-97c3-adff334cf807"}]

## I want to calculate EV according to the definition given here: http://en.wikipedia.org/wiki/Enterprise_value

[{"type": "TEXT", "value": "Enterprise value could be calculated as market cap plus debt, minority interest and preferred shares, minus total cash and cash equivalents. Data like minority interest is not currently available in BRAIN platform and might be added in the near future.

", "id": "7aab685c-b643-4744-b181-8acb3bcccd0f"}]

## I wish to use working capital in my Alpha . In the current assets, there is no provision to remove cash from it. Where is the cash equivalent /cash fundamental data?

[{"type": "TEXT", "value": "Other fundamental data such as cash & cash equivalents are not available currently and will be added in the next update in BRAIN platform. All available items have been concluded in BRAIN platform help page, and please utilize those to facilitate your Alpha idea first.

", "id": "9b6eefe6-b0ab-473e-8bb7-131c49f5db19"}]

## I wonder what's the underlying of the return variable for the Alpha expression? I mean, which stock's return is THE RETURN? By the way, is there any way to change the default underlying asset? Say I want use my Alpha to trade hi-tech companies like Google and Apple, but not retail companies like Walmart.

[{"type": "TEXT", "value": "BRAIN platform doesn't calculate returns for individual stocks or a user defined subset of instruments (stocks/contracts). Instead it calculates returns for a universe of liquid instruments. BRAIN platform gives you the option to choose from different universes (please read the FAQ for more details). Eg: If you choose USTOP3000 stocks, BRAIN platform will evaluate the expression for the top 3000 liquid stocks in the US region. Unfortunately, you cannot work with a subset of the universe or specify the industry/sub-industry. All you can do in this case is change the Universe settings using the Settings panel.
This is done by BRAIN platform to ensure that you make a robust Alpha model that is not biased to some stocks. This is a method of ensuring that your Alpha is market/industry/sub-industry neutralized.

", "id": "e24054e6-6581-47b5-886b-e952f4054343"}]

## In what way are we expected to use the fundamental data such as sales, cogs etc., as these don't change daily?

[{"type": "TEXT", "value": " You're right, some of that data will only be released quarterly, but technical data (equity related) will change regularly, so you can use a combination of data relationships.

", "id": "fd75d70b-3fbb-450c-9f14-cac838641dd7"}]

## Is option included in instruments?

[{"type": "TEXT", "value": " For the participants of WorldQuant Challenge this data is not available. After you become the Consultant there will be more opportunities to develop alphas.

", "id": "799cf501-1a90-4401-8668-c5f93ce7ea51"}]

## Is the volume vector weighted (i.e. a ratio of the traded volume of that instrument to the TOTAL volume traded on that particular day) or does it give the absolute value?
    In case it gives the absolute value, how do I sum up all the volumes to get the total volume of trade on that day?

[{"type": "TEXT", "value": "  You can use group_sum operator to sum up the volume of all stocks in a group, when the group is market, you can get the total volume of trade on that day.

", "id": "d10b15c7-a1ce-4865-a923-db3ffa54614f"}]

## Is there a way to use beta(risk)? Basically how to get the market data?

[{"type": "TEXT", "value": "You can use group_sum or the group_mean operator to calculate the total returns or the mean returns of the instruments in a specific group, and when the group is market, the output is just the market data.

", "id": "3c41104e-20a7-444d-9ec4-e35accf277e3"}]

## Is there some way I could download the data for the equity/future etc. and then work on it in Matlab etc. and then upload just the Alpha. I am unable to get the data.

[{"type": "TEXT", "value": "I am sorry but there is no way you can download data for equity/future at your end and upload the Alpha on the site.

", "id": "894d66ca-3c28-4037-a118-6be77c6c8083"}]

## The term eps - is it for one day or for a year?

[{"type": "TEXT", "value": " The fundamental data is updated once a quarter or once a year. It can also be updated more often when revisions occur.

", "id": "c6e2852d-2e6d-43f0-a89c-01c8643e72fa"}]

## What does NaN mean? Is it equal to zero?

[{"type": "TEXT", "value": "NaN stands for Not a Number. It is used to indicate results of \u2018invalid\u2019 operations like division by zero or if some data is corrupt or unavailable. If Alpha = NaN for some stock, then it means no position is taken on that stock. While if Alpha = 0 for some stock, then after operations like decay, neutralization etc. Alpha may have a non-zero value, resulting in some position being taken on the stock. In a variety of situations, if there is no Alpha value for an instrument, the Alpha is set to NaN. E.g.: if there is bad or missing data, the value is set to invalid.

", "id": "9b3968d7-4f41-4489-8ec9-9fd19c2237e4"}]

## What is the difference between covariance and correlation?

[{"type": "TEXT", "value": "

Answer: A Mathematical answer can be found here : [https://en.wikipedia.org/wiki/Covariance_and_correlation](\"https://en.wikipedia.org/wiki/Covariance_and_correlation\")

A statistical one is shown here:[http://surveymethodsaddicts.blogspot.sg/2008/09/what-is-difference-between-correlation.html](\"http://surveymethodsaddicts.blogspot.sg/2008/09/what-is-difference-between-correlation.html\")

", "id": "a3b13fee-f056-48be-b591-11c2485752c3"}]

## What reasons can cause a huge difference between the ROE and ROA of a company?

[{"type": "TEXT", "value": "Return on equity(ROE) helps investors gauge how their investments are generating income, while return on assets(ROA) helps investors measure how management is using its assets or resouces to generate more income. Though the two are measuring different management effectiveness, they are also closely related with the Dupont identity.
Since ROE, which euals net income divided by shareholders' equity, has unavailable items in BRAIN platform(we could support common equity currently), you could try to facilitate your Alpha ideas on ROA first. Other fundamental items might be added in the near future.

", "id": "d09b0122-0cb5-4f86-92ac-f92cd2c3294e"}]

## After I submit an alpha, how much time does it take for it to be reflected as the score on leaderboard?

[{"type": "TEXT", "value": "

Up to 1 hour.

", "id": "69b1dfe2-0e59-485f-8075-05a9bdaaef36"}]

## Does it mean that the score may decrease when we submit multiple alphas if performance falls?

[{"type": "TEXT", "value": "  Since the IQC score is based on merged PnL, it evaluates the performance (Sharpe, Turnover, etc.) when we distribute PnL with equal weight to each alpha. It is rare for performance to decrease after merging various signals, unless you submit multiple alphas that all have losses at a specific time. So in general, if you submit more alphas, the chances of final score decreasing is minimal due to diversification.

", "id": "9659494c-25f3-4d6a-ae63-e937b3e4c1e0"}]

## How can I explain the case where my score decrease after submitting a new alpha?

[{"type": "TEXT", "value": " As the scoring is based on merged PnL of all submitted alphas, the score can decrease if this new alpha is not helping the pool. For example if you submit low Sharpe ratio and high turnover alpha most likely your score will decrease.

", "id": "14405983-19dc-4db2-bea7-2da34556a2ae"}]

## If it takes up to 1 hour for submitted alpha to be reflected on the score, how come sometimes testing status still shows N/A 1 day after submission? Is it server delay?

[{"type": "TEXT", "value": "The IQC score displayed on the leaderboard depends only on IS performance so it is updated more frequently. The testing status of each alpha is based on OS performance, hence the alpha test result is updated less frequently.

", "id": "2c03634c-6c4b-45a3-8dc2-afd44fdc531a"}]

## Is the leaderboard score the final score and rank for Stage 1? If not, is there an additional testing used for final evaluation at the end of Stage 1?

[{"type": "TEXT", "value": "

As it is described above there is public score which everyone can see any time and there is a private score which will be revealed in the end of the stage . Each of these scores will have 50% weight for Stage 1 evaluation.

", "id": "49d03e84-77ec-414e-87b9-a1a1cdd1d3d5"}]

## Is there a way to check each score of an Alpha aside from the team score?

[{"type": "TEXT", "value": "No, you can\u2019t check score for each Alpha since it is not defined. IQC Scoring algorithm is based only on merged PnL of the team\u2019s Alpha pool.

", "id": "acc25f0f-69a5-4ca5-bb7f-ffab452afc32"}]

## Would it be beneficial to develop alphas for a long time and submit all on the last day of IQC Stage 1?

[{"type": "TEXT", "value": "If you submit alpha earlier, you can test the idea for a longer period, so it may be more beneficial. There is also a possibility that a lot of registrants will submit alphas on the last day so BRAIN platform simulation speed may be slower than usual.

", "id": "e524ea3a-18ff-4b79-8ae4-44dd2f5991c1"}]

## I am not very clear about the data construction of Out-sample. Do you mind tell me some specific things of Out-sample data?

[{"type": "TEXT", "value": "Instead of a fixed start and end date for In Sample (IS) simulation, the 5 year IS simulation starts 6 years before and ends 1 year before the present date. This is a rolling 5 year window which changes every day. The most recent year of data is hidden and used for scoring and testing. Statistics shown in the OS Tab of My Alphas page will be populated as data becomes available by each passing day.

Keeping the last year\u2019s data hidden completely leads to higher confidence in the OS performance of alphas and their scores. It will also protect against selection bias, and may help expedite usage of research consultant alphas in production strategies.

", "id": "999ebd8b-2297-40a9-9d5e-e1d8ec1c1104"}]

## What do in sample and out sample mean? And are their neutralizations the same?

[{"type": "TEXT", "value": "

In-Sample - This section has a summary of the performance of Alphas  up to the date they were first simulated on. I.e. In-sample performance  of an Alpha is the performance obtained from back testing on historical  data. This is the performance you see on the results page when  simulating an Alpha.

Out-Sample - Out sample performance of an Alpha is the performance after  its date of submission. It is the \u2018real world\u2019 performance on Alpha.  The \u2018Out-Sample\u2019 tab shows the performance over various time periods.  For selected Alphas we run out of sample simulations, the results are  shown here. The data displayed for these Alphas are - Name, Test Date,  Sharpe over various periods(e.g.: Sharpe30 is for 1 month and Sharpe 360  is for a year), Total Out Sample Sharpe, Correlation Stats (with your  own Alphas, threshold being 0.5 to 0.7) and Rating (on a scale from 0 to  100).

The Neutralization setting for your in-sample and out-sample Alphas are the same.\u00a0

", "id": "7b76d654-d5de-4335-ade7-fce3a409306d"}]

## Why do my Alphas in out sample show NA, is it negligible or is there some other issue?

[{"type": "TEXT", "value": "

Users will not be able to see all OS statistics shortly after the first OS simulation is done. They will have to wait for these statistics to be calculated as new data becomes available daily on a rolling basis. For example, the Sharpe125 field will be populated only after 125 trading days have elapsed since the alpha was submitted for OS Testing

", "id": "eaf41841-4502-4f68-a889-7ea991f9db10"}]

## "If the user specifies Neutralization, the ‘raw’ values (i.e., the values of the expression) are not used directly, and that operation is applied to calculate the final values." It is very hard for me to understand this sentence; could you please give me an example?

[{"type": "TEXT", "value": "Suppose you make an Alpha without specifying neutralization and it wants to buy $100 of Google and to buy $50 of Microsoft. Neutralization says that we have to be long-short neutral to the market as a whole. Now if market neutralization is set for the same Alpha, it would take the average ($75) and subtract from each position, so the final position would be to buy $25 of Google and to sell short $25 of Microsoft.

Let's say you have an Alpha signal which gives weight to all the instruments (according to your Alpha idea) and applies industry neutralization. By industry neutralizing, BRAIN platform separates each industry and reduces the average of the weights from all the instruments in that industry. You can do the same for sub-industry too.

", "id": "489efb1b-683b-44e2-8468-5c80cf17fc25"}]

## According to CAPM, R[i]= B(R[m]) +Alpha is this the same Alpha that we are trying to calculate here? Is it related to Long-Short Market Neutral Strategies that we ignore the beta and just concentrate on Alpha or something else?

[{"type": "TEXT", "value": "WorldQuant's definition of Alpha is quite different from what you may have studied (the one related to CAPM).
In BRAIN platform, an 'Alpha' refers to a mathematical model or strategy, written as an expression, which places different bets (weights) on different instruments (stocks), and is expected to be profitable in the long run.
In simple terms, it creates a vector of weights, with each weight corresponding to one of the stocks in the selected universe. These weights may or may not be market neutralized, as per your neutralization setting (market, industry, sub-industry or none).This creates a portfolio for each day in the simulation period, which can then be used to calculate that day's PnL.
'Alpha' is just a symbolic name and should not be confused with the common definition of Alpha which says that it is a measure of excess or abnormal returns over and above the returns predicted by a strategy (like CAPM).

", "id": "6221dfe1-d1d8-421e-9044-1f1a2cf38666"}]

## Can you explain neutralization in lay-man terms?

[{"type": "TEXT", "value": "Neutralization is a way to go neutral in $ sense, ie. Allotting the same amount of dollars in long (buying the stocks) and short (selling the stocks). Hence your total investment(called the Booksize in BRAIN platform) will be split down the middle \u2013 half for short and half for long. That way, when the entire markets goes up or down, you are less exposed to risk.

", "id": "5b2e36bf-137c-4cd1-a50c-9f9974b9c729"}]

## Could you please explain me the working of neutralization option? I'm not clear with the option and why we have to keep it none before using.

[{"type": "TEXT", "value": " Neutralization option is really helpful in reducing the risk. Neutralization is done by subtracting the mean of Alpha values of a group from each of the Alpha values for that particular group. After neutralization the values are long and short equal and hence they are more resistant to market crisis situations as there is no bias towards long or short side.

Neutralization is an operation in which the raw Alpha values are put into various groups, followed by normalization (the mean is subtracted from each value) within each group. The group can be the entire market. Or the groups could be made using other classifications like industry or sub-industry (based on SIC and NAICS codes). This is done so as not to bet in the direction of the chosen group, but only relative stock future return. As a consequence of neutralization, the entire portfolio carries neutral position (half long, half short). Doing this will guard the portfolio from market shocks and eliminate some kinds of false signals.\u00a0

I understand that this would raise questions like 'What\u2019s the difference between the three market neutralization methods? How do you decide which one is better?'
Market neutralizations determine which groups are used for neutralization of Alpha values \u2013all tickers that belong to the same sub-industry, or industry, or simply use the entire universe as one group for this purpose. As for the second question, the correct choice depends on the logic / formula used by the Alpha so there is no specific answer. The results should indicate what to go with.

", "id": "5224968d-1dcc-414f-8136-0a9b30e57129"}]

## Do not consider risk when constructing portfolio?

[{"type": "TEXT", "value": " Operations like decay and neutralization help in reducing the risk by smoothing the Alpha values and making the portfolio market neutral.

", "id": "66c4d901-87dd-4dc1-b7b9-1b24bcf48dd7"}]

## Does neutralization always reduce standard deviation of returns?

[{"type": "TEXT", "value": " Standard deviation of return is a measure of risk. Typically neutralization always reduces risk.

", "id": "d0c18b63-6d08-41e0-925d-d613df718ab2"}]

## I know neutralization is subtracting from an array its average, but how does neutralization affects our sharp ratio? Does neutralization decides whether or not to sell in this day?

[{"type": "TEXT", "value": " Neutralization is actually a risk control mechanism. By neutralizing with respect to a group (sub-industry, industry, market), you are trading spreads within the group and not having any exposure to the group itself. So, sometimes, it can help improve performance. Like sub-industry neutralized Alphas give better performance than other Alphas in most cases.

", "id": "50707171-9471-4c06-8e2b-172f9e2914c3"}]

## Is it necessary to use 'no' neutralization in simulation settings while testing Alphas? I am generally able to get good Alphas only for sub-industry neutralization.

[{"type": "TEXT", "value": " Market neutralizations determine which groups are used for neutralization of Alpha values \u2013all tickers that belong to the same sub-industry, or industry, or simply use the entire universe as one group for this purpose. We recommend long/short 1:1 to make sure it is market neutral. Setting neutralization = none is long only which is harder to get good Sharpe and easier to get highly correlated (since they all have betas).

", "id": "fdca3177-d9ce-47f7-ae91-c278e377b19e"}]

## What’s the difference between the three market neutralization methods? How do you decide which one is better?

[{"type": "TEXT", "value": " Market neutralizations determine which groups are used for neutralization of Alpha values \u2013all tickers that belong to the same sub-industry, or industry, or simply use the entire universe as one group for this purpose. As for the second question, the correct choice depends on the logic / formula used by the Alpha so there is no specific answer. The results should indicate what to go with.

", "id": "5042c718-8da7-44b3-9b3d-746afabc31f8"}]

## When Alpha expression “1” is entered, it returns nothing for every universe. How does one get rid of the NaNs?

[{"type": "TEXT", "value": " If you look in the Settings dropdown (hover over the gear-shaped icon on the right of the top navigation bar to see this), you'll note that the default neutralization settings is \u201csubindustry\u201d. This is why you are seeing NaNs when you use "1" as your expression - the neutralization operation ensures that no position is in fact taken at any point. If you change this setting to "none", you will see the expected results.

", "id": "cda3b0a9-ff79-4384-9468-bd655dcc8db9"}]

## Will good Alpha be developed without neutralization?

[{"type": "TEXT", "value": " Its possible but not recommended because not neutralizing exposes the model to the market.

", "id": "4c4b2897-1628-48d9-93c1-e7a06e7c7250"}]

## Can we see the ranking or rating of our Alphas in Out sample test?

[{"type": "TEXT", "value": " You can sort by kinds of performance filed in OS testing such as OS Sharpe, Turnover and so on.\u00a0 Currently we have not provided total ranking for Alphas.

", "id": "3a9264db-3852-463e-a1bc-0e804a683f6b"}]

## For Alphas that get selected for Out- Sample testing, how soon can I see statistics?

[{"type": "TEXT", "value": "You can see the statistics in about a weeks\u2019 time, because it is done over the weekend.

", "id": "5b0aaf36-6808-460e-8830-63964c736a51"}]

## How I can get performance for out of sample data?

[{"type": "TEXT", "value": "

Certain Alphas based on successful performance will be testing with out of sample data

", "id": "7f1278f4-4f87-4891-b357-cc24448c1c7c"}]

## How can I increase Sharpe ratio?

[{"type": "TEXT", "value": " Sharpe is a function of returns and volatility. Improving your model to increase the returns or decrease the volatility will improve Sharpe. You can also try different operations, like Sub Industry neutralization, or changing the parameters or adding a couple of conditions (but not too many, as it will result in Over-fitting).

", "id": "d61d3816-071f-42bb-84e9-98a1e25bf4da"}]

## How does the universe affect IR of an Alpha?

[{"type": "TEXT", "value": " Answer: Information Ratio (IR) of bigger universes should be better than smaller ones. But this is not always true. Some Alphas perform better for large stocks, for reasons such as:
a) Data of large stocks is cleaner. I.e. Data has fewer jumps.
b) Behaviors of big stocks are different from small ones.

", "id": "919246d6-bc30-4fa2-8d8f-5adba42d4def"}]

## How heavily is originality of idea weighted vs trading/technical understanding?

[{"type": "TEXT", "value": " Both are heavily weighted--we do perform correlation tests to check for originality of idea. It\u2019s best to move on to a new Alpha idea than sticking with the same idea and trying to improve it. Over-improving an idea will result in overfitting of Alpha signal \u2013 which will result in poor OS Sharpe.

", "id": "508f7c1b-ff85-4696-b816-10e75807e946"}]

## How to combine Alpha signals more effectively to reach a 1 + 1> 2 result?

[{"type": "TEXT", "value": " Don\u2019t combine signals based on backtest. You may want to look at signals which complement each other at the idea level together.

", "id": "0d7d6be2-bf69-4941-becf-582ed349549b"}]

## I am curious how to evaluate my OS Alphas? For the OS Sharpe, above which level, the Alpha will be considered as a "good" one?

[{"type": "TEXT", "value": " The criterion for entering an Alpha into Out of Sample testing is that the Sharpe ratio should exceed a certain threshold.\u00a0Correlation is also important to understand the idea. We already have thousands of Alphas. If your Alpha's correlations with existing models are too high (>0.7, for example), your model will probably not add value. From the correlation you can also understand the nature and category of your Alphas. So keep your OS Alpha with high Sharpe and low correlation is helpful.

", "id": "00dc6fab-d4ef-4ec2-8bad-54dbc75c861f"}]

## I can insert two Alpha expressions using a condition expression?

[{"type": "TEXT", "value": " Yes, but beware that too many conditions would result in overfitting (as explained before) and therefore, poor OS Sharpe.

", "id": "ffafba82-7b8a-4d96-8d0a-9d92f0b04049"}]

## If I change the value of decay from 1 to 5 for the same expression, does it mean I tried to over-fit the parameters?

[{"type": "TEXT", "value": "

Changing the decay from 1 to 5 is okay, but not say, changing it from 5 to 6. There is no 'exact' definition, but you should keep in mind that it is not over-fitting if it makes sense to you. If you think increasing the decay would help your Alpha's performance then you should increase it. But trying to choose between decay=5 and decay=6 is probably over-fitting.

To add to the above answer you should always check how reliable your parameters are by doing a sensitivity analysis over the parameter just to ensure that the current parameter value is not over-fitted as it may be the case that at some random parameter value the Alpha suddenly starts working which may not work in out of sample.

", "id": "e70abd05-74b9-4f70-960f-fb41b72fd2b0"}]

## When the BRAIN platform was upgraded, many of my Alphas got low performance than what they were performing before upgrade. This will be an advantage for those who created Alphas before and disadvantage to the others. Is there any system to check this anomaly?

[{"type": "TEXT", "value": "The performance of Alpha does not change with different BRAIN platform versions. However, the period of simulation might change. For example, the period of In-Sample simulation is from Feb, 2008 to Mar, 2013. This period might change in a different BRAIN platform version, but your Alpha's performance for the same period would never change. If you do see a significant difference in performance across different BRAIN platform version (but observing during the same period), please let us know the concerned Alpha.

", "id": "c39545e1-8d26-4803-9d87-1026e2bda3f7"}]

## Can you explain what decay is again?

[{"type": "TEXT", "value": " Combine today's Alpha value with previous days' values, decay is a smoothing operation.\u00a0 A linear decay will transform the Alpha vector into one that is the average of the Alpha values over the last X days. It is used to reduce turnover. It smoothens the changes in your position across days.

", "id": "dd6af972-86b7-44ec-a78d-094ef6702a80"}]

## Could you explain more about the Rank function? Why it is between 0 and 1? And how to use the return of this function?

[{"type": "TEXT", "value": "Let's say you have a vector of values. Rank will sort them and assign uniformly values between 0 and 1 based on its rank in the list. So the values of the resultant vector (i.e. Alpha weights for each instrument) will be in decimal \u2013 kind of like percentage. Depending on the rank of weight corresponding to each instrument, investment will be allocated to the vector (long and short) and a PnL will be generated. You could say Rank defines depth of investment allocated for each instrument (be it long or short).

", "id": "9a2a0f71-b2e3-4637-9695-be26c393b377"}]

## Do you recommend greater decays in Alpha or do normally shorter decays lead to better Alphas?

[{"type": "TEXT", "value": "It depends on the idea. Your final turnover must be <= 40%. Large decays smooth the signal. But all smoothing leads to some information loss from the signal.

", "id": "2099bef0-7a93-4a7d-ab8a-fc7415f4a481"}]

## I have made some Alphas where I am getting a Sharpe ratio of above 2.9 but my turnover tends to close to 90%, Can you please suggest me ways to reduce it?

[{"type": "TEXT", "value": "You should try to keep turnover below 40% in your Alphas. One of the ways to reduce turnover is to use Decay simulation setting. If your Alpha is changing very rapidly, using a decay setting equal to N days would average out the Alpha over N days, and reduce the daily turnover. However, the performance could change substantially.
Another way could be to use "Rank" function on your Alpha.

", "id": "e6d0e8c5-6085-4c72-8c5a-2cc51e03fcde"}]

## Can you go through the concept of delay again with an example?

[{"type": "TEXT", "value": "If Alpha=-returns and it is delay 1, then the Alpha vector is dependent on yesterday's return. If the delay is et to 0, then the Alpha vector is dependent on today\u2019s return too.

", "id": "e056f32e-f5f5-4844-800f-191ff0f04f49"}]

## Can you please explain the actual effect of this function Pasteurize(x) on an array?

[{"type": "TEXT", "value": "

Pasteurize(x) takes an array as input and replaces all the values which are INF in it by NAN. It means that if your Alpha is 1/returns and if returns are 0 for a day then it will give INF value to the stock and as it is not advisable to give high weightage to only one stock pasteurize(Alpha) can and should be used to replace that INF values by NAN values. A NAN value implies that no weight will be given to that stock. Please note that Alpha=NAN is different from Alpha=0 as a 0 Alpha value can be affected by operations like decay and neutralization and thus end up with non-zero value, but a NAN Alpha value will remain NAN even after the operations.

The other important feature of pasteurize - is to set NaN to the instruments that are not in the Universe defined by Settings. Imagine, that instrument x at some point of time belongs not to TOP 1000 but to TOP 2000 Universe. Then pasteurize(x) will set NaN to this instrument. This feature might be very useful when you are working with group operators that doesn't imply pasteurization as operator may be using all available instruments instead of those defined by Settings.

", "id": "b4855f64-335c-4740-a34e-4a8d8b53603e"}]

## Could you give me the exact formula which defines ts_moment command?

[{"type": "TEXT", "value": "

The function ts_moment(x, d, k=0) calculates the kth central moment of the vector x, over the last n days. It is calculated as follows:
Let m = mean of x over last n days = (x[date] + x[date-1] + ... + x[date - (n-1)]) / n
Now ts_moment(x, d, k=0) = mean of (x - m)^k over the last n days = ( (x[date] - m)^k + (x[date-1] - m)^k +... + (x[date - (n-1)] - m)^k ) / n

Observe: Setting k = 2, gives variance of x over last n days. Setting k = 3, gives skewness of x over the last n days and so on. Kth Central Moment is just a generalized concept.

", "id": "edef720c-dde0-4dad-b2a2-2cc4feb734e7"}]

## Could you please explain Smoothing Factor in Exponential Decay Function? Was that the bigger the smoothing factor is the faster the variable decay?

[{"type": "TEXT", "value": "

Exponential decay function over the past d days, where facctor is the smoothing factor.

ts_decay_exp_window(x, d, factor = 1) = (x[date] + x[date - 1] * factor + \u2026 + x[date \u2013 (d - 1)] * (factor ^ (d \u2013 1))) / (1 + factor + \u2026 + factor ^ (d - 1))

From this definition, it is clear that 0 < factor < 1. For if 'factor' was greater than 1, then more weight would be assigned to older values than the newer ones. For example, x[today - 1] would be assigned more weight than x[today], which means more recent information is given less weight, and this is probably not what you'd like.

If you decrease 'factor' (bring it closer to 0) then the function would decay faster, assigning much less weight to older value. If you increase 'factor' (bring it closer to 1) then the function would decay slowly. Setting factor = 1, would mean no decay, all terms would be assigned equal weights and it would be like taking a simple arithmetic mean of all the values.

", "id": "3bd11bbf-7e80-4c27-a5eb-27399cc813bf"}]

## Difference between delay and decay in terms of no of days?

[{"type": "TEXT", "value": "ts_delay(close,5) means the close price 5 day ago. Whereas ts_decay_linear(close,5) is the time averaged value of the close price over the last 5 days.

", "id": "47660af6-d685-4fd3-8471-af61ad01fbaa"}]

## I am unable to use the IndNeutralise option. Could you please raise an example of y in IndNeutralize(x, y)?

[{"type": "TEXT", "value": "Suppose you want to neutralize returns over industry, then you can use: IndNeutralize(returns, industry)
If you want to neutralize over sector you can use: IndNeutralize(returns, sector) .. etc.

", "id": "d92166e2-ed2c-4ba2-a381-96b1eaf355fb"}]

## I can find only a few mathematic functions and cumulate APIs here, are there any more resources can help us know much more about the Brain platform system and the RF tactics.

[{"type": "TEXT", "value": "All the functions and data available for use on Brain platform are given in the 'Available Data and Operators' section. Please refer our Examples in 'Alpha Tutorials' section to learn how to use them. We are working on releasing more functions, datasets and asset classes soon. We will also be releasing the Help Documentation that will cover Alpha research, more examples and illustrations. We will keep you updated on the same.

Until then, please feel free to send us a ticket if you have suggestions on how to improve Brain platform(eg: for a particular function/new features/etc. to be added) or technical issues faced while using Brain platform.

", "id": "ff247b42-0bb8-4606-b47e-4d83c399955d"}]

## Is it necessary for Alpha expressions to be one liner unconditioned? Depending on previous performance, can be have different sets of Alpha expressions for different performances and if yes , how to write those type of conditional Alpha expressions in the Brain platform simulator.

[{"type": "TEXT", "value": "

You can like conditional Alpha expression using the conditional operator <condition>?<expr_true>:<expr_false>. It can be used to define if..else.. like constructs.
For example:
close > open ? 0.5*(high - low) : vwap - close
this is equivalent to
if (close > open) then
 Alpha = 0.5 * (high - low)
else
 Alpha = vwap - close.

You can combine multiple conditional operators, if you want nested conditions. For example:
close > open ? (high / low > 1.25 ? close - open : 0.5 * (high - low) ) : vwap - close
this is equivalent to:
if (close > open) then
 if (high / low > 1.25) then
 Alpha = close - open
 else
 Alpha = 0.5 * (high - low)
else
 Alpha = vwap - close

", "id": "f0c84356-33f4-4363-9ccd-f937ad8819db"}]

## Is it possible to construct an Alpha with 3 conditions? e.g.
if (close>x) then a;
if (close>y) then b;
otherwise c;

[{"type": "TEXT", "value": "

Yes, you can use the conditional operator, <condition> ? <expr_true> : <expr_false>, to create nested conditions in your Alpha expression.
For example:
 close > x ? a : close > y ? b : c

", "id": "6d60b530-3ae8-445f-9d48-3b5f9195f130"}]

## Please explain Decay and Delay in detail.

[{"type": "TEXT", "value": "Delay determines when your strategy takes positions on stocks, that is at what time during the day does it decide to buy and sell.
Delay = 1 means that positions are taken in the morning just before market open, i.e. your code is run every day just before market open and can use data (like open, close, high, low) up to the previous day.
When Delay = 0, the positions are taken in the evening just before the market closes, i.e. your code is run every day just before market closes and can use data up to that day itself.

Since Delay 0, uses more recent information it is likely that a Delay 0 strategy would have better performance than a similar Delay 1 strategy, however this may not always be the case.

Decay is an operation that is applied to your Alpha's output.Decay, is used to "smooth" or average out your Alpha values. For example if you set Decay = 5, then your Alpha value is calculated using weighted sum of previous 5 day's Alpha values:
Alpha_modified = (5*Alpha[today] + 4*Alpha[today-1] + ... + 1*Alpha[today-4]) / 15

", "id": "59f272ee-8e2f-4fae-a583-6d15da24f556"}]

## The programming does not provide a function for exponential calculation. Would you please add exponential function in as there is logarithm function?

[{"type": "TEXT", "value": " We have an exponentiation operator ( ^ ), which you can use. For example if you want to calculate " e (Euler's Constant) to the power x " you may use: (2.71828 ^ x), in your expression.

", "id": "0be909d3-4d05-463a-9b1e-14f9b9615730"}]

## What is the meaning of x and y in min(x,y)?

[{"type": "TEXT", "value": "Min(x,y) calculates parallel minimum of vectors x and y (similar to the pmin function in R). This takes 2 vectors as arguments and returns a single vector giving the \u2018parallel\u2019 minima of the vectors. The first element of the result is the minimum of the first elements of all the arguments, the second element of the result is the minimum of the second elements of all the arguments and so on. eg: min(0.5*(open+close), high)
This expression takes the parallel Minimum of vectors high and the vector resulting from halving the sum of vectors open and close.

", "id": "bb34f172-7043-4dde-a4bd-6cb04ad50a6e"}]

## Can you please explain Universes top 2000, top 500, etc.?

[{"type": "TEXT", "value": " Universe is the vector (or basket) of instruments that are the most liquid in the market. Top 500 will be the top 500 volume based instruments. Top 2000 is a basket of 2000 most liquid stocks in the instruments in the market. TOP500 is therefore a subset of TOP2000. Same definition applies for the rest of the universes \u2013 TOP1000, TOP3000, etc.

", "id": "89492821-6e78-4502-9c84-92c9212f26a7"}]

## If I use universe 3000, do I trade all the 3000 equities? Can I choose some of the 3000?

[{"type": "TEXT", "value": " Yes if universe TOP3000 is chosen then approximately 3000 stocks are traded. You can choose some of the 3000 by assigning NAN values to the ones you not want to be chosen, but there should be a logical reason behind such Alpha assignment.

", "id": "224a2ca4-45fa-492e-81cd-af4e54c6119f"}]
