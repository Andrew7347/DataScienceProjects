# Portfolio Optimisation and Risk Modelling
This project Involves analysing **Institituional** level Cross-Product Portfolios subsets.
It replicates the work of asset managers in large institutions such as Blackrock, Fidelity etc
There will be applications of mean-variance optimisation, VaR calculations, stochastic simulation, and GARCH modelling — all implemented in Python.
Alongside this...  Included within the preliminary analysis include 

Return and factor attribution (Brinson and factor-based),
Factor exposure estimation (multi-factor regressions, rolling betas),
Testing predictive signals  (momentum/value/quality) alongisde (t-tests, bootstrap, p-values, information ratios),
Liquidity and turnover analysis 
Reporting / dashboards / technical memos


The entire composition of this document is exclusively attributed to showcasing discrete steps within the project while simulataneously showcasing various soft skills used within the project.
-

- Critical Thinking
- Abstract Thinking
- Analaytical thinking
- Problem solving etc.

---------------------------------------

Firstly and most fundamentally we must emphasise what our goals are, what are we trying to do? etc
and so I started the project with the following critical questions...

What is data science? What is it trying to do?
How does it do it? why does it do it? what goals does it have?

After answering these questions, it was fundamentally inherent that understanding the needs / Wants of the business guided the entire process of Data science.
Therefore, We can deduce the following universal question. 

**What is the inherent need of the business I am in? What problems is it trying to solve to close those needs?**

After careful critical thinking the following conclusions were reached... 

The inherent need in asset management is:
We operate within the capital markets. We need to design the BEST investment products for our clients to maximise returns for them, while minimise risks, Maximise our commission and profit, maximise client retention, maximise client onboarding and AUM.

Ensuring we sell products within the capital markets with the best returns, lowest risk, most transparency, ESG factors ETC (Dependig on the needs of the capital that is buying our products) is ESSENTIAL to sell as many of our products as possible. 

- **Maximizing Growth** (How can we manage our current assets or create new portfolios to maximise returns?)
- **Minimizing Risk** (how can we effectively risk manage? minimise risk for the given portfolio given our clients appetite)?
- **Attracting and Retaining Clients** (How can we retain clients by building trust, communicating and ensuring their money grows stress free?)
- **Operating Efficiently** (what inefficiencies exist? How can we improve how we run the business, carry out research etc?)
- **Innovating and Adapting** (How is new technological innovations, demand for ESG etc shaping the capital markets? How can we adapt to new products?)
- **Building Amazing Relationships** (How can we streamline and maximise the client / stakeholder strength?)
- **Complying with the Law** (What are the current legal frameworks surrounding this, how can we ensure compliance throught our departments?)

  Now that we understand the inherent needs of the business we can guide our data analysis to answer questions that EXPLICITLY and DIRECTLY tackle this problem.

  Now that we know the inherent questions we need to answer to satisfy the needs of the business... We can begin our goal orientated data collection.

  ---------

  DATA COLLECTION:

**First and foremost I need to collect data regarding my project to be able to carry out the analysis.**

inherent needs and wants determinations were implemented within preceding info situated above this log. showcasing the goals and guiding postulations for the projects actions. 

To carry out portfolio Analysis, A portfolio is required.

However, What form, type, composition, information etc regarding the portfolio is another matter.

We shall dive into this directly within this section while simultaneously collecting data.  

The criteria I have chosen for choosing the portfolio comprises of the following…

- Institutional Grade
- Diverse (Equities, Commodities)
- Publicly available information (quarterly reports, SEC filings, holdings etc)
- Must be actively managed (Implies risk and return management required, replicating asset management roles)

  After reviewing numerous institiuional grade portfolios I have succesfuly opted for the...

 **Blackrock Global Allocation Fund (Malox)**

 Next steps are...

- Extract Data from the Blackrock website
- Extract Data Bloomberg Terminal

  <img width="1684" height="487" alt="image" src="https://github.com/user-attachments/assets/935a02e9-fa07-4d6f-90da-96760b7f463c" />


I have successfully extracted A plethora of relevant data within the Blackrock website

- Exposure Breakdowns (Asset Class, Sector, Region, Currency)
- Fees (We axiomatically establish £0 fees).
- “Key” characteristics (Relative to the website and definition of key).
- Funds holdings, Market Value, Weight, Shares

This was for the most recent quarter / filings.

Once this is complete it is cruical I critically think regarding the data itself. what questions it can answer, what needs it can solve etc
Afterall, Garbage In = Garbage Out

This will outright lead to data cleaning and furthermore, analysis. 


----------------------------------------------------------------------------------------------------------------------------------------------

The collection of static holdings suffice when utilising differential static based tools, aimfully to collect questions derived answers.
Various postulations, criterions and axioms must be implemented to undertake alternative non-static based, continious time based analysis.

This arises with a municipal of difficulties faced, espsecially from the retail perspective. 
SEC13F and FCA holdings aren't obligated to disclose short sellings, historical holdings and most concurrent time updated holdings, creating a risk managerial and analysis problem.

For this designated portfion of information assymetry and the inability to access institutional grade tools to aid in further analysis, and maximise information symmetry relative to our constarint, it is therefore advisable to utilise the static holdings as best we can..

After executing analysis utilising static holdings, Divergence towards non-static formulation will begin.

Firstly, Collecting time series data regarding the static holdings is imperative for our analysis.

Below you will find all metrics collected from the individual portfolio composition and makeup.

- Company name, ISIN/ticker, country, weight, sector
- Historical prices, total returns(Calculcated), PX_LAST, TOT_RETURN_INDEX_GROSS_DVDS, P/E Ratio, P/B Ratio, dividend Yield, Forward dividends projection
- Returns on investments, Shares outstanding, Trailing dividends...
- YoY dividends growth (Calculcated).

<img width="1692" height="519" alt="image" src="https://github.com/user-attachments/assets/ec16b6d5-8558-4b48-a058-e46700fa39f6" />
<img width="1663" height="426" alt="image" src="https://github.com/user-attachments/assets/2e364fb0-8fdd-4843-bcba-17ec44e34adc" />


Now it is imperative to collect a plethora of Macro and Micro metrics for comparison and relativistic mapping between our fund and various asset classes.

FTSE 100, MSCI World, S&P 500 etc

A collection of indexes for relativistic comparison will be collected.. 
CPI, interest rates, GDP growth, unemployment

<img width="1532" height="483" alt="image" src="https://github.com/user-attachments/assets/72c1aac7-1606-49ba-9ed8-2cdb9bfeeafa" />

Now that we've collceted the data, we can begin deriving various metrics utilising model for our analysis...

**Benchmark & factor data**

- Benchmark prices (`Index` tickers) 
- Fama-French factor series (3-factor, 5-factor), momentum factor — downloadable (Kenneth French data)
- Sector classification (GICS) — Bloomberg field `GICS_SECTOR_NAME`
- Risk Free rate M Treasury / SONIA / Fed Funds Effective Rate FRED or Bloomberg: USGG3M, SONIO/N Index
- ADV, spread, turnover VOLUME, PX_BID, PX_ASK

Here is data regarding Fama-French Factor series parameter values for discrete dates and time intervals. 
mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html


With static holdings, we can:

Compute and visualise risk metrics (VaR, vol, correlations)
Run mean–variance optimisation on current assets
Estimate factor exposures & factor sensitivities
Perform GARCH modelling on portfolio or benchmark returns
Test for momentum, value, and quality biases
Assess liquidity, market cap, and sector concentration
Build a dashboard + memo reporting all of the above
When we later obtain get historical holdings, We will upgrade the analysis to include:
Brinson attribution
True rolling factor exposures
Turnover & transaction cost analysis

These will be simulated on the assumption that any institutional analyst will have access to these.

Commands situated below highlight efficiency utilisation concerning data extraction, superceding manual extraction which is time consuming..
WE can also utilise the bloomberg spreadsheet builder to compute a des

**last_price**
=BDH("TICKER","PX_LAST","2022-11-07","2025-11-04","Dir=V","Dts=S","Fill=C","Sort=A")

**Bid_price**
=BDH("TICKER","BID","2022-11-07","2025-11-04","Dir=V","Dts=S","Fill=C","Sort=A")

**Ask_price**
=BDH("TICKER","ASK","2022-11-07","2025-11-04","Dir=V","Dts=S","Fill=C","Sort=A")

**Volume**
=BDH("TICKER","VOLUME","2022-11-07","2025-11-04","Dir=V","Dts=S","Fill=C","Sort=A")

**P/E Ratio**
=BDH("Equity", "PE_RATIO", "01/07/2022", "04/07/2025", "PERIOD=Q", "FILL=PREV")

**P/B Ratio**
=BDH("Equity", "PX_TO_BOOK_RATIO", "01/07/2022", "04/07/2025", "PERIOD=Q", "FILL=PREV")


Now that we have estbalished the Goals of our analysis, Portfolio, Data etc
We can begin our analysis!

(Refer to the notebooks to view these)!
