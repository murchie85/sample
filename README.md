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

Your Jenkins job will now run every hour.
# PARSING JSON DATA

## STORING DATA IN VAR

Ok your report is a good first step, but its not very useful, we need to convert the data to usable objects we can manipulate at will, then we can do stuff like build a report. The first step is to change the code so it doesn't write out the data to file, but saves it as a variable. 

```
$url = "https://api.coinmarketcap.com/v1/ticker/?convert=GBP"

$output = Invoke-WebRequest -Uri $url -UseDefaultCredentials -UseBasicParsing 

Write-Host $output
```

* You can see this is much more simpler, we just invoke the web request on the URI and save it to a variable $output, then we use Write-Host to display it.

Run this code in Jenkins to be sure it works. 

## Converting to json

Ok, this is good, but your variable is still a massive string even though it looks like Json, it isn't Json, its just a string. So lets convert it using the powershell special command (other langauges have a similar command).

