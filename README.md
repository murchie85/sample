# sample
test code

First lets run the below code **REMEMBER** to change your path:

```
$url = "https://api.coinmarketcap.com/v1/ticker/?convert=GBP"

Invoke-WebRequest -Uri $url -UseDefaultCredentials -UseBasicParsing | Select-Object -ExpandProperty content > C:\users\adam\desktop\output.json

```
You can now find the json report file in the directory containing values for all of these coins

# Schedule reports

Imagine this was an important report that you had processed (we will do a little later), you want to produce it every hour and do something with it. So here we will do the first step of running it every hour.

In your jenkins job, select __configure__ now scroll down until you see __BUILD TRIGGERS__ and click on __build periodically__ . 
This clock timing is a bit confusing, but you can always google the time conversion you need, for now we will build every hour to do this simply paste in the following. 

```
0 * * * *
```

Apply and save and now the job will tell you the next time it will run under the box where you just inserted the timecode. 
