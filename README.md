TomTom Geocoding / Reverse-Geocoding Utilities (Python)
This project contains two helper functions that interface with the TomTom Search API:
File	Function	Purpose
findAddress.py	findAddress(lat, lng, key)	Takes latitude/longitude pairs → returns address(es)
findCoordinates.py	findCoordinates(address, key)	Takes address strings → returns latitude/longitude
Both functions return Pandas DataFrames for easy use in data workflows.
Requirements
Python 3.9+
pandas
requests
install requirements:
pip install pandas requests
API Key
Both functions accept a parameter key.
If none is passed, the functions default to:
gTGlKsrxmGjsdTE0TN71A8wSxAM4GbCl
You should replace this with your own key from:
https://developer.tomtom.com/
Never commit keys to public repos.
Store locally using environment variables if possible.
Example:
export TOMTOM_KEY="your key here"
Then in code:
import os
key = os.getenv("TOMTOM_KEY")
Usage Examples
Reverse Geocoding → lat/lng → address
from findAddress import findAddress

lats = (33.6405, 34.0522)
lngs = (-117.8443, -118.2437)

df = findAddress(lats, lngs, key="YOUR_KEY")
print(df)
Output columns:
address	status_code
Forward Geocoding → address → lat/lng
from findCoordinates import findCoordinates

addresses = ["1 Microsoft Way, Redmond WA", "Times Square, New York NY"]

df = findCoordinates(addresses, key="YOUR_KEY")
print(df)
Output columns:
lat	lng	address	status_code
Notes
TomTom rate-limits requests — so both functions automatically sleep(0.1) between calls
Returned DataFrames allow easy filtering, merging, or joining with other datasets
Status codes are returned so users can inspect failures (404, 403, etc)
License
MIT (or whatever license you plan to use)
