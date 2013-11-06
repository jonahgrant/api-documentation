API v0 Documentation
====================

The Magic Bus API is available for non-commercial use by third-party developers. Commercial use is strictly prohibited.

Please note that this is an early development version of the API. This version is liable to break or change at any time,
so we do not recommended using it for any production purposes. Please [let us know](mailto:magicbus@umich.edu?subject=API Feedback) if you have any feedback.

The API:
* has no usage limits (unless you abuse it to the point that we have to implement them)
* is in development
* does not necessarily match this documentation. This documentation is being used as a specification during development, so not all functionality described here is necessarily implemented.

Known Issues which will be resolved before the v1 release:
* Does not include arrival times for each stop
* Does not pretty print by default
* Does not necessarily return accurate data

In the future:
* will require developers to register with their email to receive an authentication token. This will enable us to track usage and contact developers regarding update and deprecation schedules.
* will hopefully return gzip'd responses
* will possibly use CORS instead of JSONP

## Request Format

The API uses only RESTful HTTP GET methods. The standard format for a request is:
`GET http://mbus.pts.umich.edu/api/<version>/<resource>/`
Where:
* `<version>` is the API version you want to use. Currently `v0` is the only option.
* `<resource>` is the type of data you want to receive, such as `routes`, `buses`, `stops`, etc.

See below for specifics on each method.

## Response Format

The API returns JSON-encoded objects with the 'Content-Type: application/json' header.

All requests are JSONP enabled. To use JSONP, append `callback=your_callback` to the query string of the request. For example, to retrieve a JSONP response with the routes data: `GET http://mbus.pts.umich.edu/api/v0/routes/?callback=process_routes`

## Methods

### Routes

This method returns the bus routes operated by Magic Bus.

[`GET http://mbus.pts.umich.edu/api/v0/routes/`](http://mbus.pts.umich.edu/api/v0/routes/)

#### Request Parameters

<table>
<th>Parameter</th>
<th>Type</th>
<th>Description</th>
<th>Default</th>
<th>Required</th>
<tr>
<td>active</td><td>boolean (true/false)</td><td>Only return active routes</td><td>true</td><td>No</td>
</tr>
</table>

#### Response Fields

<table>
<th>Field</th>
<th>Description</th>
<tr>
<td>id</td><td>The unique route ID</td>
</tr>
<tr>
<td>name</td><td>The route name</td>
</tr>
<tr>
<td>color</td><td>The route color, used for text, route traces, and buses on the route. You must use this color for the user to be able to identify the route by sight. <em>Do not use a different color.</em></td>
</tr>
<tr>
<td>top_of_loop_stop_id</td><td>If this route is a loop, this is the ID of the stop which is at the top of the loop. This stop can be considered the start and end of the loop. If this route is not a loop, this value is `null`.</td>
</tr>
<tr>
<td>stops</td><td>The list of stop IDs for all the stops which this route services, in route order.  </td>
</tr>
</table>

#### Example Response

```json
{
   "response":[
      {
         "id":"0",
         "name":"Commuter Southbound",
         "color":"#0066FF",
         "stops":[
            "65",
            "58",
            "134",
            "58",
            "52",
            "53",
            "54",
            "55",
            "22",
            "81",
            "56",
            "10",
            "23",
            "24",
            "57",
            "49",
            "48",
            "1"
         ],
         "top_of_loop_stop_id":null
      },
      {
         "id":"3",
         "name":"Go Blue",
         "color":"#ff4523",
         "stops":[
         ],
         "top_of_loop_stop_id":null
      },
      {
         "id":"4",
         "name":"Bursley-Baits",
         "color":"#00532d",
         "stops":[
            "10",
            "42",
            "46",
            "15",
            "59",
            "43",
            "44",
            "45",
            "60",
            "61",
            "39",
            "52",
            "25",
            "56"
         ],
         "top_of_loop_stop_id":"7"
      }
   ]
}
```


### Stops

Get all stops. Active stops can be found on the client side using the `stops` array in each `route` object.  
[`GET http://mbus.pts.umich.edu/api/v0/stops/`](http://mbus.pts.umich.edu/api/v0/stops/)

#### Request Parameters

<table>
<th>Parameter</th>
<th>Type</th>
<th>Description</th>
<th>Default</th>
<th>Required</th>
</table>

#### Response Fields

<table>
<th>Field</th>
<th>Description</th>
</table>

`"id"`: The stop ID  
`"unique_name"`: A unique name describing the stop. Differentiates multiple stops at a single location (e.g. NW vs SE sides of Central Transit Center).  
`"human_name"`: The colloquial name for the stop  
`"additional_name"`: An optional additional name describing the stop  
`"latitude"`: The latitude of the stop's location  
`"longitude"`: The longitude of the stop's location  
`"heading"`: The heading of the stop  

#### Example Response

```json
{
   "response":[
      {
         "id":"10",
         "unique_name":"C.C. Little SE",
         "human_name":"Central Transit Center",
         "additional_name":"C.C. Little",
         "latitude":"42.27778",
         "longitude":"-83.73503",
         "heading":"135"
      },
      {
         "id":"51",
         "unique_name":"C.C. Little NW",
         "human_name":"Central Transit Center",
         "additional_name":"Ruthven Museum",
         "latitude":"42.27818197456284",
         "longitude":"-83.73513489961624",
         "heading":"315"
      },
      {
         "id":"39",
         "unique_name":"Murfin and Bonisteel S",
         "human_name":"Pierpont",
         "additional_name":"None",
         "latitude":"42.29063",
         "longitude":"-83.71858",
         "heading":"180"
      }
   ]
}
```

### Buses

Get all buses which are currently in service.

[`GET http://mbus.pts.umich.edu/api/v0/buses/`](http://mbus.pts.umich.edu/api/v0/buses/)

#### Request Parameters

<table>
<th>Parameter</th>
<th>Type</th>
<th>Description</th>
<th>Default</th>
<th>Required</th>
</table>

#### Response Fields

<table>
<th>Field</th>
<th>Description</th>
</table>

`"id"`: The ID of the bus  
`"latitude"`: The bus's current latitude  
`"longitude"`: The bus's current longitude  
`"heading"`: The bus's current heading  
`"route"`: The bus's current route

#### Example Response

```json
{
   "response":[
      {
         "id":"3",
         "latitude":"42.2704010009766",
         "longitude":"-83.7475433349609",
         "heading":"179",
         "route":"-3"
      },
      {
         "id":"4",
         "latitude":"42.2943649291992",
         "longitude":"-83.7111511230469",
         "heading":"0",
         "route":"-3"
      },
      {
         "id":"12",
         "latitude":"42.2670783996582",
         "longitude":"-83.7447738647461",
         "heading":"333",
         "route":"144"
      },
      {
         "id":"2",
         "latitude":"42.2904205322266",
         "longitude":"-83.7160797119141",
         "heading":"288",
         "route":"93"
      },
   ]
}
```

### Arrivals

Get bus arrival times for each stop which is currently being serviced.

[`GET http://mbus.pts.umich.edu/api/v0/arrivals/`](http://mbus.pts.umich.edu/api/v0/arrivals/)

#### Request Parameters

<table>
<th>Parameter</th>
<th>Type</th>
<th>Description</th>
<th>Default</th>
<th>Required</th>
</table>

#### Response Fields

<table>
<th>Field</th>
<th>Description</th>
</table>

#### Example Response

```json
{
   "response":[
      {
         "stop_id":"0",
         "arrivals":[
            {
               "route_id":"60",
               "next":"39.23",
               "second":"1496.90"
            },
            {
               "route_id":"70",
               "next":"1142.50",
               "second":"3402.47"
            }
         ]
      },
      {
         "stop_id":"1",
         "arrivals":[
            {
               "route_id":"60",
               "next":"39.23",
               "second":"1496.90"
            }
         ]
      },
   ]
}
```


### Announcements

Get all active announcements. These announcements will contain important information about service changes. It is recommended that these announcements are displayed to the user.

[`GET http://mbus.pts.umich.edu/api/v0/announcements/`](http://mbus.pts.umich.edu/api/v0/announcements/)

#### Request Parameters

<table>
<th>Parameter</th>
<th>Type</th>
<th>Description</th>
<th>Default</th>
<th>Required</th>
</table>

#### Response Fields

<table>
<th>Field</th>
<th>Description</th>
</table>

`"title"`: The title of the service announcement  
`"text"`: The text of the announcement  
`"color"`: The display color in hex of the announcement text. This value is obeyed on mbus.pts.umich.edu and it is recommended that you obey it as well.  
`"type"`: The type of the announcement. Possible values include `"Status Update"` and `"Emergency Message"`.  

#### Example Response

```json
{
   "response":[
      {
         "title":"CSSouthU",
         "text":"SERVICE ALERT--COMMUTER SOUTHBOUND DETOUR due to South University Ave. reconstruction. NO SERVICE TO: Art Museum stop.  TEMPORARY STOP: Located near Hutchins Hall on north side of Monroe St., east of State St.  EFFECTIVE UNTIL: 23-Aug-13. ",
         "color":"#FF3300",
         "type":"Status Update"
      },
      {
         "title":"NWWaterMainProj",
         "text":"SERVICE ALERT--NORTHWOOD DETOUR due to water main project. NO SERVICE TO: Cram Circle* or Bishop St.** stops.  SUBSTITUTE and TEMPORARY STOP: Located near Cram Circle on Hubbard St.* and near Bishop St. on Beal Ave**.  EFFECTIVE UNTIL: 20-Aug-13.",
         "color":"#990000",
         "type":"Status Update"
      }
   ]
}
```
