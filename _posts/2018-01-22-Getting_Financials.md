Allow me to start with a caveat.  I tried many things to get financial data.

I tried to write my own scripts to scrape from Yahoo Finance.  I tried to access Yahoo Finance's API along with Google Finance's API.  This post is going to focus on the things that I was able to successfuly use when looking to scrape financial data for US Listed Equity Secruities.

I was able to find success with three different resources:
1. [Alpha Vantage] (https://www.alphavantage.co/)
2. [Quandl] (https://www.quandl.com/)
3. [pandas_datareader] (https://pandas-datareader.readthedocs.io/en/latest/)

Each of these sources has positives and negatives.  The first two require you to set up an account to get a free API Key.
These two both have decent documentation on how to use their resources.  Problematically, some of the data you are looking for will be accessible with your free API key, while other data is pay to access.  Depending on your individual needs, this may do.  I was specifically looking for adjusted close data on US Equity Securities.  All of these sources allowed me to get that in some kind of format.

`datareader`
The following block of code would try to pull down the tickers you gave it (I was using a dataframe with a Symbol column).  It would get the specified date range, returning it and saving it to a new csv file in your specified path.  It was also keeping track of a list of symbols that I missed on the initial attempt.  I was then comparing two lists to get what information I missed and submit a new request.  I used the command line with `ls` to pipe out the files I had created and run my returnNoMatchese function.
```python
from pandas_datareader import data, wb

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
            
def returnNoMatches(a, b):
    return [list(b-a), list(a-b)]
    
stock_change = stocks.apply(lambda x: np.log(x) - np.log(x.shift(1))) # shift moves dates back by 1.
df = df[(df['date'] > "2015-12-31") & (df['date'] <= "2018-01-25")]
```
To illustrate the types of information you can access with the `pandas_datareader`.  I was looking for lognormal returns so the stock_change applied a lambda function to my dataframe to get my returns in the desired format.  The df simply ensures that I am looking at my data in the desired time frame.
```python
print(dir(data), end=' ')
```
*returns*
`['DataReader', 'EdgarIndexReader', 'EnigmaReader', 'EurostatReader', 'FamaFrenchReader', 'FredReader', 'GoogleDailyReader', 'GoogleOptions', 'GoogleQuotesReader', 'OECDReader', 'Options', 'QuandlReader', 'YahooActionReader', 'YahooDailyReader', 'YahooDivReader', 'YahooOptions', 'YahooQuotesReader', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'get_components_yahoo', 'get_data_enigma', 'get_data_famafrench', 'get_data_fred', 'get_data_google', 'get_data_quandl', 'get_data_yahoo', 'get_data_yahoo_actions', 'get_nasdaq_symbols', 'get_quote_google', 'get_quote_yahoo', 'warnings'] `

Next lets take a look at Quandl.  Ultimately, I found their API to be very useful in getting my desired data in an easy to use format.  From a high level, I was getting adjusted information and all of the other usefull stuff in a single call.

```python 
import quandl

quandl.ApiConfig.api_key = 'YOUR API KEY'
df = quandl.get('WIKI/'+ticker+'') # WIKI was the database I was getting my information from
```
This call would return the following ticker information:
`Open	High	Low	Close	Volume	Ex-Dividend	Split Ratio	Adj. Open	Adj. High	Adj. Low	Adj. Close	Adj. Volume`

```python 
print(dir(quandl), end=' ')
```
*returns* 
`['ApiConfig', 'AuthenticationError', 'ColumnNotFound', 'Data', 'Database', 'Dataset', 'Datatable', 'ForbiddenError', 'InternalServerError', 'InvalidDataError', 'InvalidRequestError', 'LimitExceededError', 'MergedDataset', 'NotFoundError', 'QuandlError', 'ServiceUnavailableError', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', 'api_config', 'bulkdownload', 'connection', 'errors', 'get', 'get_table', 'message', 'model', 'operations', 'util', 'utils', 'version'] `

