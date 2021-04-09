## Disclaimer

Do not risk money which you are afraid to lose. USE THE SOFTWARE AT YOUR OWN RISK. THE AUTHORS AND ALL AFFILIATES ASSUME NO RESPONSIBILITY FOR YOUR TRADING RESULTS.

> This repo only contain user directory for freqtrade crypto-currency algorithmic trading software. Please read more about the software here: [Freqtrade Documentation](https://www.freqtrade.io/en/latest)

## Installation

1. Install docker-compose. Please read [Docker installation](https://docs.docker.com/compose/install/)
2. Pull the freqtrade image <br/>
   `docker-compose pull`
3. Clone this repo: <br/>
   `git clone https://github.com/xerod/wutang-financial.git`
4. See your container status: <br/>
   `docker ps -a`
5. Check if your freqtrade running: <br/>
   `docker-compose run freqtrade --help`

## Commands

Since we running it on docker container, every specific command that not registered on `docker-compose.yml` should use a `docker-compose run --rm` as a prefix.

For instance, Run this command to download any data within 180 days : <br/>
`docker-compose run --rm freqtrade download-data`

### Bot Commands

```
usage: freqtrade [-h] [-V]
                 {trade,create-userdir,new-config,new-hyperopt,new-strategy,download-data,convert-data,convert-trade-data,backtesting,edge,hyperopt,hyperopt-list,hyperopt-show,list-exchanges,list-hyperopts,list-markets,list-pairs,list-strategies,list-timeframes,show-trades,test-pairlist,plot-dataframe,plot-profit}
                 ...

Free, open source crypto trading bot

positional arguments:
  {trade,create-userdir,new-config,new-hyperopt,new-strategy,download-data,convert-data,convert-trade-data,backtesting,edge,hyperopt,hyperopt-list,hyperopt-show,list-exchanges,list-hyperopts,list-markets,list-pairs,list-strategies,list-timeframes,show-trades,test-pairlist,plot-dataframe,plot-profit}
    trade               Trade module.
    create-userdir      Create user-data directory.
    new-config          Create new config
    new-hyperopt        Create new hyperopt
    new-strategy        Create new strategy
    download-data       Download backtesting data.
    convert-data        Convert candle (OHLCV) data from one format to
                        another.
    convert-trade-data  Convert trade data from one format to another.
    backtesting         Backtesting module.
    edge                Edge module.
    hyperopt            Hyperopt module.
    hyperopt-list       List Hyperopt results
    hyperopt-show       Show details of Hyperopt results
    list-exchanges      Print available exchanges.
    list-hyperopts      Print available hyperopt classes.
    list-markets        Print markets on exchange.
    list-pairs          Print pairs on exchange.
    list-strategies     Print available strategies.
    list-timeframes     Print available timeframes for the exchange.
    show-trades         Show trades.
    test-pairlist       Test your pairlist configuration.
    plot-dataframe      Plot candles with indicators.
    plot-profit         Generate plot showing profits.

optional arguments:
  -h, --help            show this help message and exit
  -V, --version         show program's version number and exit
```

## Further read

[Freqtrade Documentation](https://www.freqtrade.io/en/latest)

[Docker Documentation](https://docs.docker.com)
