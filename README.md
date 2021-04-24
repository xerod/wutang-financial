## Disclaimer

![Alt Text](https://media.giphy.com/media/128RvI3CzjuXG8/giphy.gif)

Do not risk money which you are afraid to lose. USE THE SOFTWARE AT YOUR OWN RISK. THE AUTHORS AND ALL AFFILIATES ASSUME NO RESPONSIBILITY FOR YOUR TRADING RESULTS.

> This repo only contain user directory for freqtrade crypto-currency algorithmic trading software. Please read more about the software here: [Freqtrade Documentation](https://www.freqtrade.io/en/latest)

# 🛠 Installation

1. Install docker-compose. Please read [Docker installation](https://docs.docker.com/compose/install/)
2. Clone this repo: <br/>
   `git clone https://github.com/xerod/wutang-financial.git`
3. Pull the freqtrade image <br/>
   `docker-compose pull`
4. Check your docker images: <br/>
   `docker images -a`
5. Check if your freqtrade running: <br/>
   `docker-compose run freqtrade --help`

# 🤖 Basic Commands

Since we are running Freqtrade on docker container, every specific command that not registered on `docker-compose.yml` should use a `docker-compose run --rm` as a prefix.

For instance, run this command to download any data within 180 days : <br/>

```
docker-compose run --rm freqtrade download-data
```

### Start the bot

To do a dry-run, please make sure `dry_run` value is **true** inside `config.json`, then run this bot using:

```
docker-compose up
```

Once the bot started, the Freqtrade UI will be available at http://localhost:8080.

### Other bot Commands

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

# 🔑 Production and Security

Securing all secret key, token, and passwords is a top priority. This section guides you on how to eliminate this risk and run your bot securely **BY NOT EXPOSING**:

1. Crypto exchange API key
2. Telegram BOT token and chat id
3. FreqUI username & password
4. FreqUI listen port
5. FreqUI public and private IP

> A production installation using bash script is an ongoing effort.

For now, this is what you gonna do:

### 1. Initial Setup

Create `freqtrade.log` as this files is needed for `docker-compose up` command.

```
touch user_data/logs/freqtrade.log
```

### 2. Freqtrade

On production environment, you should set-up a `config.production.json`:

```
cp user_data/config.json user_data/config.production.json
```

DO NOT USE the default `config.json`. If you're going to do a dry-run on `VPS, use`config.dry.json` instead.

> `config.production.json` and `config.dry.json` is ignored by git, eliminating the case of exposing your public IP and Telegram token.

Running docker-compose on production also need a special tag. Read about [running at production](###5.-launch-the-bot)

### 3. FreqUI

> It is strongly recommend to not expose this API to the internet and choose a strong, unique password, since others will potentially be able to control your bot.

If FreqUI is a high priority, you could change this behaviour by setting the listen port on `production.yml`:

```
    ports:
      - "{YOUR_PRIVATE_IP}:8080:8080"
```

Once you run the bot, your UI would be accessible via [https://{YOUR_PUBLIC_IP}:8080]()

### 4. Telegram

For now, **there's no options** that we considered secure enough to run a Telegram bot on production. However we're still trying to solve this issue.

### 5. Launch the bot

Running the bot on production by specifying `production.yml` file:

```
docker-compose -f production.yml run
```

## Further read

[Freqtrade Documentation](https://www.freqtrade.io/en/latest)

[Docker Documentation](https://docs.docker.com)
