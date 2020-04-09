# komoot-export

Export GPS tracks and tour data from komoot.de
Credits go to: Matthias-hi https://github.com/matthias-hi for the base of the sourcecode

## Disclaimer

This repository is in NO way affiliated to Komoot. It uses non-public APIs to extract user data and will cease to work as soon as their APIs change.

## Overview

The repository contains one scripts

* __pykomoot_gpx.py__ Download GPX tracks of planned and recorded tours.

## Requirements

* Recent version of Python 3
* requests

## pykomoot_gpx.py

###HowTo

* You need to login manually via the browser
* Press F12 in the Browser and switch to the network tab
* Visit "https://www.komoot.de/api/v007/users/696489732183/tours/?page=0&limit=100"
* Click on the request which looks similar to "?page=0&limit=100"
* Copy from the RequestHeaders the complete part: "Cookie: ...." (you can use tripple click to mark everything)
* Add it as the second parameter

### Limitations

* I don't have an account via email so the login/session functionality is not available

### Examples

Download all "recorded" tours into directory "gpx_download/recorded/"
```
$ ./pykomoot_gpx.py -r gpx_download/recorded/ <cookies>
```

Download all "planned" tours into directory "gpx_download/planned/"
```
$ ./pykomoot_gpx.py -p gpx_download/planned/ <cookies>
```

Only download tour data in JSON format (tours.json) which is used as input for pykomoot_tours.py
```
$ ./pykomoot_gpx.py <cookies>
```

## pykomoot_tours.py

### Examples

Convert tours.json to tours.csv
```
$ ./pykomoot_tours.py tours.json
```

Get tours.json by running pykomoot_gpx.py.