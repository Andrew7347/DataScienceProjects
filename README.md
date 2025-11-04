# Portfolio Optimisation and Risk Modelling
This project Involves analysing several realistic **Institituional** level Cross-Product Portfolios.
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
- Anstract Thinking
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

  The tools we will use (As listed at the beginning) include... (See the very start of this document).

  Now that we know the inherent questions we need to answer to satisfy the needs of the business... We can begin our goal orientated data analysis.

  ---------

  DATA COLLECTION:

**First and foremost I need to collect data regarding my project to be able to carry out the analysis.**

inherent needs and wants determinations were implemented within preceding info situated above this log. showcasing the goals and guiding postulations for the projects actions. 

To carry out portfolio Analysis, A portfolio is required.

However, What form, type, composition, information etc regarding the portfolio is another matter.

We shall dive into this directly within this section while simultaneously collecting data.  

The criteria I have chosen for choosing the portfolio comprises of the following…

- Institutional Grade
- Diverse (Equities, Bonds, Commodities)
- Publicly available information (quarterly reports, SEC filings, holdings etc)
- Must be actively managed (Implies risk and return management required, replicating asset management roles)

  After reviewing numerous institiuional grade portfolios I have succesfuly opted for the...

 **Blackrock Global Allocation Fund (Malox)**

 Next steps are...

- Extract Data from the Blackrock website
- Extract Data Bloomberg Terminal
- Extract data not from Blackrock

  (Include Image))))))))))))))))))))))

I have successfully extracted A plethora of relevant data within the Blackrock website.

To account for survivorship bias and proportionally decrease bias, I will confer with the data from alternative source (Bloomberg, Yahoo etc).

(Include Images))))))))))))))))))

I have extracted…

- Exposure Breakdowns (Asset Class, Sector, Region, Currency)
- Fees
- “Key” characteristics (Relative to the website and definition of key).
- Performance relative to indicators, Morningstar ranking etc
- Total returns and benchmarks
- Funds holdings, Market Value, Weight, Shares

This was for the most recent quarter / filings.

A problem was run into while carrying out this task.

To execute effective time series, statistical and mathematical analysis we require consistent data about each quarters holding (as stated above). However the data for previous quarters on Bloomberg has induced issues such as displaying the quantity of shares within the portfolio.

This creates a data cleaning and analysis problem, Attempts to fix this have been carried out using alternative sources, more recent holdings and there doesn’t seem to be a viable solution within this avenue.

Therefore my next step of action is to manually derive the data above, How? By utilising formula to extract holdings, share prices etc to manually compute the above data.

**I have established that excel can’t handle the huge array of data on the SEC filing.** 

**Therefore my next course of action is to extract the data and clean it within Python,**

**Afterwards this will be imported into Excel.** 

Then we can focus on obtaining differeing sources of data.

Once this is complete it is cruical I critically think regarding the data itself. what questions it can answer, what needs it can solve etc

Then we can begin our analysis or rather (Clean the data) and begin our analysis.


----------------------------------------------------------------------------------------------------------------------------------------------

**Liontrust Global Smaller Companies Fund**

I have accumulated a snapshot of the most recent holdings (2024).

<img width="1104" height="864" alt="image" src="https://github.com/user-attachments/assets/7c4b8064-9d90-4ac8-9270-61585ff8c3c9" />

The breakdown includes:

Country	
Company	
Nominal (units)	
Market Value (GBP)
% of Net Assets

The collection of static holdings suffice when utilising differential static based tools, aimfully to collect questions derived answers.
Various postulations, criterions and axioms must be implemented to undertake alternative non-static based, continious time based analysis.

This arises with a municipal of difficulties faced, espsecially from the retail perspective. 
SEC13F and FCA holdings aren't obligated to disclose short sellings, historical holdings and most concurrent time updated holdings, creating a risk managerial and analysis problem.

For this designated portfion of information assymetry and the inability to access institutional grade tools to aid in further analysis, and maximise information symmetry relative to our constarint, it is therefore advisable to utilise the static holdings as best we can..

Firstly, Collecting time series data regarding the static holdings is imperative for our analysis.

Below you will find all metrics collected from the individual portfolio composition and makeup.

- Company name, ISIN/ticker, country, weight, sector
- Historical prices, total returns PX_LAST, TOT_RETURN_INDEX_GROSS_DVDS, Yahoo/AlphaVantage

(Insert Image)))))))))))))))))))))))))))))))

Now it is imperative to collect a plethora of Macro and Micro metrics for comparison and relativistic mapping between our fund and various asset classes.

FTSE 100, MSCI World, S&P 500 etc

A collection of indexes for relativistic comparison will be collected.. 
CPI, interest rates, GDP growth, unemployment

After collecting these data we can begin deriving various metrics utilising model for our analysis...

**Benchmark & factor data**

- Benchmark prices (`Index` tickers) 
- Fama-French factor series (3-factor, 5-factor), momentum factor — downloadable (Kenneth French data)
- Sector classification (GICS) — Bloomberg field `GICS_SECTOR_NAME`
- Market cap, book/price, earnings, ROE (fundamentals) — Bloomberg fields: `CUR_MKT_CAP`, `PE_RATIO`, `PB_RATIO`, `RETURN_ON_EQUITY`
- Risk Free rate M Treasury / SONIA / Fed Funds Effective Rate FRED or Bloomberg: USGG3M, SONIO/N Index
- ADV, spread, turnover VOLUME, PX_BID, PX_ASK

Here is data regarding Fama-French Factor series parameter values for discrete dates and time intervals. 
mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html


With static holdings, you can:

Compute and visualise risk metrics (VaR, vol, correlations)
Run mean–variance optimisation on current assets
Estimate factor exposures & factor sensitivities
Perform GARCH modelling on portfolio or benchmark returns
Test for momentum, value, and quality biases
Assess liquidity, market cap, and sector concentration
Build a dashboard + memo reporting all of the above
If you later get historical holdings, you can upgrade the analysis to include:
Brinson attribution
True rolling factor exposures
Turnover & transaction cost analysis
