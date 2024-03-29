# Stops

Get all stops. Active stops can be found on the client side using the `stops` array in each `route` object.

[`GET` http://mbus.pts.umich.edu/api/v0/stops/](http://mbus.pts.umich.edu/api/v0/stops/)

## Request Parameters

<table>
<th>Parameter</th>
<th>Type</th>
<th>Description</th>
<th>Default</th>
<th>Required</th>
<tr>
<td>callback</td>
<td>string</td>
<td>The callback to wrap a JSONP object in. Including this parameter will cause the API to return JSONP.</td>
<td>None (JSON response)</td>
<td>No</td>
</tr>
</table>

#### Example

[`GET` http://mbus.pts.umich.edu/api/v0/stops/?callback=process_stops](http://mbus.pts.umich.edu/api/v0/stops/?callback=process_stops)


## Response Fields

<table>
<th>Field</th>
<th>Description</th>
<tr>
<td>id</td>
<td>The stop ID</td>
</tr>
<tr>
<td>unique_name</td>
<td>A unique name describing the stop. Differentiates multiple stops at a single location (e.g. NW vs SE sides of Central Transit Center).</td>
</tr>
<tr>
<td>human_name</td>
<td>The colloquial name for the stop</td>
</tr>
<tr>
<td>additional_name</td>
<td>An optional additional name describing the stop</td>
</tr>
<tr>
<td>latitude</td>
<td>The latitude of the stop's location</td>
</tr>
<tr>
<td>longitude</td>
<td>The longitude of the stop's location</td>
</tr>
<tr>
<td>heading</td>
<td>The heading of the stop</td>
</tr>
</table>

#### Example

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
