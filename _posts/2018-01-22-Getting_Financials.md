Allow me to start with a caveat.  I tried many things to get financial data.

I tried to write my own scripts to scrape from Yahoo Finance.  I tried to access Yahoo Finance's API along with Google Finance's API.  This post is going to focus on the things that I was able to successfuly use when looking to grap financial data for US Listed Equity Secruities.

I was able to find success with three different resources:
1. [Alpha Vantage] (https://www.alphavantage.co/)
2. [Quandl] (https://www.quandl.com/)
3. [pandas_datareader] (https://pandas-datareader.readthedocs.io/en/latest/)

Each of these sources has positives and negatives.  The first two require you to set up an account to get a free API Key.
These two both have decent documentation on how to use their resources.  Problematically, some of the data you are looking for will be accessible with your free API key, while other data is pay to access.  Depending on your individual needs, this may do.  I was specifically looking for adjusted close data on US Equity Securities.  All of these sources allowed me to get that in some kind of format.

*datareader*
```python
start = datetime.datetime(2015, 12, 31)
end = datetime.datetime(2018, 1, 26)

for ticker in tickers_list['Symbol'].values
    retries = 10
    missed = []
    for i in range(retries):
        try:
            my_ticker = str(ticker)
            ticker = data.DataReader(ticker, "yahoo", start, end)
            ticker.to_csv("alt_data/"+my_ticker+".csv", header=True)
        except:
            missed.append(ticker)
            continue
```
