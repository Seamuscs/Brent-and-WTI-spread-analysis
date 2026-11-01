# Brent-and-WTI-spread-analysis
Analysis of the Brent-WTI crude oil, the two major oil benchmarks, spread (1987 to 2026) in Python including regimes, structural breaks and statistical analysis.

# Background

Brent, named that as it comes from the Brent Field in the North Sea, serves as a benchmark price for the majority of crude oil traded around the world. The two biggest benchmarks in the world are Brent and WTI, standing for West Texas Intermediate, and a sizeable portion of the world's oil is priced at those benchmarks, there are others but it makes sense to compare the two biggest and also because they are very similar types of Oil. Brent is a sweet type of oil, meaning it has a low sulphur content, WTI is also sweet but to a greater extent, though close enough to warrant comparison, Brent being around 0.4% and WTI around 0.24%. The amount of impurities determines how much processing is required to be done before refining the crude oil, sweet oil means less processing but will be sold at a premium for the same reason. They also have similar API gravity, both are very light, with WTI being the lighter of the two. API gravity is a measure of how heavy the oil is compared to water, higher than 10 means it floats and is lighter than water, less than 10 being the opposite. Brent averages around 38 API and WTI being around 40. So they are similar types of oil but are transported in different ways. Brent is drilled from the North Sea, meaning it can directly be transferred off the offshore oil rigs and transported across the world. On the other hand, WTI is inland and so requires higher transport costs to move it to the coast if it was to be traded intercontinentally. You can assume the spread is therefore pretty uniform, spread being the difference in spot oil price. The question we want to answer is, does the spread diverge? The answer is almost certainly yes, Real word events influence how oil is traded, so the follow-up question is, if so why does it diverge and when? What key events can we say causes the spread to diverge?

# Data

Both Brent and WTI spot prices can be found on FRED, the Federal Reserve Bank of St. Louis, for free and mostly daily. They can be downloaded as csv or excel, though I chose to use csv specifically to use pandas. It should be noted that not every day was traded on, nor did they start recording at the same time. The data must be cleaned before we can actually plot and analyse. This is where python and pandas is useful.

# Methodology

Part I:
The first job is clean the data. I cleaned the data using pandas, indexing the data by date and removing days they did not have in common. I then removed any day that was not traded on by either benchmark, so no NaN data in the data frames as they cannot be plotted. The next step was to then plot the spread. Though, you will see I plotted both benchmarks too as I wanted to illustrate where the spread comes from and identify key events in the historical data. I then calculated the mean and standard deviation using the describe function. I removed one of the limitations of the model by adjusting the spot prices for inflation by using the purchasing power index and calculating the spot prices value in today's dollars. The next step is to calculate a z-score using the historical mean and standard deviation. This shows us how far any spot oil price deviates from the historical mean as a multiple of the historic standard deviation. 

Part II:
I imported futures data from yahoo finance. Sadly, it does not date back as far as our original spot prices but there is enough data to work with. I cleaned the futures prices of Brent and WTI to then plot their spot and futures together to show the difference and the spread between the spot price and its future. After that, I imported the ADF test and the KPSS test. Each test reinforces the outcome of the other test which is why I used both to test for a stationary time series in our futures spread. The next thing to do is apply an Ornstein-Uhlenbeck process.

Any and all findings can be found within the document.

# Appendix

For those who are more interested in the statistical methods I will include an appendix in the repository that will detail necessary knowledge of stochastic processes and derivations of the statistical tests I used in Part II.
