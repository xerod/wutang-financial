## Disclaimer

Do not risk money which you are afraid to lose. USE THE SOFTWARE AT YOUR OWN RISK. THE AUTHORS AND ALL AFFILIATES ASSUME NO RESPONSIBILITY FOR YOUR TRADING RESULTS.

> This repo only contain user directory for freqtrade crypto-currency algorithmic trading software. Please read more about the software here: [Freqtrade Documentation](https://www.freqtrade.io/en/latest)

## Installation

1. Install docker-compose. Please read [Docker installation](https://docs.docker.com/compose/install/)
2. Clone this repo: <br/>
   `git clone https://github.com/xerod/wutang-financial.git`
3. See your container status: <br/>
   `docker ps -a`
4. Check if your freqtrade running: <br/>
   `docker-compose run freqtrade --help`

## Backtesting

Since we running it on docker container, every specific command that not registered on `docker-compose.yml` should use a `docker-compose run --rm` as a prefix.

For instance, Run this command to download any data within 180 days : <br/>
`docker-compose run --rm freqtrade download-data`

## Further read

[Freqtrade Documentation](https://www.freqtrade.io/en/latest)

[Docker Documentation](https://docs.docker.com)
