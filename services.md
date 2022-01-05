[<<Back to index](/)

## Services and events

HASL implements some services that can be useful for accessing data and using for automations or whatnot. Anyway; there are five services that can be used. They return data by triggering an event on the `hasl3_response` topic.

- `dump_cache` No arguments. Dumps the cache to a file in the Home Assistant configuration directory. Returns the filename of the created file in an event.
- `get_cache` No arguments. Returns the cache of the created file in an event.
- `find_location`: Arguments `api_key`, `search_string`. Returns the closest stop to the search string provided.
- `find_trip_id` Arguments `api_key`, `org`, `dest`. Returns a trip from org to dest.
- `find_trip_pos` Arguments `api_key`, `orig_lat`, `orig_long`, `dest_lat`, `dest_long`. Returns a trip from org to dest.