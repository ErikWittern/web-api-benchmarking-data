# Web API Benchmarking Data

The here presented data (contained in `data.zip` reflects measured qualities for 15 Web API endpoints.
The collection and analysis of this data has been published in the research paper "Benchmarking Web API Quality", presented at the 2016 International Conference on Web Engineering (ICWE '16).

## Data description
The data has been collected over a period of 3 months, from August 20th, 2015 (16:00h CEST) until November 20th (16:00 CEST).
The data was collected for the following Web API endpoints:

|API name           | Ping | HTTP | HTTPS | URL                                                                                                                                                                                                                                                                 |
|-------------------|------|------|-------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Flickr             | X    | X    | X     | api.flickr.com/services/feeds/photos_public.gne                                                                                                                                                                                                                     |
|OpenWeatherMap     | X    | X    | -     | api.openweathermap.org/data/2.5/weather?q=New\%20York,us                                                                                                                                                                                                            |
|Postcodes.io       | X    | X    | X     | api.postcodes.io/postcodes/GU50BD                                                                                                                                                                                                                                   |
|ConsumerFinance    | X    | X    | X     | data.consumerfinance.gov/api/views/fphp-cr5a/rows.json                                                                                                                                                                                                              |
|Police.uk.co       | -    | X    | X     | data.police.uk/api/crimes-street-dates                                                                                                                                                                                                                              |
|Wikipedia          | X    | X    | X     | en.wikipedia.org/w/api.php?action=query\&titles=Albert_Einstein\&prop=images\&format=json                                                                                                                                                                           |
|Apple iTunes       | X    | X    | X     | itunes.apple.com/search?term=u2\&entity=musicVideo                                                                                                                                                                                                                  |
|Google Maps        | X    | X    | X     | maps.googleapis.com/maps/api/geocode/json?address=New\%20York\%20City\%20US\&sensor=false                                                                                                                                                                           |
|MusicBrainz        | X    | X    | X     | musicbrainz.org/ws/2/recording?query=\%22we\%20will\%20rock\%20you\%22\%20AND\%20arid:0383dadf-2a4e-4d10-a46a-e9e041da8eb3                                                                                                                                          |
|Yahoo              | X    | X    | X     | query.yahooapis.com/v1/public/yql?q=select\%20*\%20from\%20weather.forecast\%20where\%20woeid\%20in\%20(select\%20woeid\%20from\%20geo.places(1)\%20where\%20text\%3D\%22nome\%2C\%20ak\%22)\&format=json\&env=store\%3A\%2F\%2Fdatatables.org\%2Falltableswithkeys |
|Amazon S3          | -    | X    | X     | s3.amazonaws.com/1000genomes                                                                                                                                                                                                                                        |
|Twitter            | X    | X    | -     | urls.api.twitter.com/1/urls/count.json?url=http://www.tu-berlin.de                                                                                                                                                                                                  |
|Spotify            | X    | X    | X     | ws.spotify.com/search/1/album?q=u2                                                                                                                                                                                                                                  |
|BBC                | -    | X    | -     | www.bbc.co.uk/radio1/playlist.json                                                                                                                                                                                                                                  |
|Google Books       | X    | -    | X     | www.googleapis.com/books/v1/volumes?q=isbn:0321751043                                                                                                                                                                                                               |

The data has been collected from virtual machines running in the following geographic regions: EU (Ireland), US West (Oregon), South America (Sao Paulo), Asia (Singapore), Australia (Sydney), Tokyo, US East.
For every region, the data consists of 4 files:

* `httpget_output.csv` contains data about performing an HTTP GET request to each endpoint every 5 minutes. Per request, the timestamp, the HTTP status code, the latency in milliseconds, and the response size in byte are stated. 
* `httpgets_output.csv` contains data about performing an HTTPS GET request to each endpoint every 5 minutes. Per request, the timestamp, the HTTP status code, the latency in milliseconds, and the response size in byte are stated.
* `ping_output.csv` contains data about performing a ping request (using the ICMP protocol) to each endpoint every 5 minutes. Per request, the timestamp at the beginning and end of the request are contained. The pingability measure denotes how many of 5 subsequent ping requests succeeded. Finally, we provide the average latency across the 5 ping requests.
* `errors.log` contains logged error messages in case that HTTP or HTTPS GET requests failed. They can be correlated to the other HTTP and HTTPS request data by means of the invoked endpoint and the timestamp.


## Web API anonymization
The measured qualities of Web APIs are subject to various factors, like server outages, network partitionings, or client errors.
Not all of these factors lie under the control of the API provider.
Thus, in order to not suggest poor performance of specific providers, we chose to anonymize the data.
Correspondingly, APIs are randomly assigned with the names `api_1` to `api_15`.
Upon reasonable request, we will consider providing a mapping between the random names and the actual API endpoints.
Please contact us under (witternj@us.ibm.com)[mailto:witternj@us.ibm.com] or (david.bermbach@tu-berlin.de)[mailto:david.bermbach@tu-berlin.de].