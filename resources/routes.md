# Routes

This method returns the bus routes operated by Magic Bus.

[`GET http://mbus.pts.umich.edu/api/v0/routes/`](http://mbus.pts.umich.edu/api/v0/routes/)

## Request Parameters

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

## Response Fields

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

## Example Response

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
