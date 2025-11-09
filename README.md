# TomTom Geocoding / Reverse-Geocoding Utilities (Python)

This project contains two small Python helper modules that use the TomTom Search API to convert between addresses and latitude/longitude coordinates.

## Files
| File | Function | Description |
|------|----------|-------------|
| `findAddress.py` | `findAddress(lat, lng, key)` | Reverse geocodes latitude + longitude → address |
| `findCoordinates.py` | `findCoordinates(address, key)` | Forward geocodes address → lat/lng |

Both functions return Pandas DataFrames.

## Requirements

Install dependencies:
pip install pandas requests

Python 3.9+ recommended.

## API Key

Both functions accept an API key parameter.  
If one is not provided, both functions currently default to a sample hardcoded key:


You should replace this with your own TomTom key from:
https://developer.tomtom.com/

## Usage Examples

### Reverse Geocoding: lat/lng → address
```python
from findAddress import findAddress

lats = (33.6405, 34.0522)
lngs = (-117.8443, -118.2437)

df = findAddress(lats, lngs, key="YOUR_KEY")
print(df)
from findCoordinates import findCoordinates

addresses = ["Times Square, NY", "1 Microsoft Way, Redmond WA"]

df = findCoordinates(addresses, key="YOUR_KEY")
print(df)

