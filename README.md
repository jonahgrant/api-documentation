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


## Format

### Requests

The API uses only RESTful HTTP GET methods. The standard format for a request is:
`GET http://mbus.pts.umich.edu/api/<version>/<resource>/`
Where:
* `<version>` is the API version you want to use. Currently `v0` is the only option.
* `<resource>` is the type of data you want to receive, such as `routes`, `buses`, `stops`, etc.

See below for specifics on each method.

### Responses

The API returns JSON-encoded objects with the 'Content-Type: application/json' header.

All requests are JSONP enabled. To use JSONP, append `callback=your_callback` to the query string of the request. For example, to retrieve a JSONP response with the routes data: `GET http://mbus.pts.umich.edu/api/v0/routes/?callback=process_routes`


## Resources

- **<code>GET</code>  /api/v0/announcements/**](https://github.com/magic-bus/api-documentation/blob/master/resources/announcements.md)
- **<code>GET</code>  /api/v0/arrivals/**](https://github.com/magic-bus/api-documentation/blob/master/resources/arrivals.md)
- **<code>GET</code>  /api/v0/buses/**](https://github.com/magic-bus/api-documentation/blob/master/resources/buses.md)
- **<code>GET</code>  /api/v0/routes/**](https://github.com/magic-bus/api-documentation/blob/master/resources/routes.md)
- **<code>GET</code>  /api/v0/stops/**](https://github.com/magic-bus/api-documentation/blob/master/resources/stops.md)


## Contributions

While designing the Magic Bus API and its documentation, we looked for help and inspiration from other well-designed APIs.

* [Kippt](https://github.com/kippt/api-documentation)
* [Tumblr](http://www.tumblr.com/docs/en/api/v2)

## Authors

[Thomas Lovett](http://tklovett.com/)