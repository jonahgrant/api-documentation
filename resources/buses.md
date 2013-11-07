# Buses

Get all buses which are currently in service.

[`GET` http://mbus.pts.umich.edu/api/v0/buses/](http://mbus.pts.umich.edu/api/v0/buses/)

#### Request Parameters

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

`"id"`: The ID of the bus  
`"latitude"`: The bus's current latitude  
`"longitude"`: The bus's current longitude  
`"heading"`: The bus's current heading  
`"route"`: The bus's current route

## Example Response

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
