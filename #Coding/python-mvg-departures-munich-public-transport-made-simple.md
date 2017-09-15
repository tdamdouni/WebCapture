# python_mvg_departures – Munich Public Transport made simple

_Captured: 2017-08-30 at 10:52 from [python-mvg-departures.readthedocs.io](http://python-mvg-departures.readthedocs.io/en/latest/?)_

## Intro

Not too long ago, MVG (aka Munchner Verkehrsgesellschaft) relaunched their [Website](http://mvg.de), which now actually utilizes a JSON api! (I know, crazy, right?) This python module tries to provide super easy, gluten free [[1]](http://python-mvg-departures.readthedocs.io/en/latest/?) access to most aspects of the mvg api.

It offers:

  * The next departures for any station in the MVV (duh)
    * This includes S-Bahn and Schienenersatzverkehr
  * Listing nearby stations based on geolocation
  * Routing from station to station
    * Routing from anywhere to anywhere (coming soon!)

Take a look at example.py, it shows some basic concepts, or at the rest of the docs, where every aspect is hopefully adequately documented.

[[1]](http://python-mvg-departures.readthedocs.io/en/latest/?)
mvg.de uses stuff like an api key (although _they only give it to themselves_) and Unix time in milliseconds (although the last four digits are always 0). Whith this module, you won't have to worry about all that.

## Module documentation

_class _`mvg_api.``Station`(_station_)
    

Gives you a proxy to get the next departures for a particular station.

Either give it an exact station name (like "Hauptbahnhof") or a station_id.

Deprecated-ish: This is not really all that useful. Just using `[get_id_for_station()`](http://python-mvg-departures.readthedocs.io/en/latest/?) and `[get_departures()`](http://python-mvg-departures.readthedocs.io/en/latest/?) really is the nicer way in most cases.

`mvg_api.``get_departures`(_station_id_)
    

Get the next departures for station_id.

To get the station_id associated with a station name, use `[get_id_for_station()`](http://python-mvg-departures.readthedocs.io/en/latest/?).

Returns a list like:
    
    
    [
        {
            'departureTimeMinutes': 0,
            'destination': 'Laimer Platz',
            'sev': False,
            'departureId': 1188266868,
            'live': True,
            'departureTime': 1478644495000,
            'lineBackgroundColor': '#b78730',
            'label': '5',
            'product': 'u'
        },
    ]
    

departureTimeMinutes, the time left to the departure in minutes, is added to the response from the api for your convenience.

`mvg_api.``get_id_for_station`(_station_name_)
    

Returns the station_id for the given station name.

If more than one station match, the first result is given. None is returned if no match was found.

`mvg_api.``get_locations`(_query_)
    

Returns all matches from the search for the given query string.

query can either be a name of a station or of a street, square, etc.

Returns a list wich looks somewhat like this:
    
    
    [
        {
            'lines':
                {
                'nachtbus': [],
                'ubahn': ['2', '5', '7'],
                'tram': [],
                'sbahn': [],
                'otherlines': [],
                'nachttram': [],
                'bus': []
                },
            'hasLiveData': True,
            'place': 'München',
            'products': ['u'],
            'id': 1060,
            'type': 'nearbystation',
            'name': 'Innsbrucker Ring',
            'hasZoomData': True,
            'distance': 59,
            'longitude': 11.619138,
            'latitude': 48.120408
        },
    ]
    

`mvg_api.``get_nearby_stations`(_lat_, _lon_)
    

Stations nearby the given location.

Returns a list which is formated in this fassion:
    
    
    [
        {
            'lines':
                {
                'nachtbus': [],
                'ubahn': ['2', '5', '7'],
                'tram': [],
                'sbahn': [],
                'otherlines': [],
                'nachttram': [],
                'bus': []
                },
            'hasLiveData': True,
            'place': 'München',
            'products': ['u'],
            'id': 1060,
            'type': 'nearbystation',
            'name': 'Innsbrucker Ring',
            'hasZoomData': True,
            'distance': 59,
            'longitude': 11.619138,
            'latitude': 48.120408
         },
     ]
    

`mvg_api.``get_route`(_start_, _dest_, _time=None_, _arrival_time=False_, _max_walk_time_to_start=None_, _max_walk_time_to_dest=None_)
    

Plans a route from start to dest

Parameters:

  * **start** (_int/tuple_) - The station_id of the starting station or a tuple of coordinates
  * **dest** (_int/tuple_) - station_id of the destination station or a tuple of coordinates
  * **time** (_datetime__, __optional_) -
  * **arrival_time** (_bool__, __optional_) - Specifies if time is the starting time (which is default) or the desired time of arrival.
  * **max_walk_time_to_dest** (_max_walk_time_to_start__,_) - Maximum time of walking in minutes required to reach the start/dest.
