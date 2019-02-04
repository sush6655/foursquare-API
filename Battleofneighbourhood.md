
# **BATTLE OF NEIGHBOURHOOD**
## INTRODUCTION
-  PROBLEM: The main aim of the project is to solve the problem of an Indian business man trying to find a place to open an Indian restaurant in the city of Fairfax. In this the major problem is that if there are other Indian restaurants stationed in Fairfax city it will be difficult for the business to grow eventually as people most of the time prefer the eat at a know place rather than trying the new cuisine. And, if the business is located near to many Indian restaurants the number of customers arriving the restaurant gradually decreases. Since many people living in the united states are from various culture and background It is also wise to choose location near more populated area with people having the crave for the Indian cuisine. In the proper location there must be various other factors that must be considered.

-  SOLUTION: In this the solution can be obtained using the map locator or an application which is mainly used by the top companies like the google, snapchat, Instagram. The Foursquare API is a platform which has the information of the various restaurants, business, gas stations and information of many more places to explore are available at one place. Let us consider the problem of the business man to open an Indian restaurant in the city of Fairfax from the place of the center of city. Consider through the foursquare API developer tool we can obtain the near by restaurants available near to the center of the city. Thus, solving half of the problem know how many other restaurants are available. In the further problem. The location can be obtained through the maps. The folium maps are using to locate the near by restaurants and help us in obtaining the location to open a new one with in a respective radius. The data used in this project is from the foursquare API where the data of the other restaurants is depicted through a data frame. Though this the map is constructed with the markers and hence an idea of the location can be drawn looking at the coordinates according with the distance from the other dealers.


### Installing the library and importing the packages.


```python
import requests
import pandas as pd
import numpy as np
import random

from geopy.geocoders import Nominatim

from IPython.display import Image
from IPython.core.display import HTML

from pandas.io.json import json_normalize

import folium

print('folium installed')
print('Libraries imported')
```

    folium installed
    Libraries imported


### Getting access with the foursquare API using the id and secret of the developer tool.


```python
client_id = 'NMJ52A3K5W1PN2SZZEVLJ0NPCOCE1VLKTIFAYVMVSXHTHHKP'
client_secret = '4Y2KMTAWBAHB41AZN5U0HFMQZCLA4VKXTAX3PP14TK0RYITU'
version='20180604'
limit=30
print('client_id:'+ client_id)
print('client_secret:'+ client_secret)
```

    client_id:NMJ52A3K5W1PN2SZZEVLJ0NPCOCE1VLKTIFAYVMVSXHTHHKP
    client_secret:4Y2KMTAWBAHB41AZN5U0HFMQZCLA4VKXTAX3PP14TK0RYITU



```python
address = '4311 bob court, fairfax,VA'

geolocator =Nominatim(user_agent="foursquare_agent")
location=geolocator.geocode(address)
latitude=location.latitude
longitude=location.longitude
print(latitude,longitude)

```

    38.839009 -77.314171


### Searching for the required type of the restaurant to be located in the city.


```python
search_query = 'Indian'
radius=1000
print(search_query + '---------ok!')
```

    Indian---------ok!



```python
url = 'https://api.foursquare.com/v2/venues/search?client_id={}&client_secret={}&ll={},{}&v={}&query={}&radius={}&limit={}'.format(client_id,client_secret, latitude, longitude,version, search_query, radius,limit)
url
```




    'https://api.foursquare.com/v2/venues/search?client_id=NMJ52A3K5W1PN2SZZEVLJ0NPCOCE1VLKTIFAYVMVSXHTHHKP&client_secret=4Y2KMTAWBAHB41AZN5U0HFMQZCLA4VKXTAX3PP14TK0RYITU&ll=38.839009,-77.314171&v=20180604&query=Indian&radius=1000&limit=30'




```python
results=requests.get(url).json()
results
```




    {'meta': {'code': 200, 'requestId': '5c57857b4c1f674556ca9e92'},
     'response': {'venues': [{'id': '4ca66839a6e08cfa37567a94',
        'name': 'Bombay Garden',
        'location': {'address': 'University Drive',
         'crossStreet': 'Main Street',
         'lat': 38.84557,
         'lng': -77.30546873333333,
         'labeledLatLngs': [{'label': 'display',
           'lat': 38.84557,
           'lng': -77.30546873333333}],
         'distance': 1050,
         'postalCode': '22030',
         'cc': 'US',
         'city': 'Fairfax',
         'state': 'VA',
         'country': 'United States',
         'formattedAddress': ['University Drive (Main Street)',
          'Fairfax, VA 22030',
          'United States']},
        'categories': [{'id': '4bf58dd8d48988d10f941735',
          'name': 'Indian Restaurant',
          'pluralName': 'Indian Restaurants',
          'shortName': 'Indian',
          'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/indian_',
           'suffix': '.png'},
          'primary': True}],
        'referralId': 'v-1549239675',
        'hasPerk': False}]}}



### The list of the restaurants situated near to the city address.


```python
venues=results['response']['venues']

dataframe=json_normalize(venues)
dataframe.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>categories</th>
      <th>hasPerk</th>
      <th>id</th>
      <th>location.address</th>
      <th>location.cc</th>
      <th>location.city</th>
      <th>location.country</th>
      <th>location.crossStreet</th>
      <th>location.distance</th>
      <th>location.formattedAddress</th>
      <th>location.labeledLatLngs</th>
      <th>location.lat</th>
      <th>location.lng</th>
      <th>location.postalCode</th>
      <th>location.state</th>
      <th>name</th>
      <th>referralId</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>[{'id': '4bf58dd8d48988d10f941735', 'name': 'I...</td>
      <td>False</td>
      <td>4ca66839a6e08cfa37567a94</td>
      <td>University Drive</td>
      <td>US</td>
      <td>Fairfax</td>
      <td>United States</td>
      <td>Main Street</td>
      <td>1050</td>
      <td>[University Drive (Main Street), Fairfax, VA 2...</td>
      <td>[{'label': 'display', 'lat': 38.84557, 'lng': ...</td>
      <td>38.84557</td>
      <td>-77.305469</td>
      <td>22030</td>
      <td>VA</td>
      <td>Bombay Garden</td>
      <td>v-1549239675</td>
    </tr>
  </tbody>
</table>
</div>




```python
filtered_columns = ['name', 'categories'] + [col for col in dataframe.columns if col.startswith('location.')] + ['id']
dataframe_filtered = dataframe.loc[:, filtered_columns]

def get_category_type(row):
    try:
        categories_list = row['categories']
    except:
        categories_list = row['venue.categories']
        
    if len(categories_list) == 0:
        return None
    else:
        return categories_list[0]['name']
    
dataframe_filtered['categories'] = dataframe_filtered.apply(get_category_type, axis=1)
dataframe_filtered.columns = [column.split('.')[-1] for column in dataframe_filtered.columns]

dataframe_filtered
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>categories</th>
      <th>address</th>
      <th>cc</th>
      <th>city</th>
      <th>country</th>
      <th>crossStreet</th>
      <th>distance</th>
      <th>formattedAddress</th>
      <th>labeledLatLngs</th>
      <th>lat</th>
      <th>lng</th>
      <th>postalCode</th>
      <th>state</th>
      <th>id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Bombay Garden</td>
      <td>Indian Restaurant</td>
      <td>University Drive</td>
      <td>US</td>
      <td>Fairfax</td>
      <td>United States</td>
      <td>Main Street</td>
      <td>1050</td>
      <td>[University Drive (Main Street), Fairfax, VA 2...</td>
      <td>[{'label': 'display', 'lat': 38.84557, 'lng': ...</td>
      <td>38.84557</td>
      <td>-77.305469</td>
      <td>22030</td>
      <td>VA</td>
      <td>4ca66839a6e08cfa37567a94</td>
    </tr>
  </tbody>
</table>
</div>



- Getting the location of the restaurants near to the location of the city. Thus we can see that there are very few restaurants available near to to city of fairfax with in the radius of 500 thus one can easily establish thier business of a restaurant near too the city and we can also observe in the map that the location is near to the university where many students from different cultural background come to study thus providing a good business to the owner when located to the area near a highly populated location.


```python
venues_map=folium.Map(location=[latitude,longitude],zoom_start=10)

folium.features.CircleMarker(
    [latitude,longitude],
    radius=7,
    color='blue',
    popup='Bombay Bistro',
    fill = True,
    fillcolor='blue',
    fill_opacity=0.5
    ).add_to(venues_map)

for lat,lng,categories in zip(dataframe_filtered.lat,dataframe_filtered.lng,dataframe_filtered.categories):
    folium.features.CircleMarker(
    [lat,lng],
    radius=4,
    color='red',
    popup='label',
    fill_color='red',
    fill_opacity=0.4
    ).add_to(venues_map)
    
venues_map
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><iframe src="data:text/html;charset=utf-8;base64,PCFET0NUWVBFIGh0bWw+CjxoZWFkPiAgICAKICAgIDxtZXRhIGh0dHAtZXF1aXY9ImNvbnRlbnQtdHlwZSIgY29udGVudD0idGV4dC9odG1sOyBjaGFyc2V0PVVURi04IiAvPgogICAgPHNjcmlwdD5MX1BSRUZFUl9DQU5WQVMgPSBmYWxzZTsgTF9OT19UT1VDSCA9IGZhbHNlOyBMX0RJU0FCTEVfM0QgPSBmYWxzZTs8L3NjcmlwdD4KICAgIDxzY3JpcHQgc3JjPSJodHRwczovL2Nkbi5qc2RlbGl2ci5uZXQvbnBtL2xlYWZsZXRAMS4yLjAvZGlzdC9sZWFmbGV0LmpzIj48L3NjcmlwdD4KICAgIDxzY3JpcHQgc3JjPSJodHRwczovL2FqYXguZ29vZ2xlYXBpcy5jb20vYWpheC9saWJzL2pxdWVyeS8xLjExLjEvanF1ZXJ5Lm1pbi5qcyI+PC9zY3JpcHQ+CiAgICA8c2NyaXB0IHNyYz0iaHR0cHM6Ly9tYXhjZG4uYm9vdHN0cmFwY2RuLmNvbS9ib290c3RyYXAvMy4yLjAvanMvYm9vdHN0cmFwLm1pbi5qcyI+PC9zY3JpcHQ+CiAgICA8c2NyaXB0IHNyYz0iaHR0cHM6Ly9jZG5qcy5jbG91ZGZsYXJlLmNvbS9hamF4L2xpYnMvTGVhZmxldC5hd2Vzb21lLW1hcmtlcnMvMi4wLjIvbGVhZmxldC5hd2Vzb21lLW1hcmtlcnMuanMiPjwvc2NyaXB0PgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL2Nkbi5qc2RlbGl2ci5uZXQvbnBtL2xlYWZsZXRAMS4yLjAvZGlzdC9sZWFmbGV0LmNzcyIvPgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL21heGNkbi5ib290c3RyYXBjZG4uY29tL2Jvb3RzdHJhcC8zLjIuMC9jc3MvYm9vdHN0cmFwLm1pbi5jc3MiLz4KICAgIDxsaW5rIHJlbD0ic3R5bGVzaGVldCIgaHJlZj0iaHR0cHM6Ly9tYXhjZG4uYm9vdHN0cmFwY2RuLmNvbS9ib290c3RyYXAvMy4yLjAvY3NzL2Jvb3RzdHJhcC10aGVtZS5taW4uY3NzIi8+CiAgICA8bGluayByZWw9InN0eWxlc2hlZXQiIGhyZWY9Imh0dHBzOi8vbWF4Y2RuLmJvb3RzdHJhcGNkbi5jb20vZm9udC1hd2Vzb21lLzQuNi4zL2Nzcy9mb250LWF3ZXNvbWUubWluLmNzcyIvPgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL2NkbmpzLmNsb3VkZmxhcmUuY29tL2FqYXgvbGlicy9MZWFmbGV0LmF3ZXNvbWUtbWFya2Vycy8yLjAuMi9sZWFmbGV0LmF3ZXNvbWUtbWFya2Vycy5jc3MiLz4KICAgIDxsaW5rIHJlbD0ic3R5bGVzaGVldCIgaHJlZj0iaHR0cHM6Ly9yYXdnaXQuY29tL3B5dGhvbi12aXN1YWxpemF0aW9uL2ZvbGl1bS9tYXN0ZXIvZm9saXVtL3RlbXBsYXRlcy9sZWFmbGV0LmF3ZXNvbWUucm90YXRlLmNzcyIvPgogICAgPHN0eWxlPmh0bWwsIGJvZHkge3dpZHRoOiAxMDAlO2hlaWdodDogMTAwJTttYXJnaW46IDA7cGFkZGluZzogMDt9PC9zdHlsZT4KICAgIDxzdHlsZT4jbWFwIHtwb3NpdGlvbjphYnNvbHV0ZTt0b3A6MDtib3R0b206MDtyaWdodDowO2xlZnQ6MDt9PC9zdHlsZT4KICAgIAogICAgICAgICAgICA8c3R5bGU+ICNtYXBfZDU3NDQ4Yjg2ZDIzNDQ1OGE2ZWZjMDIwNTNmNTZkNjAgewogICAgICAgICAgICAgICAgcG9zaXRpb24gOiByZWxhdGl2ZTsKICAgICAgICAgICAgICAgIHdpZHRoIDogMTAwLjAlOwogICAgICAgICAgICAgICAgaGVpZ2h0OiAxMDAuMCU7CiAgICAgICAgICAgICAgICBsZWZ0OiAwLjAlOwogICAgICAgICAgICAgICAgdG9wOiAwLjAlOwogICAgICAgICAgICAgICAgfQogICAgICAgICAgICA8L3N0eWxlPgogICAgICAgIAo8L2hlYWQ+Cjxib2R5PiAgICAKICAgIAogICAgICAgICAgICA8ZGl2IGNsYXNzPSJmb2xpdW0tbWFwIiBpZD0ibWFwX2Q1NzQ0OGI4NmQyMzQ0NThhNmVmYzAyMDUzZjU2ZDYwIiA+PC9kaXY+CiAgICAgICAgCjwvYm9keT4KPHNjcmlwdD4gICAgCiAgICAKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGJvdW5kcyA9IG51bGw7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgdmFyIG1hcF9kNTc0NDhiODZkMjM0NDU4YTZlZmMwMjA1M2Y1NmQ2MCA9IEwubWFwKAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJ21hcF9kNTc0NDhiODZkMjM0NDU4YTZlZmMwMjA1M2Y1NmQ2MCcsCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7Y2VudGVyOiBbMzguODM5MDA5LC03Ny4zMTQxNzFdLAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgem9vbTogMTAsCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICBtYXhCb3VuZHM6IGJvdW5kcywKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGxheWVyczogW10sCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB3b3JsZENvcHlKdW1wOiBmYWxzZSwKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNyczogTC5DUlMuRVBTRzM4NTcKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgfSk7CiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciB0aWxlX2xheWVyXzk0MmFiYzkzOWRkNDQ1YTM4NjliOGIwNWVkY2IxNmQxID0gTC50aWxlTGF5ZXIoCiAgICAgICAgICAgICAgICAnaHR0cHM6Ly97c30udGlsZS5vcGVuc3RyZWV0bWFwLm9yZy97en0ve3h9L3t5fS5wbmcnLAogICAgICAgICAgICAgICAgewogICJhdHRyaWJ1dGlvbiI6IG51bGwsCiAgImRldGVjdFJldGluYSI6IGZhbHNlLAogICJtYXhab29tIjogMTgsCiAgIm1pblpvb20iOiAxLAogICJub1dyYXAiOiBmYWxzZSwKICAic3ViZG9tYWlucyI6ICJhYmMiCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2Q1NzQ0OGI4NmQyMzQ0NThhNmVmYzAyMDUzZjU2ZDYwKTsKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9lMTYxZDExNTA1ZjU0ZmVlODY3MTAzNWQ0NzAxZTE0ZSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzM4LjgzOTAwOSwtNzcuMzE0MTcxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICJibHVlIiwKICAiZmlsbE9wYWNpdHkiOiAwLjUsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA3LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2Q1NzQ0OGI4NmQyMzQ0NThhNmVmYzAyMDUzZjU2ZDYwKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2ZiN2VmNmRhYmYzYTQ5MmE5OGUzZmMzNGY5YzRlMjViID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2U2YmU0Nzk4NmNmMDRkMTFhNDY0ODA4NzJiZWY3OTg2ID0gJCgnPGRpdiBpZD0iaHRtbF9lNmJlNDc5ODZjZjA0ZDExYTQ2NDgwODcyYmVmNzk4NiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+Qm9tYmF5IEJpc3RybzwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfZmI3ZWY2ZGFiZjNhNDkyYTk4ZTNmYzM0ZjljNGUyNWIuc2V0Q29udGVudChodG1sX2U2YmU0Nzk4NmNmMDRkMTFhNDY0ODA4NzJiZWY3OTg2KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2UxNjFkMTE1MDVmNTRmZWU4NjcxMDM1ZDQ3MDFlMTRlLmJpbmRQb3B1cChwb3B1cF9mYjdlZjZkYWJmM2E0OTJhOThlM2ZjMzRmOWM0ZTI1Yik7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9hZmM4Mjg2NTlkNjY0NjU1YjY5Y2NlNDgwOGJkOWQ3NSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzM4Ljg0NTU3LC03Ny4zMDU0Njg3MzMzMzMzM10sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJyZWQiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IGZhbHNlLAogICJmaWxsQ29sb3IiOiAicmVkIiwKICAiZmlsbE9wYWNpdHkiOiAwLjQsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA0LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2Q1NzQ0OGI4NmQyMzQ0NThhNmVmYzAyMDUzZjU2ZDYwKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzZiZWFjYTcwOGQ5NTQ2NjI4Y2Y4MWVlZGRlMGZlNWQ3ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2RiYjAxMTRlOGZhMDQ5NTU4YTdiOTY2MzA4M2RjYzhkID0gJCgnPGRpdiBpZD0iaHRtbF9kYmIwMTE0ZThmYTA0OTU1OGE3Yjk2NjMwODNkY2M4ZCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+bGFiZWw8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzZiZWFjYTcwOGQ5NTQ2NjI4Y2Y4MWVlZGRlMGZlNWQ3LnNldENvbnRlbnQoaHRtbF9kYmIwMTE0ZThmYTA0OTU1OGE3Yjk2NjMwODNkY2M4ZCk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9hZmM4Mjg2NTlkNjY0NjU1YjY5Y2NlNDgwOGJkOWQ3NS5iaW5kUG9wdXAocG9wdXBfNmJlYWNhNzA4ZDk1NDY2MjhjZjgxZWVkZGUwZmU1ZDcpOwoKICAgICAgICAgICAgCiAgICAgICAgCjwvc2NyaXB0Pg==" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>




```python

```


```python

```


```python

```


```python

```


```python

```
