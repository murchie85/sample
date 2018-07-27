# sample
test code

First lets run the below code **REMEMBER** to change your path:

```
$url = "https://api.coinmarketcap.com/v1/ticker/?convert=GBP"

Invoke-WebRequest -Uri $url -UseDefaultCredentials -UseBasicParsing | Select-Object -ExpandProperty content > C:\users\adam\desktop\output.json

```
You can now find the json report file in the directory containing values for all of these coins
