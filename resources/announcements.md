# Announcements

Get all active announcements. These announcements will contain important information about service changes. It is recommended that these announcements are displayed to the user.

[`GET` http://mbus.pts.umich.edu/api/v0/announcements/](http://mbus.pts.umich.edu/api/v0/announcements/)

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
<tr>
<td>title</td>
<td>The title of the service announcement</td>
</tr>
<tr>
<td>text</td>
<td>The text of the announcement</td>
</tr>
<tr>
<td>color</td>
<td>The display color in hex of the announcement text. This value is obeyed on mbus.pts.umich.edu and it is recommended that you obey it as well.</td>
</tr>
<tr>
<td>type</td>
<td>The type of the announcement. Possible values include <code>"Status Update"</code> and <code>"Emergency Message"</code>.</td>
</tr>
</table>


## Example Response

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
