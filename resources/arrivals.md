# Arrivals

Get bus arrival times for each stop which is currently being serviced.

[`GET http://mbus.pts.umich.edu/api/v0/arrivals/`](http://mbus.pts.umich.edu/api/v0/arrivals/)

## Request Parameters

<table>
<th>Parameter</th>
<th>Type</th>
<th>Description</th>
<th>Default</th>
<th>Required</th>
</table>

## Response Fields

<table>
<th>Field</th>
<th>Description</th>
</table>

## Example Response

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
